---
title: 数学错误 M6111
ms.date: 11/04/2016
f1_keywords:
- M6111
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
ms.openlocfilehash: 44f406881d64d13e23ca2c0911ee278c864a2c11
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50510781"
---
# <a name="math-error-m6111"></a>数学错误 M6111

堆栈下溢

浮点运算导致堆栈下溢 8087/287/387 协处理器或仿真程序上。

此错误通常通过调用引起`long double`不返回值的函数。 例如，以下生成此错误在编译和运行：

```
long double ld() {};
main ()
{
  ld();
}
```

程序终止，退出代码为 139。