---
title: 装箱 (C++/CX)
ms.date: 12/30/2016
ms.assetid: edfb12fa-2a9b-42f6-bdac-d4d76cb8274e
ms.openlocfilehash: c680ea0262e8e65345cba40280a389453c2985bb
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519511"
---
# <a name="boxing-ccx"></a>装箱 (C++/CX)

 装箱就是当一个值类型变量（如 [Windows::Foundation::DateTime](https://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx)）或基础标量类型（如 `int`）传递给以 [Platform::Object^](../cppcx/platform-object-class.md) 作为其输入类型的方法时，将该变量或类型包装在一个 ref 类中的过程。

## <a name="passing-a-value-type-to-an-object-parameter"></a>将值类型传递给 Object^ 参数

虽然无需显式装箱变量以将该其传递给类型 [Platform::Object^](../cppcx/platform-object-class.md)的方法参数，但当你检索之前已装箱的值时，必须显式转换回原始类型。

[!code-cpp[cx_boxing#01](../cppcx/codesnippet/CPP/cx_boxing/class1.cpp#01)]

### <a name="using-platformiboxt-to-support-nullable-value-types"></a>使用 platform:: ibox\<T > 若要支持可以为 null 值类型

C# 和 Visual Basic 支持可以为 null 的值类型的概念。 在 C + + /CX 中，可以使用`Platform::IBox<T>`类型以公开支持可以为 null 的值类型参数的公共方法。 下面的示例演示 C + + /cli CX 公共方法，在 C# 调用方传递一个参数为 null 时返回 null。

[!code-cpp[cx_boxing#02](../cppcx/codesnippet/CPP/cx_boxing/class1.h#02)]

在 C# XAML 客户端中，可按以下方式使用它：

```

// C# client code
    BoxingDemo.Class1 obj = new BoxingDemo.Class1();
    int? a = null;
    int? b = 5;
    var result = obj.Multiply(a,b); //result = null
```

## <a name="see-also"></a>请参阅

[类型系统 (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[强制转换 (C++/CX)](../cppcx/casting-c-cx.md)<br/>
[Visual c + + 语言参考](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[命名空间参考](../cppcx/namespaces-reference-c-cx.md)