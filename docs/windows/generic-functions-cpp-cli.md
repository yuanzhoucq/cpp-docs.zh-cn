---
title: "泛型函数 (C + + /cli CLI) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- functions [C++], generic
- generic methods
- generics [C++], functions
- methods [C++], generic
- generic functions
ms.assetid: 8e409364-58f9-4360-b486-e7d555e0c218
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9ebafa409680609d6e097b803be2b539ccdc7601
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="generic-functions-ccli"></a>泛型函数 (C++/CLI)
泛型函数是具有类型参数声明的函数。 当调用，而不是类型参数使用实际类型。  
  
## <a name="all-platforms"></a>所有平台  
 **备注**  
  
 此功能不适用于所有平台。  
  
## <a name="windows-runtime"></a>Windows 运行时  
 **备注**  
  
 在 Windows 运行时中不支持此功能。  
  
### <a name="requirements"></a>惠?  
 编译器选项： **/ZW**  
  
## <a name="common-language-runtime"></a>公共语言运行时 
 泛型函数是具有类型参数声明的函数。 当调用，而不是类型参数使用实际类型。  
  
 **语法**  
  
```  
[attributes] [modifiers]  
return-type identifier<type-parameter identifier(s)>  
[type-parameter-constraints clauses]  
  
([formal-parameters])  
{function-body}  
```  
  
 **参数**  
  
 *属性*（可选）  
 附加的声明信息。 有关特性和特性类的详细信息，请参阅属性。  
  
 *修饰符*（可选）  
 对于函数，如静态修饰符。  `virtual`不允许由于虚方法不能是泛型。  
  
 *返回类型*  
 由方法返回的类型。 如果返回类型为 void，没有返回值是必需的。  
  
 *identifier*  
 函数名称。  
  
 *类型参数标识符*  
 以逗号分隔标识符列表。  
  
 *正式参数*（可选）  
 参数列表。  
  
 *类型形参约束子句*  
 这可能用作类型参数的类型上指定限制，并采用中指定格式[泛型类型参数的约束 (C + + /cli CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md)。  
  
 *函数体*  
 方法，其可能引用的类型参数标识符的正文。  
  
 **备注**  
  
 泛型函数是使用泛型类型参数声明的函数。 它们可能在类或结构或独立的函数中的方法。 单个的泛型声明隐式声明一的系列函数仅在不同的实际类型为泛型类型参数替换存在差异。  
  
 Visual c + + 中不能具有泛型类型参数声明类或结构的构造函数。  
  
 调用时，泛型类型参数替换为实际类型。 实际的类型可能在尖括号使用语法类似于模板函数调用中显式指定。 如果调用不带类型参数，编译器将尝试推导从函数调用中提供的参数的实际类型。 如果不能从所使用的参数中推导预期的类型参数，编译器将报告错误。  
  
### <a name="requirements"></a>惠?  
 编译器选项： **/clr**  
  
### <a name="examples"></a>示例  
 **示例**  
  
 下面的代码示例演示如何泛型函数。  
  
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
  
 泛型函数可以基于签名或 arity、 在函数上的类型参数的数目进行重载。 此外，泛型函数可以与非泛型函数具有相同名称的重载，只要函数不同，某些类型参数中。 例如，以下函数可以进行重载：  
  
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
  
 下面的示例使用泛型函数查找数组中的第一个元素。 它声明`MyClass`，它继承自的基类`MyBaseClass`。 `MyClass`包含泛型函数时， `MyFunction`，从而调用另一个泛型函数时，`MyBaseClassFunction`中的基类。 在**主要**，泛型函数时， `MyFunction`，称为使用不同的类型参数。  
  
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
  
 **输出**  
  
```Output  
My function returned an int: 2003  
My function returned a string: Hello generic functions!  
```  
  
## <a name="see-also"></a>请参阅  
 [运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)   
 [泛型](../windows/generics-cpp-component-extensions.md)