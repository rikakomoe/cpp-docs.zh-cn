---
title: 设置静态链接到的注册机构代码 （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
- statically linking to ATL Registrar code
- linking [C++], to ATL Registrar code
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
ms.openlocfilehash: 11600b47abbbd247d099d871fce5e9d5d17d3cf4
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327884"
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>设置静态链接到的注册机构代码 （c + +）

C + + 客户端可以创建注册机构的代码的静态链接。 静态链接的注册机构的分析器将大约 5 K 添加到发布版本。

若要设置静态链接的最简单方法假定已指定[DECLARE_REGISTRY_RESOURCEID](reference/registry-macros.md#declare_registry_resourceid)对象的声明中。 （这是 ATL 的使用的默认值规范）

## <a name="to-create-a-static-link-using-declareregistryresourceid"></a>若要创建使用 DECLARE_REGISTRY_RESOURCEID 的静态链接

1. 指定[/D](../build/reference/d-preprocessor-definitions.md)  **\_ATL\_静态\_注册表**而不是 **/D \_ATL\_DLL**。

1. 重新编译。

## <a name="see-also"></a>请参阅

[注册表组件 （注册器）](../atl/atl-registry-component-registrar.md)
