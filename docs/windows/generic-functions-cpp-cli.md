---
title: "泛型函数 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
  - "函数 [C++], 泛型"
  - "泛型函数"
  - "泛型方法"
  - "泛型 [C++], 函数"
  - "方法 [C++], 泛型"
ms.assetid: 8e409364-58f9-4360-b486-e7d555e0c218
caps.latest.revision: 21
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 泛型函数 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

是泛型函数声明与类型参数的函数。  在调用中，实际类型来代替使用类型参数。  
  
## 所有平台  
 **备注**  
  
 此功能不适用于所有平台。  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 **备注**  
  
 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 不支持此功能。  
  
### 要求  
 编译器选项：**\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 是泛型函数声明与类型参数的函数。  在调用中，实际类型来代替使用类型参数。  
  
 **语法**  
  
```  
[attributes] [modifiers]  
return-type identifier <type-parameter identifier(s)>  
[type-parameter-constraints clauses]  
  
([formal-parameters])  
{  
   function-body  
}  
```  
  
 **参数**  
  
 *attributes*（可选）  
 附加的声明信息。  有关特性和特性类的更多信息，请参见特性。  
  
 *modifiers*（可选）  
 函数的一个 st 修饰符，如 atic 的。因为虚方法不能是泛型，`virtual` 不允许。  
  
 *return\-type*  
 由方法返回的类型。  如果返回类型是无效的，不需要返回值。  
  
 *identifier*  
 函数名。  
  
 *type\-parameter identifier\(s\)*  
 逗号分隔的标识符列表。  
  
 *formal\-parameters*（可选）  
 参数列表  
  
 *type\-parameter\-constraints\-clauses*  
 这对能用作类型参数指定类型的限制，以及 [约束](../windows/constraints-on-generic-type-parameters-cpp-cli.md)采用指定的窗体。  
  
 *function\-body*  
 方法体可以引用标识符类型参数。  
  
 **备注**  
  
 泛型函数是函数声明的泛型类型参数。  它们可能是类或结构独立的方法或函数。  一个泛声明隐式声明在其他的实际类型不同仅替换泛型类型参数的函数系列。  
  
 在 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)]，类或结构构造函数都不能声明具有泛型类型参数。  
  
 在调用时，泛型类型参数的实际类型替换。  实际类型在尖括号可以显式指定使用语法类似于模板函数调用。  如果调用，但没有参数类型，编译器将尝试从函数调用中提供参数推断实际类型。  当调用泛型函数时，如果无法从使用的参数推导出预期的类型变量，编译器将报告错误。  
  
### 要求  
 编译器选项：**\/clr**  
  
### 示例  
 **示例**  
  
 下面的代码示例演示泛型函数。  
  
```  
// generics_generic_function_1.cpp  
// compile with: /clr  
generic <typename ItemType>  
void G(int i) {}  
  
ref struct A {  
   generic <typename ItemType>  
   void G(ItemType) {}  
  
   generic <typename ItemType>  
   static void H(int i) {}  
};  
  
int main() {  
   A myObject;  
  
   // generic function call  
   myObject.G<int>(10);  
  
   // generic function call with type parameters deduced  
   myObject.G(10);  
  
   // static generic function call  
   A::H<int>(10);  
  
   // global generic function call  
   G<int>(10);  
}  
```  
  
 **示例**  
  
 常规函数可重载的签名或 arity，类型参数的数目进行函数上。  此外，在某些类型，只要函数的参数不同，泛型函数可重载同名的非泛型函数。  例如，现在可以自动执行下列任务：  
  
```  
// generics_generic_function_2.cpp  
// compile with: /clr /c  
ref struct MyClass {  
   void MyMythod(int i) {}  
  
   generic <class T>   
   void MyMythod(int i) {}  
  
   generic <class T, class V>   
   void MyMythod(int i) {}  
};  
```  
  
 **示例**  
  
 下面的示例使用泛功能查找数组中的第一个元素。  它将声明 `MyClass`，从基类 `MyBaseClass`继承。  `MyClass` 包含泛型函数，`MyFunction`，另调用泛型函数，`MyBaseClassFunction`，在基类中。  在 **主函数**，泛型函数，即 `MyFunction`，使用不同类型参数。  
  
```  
// generics_generic_function_3.cpp  
// compile with: /clr  
using namespace System;  
  
ref class MyBaseClass {  
protected:  
   generic <class ItemType>  
   ItemType MyBaseClassFunction(ItemType item) {  
      return item;  
   }  
};  
  
ref class MyClass: public MyBaseClass {  
public:  
   generic <class ItemType>  
   ItemType MyFunction(ItemType item) {  
      return MyBaseClass::MyBaseClassFunction<ItemType>(item);  
   }  
};  
  
int main() {  
   MyClass^ myObj = gcnew MyClass();  
  
   // Call MyFunction using an int.  
   Console::WriteLine("My function returned an int: {0}",  
                           myObj->MyFunction<int>(2003));  
  
   // Call MyFunction using a string.  
   Console::WriteLine("My function returned a string: {0}",  
   myObj->MyFunction<String^>("Hello generic functions!"));  
}  
```  
  
 **Output**  
  
  **我返回 int 的函数：2003 年**  
 **我的函数返回字符串：Hello\!泛型函数**   
## 请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)   
 [泛型](../windows/generics-cpp-component-extensions.md)