---
title: "nullptr | Microsoft Docs"
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
  - "__nullptr 关键字 (C++)"
  - "nullptr 关键字 [C++]"
ms.assetid: 594cfbf7-06cb-4366-9ede-c0b703e1d095
caps.latest.revision: 24
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# nullptr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`nullptr` 关键字表示 *空指针值*。  关键字指示对象句柄、内部指针或本机指针类型不指向对象。  
  
 使用托管 `nullptr` 或本机代码。  编译器发出的托管代码和本机的 null 指针值的相应，但不同的指令。  有关使用此关键字 ISO C\+\+ 标准版本的信息，请参见 [nullptr](../cpp/nullptr.md)。  
  
 特定于 Microsoft 的 `__nullptr` 关键字与 `nullptr` 的含义相同，但前者仅适用于本机代码。  如果使用具有本机 C\/C\+\+ 代码的 `nullptr` 和编译与 [\/clr](../build/reference/clr-common-language-runtime-compilation.md) 编译器选项，编译器无法确定 `nullptr` 是否指示本机或托管的 null 指针值。  若要使编译器意图，请使用 `nullptr` 指定托管的值或 `__nullptr` 指定本机的值。  
  
 （这 `nullptr`的关键字等效于 Visual Basic 中的 `Nothing` 和 C\#中的 `null`。）  
  
## 用法  
 可以使用 `nullptr` 关键字。任何句柄，本机指针，或可以使用函数参数。  
  
 `nullptr` 关键字不是类型而不支持用于：  
  
-   [sizeof](../cpp/sizeof-operator.md)  
  
-   [typeid](../cpp/typeid-operator.md)  
  
-   `throw nullptr` 虽然会起作用 \( `throw (Object^)nullptr;` \)  
  
 `nullptr` 关键字可在以下类型指针的初始值：  
  
-   本机指针  
  
-   Windows 运行时句柄  
  
-   托管处理  
  
-   托管的内部指针  
  
 `nullptr` 关键字可用来测试，如果是指针或句柄引用空，在使用之前引用。  
  
 的语言中的应正确解释函数调用之间用于错误检查使用 null 指针值。  
  
 不能初始化为零；句柄可以只使用 `nullptr`。  常数 0 的分配给对象句柄的生产装箱的 `Int32` 和一个转换为 `Object^`。  
  
## 示例  
 下面的代码示例说明，可以使用 `nullptr` 关键字。句柄，本机指针，或可以使用函数参数。  此示例说明，`nullptr` 关键字可用来检查引用，然后使用它之前对它。  
  
```  
// mcpp_nullptr.cpp  
// compile with: /clr  
value class V {};  
ref class G {};  
void f(System::Object ^) {}  
  
int main() {  
// Native pointer.  
   int *pN = nullptr;  
// Managed handle.  
   G ^pG = nullptr;  
   V ^pV1 = nullptr;  
// Managed interior pointer.  
   interior_ptr<V> pV2 = nullptr;  
// Reference checking before using a pointer.  
   if (pN == nullptr) {}  
   if (pG == nullptr) {}  
   if (pV1 == nullptr) {}  
   if (pV2 == nullptr) {}  
// nullptr can be used as a function argument.  
   f(nullptr);   // calls f(System::Object ^)  
}  
```  
  
## 示例  
 **示例**  
  
 下面的代码示例显示该 `nullptr` 以及零在本机指针可以交换使用。  
  
```  
// mcpp_nullptr_1.cpp  
// compile with: /clr  
class MyClass {  
public:  
   int i;  
};  
  
int main() {  
   MyClass * pMyClass = nullptr;  
   if ( pMyClass == nullptr)  
      System::Console::WriteLine("pMyClass == nullptr");  
  
   if ( pMyClass == 0)  
      System::Console::WriteLine("pMyClass == 0");  
  
   pMyClass = 0;  
   if ( pMyClass == nullptr)  
      System::Console::WriteLine("pMyClass == nullptr");  
  
   if ( pMyClass == 0)  
      System::Console::WriteLine("pMyClass == 0");  
}  
```  
  
 **Output**  
  
  **pMyClass \=\= nullptr**  
 **pMyClass \=\= 0**  
 **pMyClass \=\= nullptr**  
 **pMyClass \=\= 0**   
## 示例  
 **示例**  
  
 下面的代码示例演示一，`nullptr` 被解释，则对任何类型或本机指针的句柄到任何类型。  对于重载与句柄函数的情况下对不同类型，则不确定性甚至会生成错误。  `nullptr` 必须显式转换为类型。  
  
```  
// mcpp_nullptr_2.cpp  
// compile with: /clr /LD  
void f(int *){}  
void f(int ^){}  
  
void f_null() {  
   f(nullptr);   // C2668  
   // try one of the following lines instead  
   f((int *) nullptr);  
   f((int ^) nullptr);  
}  
```  
  
## 示例  
 **示例**  
  
 下面的代码示例演示一，转换使用 `nullptr` 并返回指针或句柄到包含 `nullptr` 值的转换类型。  
  
```  
// mcpp_nullptr_3.cpp  
// compile with: /clr /LD  
using namespace System;  
template <typename T>   
void f(T) {}   // C2036 cannot deduce template type because nullptr can be any type  
  
int main() {  
   f((Object ^) nullptr);   // T = Object^, call f(Object ^)  
  
   // Delete the following line to resolve.  
   f(nullptr);  
  
   f(0);   // T = int, call f(int)  
}  
```  
  
## 示例  
 **示例**  
  
 下面的代码示例演示一，`nullptr` 可用作函数参数。  
  
```  
// mcpp_nullptr_4.cpp  
// compile with: /clr  
using namespace System;  
void f(Object ^ x) {  
   Console::WriteLine("test");  
}  
  
int main() {  
   f(nullptr);  
}  
```  
  
 **Output**  
  
  **测试**   
## 示例  
 **示例**  
  
 下面的代码示例演示处理，那么，当声明并且不显式初始化时，会默认初始化为 `nullptr`。  
  
```  
// mcpp_nullptr_5.cpp  
// compile with: /clr  
using namespace System;  
ref class MyClass {  
public:  
   void Test() {  
      MyClass ^pMyClass;   // gc type  
      if (pMyClass == nullptr)  
         Console::WriteLine("NULL");  
   }  
};  
  
int main() {  
   MyClass ^ x = gcnew MyClass();  
   x -> Test();  
}  
```  
  
 **Output**  
  
  **NULL**   
## 示例  
 **示例**  
  
 下面的代码示例演示 `nullptr`，可以分配给本机指针，在使用 **\/clr**编译时。  
  
```  
// mcpp_nullptr_6.cpp  
// compile with: /clr  
int main() {  
   int * i = 0;  
   int * j = nullptr;  
}  
```  
  
## 要求  
 编译器选项：\(不要求；支持所有代码生成选项，包括 **\/ZW** 和 **\/clr**\)。  
  
## 请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)   
 [nullptr](../cpp/nullptr.md)