---
title: 在 （c + + COM 属性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.in
helpviewer_keywords:
- in attribute
ms.assetid: 7b450cc4-4d2e-4910-a195-7487c6b7c373
ms.openlocfilehash: bf23b1c776eccc284e5329b62bd45b0bd678823f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449694"
---
# <a name="in-c"></a>in (C++)

指示参数是要从调用过程传递给被调用过程。

## <a name="syntax"></a>语法

```cpp
[in]
```

## <a name="remarks"></a>备注

**中**c + + 属性具有相同的功能[中](/windows/desktop/Midl/in)MIDL 特性。

## <a name="example"></a>示例

请参阅[可绑定](bindable.md)有关如何使用的示例**中**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|接口参数，接口方法|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|**retval**|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[参数特性](parameter-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[id](id.md)<br/>
[out](out-cpp.md)