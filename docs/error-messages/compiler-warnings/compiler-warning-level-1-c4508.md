---
title: 编译器警告（等级 1）C4508
ms.date: 11/04/2016
f1_keywords:
- C4508
helpviewer_keywords:
- C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
ms.openlocfilehash: c96db3d4bd1124c96b22363531b7739d0757b613
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624007"
---
# <a name="compiler-warning-level-1-c4508"></a>编译器警告（等级 1）C4508

function： 函数应返回一个值;void 返回类型假定

该函数具有指定没有返回类型。 在这种情况下，也应激发 C4430 和编译器实现报告的 C4430 （默认值为 int） 的修复。

若要解决此警告，显式声明函数的返回类型。

下面的示例生成 C4508:

```
// C4508.cpp
// compile with: /W1 /c
#pragma warning (disable : 4430)
func() {}   // C4508
void func2() {}   // OK
```