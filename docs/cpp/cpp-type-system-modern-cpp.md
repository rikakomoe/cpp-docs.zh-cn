---
title: C++ 类型系统（现代 C++）
ms.date: 11/19/2018
ms.topic: conceptual
ms.assetid: 553c0ed6-77c4-43e9-87b1-c903eec53e80
ms.openlocfilehash: 476ebabc4bfc19f995119649d6f012d4b39d8369
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176336"
---
# <a name="c-type-system-modern-c"></a>C++ 类型系统（现代 C++）

*类型*的概念在 C++ 中非常重要。
变量、函数参数和函数返回值必须具有一个类型以进行编译。
此外，在计算表达式前，编译器会给出每个表达式（包括字面值）的隐式类型。
类型的一些示例包括用于存储整数值的 **int** ，用于存储浮点值（也称为*标量*数据类型）的 **double**，或用于存储文本的标准库类 [std::basic_string](../standard-library/basic-string-class.md)。
你可以通过定义**类**或**结构**来创建你自己的类型。该类型指定将分配给变量（或表达式结果）的内存量、可能存储在该变量中的值类型、
如何对那些值（作为位模式）进行解释以及可对其执行的操作。本文包含对 C++ 类型系统主要功能的非正式概述。

## <a name="terminology"></a>术语

**变量**：一些数据的符号化名称，可以在整个它被定义了的代码作用域中使用它来访问它指代的数据。
在 C++ 中，*变量*通常用于指代标量数据类型的实例，而其他类型的实例通常称为*对象*。

**对象**：为了简洁性和一致性，本文使用术语*对象*来指代任何类或结构的实例。同时当它作为一般意义的“对象”时，也可以是任何类型，包括标量变量。

**POD 类型**（纯旧数据）：这个非正式的 C++ 数据类型类别是指那些标量类型（参见基础类型章节）或*POD 类*。
POD 类没有不是 POD 的静态数据成员，没有用户定义的构造函数、用户定义的析构函数或用户定义的赋值运算符。
此外，POD 类无虚函数、基类、私有的或受保护的非静态数据成员。
POD 类型通常用于外部数据交换，例如与用 C 语言编写的模块（仅具有 POD 类型）进行的数据交换。

## <a name="specifying-variable-and-function-types"></a>指定变量和函数类型

C++ 是*强类型*语言，同时也是*静态类型语言*：每个对象都具有类型而且类型永远不会更改（不要与静态数据对象相混淆）。
**当你声明一个变量时**，你必须在代码中显式指定其类型或使用 **auto** 关键字指示编译器通过初始化式推断类型。
**当你声明一个函数时**，你必须在代码中指定每个参数和其返回值的类型，或 **void** 如果函数不返回任何值。例外的情况是，当使用允许任意类型参数的函数模板时。

在你首次声明变量后，你将无法在以后的某个点更改其类型。
但是，你可以将变量的值或函数的返回值复制到其他类型的另一个具有其他类型的变量中。
此类操作称为*类型转换*，这有时是必需的但有时也是数据丢失或错误的潜在来源。

在声明 POD 类型的变量时，强烈建议你将其初始化，也就是为其指定初始值。
在初始化某个变量之前，该变量会有一个“垃圾”值，该值包含之前正好位于该内存位置的那些位，无论是什么。
这是 C++ 需要注意的一个重要方面，尤其是如果你来自一种能够自动帮你处理初始化的语言。如果声明非 POD 类型的变量，则构造函数会处理初始化。

下面的示例演示了一些简单变量声明，并分别对它们进行了说明。该示例还演示了编译器如何使用类型信息允许或禁止对变量进行某些后续操作。

```cpp
int result = 0;              // Declare and initialize an integer.
double coefficient = 10.8;   // Declare and initialize a floating
                             // point value.
auto name = "Lady G.";       // Declare a variable and let compiler
                             // deduce the type.
auto address;                // error. Compiler cannot deduce a type
                             // without an initializing value.
age = 12;                    // error. Variable declaration must
                             // specify a type or use auto!
result = "Kenny G.";         // error. Can’t assign text to an int.
string result = "zero";      // error. Can’t redefine a variable with
                             // new type.
int maxValue;                // Not recommended! maxValue contains
                             // garbage bits until it is initialized.
```

## <a name="fundamental-built-in-types"></a>基本（内置）类型

不同于某些语言，C++ 中不存在派生所有其他类型的通用基类型。语言的 Visual C++ 实现包括许多*基本类型*，也称为*内置类型*。
这包括数值类型，如 **int**、**double**、**long**、**bool**，再加上 **char** 和 **wchar_t** 类型分别是 ASCII 和 UNICODE 字符。
大多数基本类型（除了 **bool**、**double**、**wchar_t** 和相关类型）都具有无符号版本，无符号版本的值范围和带符号版本有所区别。
例如，**int**，它存储 32 位带符号的整数可以表示介于 -2,147,483,648 到 2,147,483,647 的值。
**unsigned int**，也存储为 32 位，可以存储的值介于 0 和 4,294,967,295 之间。可能的值的总数在两个版本下都相同，只是范围不同。

基础类型由编译器识别，编译器包含内置规则，这些规则制约你可对它们执行的操作以及将它们转换为其他基础类型的方式。
有关内置类型及其大小和数值限制的完整列表，请参阅[基本类型](../cpp/fundamental-types-cpp.md)。

下图显示了内置类型的相对大小：

![内置类型的大小（字节）](../cpp/media/built-intypesizes.png)

下表列出了最常用的基础类型：

|类型|大小|注释|
|----------|----------|-------------|
|int|4 字节|整数值的默认选择。|
|double|8 字节|浮点值的默认选择。|
|bool|1 字节|表示可为 true 或 false 的值。|
|char|1 字节|用于早期 C 风格字符串或 std::string 对象中无需转换为 UNICODE 的 ASCII 字符。|
|wchar_t|2 字节|表示可能以 UNICODE 格式进行编码的“宽”字符值（Windows 上为 UTF-16，其他操作系统上可能不同）。这是用于 `std::wstring` 类型字符串的字符类型。|
|unsigned char|1 字节|C++ 没有内置的 `byte` 类型。使用 unsigned char 来表示字节值。|
|unsigned int|4 字节|位标志的默认选择。|
|long long|8 字节|表示非常大的整数值。|

## <a name="the-void-type"></a>void 类型

**void** 类型是一种特殊类型；你不能声明变量的类型为 **void**，但可以声明变量的类型为 __void \*__（**void** 指针）。
当你分配原始（非类型化）内存时，这么做有时是必要的。但是，**void** 指针不是类型安全的，通常在现代 C++ 中使用 **void** 指针是强烈不推荐的。
在函数声明中，**void** 返回值表示函数不返回值，这是 **void** 常见和可接受的用法。
尽管 C 语言要求具有零个参数的函数声明 **void** 在参数列表中，例如， `fou(void)`，这种做法在现代 C++ 中是不推荐的，应当声明为`fou()`。
有关详细信息，请参阅[类型转换和类型安全](../cpp/type-conversions-and-type-safety-modern-cpp.md)。

## <a name="const-type-qualifier"></a>const 类型限定符

任何内置或用户定义的类型都可由 const 关键字限定。此外，成员函数可被 **const** 限定甚至 **const** 重载。**const** 类型的值在初始化后无法修改。

```cpp

const double PI = 3.1415;
PI = .75 //Error. Cannot modify const variable.
```

**const** 限定符广泛应用于函数和变量声明。“const 正确性”是 C++ 中的重要概念；本质上它意味着使用 **const** 来在编译时确保值不会被无意中修改。
有关详细信息，请参阅 [const](../cpp/const-cpp.md)。

一个 **const** 类型是不同于其非常量版本的；例如，**const int** 是与 **int** 不同的类型。
你可以在那些极少数的必须从一个变量上移除其*常量性*的情况下使用 C++ **const_cast** 运算符。
有关详细信息，请参阅[类型转换和类型安全](../cpp/type-conversions-and-type-safety-modern-cpp.md)。

## <a name="string-types"></a>字符串类型

严格地说，C++ 语言不具有内置的字符串类型；**char** 和 **wchar_t** 存储单个字符——你必须声明一个这些变量类型的数组，
在数组最后一个元素的最后添加一个终止 null 值（例如，ASCII 的 `'\0'`），来近似字符串（也称为*C 风格字符串*）。
C 风格字符串要求你编写更多的代码或者使用外部字符串实用工具库函数。
但在现代 C++ 中，我们已经有标准库类型 `std::string`（用于 8 位 **char** 类型字符的字符串）或 `std::wstring`（用于 16 位 **wchar_t** 类型字符的字符串）。
这些 C++ 标准库容器可以被视为原生字符串类型，因为它们是 C++ 标准库的一部分，包含在任何兼容 C++ 的构建环境中。
只需使用 `#include <string>` 指令即可使这些类型在你的程序中可用。（如果使用的是 MFC 或 ATL，还可使用 CString 类，但它不是 C++ 标准的一部分。）
使用 null 终止的字符数组（前面提到的 C 风格字符串）在现代 C++ 中是强烈不推荐的。

## <a name="user-defined-types"></a>用户定义的类型

如果你定义了一个 **类**，**结构**，**联合体**，或者**枚举**，其构造可以应用在你代码的其余部分中，就像是一种基本类型。
它具有已知的内存大小，以及可以用于编译时检查和运行时，整个程序生命期内的规则。
基本内置类型和用户定义的类型之间的主要区别如下：

- 编译器没有用户定义的类型的内置知识。它在编译过程中第一次遇到该类型的定义时了解这个类型。

- 通过定义（通过重载）适当的运算符作为类成员或非成员函数，你可以指定对你的类型可执行的操作以及你的类型转换为其他类型的方式。有关详细信息，请参阅[函数重载](function-overloading.md)。

- 不必将它们静态类型化（对象类型的规则从不改变）。通过*继承*和*多态*机制，声明为用户定义类型的类的变量（称为类的对象实例）可能会在运行时具有和编译时不同的类型。 有关详细信息，请参阅[继承](../cpp/inheritance-cpp.md)。

## <a name="pointer-types"></a>指针类型

C++ 仍然允许使用特殊声明符 `*`（星号）来声明指针类型的变量，此功能可以追溯到 C 语言的最早版本。指针类型存储实际数据值在内存中存储时的位置所对应的地址。
在现代 C++ 中，这些指针称为*裸指针*，可以在代码中通过特殊运算符 `*`（星号）或 `->`（短划线加大于号）进行访问。这称为*解引用*。
使用哪一种符号取决于你是解引用标量的指针还是解引用对象中成员的指针。使用指针类型长期以来都是 C 和 C++ 程序开发过程中最具挑战性和最难以理解的内容之一。
本部分概述了一些事实和实践来帮助那些希望使用裸指针的用户。
但在现代 C++ 中，随着[智能指针](../cpp/smart-pointers-modern-cpp.md)（在本节末尾有详细讨论）的发展，已经不再需要使用裸指针来表示对象所有权（也不建议这样做）。
使用裸指针来观察对象仍是有用且安全的，但如果必须将其用于对象所有权，你应当谨慎操作并仔细考虑其所拥有的对象是如何被创建和销毁的。

首先你应该知道的是，声明一个裸指针变量只会分配存储了解引用时所需的内存地址的内存。数据值本身的内存（也称为*后备存储*）尚未分配。
换言之，通过声明裸指针变量，将创建内存地址变量而非实际数据变量。在确保指针变量指向有效后备存储的地址前解引用将导致程序发生未定义行为（通常为致命错误）。
下面的示例演示了此种错误：

```cpp
int* pNumber;       // Declare a pointer-to-int variable.
*pNumber = 10;      // error. Although this may compile, it is
                    // a serious error. We are dereferencing an
                    // uninitialized pointer variable with no
                    // allocated memory to point to.
```

该示例解引用指针类型，但尚未分配用于存储实际整数数据的任何内存或向其分配有效内存地址。下面的代码更正这些错误：

```cpp
    int number = 10;          // Declare and initialize a local integer
                              // variable for data backing store.
    int* pNumber = &number;   // Declare and initialize a local integer
                              // pointer variable to a valid memory
                              // address to that backing store.
...
    *pNumber = 41;            // Dereference and store a new value in
                              // the memory pointed to by
                              // pNumber, the integer variable called
                              // "number". Note "number" was changed, not
                              // "pNumber".
```

已纠正的代码示例使用本地栈内存创建 `pNumber` 指向的后备存储。我们为了简洁使用了一个基本类型。
在实践中，指针的后备存储通常是在一块称为*堆*（或*自由存储*）的内存中的用户自定义类型，通过 **new** 关键字表达式（在 C 风格编程中，使用较旧的 `malloc()` C 运行库函数）动态分配。
分配后，这些变量通常称为对象，尤其是如果它们是基于一个类定义的。
使用 **new** 分配的内存必须被相应的 **delete** 语句释放（或者，如果你使用 `malloc()` 函数分配它，使用 C 运行时函数 `free()` 来释放)。

但是，很容易忘记 delete 一个动态分配的对象——尤其是在复杂代码中，这会导致一个资源 bug 叫做*内存泄漏*。因此裸指针在现代 C++ 中是强烈不推荐的。
将裸指针包装在[智能指针](../cpp/smart-pointers-modern-cpp.md)中几乎始终是更好的做法，这将在其析构函数被调用时（当代码超出智能指针的范围）自动释放内存；
使用智能指针你几乎消除了一大类 C++ 程序中的 bug。在下面的示例中，假定 `MyClass` 是具有公共方法 `DoSomeWork();` 的用户定义的类型

```cpp
void someFunction() {
    unique_ptr<MyClass> pMc(new MyClass);
    pMc->DoSomeWork();
}
  // No memory leak. Out-of-scope automatically calls the destructor
  // for the unique_ptr, freeing the resource.
```

有关智能指针的详细信息，请参阅[智能指针](../cpp/smart-pointers-modern-cpp.md)。

有关指针转换的详细信息，请参阅[类型转换和类型安全](../cpp/type-conversions-and-type-safety-modern-cpp.md)。

有关指针更全面的详细信息，请参阅[指针](../cpp/pointers-cpp.md)。

## <a name="windows-data-types"></a>Windows 数据类型

在经典 Win32 C 和 C++ 编程中，大多数函数使用 Windows 特定的 typedef 和 #define 宏（在 `windef.h` 中定义）来指定参数类型和返回值。
这些 Windows 数据类型通常是只是 C/C++ 内置类型的特殊名称（别名）。
有关这些 typedef 和预处理器定义的完整列表，请参阅 [Windows 数据类型](/windows/desktop/WinProg/windows-data-types)。
这些 typedef 中的一些（例如 HRESULT 和 LCID），有用且具有描述性。其他的一些（例如 INT ），没有特殊含义，只是 C++ 基础类型的别名。
其他 Windows 数据类型的名称保留自 C 编程和 16 位处理器的时代，在现代硬件或操作系统中不再具有目的和意义。
也有特殊的数据类型与 Windows 运行时库有关，列出在[Windows 运行时的基本数据类型](/windows/desktop/WinRT/base-data-types)。
在现代 C++ 中，一般准则是首选 C++ 基本类型，除非 Windows 类型传达一些有关如何解释值的附加意义。

## <a name="more-information"></a>详细信息

有关 C++ 类型系统的更多信息，请参见下列主题。

|||
|-|-|
|[值类型](../cpp/value-types-modern-cpp.md)|介绍*值类型*以及与其使用相关的问题。|
|[类型转换和类型安全](../cpp/type-conversions-and-type-safety-modern-cpp.md)|描述常见类型转换问题并说明如何避免这些问题出现。|

## <a name="see-also"></a>请参阅

[欢迎回到 C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[C++ 标准库](../standard-library/cpp-standard-library-reference.md)
