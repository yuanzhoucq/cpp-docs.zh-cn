---
title: "String（C++ 组件扩展） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr 编译器选项 [C++], 字符串支持"
  - "使用 /clr 时的字符串支持"
ms.assetid: c695f965-9be0-4e20-9661-373bfee6557e
caps.latest.revision: 19
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# String（C++ 组件扩展）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+编译器支持*strings*，它是作为字符序列来代表文本的对象。  Visual C\+\+ 支持字符串变量，值是隐式的，和文本，值是一个显式引证字符串。  
  
## 所有运行时  
 Windows 运行时和公共语言运行时把字符串当作为其分配自动管理内存的对象。  也就是说，当运行变量超出范围或应用程序结束时，不需要显式放弃字符串的内存。  为了表明字符串对象的生命周期要被自动管理，用 [handle\-to\-object \(^\)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)修改器声明字符串类型。  
  
## Windows 运行时  
 Windows Runtime体系要求Visual C\+\+实现`Platform`命名空间中的`String`数据类型。  为了方便，Visual C\+\+在`default` 命名空间也提供`string`数据类型，这是 `Platform::String` 的同义词。  
  
### 语法  
  
```cpp  
  
// compile with /ZW  
using namespace Platform;  
using namespace default;  
   Platform::String^ MyString1 = "The quick brown fox";  
   String^ MyString2 = "jumped over the lazy dog.";  
   String^ MyString3 = "Hello, world!";  
  
```  
  
### 备注  
 有关字符串的更多信息和示例，请参见[Platform::String, std::wstring, and Literals \(Platform\)](http://msdn.microsoft.com/zh-cn/ec92fbc6-edf3-4137-a85e-8e29bdb857a8)。  
  
### 要求  
 编译器选项：**\/ZW**  
  
## 公共语言运行时  
 这个主题讨论了当你用**\/clr**编译器选项运行Visual C\+\+编译器，它是如何处理字符串文本的。  要使用**\/clr**，你必须使用common language runtime \(CLR\), C\+\+\/CLI 语法和被托管的对象。  有关 **\/clr**的更多信息，请参见[\/clr（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)。  
  
 当使用**\/clr**编译时，编译器会把字符串文本转化为<xref:System.String>类型的字符串。  若要用有两个异常的现有代码保留向后兼容性：  
  
-   异常处理  当字符串写入引发异常，编译器将捕捉为字符串文本。  
  
-   模板扣除。  当字符串文本被作为模板参数传递时，编译器将不会把它转化为<xref:System.String>。  注意，作为一个泛型参数被传递的字符串文本将被提升为<xref:System.String>。  
  
 编译器还具有对三种运算符的内置支持，可以重写自定义其行为：  
  
-   System::String ^ 运算符 \+ \(System::String，System::String\);  
  
-   System::String ^ 运算符 \+ \(System::Object，System::String\);  
  
-   System::String ^ 运算符 \+ \(System::String，System::Object\);  
  
 当传递一个<xref:System.String>时，编译器会装入，如果必要，然后用字符串链接对象（用ToString）。  
  
 当用**\/clr:oldSyntax**编译时，字符串文本不会被转化为<xref:System.String>。  
  
> [!NOTE]
>  插入符号 \(^ " "\) 指示已声明的变量是处理对 c. C\+\+\/CLI 托管对象。  
  
 有关更多信息，请参见[字符串和字符文本](../cpp/string-and-character-literals-cpp.md)。  
  
### 要求  
 编译器选项：**\/clr**  
  
### 示例  
 **示例**  
  
 下面的代码示例演示连接和比较字符串。  
  
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
  
 **Output**  
  
  **abcdef**  
 **abcghi**  
 **ghiabc**  
 **c**  
 **abcdefghi**  
 **abczzz**  
 **abc1**  
 **abc97**  
 **abc3.1**  
 **abcdef**  
 **a和b是相等的。**  
 **a和b是不相等的。**  
 **abc**  
 **n为空。** **示例**  
  
 下边的例子展示了你可以重载编译器提供的操作符，并且编译器可以找到一个基于<xref:System.String>类型的函数重载。  
  
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
  
 **Output**  
  
  **重载 \+ \(字符串 ^ 中，字符串 ^ b\)**  
 **重载 \+ \(字符串 ^ 中，对象 ^ b\)**  
 **重载 \+ \(对象 ^ 中，字符串 ^ b\)**  
 **字符串 ^ a**  
 **const char \* a** **示例**  
  
 下边的例子展示了编译器在本地字符串和<xref:System.String>之间进行区分。  
  
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
  
 **Output**  
  
  **char \***  
 **String^ str**  
 **System.SByte\***  
 **System.String**   
## 请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)   
 [字符串和字符文本](../cpp/string-and-character-literals-cpp.md)   
 [\/clr（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)