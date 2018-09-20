---
title: 字符串 （c + + 组件扩展） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- string support with /clr
- /clr compiler option [C++], string support
ms.assetid: c695f965-9be0-4e20-9661-373bfee6557e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2d6b6ce066c84056997ec9b54c9d74e782064df4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408396"
---
# <a name="string--c-component-extensions"></a>String（C++ 组件扩展）

Visual c + + 编译器支持*字符串*，这是对象，表示为一系列字符的文本。 Visual c + + 支持字符串变量，其值是隐式和原义字符，其值是显式带引号的字符串。

## <a name="all-runtimes"></a>所有运行时

Windows 运行时和公共语言运行时表示为自动管理其已分配的内存对象的字符串。 也就是说，不需要显式放弃字符串的内存，字符串变量超出范围或你的应用程序结束时。 若要指示字符串对象的生存期是自动管理，声明类型字符串[句柄到对象 (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)修饰符。

## <a name="windows-runtime"></a>Windows 运行时

Windows 运行时体系结构需要 Visual c + + 实现`String`中的数据类型`Platform`命名空间。 为方便起见，还提供 Visual c + +`string`数据类型，即的同义词`Platform::String`，请在`default`命名空间。

### <a name="syntax"></a>语法

```cpp
// compile with /ZW
using namespace Platform;
using namespace default;
   Platform::String^ MyString1 = "The quick brown fox";
   String^ MyString2 = "jumped over the lazy dog.";
   String^ MyString3 = "Hello, world!";
```

### <a name="requirements"></a>要求

编译器选项：`/ZW`

## <a name="common-language-runtime"></a>公共语言运行时

本主题讨论使用运行时，Visual c + + 编译器如何处理字符串文本`/clr`编译器选项。 若要使用`/clr`，还必须使用公共语言运行时 (CLR) 中 C + + /cli 语法和托管对象。 有关详细信息`/clr`，请参阅[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)。

使用编译时`/clr`，编译器会将字符串文字转换为字符串类型的<xref:System.String>。 若要保留与现有代码存在向后的兼容性是两个例外情况：

- 异常处理。 当引发字符串文字时，编译器将捕获它作为字符串文字。

- 模板推导。 当字符串文字作为模板参数传递时，编译器将不将其转换为<xref:System.String>。 请注意，作为泛型自变量传递的字符串文字将提升为<xref:System.String>。

编译器还具有对三个运算符，可以重写自定义其行为的内置支持：

- System:: string ^ 运算符 + （system:: string、 system:: string）

- System:: string ^ 运算符 + (system:: object，system:: string);

- System:: string ^ 运算符 + (system:: string，system:: object);

当传递<xref:System.String>，编译器将框中，如有必要，，然后执行连接字符串 （具有 ToString) 的对象。

> [!NOTE]
> 将插入符号 ("^") 指示声明的变量的句柄的 C + + /cli CLI 托管对象。

有关详细信息请参阅[字符串和字符文本](../cpp/string-and-character-literals-cpp.md)。

### <a name="requirements"></a>要求

编译器选项： **/clr**

### <a name="examples"></a>示例

下面的代码示例演示连接在一起和比较字符串。

```cpp
// string_operators.cpp
// compile with: /clr
// In the following code, the caret ("^") indicates that the
// declared variable is a handle to a C++/CLI managed object.
using namespace System;

int main() {
   String ^ a = gcnew String("abc");
   String ^ b = "def";   // same as gcnew form
   Object ^ c = gcnew String("ghi");

   char d[100] = "abc";

   // variables of System::String returning a System::String
   Console::WriteLine(a + b);
   Console::WriteLine(a + c);
   Console::WriteLine(c + a);

   // accessing a character in the string
   Console::WriteLine(a[2]);

   // concatenation of three System::Strings
   Console::WriteLine(a + b + c);

   // concatenation of a System::String and string literal
   Console::WriteLine(a + "zzz");

   // you can append to a System::String ^
   Console::WriteLine(a + 1);
   Console::WriteLine(a + 'a');
   Console::WriteLine(a + 3.1);

   // test System::String ^ for equality
   a += b;
   Console::WriteLine(a);
   a = b;
   if (a == b)  
      Console::WriteLine("a and b are equal");

   a = "abc";
   if (a != b)  
      Console::WriteLine("a and b are not equal");

   // System:String ^ and tracking reference
   String^% rstr1 = a;
   Console::WriteLine(rstr1);

   // testing an empty System::String ^
   String ^ n;
   if (n == nullptr)  
      Console::WriteLine("n is empty");
}
```

```Output
abcdef

abcghi

ghiabc

c

abcdefghi

abczzz

abc1

abc97

abc3.1

abcdef

a and b are equal

a and b are not equal

abc

n is empty
```

下面的示例演示您可以重载编译器提供的运算符，编译器会找到基于了函数重载<xref:System.String>类型。

```cpp
// string_operators_2.cpp
// compile with: /clr
using namespace System;

// a string^ overload will be favored when calling with a String
void Test_Overload(const char * a) {
   Console::WriteLine("const char * a");
}
void Test_Overload(String ^ a) {
   Console::WriteLine("String ^ a");
}

// overload will be called instead of compiler defined operator
String ^ operator +(String ^ a, String ^ b) {
   return ("overloaded +(String ^ a, String ^ b)");
}

// overload will be called instead of compiler defined operator
String ^ operator +(Object ^ a, String ^ b) {
   return ("overloaded +(Object ^ a, String ^ b)");
}

// overload will be called instead of compiler defined operator
String ^ operator +(String ^ a, Object ^ b) {
   return ("overloaded +(String ^ a, Object ^ b)");
}

int main() {
   String ^ a = gcnew String("abc");
   String ^ b = "def";   // same as gcnew form
   Object ^ c = gcnew String("ghi");

   char d[100] = "abc";

   Console::WriteLine(a + b);
   Console::WriteLine(a + c);
   Console::WriteLine(c + a);

   Test_Overload("hello");
   Test_Overload(d);
}
```

```Output
overloaded +(String ^ a, String ^ b)

overloaded +(String ^ a, Object ^ b)

overloaded +(Object ^ a, String ^ b)

String ^ a

const char * a
```

下面的示例演示编译器区分本机字符串和<xref:System.String>字符串。

```cpp
// string_operators_3.cpp
// compile with: /clr
using namespace System;
int func() {
   throw "simple string";   // const char *  
};

int func2() {
   throw "string" + "string";   // returns System::String
};

template<typename T>
void func3(T t) {
   Console::WriteLine(T::typeid);
}

int main() {
   try {
      func();
   }
   catch(char * e) {
      Console::WriteLine("char *");
   }

   try {
      func2();
   }
   catch(String^ str) {
      Console::WriteLine("String^ str");
   }

   func3("string");   // const char *  
   func3("string" + "string");   // returns System::String
}
```

```Output
char *

String^ str

System.SByte*

System.String
```

## <a name="see-also"></a>请参阅

[适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)<br/>
[字符串和字符文本](../cpp/string-and-character-literals-cpp.md)<br/>
[/cgthreads（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)