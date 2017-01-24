---
title: "typeid（C++ 组件扩展） | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "typeid 关键字 [C++]"
ms.assetid: e9706cae-e7c4-4d6d-b474-646d73df3e70
caps.latest.revision: 35
caps.handback.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# typeid（C++ 组件扩展）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

获取一个指示对象类型的值。  
  
> [!WARNING]
>  本主题引用 typeid 的 C\+\+ 组件扩展版本。  有关此关键字的ISO C\+\+版本，请参见[typeid 运算符](../cpp/typeid-operator.md)。  
  
## 所有运行时  
  
### 语法  
  
```cpp  
  
T::typeid  
```  
  
### 参数  
 *T*  
 类型名称。  
  
## Windows 运行时  
  
### 语法  
  
```cpp  
Platform::Type^ type = T::typeid;  
```  
  
### 参数  
 `T`  
 类型名称。  
  
### 备注  
 在 [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)] 中，typeid 返回根据运行时类型信息构造的 [Platform::Type](../Topic/Platform::Type%20Class.md)。  
  
### 要求  
 编译器选项：**\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **语法**  
  
```  
  
type::typeid  
```  
  
 **参数**  
  
 *type*  
 您想要的 System::Type 对象的类型名称（抽象声明符）。  
  
 **备注**  
  
 `typeid` 用于在编译时获取类型的 <xref:System.Type>。  
  
 `typeid` 类似于在运行时使用 <xref:System.Type.GetType%2A> 或 <xref:System.Object.GetType%2A> 获取类型的 System::Type。  但是，typeid 只接受作为参数的类型名称。如要使用类型实例以获取其 System::Type 名称，请使用 GetType。  
  
 `typeid` 必须能够在编译时评估类型名称（类型），而 GetType 将评估该类型是否在运行时返回。  
  
 `typeid` 可以采用本机类型名称或本机类型名称的公共语言运行时别名；有关更多信息，请参见 [对应于 C\+\+ 本机类型的 .NET Framework 类型](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)。  
  
 `typeid` 还适用于本机类型，不过它将返回 System::Type。要获取 type\_info 结构，请使用 [typeid 运算符](../cpp/typeid-operator.md)。  
  
 `typeid` 是上述 **\/clr** 语法的 [\_\_typeof](../misc/typeof.md) 后继。  
  
### 要求  
 编译器选项：**\/clr**  
  
### 示例  
 **示例**  
  
 以下示例将比较 typeid 关键字与 GetType\(\) 成员。  
  
```  
// keyword__typeid.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct G {  
   int i;  
};  
  
int main() {  
   G ^ pG = gcnew G;  
   Type ^ pType = pG->GetType();  
   Type ^ pType2 = G::typeid;  
  
   if (pType == pType2)  
      Console::WriteLine("typeid and GetType returned the same System::Type");  
   Console::WriteLine(G::typeid);  
  
   typedef float* FloatPtr;  
   Console::WriteLine(FloatPtr::typeid);  
}  
```  
  
 **Output**  
  
  **Typeid 和 GetType 返回相同的 System::Type**  
**G**  
 **System.Single\*** **示例**  
  
 以下示例说明了 System::Type 变量可用于获取在类型上的属性。对于某些类型，它还说明必须创建 typedef 以使用 `typeid`。  
  
```  
// keyword__typeid_2.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Security;  
using namespace System::Security::Permissions;  
  
typedef int ^ handle_to_int;  
typedef int * pointer_to_int;  
  
public ref class MyClass {};  
  
class MyClass2 {};  
  
[attribute(AttributeTargets::All)]  
ref class AtClass {  
public:  
   AtClass(Type ^) {  
      Console::WriteLine("in AtClass Type ^ constructor");  
   }  
};  
  
[attribute(AttributeTargets::All)]  
ref class AtClass2 {  
public:  
   AtClass2() {  
      Console::WriteLine("in AtClass2 constructor");  
   }  
};  
  
// Apply the AtClass and AtClass2 attributes to class B  
[AtClass(MyClass::typeid), AtClass2]     
[AttributeUsage(AttributeTargets::All)]  
ref class B : Attribute {};  
  
int main() {  
   Type ^ MyType = B::typeid;  
  
   Console::WriteLine(MyType->IsClass);  
  
   array<Object^>^ MyArray = MyType -> GetCustomAttributes(true);  
   for (int i = 0 ; i < MyArray->Length ; i++ )  
      Console::WriteLine(MyArray[i]);  
  
   if (int::typeid != pointer_to_int::typeid)  
      Console::WriteLine("int::typeid != pointer_to_int::typeid, as expected");  
  
   if (int::typeid == handle_to_int::typeid)  
      Console::WriteLine("int::typeid == handle_to_int::typeid, as expected");  
}  
```  
  
 **Output**  
  
  **True**  
 **在 AtClass2 构造函数中**  
 **在 AtClass 类型 ^ 构造函数中**  
 **AtClass2**  
 **System.AttributeUsageAttribute**  
 **AtClass**  
 **int::typeid\! \= pointer\_to\_int::typeid，按预期**  
 **int::typeid \=\= handle\_to\_int::typeid，按预期**   
## 请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)