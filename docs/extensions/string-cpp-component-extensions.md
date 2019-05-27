---
title: String（C++/CLI 和 C++/CX）
ms.date: 10/08/2018
ms.topic: reference
helpviewer_keywords:
- string support with /clr
- /clr compiler option [C++], string support
ms.assetid: c695f965-9be0-4e20-9661-373bfee6557e
ms.openlocfilehash: 8440ddf510f99618c28a6b6d585c8628df85f9cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516022"
---
# <a name="string--ccli-and-ccx"></a>String（C++/CLI 和 C++/CX）

Windows 运行时和公共语言运行时将字符串表示为，已分配内存受自动管理的对象。 也就是说，当字符串变量超出范围或应用程序结束时，不必显式放弃字符串的内存。 若要指明字符串对象的生存期受自动管理，请使用[指向对象的句柄 (^)](handle-to-object-operator-hat-cpp-component-extensions.md) 修饰符来声明字符串类型。

## <a name="windows-runtime"></a>Windows 运行时

Windows 运行时体系结构要求，`String` 数据类型必须位于 `Platform` 命名空间中。 为了方便起见，Visual C++ 还在 `default` 命名空间中提供了 `string` 数据类型（它是 `Platform::String` 的同义词）。

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

当你使用 `/clr` 进行编译时，编译器会将字符串文字转换为 <xref:System.String> 类型的字符串。 为了保持与现有代码的向后兼容性，有两个例外情况：

- 异常处理。 编译器会将抛出的字符串文字捕获为字符串文字。

- 模板推导。 编译器不会将作为模板参数传递的字符串文字转换为 <xref:System.String>。 请注意，作为泛型参数传递的字符串文字将被提升为 <xref:System.String>。

编译器还内置了对三个运算符的支持，可以通过重写它们来自定义行为：

- System::String^ 运算符 +( System::String, System::String)；

- System::String^ 运算符 +( System::Object, System::String)；

- System::String^ 运算符 +( System::String, System::Object)；

如果传递的是 <xref:System.String>，编译器会根据需要进行装箱，然后将对象（包含 ToString）与字符串连接起来。

> [!NOTE]
> 脱字号（“^”）指明，声明的变量是指向 C++/CLI 托管对象的句柄。

有关详细信息，请参阅[字符串文字和字符文字](../cpp/string-and-character-literals-cpp.md)。

### <a name="requirements"></a>要求

编译器选项： **/clr**

### <a name="examples"></a>示例

下面的代码示例展示了如何连接和比较字符串。

```cpp
// string_operators.cpp
// compile with: /clr
// In the following code, the caret ("^") indicates that the
// declared variable is a handle to a C++/CLI managed object.
using namespace System;

int main() {
   String^ a = gcnew String("abc");
   String^ b = "def";   // same as gcnew form
   Object^ c = gcnew String("ghi");

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

   // you can append to a System::String^
   Console::WriteLine(a + 1);
   Console::WriteLine(a + 'a');
   Console::WriteLine(a + 3.1);

   // test System::String^ for equality
   a += b;
   Console::WriteLine(a);
   a = b;
   if (a == b)
      Console::WriteLine("a and b are equal");

   a = "abc";
   if (a != b)
      Console::WriteLine("a and b are not equal");

   // System:String^ and tracking reference
   String^% rstr1 = a;
   Console::WriteLine(rstr1);

   // testing an empty System::String^
   String^ n;
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

下面的示例展示了可以重载编译器提供的运算符，编译器会根据 <xref:System.String> 类型查找函数重载。

```cpp
// string_operators_2.cpp
// compile with: /clr
using namespace System;

// a string^ overload will be favored when calling with a String
void Test_Overload(const char * a) {
   Console::WriteLine("const char * a");
}
void Test_Overload(String^ a) {
   Console::WriteLine("String^ a");
}

// overload will be called instead of compiler defined operator
String^ operator +(String^ a, String^ b) {
   return ("overloaded +(String^ a, String^ b)");
}

// overload will be called instead of compiler defined operator
String^ operator +(Object^ a, String^ b) {
   return ("overloaded +(Object^ a, String^ b)");
}

// overload will be called instead of compiler defined operator
String^ operator +(String^ a, Object^ b) {
   return ("overloaded +(String^ a, Object^ b)");
}

int main() {
   String^ a = gcnew String("abc");
   String^ b = "def";   // same as gcnew form
   Object^ c = gcnew String("ghi");

   char d[100] = "abc";

   Console::WriteLine(a + b);
   Console::WriteLine(a + c);
   Console::WriteLine(c + a);

   Test_Overload("hello");
   Test_Overload(d);
}
```

```Output
overloaded +(String^ a, String^ b)

overloaded +(String^ a, Object^ b)

overloaded +(Object^ a, String^ b)

String^ a

const char * a
```

下面的示例展示了编译器区分本机字符串和 <xref:System.String> 字符串。

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

[ .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)<br/>
[字符串和字符文本](../cpp/string-and-character-literals-cpp.md)<br/>
[/cgthreads（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)