---
title: "safe_cast（C++ 组件扩展） | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "safe_cast"
  - "safe_cast_cpp"
  - "stdcli::language::safe_cast"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "safe_cast 关键字 [C++]"
ms.assetid: 4fa688bf-a8ec-49bc-a4c5-f48134efa4f7
caps.latest.revision: 26
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# safe_cast（C++ 组件扩展）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果成功，则 `safe_cast` 操作以指定类型的形式返回指定表达式；否则引发 `InvalidCastException`。  
  
## 所有运行时  
 （此语言功能没有适用于所有运行时的备注。）  
  
### 语法  
  
```cpp  
  
[default]:: safe_cast<  
type-id  
>(  
expression  
)  
  
```  
  
### 参数  
  
### 备注  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 `safe_cast` 允许你更改指定表达式的类型。  在完全可预期变量或参数会转换为特定类型的情况下，可以使用不带 try\-catch 块的 safe\_cast 在开发过程中检测编程错误。  有关详细信息，请参阅[强制转换 \(C\+\+\/CX\)](http://msdn.microsoft.com/library/windows/apps/hh755802.aspx)。  
  
### 语法  
  
```cpp  
  
[default]:: safe_cast<  
type-id  
>(  
expression  
)  
  
```  
  
### 参数  
 *type\-id*  
 要将 *expression* 转换为的类型。  引用或值类型的句柄、值类型或是对引用或值类型的跟踪引用。  
  
 *expression*  
 一个表达式，计算结果是引用或值类型的句柄、值类型或是对引用或值类型的跟踪引用。  
  
### 备注  
 如果不能将 *expression* 转换为 *type\-id* 指定的类型，`safe_cast` 将引发 `InvalidCastException`。  若要捕获 `InvalidCastException`，请指定 [\/EH（异常处理模型）](../build/reference/eh-exception-handling-model.md) 编译器选项，并使用 try\/catch 语句。  
  
### 要求  
 编译器选项：**\/ZW**  
  
### 示例  
 **示例**  
  
 下面的代码示例演示如何将 `safe_cast` 与 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 一起使用。  
  
```cpp#  
// safe_cast_ZW.cpp  
// compile with: /ZW /EHsc  
  
using namespace default;  
using namespace Platform;  
  
interface class I1 {};  
interface class I2 {};  
interface class I3 {};  
  
ref class X : public I1, public I2 {};  
  
int main(Array<String^>^ args) {  
   I1^ i1 = ref new X;  
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X  
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead  
   try {  
      I3^ i4 = safe_cast<I3^>(i1);   // Fails because i1 is not derived from I3.  
   }   
   catch(InvalidCastException^ ic) {  
     wprintf(L"Caught expected exception: %s\n", ic->Message);  
   }  
}  
```  
  
 **输出**  
  
  **捕获预期异常：InvalidCastException**   
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 `safe_cast` 允许更改表达式的类型并生成可验证的 MSIL 代码。  
  
### 语法  
  
```cpp  
  
[cli]:: safe_cast<  
type-id  
>(  
expression  
)  
  
```  
  
### 参数  
 *type\-id*  
 引用或值类型的句柄、值类型或是对引用或值类型的跟踪引用。  
  
 *expression*  
 一个表达式，计算结果是引用或值类型的句柄、值类型或是对引用或值类型的跟踪引用。  
  
### 备注  
 表达式 `safe_cast<`*type\-id*`>(`*expression*`)` 会将操作数表达式转换为类型 type\-id 的对象。  
  
 编译器在大多数接受 `safe_cast` 的位置处会接受 [static\_cast](../cpp/static-cast-operator.md)。  但是，`safe_cast` 可保证生成可验证的 MSIL，而 `static_cast` 可能会生成无法验证的 MSIL。  有关可验证代码的详细信息，请参阅[纯代码和可验证代码](../dotnet/pure-and-verifiable-code-cpp-cli.md)和 [Peverify.exe（PEVerify 工具）](../Topic/Peverify.exe%20\(PEVerify%20Tool\).md)。  
  
 与 `static_cast` 一样，`safe_cast` 会调用用户定义的转换。  
  
 有关强制转换的详细信息，请参阅[强制转换运算符](../cpp/casting-operators.md)。  
  
 `safe_cast` 不应用 **const\_cast**（丢掉 **const**）。  
  
 `safe_cast` 位于 cli 命名空间中。  有关详细信息，请参阅 [Platform、default 和 cli 命名空间](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)。  
  
 有关 **safe\_cas**t 的详细信息，请参阅：  
  
-   [C 风格的强制转换和 \/clr \(C\+\+\/CLI\)](../windows/c-style-casts-with-clr-cpp-cli.md)  
  
-   [如何：在 C\+\+\/CLI 中使用 safe\_cast](../dotnet/how-to-use-safe-cast-in-cpp-cli.md)  
  
-   [如何：使用 safe\_cast 向下转换](../misc/how-to-downcast-with-safe-cast.md)  
  
-   [如何：使用 safe\_cast 和泛型类型](../misc/how-to-use-safe-cast-and-generic-types.md)  
  
-   [如何：使用 safe\_cast 和用户定义的转换](../misc/how-to-use-safe-cast-and-user-defined-conversions.md)  
  
-   [如何：使用 safe\_cast 和装箱](../misc/how-to-use-safe-cast-and-boxing.md)  
  
-   [如何：使用 safe\_cast 和取消装箱](../misc/how-to-use-safe-cast-and-unboxing.md)  
  
### 要求  
 编译器选项：**\/clr**  
  
### 示例  
 **示例**  
  
 编译器不接受 `static_cast` 但接受 `safe_cast` 的情况的一个示例是不相关接口类型之间的强制转换。  使用 `safe_cast` 时，编译器不会发出转换错误，会在运行时执行检查以查看强转换是否可以进行  
  
```cpp  
// safe_cast.cpp  
// compile with: /clr  
using namespace System;  
  
interface class I1 {};  
interface class I2 {};  
interface class I3 {};  
  
ref class X : public I1, public I2 {};  
  
int main() {  
   I1^ i1 = gcnew X;  
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X  
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead  
   try {  
      I3^ i4 = safe_cast<I3^>(i1);   // fail at runtime, no common type  
   }   
   catch(InvalidCastException^) {  
      Console::WriteLine("Caught expected exception");  
   }  
}  
```  
  
 **输出**  
  
  **捕获预期异常**   
## 请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)