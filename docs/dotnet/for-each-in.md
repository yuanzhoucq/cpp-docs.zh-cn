---
title: for each, in
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::foreach
- for
- each
- in
helpviewer_keywords:
- for each keyword [C++]
ms.assetid: 0c3a364b-2747-43f3-bb8d-b7d3b7023f79
ms.openlocfilehash: f1f5523eb22bd8a839da9b3f73dd6c3718b4fd63
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825782"
---
# <a name="for-each-in"></a>for each, in

通过数组或集合迭代。 此非标准关键字在 C++/CLI 和本机 C++ 项目中可用。 但是，建议不使用它。 请考虑改用标准[的基于范围的 For 语句（c + +）](../cpp/range-based-for-statement-cpp.md) 。

## <a name="all-runtimes"></a>所有运行时

### <a name="syntax"></a>语法

> **对于每个（** *表达式***中**的*类型**标识符* **） {**\
> &nbsp;&nbsp;&nbsp;&nbsp;*前瞻性*\
> **}**

### <a name="parameters"></a>参数

*type*<br/>
`identifier` 的类型。

*标识符 (identifier)*<br/>
代表集合元素的迭代变量。  当`identifier`是[跟踪引用运算符](../extensions/tracking-reference-operator-cpp-component-extensions.md)时，可以修改元素。

*expression*<br/>
数组表达式或集合。 集合元素必须让编译器能将其转换为 `identifier` 类型。

*前瞻性*<br/>
要执行的一个或多个语句。

### <a name="remarks"></a>备注

`for each` 语句用于循环访问集合。 可修改集合中的元素，但无法添加或删除元素。

对数组或集合中的每个元素执行这些*语句*。 为集合中的所有元素完成迭代后，控制将传递给 `for each` 块之后的语句。

`for each`和`in`是[上下文相关的关键字](../extensions/context-sensitive-keywords-cpp-component-extensions.md)。

参考信息：

- [使用 for each 循环访问 C++ 标准库集合](../dotnet/iterating-over-stl-collection-by-using-for-each.md)

- [如何：使用 for each 循环访问数组](../dotnet/how-to-iterate-over-arrays-with-for-each.md)

- [如何：使用 for each 循环访问泛型集合](../dotnet/how-to-iterate-over-a-generic-collection-with-for-each.md)

- [如何：使用 for each 循环访问用户定义集合](../dotnet/how-to-iterate-over-a-user-defined-collection-with-for-each.md)

## <a name="windows-runtime"></a>Windows 运行时

### <a name="requirements"></a>要求

编译器选项： **/ZW**

### <a name="example"></a>示例

本示例演示了如何使用 `for each` 来循环访问字符串。

```cpp
// for_each_string1.cpp
// compile with: /ZW
#include <stdio.h>
using namespace Platform;

ref struct MyClass {
   property String^ MyStringProperty;
};

int main() {
   String^ MyString = ref new String("abcd");

   for each ( char c in MyString )
      wprintf("%c", c);

   wprintf("/n");

   MyClass^ x = ref new MyClass();
   x->MyStringProperty = "Testing";

   for each( char c in x->MyStringProperty )
      wprintf("%c", c);
}
```

**输出**

```Output
abcd

Testing
```

## <a name="common-language-runtime"></a>公共语言运行时

**备注**

CLR 语法与**所有运行时**语法相同，但以下情况除外。

*expression*<br/>
托管的数组表达式或集合。 集合元素必须是，以便编译器可以将其转换<xref:System.Object>为*标识符*类型。

*expression* <xref:System.Collections.IEnumerable>的计算结果为实现、 <xref:System.Collections.Generic.IEnumerable%601>的类型，或定义`GetEnumerator`方法的类型，该方法返回实现<xref:System.Collections.IEnumerator>或声明中`IEnumerator`定义的所有方法的类型。

### <a name="requirements"></a>要求

编译器选项： **/clr**

### <a name="example"></a>示例

本示例演示了如何使用 `for each` 来循环访问字符串。

```cpp
// for_each_string2.cpp
// compile with: /clr
using namespace System;

ref struct MyClass {
   property String ^ MyStringProperty;
};

int main() {
   String ^ MyString = gcnew String("abcd");

   for each ( Char c in MyString )
      Console::Write(c);

   Console::WriteLine();

   MyClass ^ x = gcnew MyClass();
   x->MyStringProperty = "Testing";

   for each( Char c in x->MyStringProperty )
      Console::Write(c);
}
```

**输出**

```Output
abcd

Testing
```

## <a name="see-also"></a>另请参阅

[适用于运行时平台的组件扩展](../extensions/component-extensions-for-runtime-platforms.md)
