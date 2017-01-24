---
title: "泛型委托 (Visual C++) | Microsoft Docs"
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
  - "委托, 泛型 [C++]"
  - "泛型委托"
ms.assetid: 09d430b2-1aef-4fbc-87f9-9d7b8185d798
caps.latest.revision: 20
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 泛型委托 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

你能够使用具有泛型类型参数的委托。  有关委托的更多信息，请参见[委托](../windows/delegate-cpp-component-extensions.md)。  
  
## 语法  
  
```  
[attributes]   
generic < [class | typename] type-parameter-identifiers >  
[type-parameter-constraints-clauses]  
[accessibility-modifiers] delegate result-type identifier   
([formal-parameters]);  
```  
  
#### 参数  
 `attributes`（可选）  
 附加的声明信息。  有关特性和特性类的更多信息，请参见特性。  
  
 *类型参数标识符*,  
 标识符逗号分隔列表类型参数的数组。  
  
 `type-parameter-constraints-clauses`  
 采用 [约束](../windows/constraints-on-generic-type-parameters-cpp-cli.md)指定的窗体  
  
 *可访问性修饰符* \(可选\)  
 可访问性修饰符（例如  **public**， `private`\)。  
  
 *结果类型*  
 委托的返回类型。  
  
 *identifier*  
 委托的名称。  
  
 *可选参数*（选项）。  
 委托的参数列表。  
  
## 示例  
 委托的类型参数指定在创建委托对象的点。  委托和方法与它必须有相同的签名。  下面的示例显示了事件委托声明。  
  
```  
// generics_generic_delegate1.cpp  
// compile with: /clr /c  
generic < class ItemType>  
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);  
```  
  
## 示例  
 下面的示例显示：  
  
-   不能使用为其他的构造类型相同的委托对象。  创建不同类型的变体委托对象。  
  
-   委托可以与命名方法关联。  
  
-   当调用泛型方法时，无需指定类型变量，编译器尝试推断调用的类型参数。  
  
```  
// generics_generic_delegate2.cpp  
// compile with: /clr  
generic < class ItemType>  
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);  
  
generic < class ItemType>  
ref struct MyGenClass {  
   ItemType MyMethod(ItemType i, ItemType % j) {  
      return ItemType();  
   }  
};  
  
ref struct MyClass {  
   generic < class ItemType>  
   static ItemType MyStaticMethod(ItemType i, ItemType % j) {  
      return ItemType();  
   }  
};  
  
int main() {  
   MyGenClass<int> ^ myObj1 = gcnew MyGenClass<int>();  
   MyGenClass<double> ^ myObj2 = gcnew MyGenClass<double>();  
   GenDelegate<int>^ myDelegate1 =  
      gcnew GenDelegate<int>(myObj1, &MyGenClass<int>::MyMethod);  
  
   GenDelegate<double>^ myDelegate2 =   
      gcnew GenDelegate<double>(myObj2, &MyGenClass<double>::MyMethod);  
  
   GenDelegate<int>^ myDelegate =  
      gcnew GenDelegate<int>(&MyClass::MyStaticMethod<int>);  
}  
```  
  
## 示例  
 下面的示例声明一个泛型委托 `GenDelegate<ItemType>`，将其实例化然后给使用类型参数 `ItemType`的 `MyMethod` 方法。  委托 \(整型和双精度型\) 的两个实例创建并调用。  
  
```  
// generics_generic_delegate.cpp  
// compile with: /clr  
using namespace System;  
  
// declare generic delegate  
generic <typename ItemType>  
delegate ItemType GenDelegate (ItemType p1, ItemType% p2);  
  
// Declare a generic class:  
generic <typename ItemType>  
ref class MyGenClass {  
public:  
   ItemType MyMethod(ItemType p1, ItemType% p2) {  
      p2 = p1;  
      return p1;  
    }  
};  
  
int main() {  
   int i = 0, j = 0;   
   double m = 0.0, n = 0.0;  
  
   MyGenClass<int>^ myObj1 = gcnew MyGenClass<int>();  
   MyGenClass<double>^ myObj2 = gcnew MyGenClass<double>();   
  
   // Instantiate a delegate using int.  
   GenDelegate<int>^ MyDelegate1 =   
      gcnew GenDelegate<int>(myObj1, &MyGenClass<int>::MyMethod);  
  
   // Invoke the integer delegate using MyMethod.  
   i = MyDelegate1(123, j);  
  
   Console::WriteLine(  
      "Invoking the integer delegate: i = {0}, j = {1}", i, j);  
  
   // Instantiate a delegate using double.  
   GenDelegate<double>^ MyDelegate2 =   
      gcnew GenDelegate<double>(myObj2, &MyGenClass<double>::MyMethod);  
  
   // Invoke the integer delegate using MyMethod.  
   m = MyDelegate2(0.123, n);  
  
   Console::WriteLine(  
      "Invoking the double delegate: m = {0}, n = {1}", m, n);  
}  
```  
  
  **调用整数委托：i \= 123，j \= 123**  
**调用两个委托：m \= 0.123，n \= 0.123**   
## 请参阅  
 [泛型](../windows/generics-cpp-component-extensions.md)