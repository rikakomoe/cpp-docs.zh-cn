---
title: 优点和缺点的链接到 CRT 所使用的方法
ms.date: 11/04/2016
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 49b485f7-9487-49e4-b12a-0f710b620e2b
ms.openlocfilehash: b4c91b7fe5182c8457d16de57792ba1b5ab7b3be
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496975"
---
# <a name="benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt"></a>优点和缺点的链接到 CRT 所使用的方法

你的项目可以链接的 CRT 动态或静态。 下表概述了的优点和缺点参与选择要使用的方法。

|方法|好处|权衡|
|------------|-------------|--------------|
|以静态方式链接到 CRT<br /><br /> (**运行时库**设置为**单线程**)|图像将在其中运行的系统上不需要 CRT DLL。|大约 25 K 的启动代码添加到你的映像会显著增加其大小。|
|动态链接到 CRT<br /><br /> (**运行时库**设置为**多线程**)|你的映像不需要 CRT 启动代码，因此要小得多。|CRT DLL 必须位于运行该映像的系统上。|

本主题[将链接到 ATL 项目中的 CRT](../atl/linking-to-the-crt-in-your-atl-project.md)讨论如何选择要链接到 CRT 的方式。

## <a name="see-also"></a>请参阅

[使用 ATL 和 C 运行时代码进行编程](../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[DLL 和 Visual C++ 运行时库行为](../build/run-time-library-behavior.md)<br/>
[CRT 库功能](../c-runtime-library/crt-library-features.md)

