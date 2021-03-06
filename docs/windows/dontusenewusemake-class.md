---
title: DontUseNewUseMake 类
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
- implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
helpviewer_keywords:
- Microsoft::WRL::Details::DontUseNewUseMake class
- Microsoft::WRL::Details::DontUseNewUseMake::operator new operator
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
ms.openlocfilehash: f38833fa851030735dca34f16be9eaa9eb52069a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466750"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake 类

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
class DontUseNewUseMake;
```

## <a name="remarks"></a>备注

阻止使用运算符`new`在`RuntimeClass`。 因此，必须使用[使函数成为](../windows/make-function.md)相反。

## <a name="members"></a>成员

### <a name="public-operators"></a>公共运算符

名称                                             | 描述
------------------------------------------------ | ---------------------------------------------------------------------------
[Dontusenewusemake:: Operator 新](#operator-new) | 重载运算符`new`，并防止中正在使用`RuntimeClass`。

## <a name="inheritance-hierarchy"></a>继承层次结构

`DontUseNewUseMake`

## <a name="requirements"></a>要求

**标头：** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="operator-new"></a>Dontusenewusemake:: Operator 新

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
void* operator new(
   size_t,
   _In_ void* placement
);
```

### <a name="parameters"></a>参数

*__unnamed0*<br/>
一个未命名的参数，它指定要分配的内存字节数。

*放置*<br/>
要分配的类型。

### <a name="return-value"></a>返回值

提供了一种方法将传递其他参数，如果重载运算符`new`。

### <a name="remarks"></a>备注

重载运算符`new`，并防止中正在使用`RuntimeClass`。
