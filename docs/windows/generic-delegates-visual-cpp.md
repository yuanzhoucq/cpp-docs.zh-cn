---
title: 泛型委托 （Visual c + +） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- generic delegates
- delegates, generic [C++]
ms.assetid: 09d430b2-1aef-4fbc-87f9-9d7b8185d798
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ecbfebc49f76eee7bb753af3d07052d1e05d73be
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875593"
---
# <a name="generic-delegates-visual-c"></a>泛型委托 (Visual C++)
你可以使用具有委托的泛型类型参数。 有关委托的更多信息，请参阅[委托 （c + + 组件扩展）](../windows/delegate-cpp-component-extensions.md)。  
  
## <a name="syntax"></a>语法  
  
```  
[attributes]   
generic < [class | typename] type-parameter-identifiers>  
[type-parameter-constraints-clauses]  
[accessibility-modifiers] delegate result-type identifier   
([formal-parameters]);  
```  
  
#### <a name="parameters"></a>参数  
 `attributes` （可选）  
 附加的声明信息。 有关特性和特性类的详细信息，请参阅“特性”。  
  
 *type-parameter-identifier(s)*  
 类型参数标识符的逗号分隔列表。  
  
 `type-parameter-constraints-clauses`  
 中指定的形式[泛型类型参数的约束 (C + + /cli CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md)  
  
 *可访问性修饰符*（可选）  
 可访问性修饰符 (例如**公共**， `private`)。  
  
 *result-type*  
 委托的返回类型。  
  
 *identifier*  
 该委托的名称。  
  
 *正式参数*（可选）  
 委托的参数列表。  
  
## <a name="example"></a>示例  
 委托类型参数在创建委托对象时指定。 与其相关联的委托和方法必须有相同的签名。 下面是泛型委托声明的示例。  
  
```  
// generics_generic_delegate1.cpp  
// compile with: /clr /c  
generic <class ItemType>  
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);  
```  
  
## <a name="example"></a>示例  
 下面的示例显示：  
  
-   不能使用具有不同构造类型的相同委托对象。 针对不同类型创建不同的委托对象。  
  
-   泛型委托可以与泛型方法相关联。  
  
-   当调用泛型方法而不指定类型参数时，编译器会尝试推断调用的类型参数。  
  
```  
// generics_generic_delegate2.cpp  
// compile with: /clr  
generic <class ItemType>  
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);  
  
generic <class ItemType>  
ref struct MyGenClass {  
   ItemType MyMethod(ItemType i, ItemType % j) {  
      return ItemType();  
   }  
};  
  
ref struct MyClass {  
   generic <class ItemType>  
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
  
## <a name="example"></a>示例  
 以下示例声明泛型委托 `GenDelegate<ItemType>`，然后将其与使用类型参数 `MyMethod` 的方法 `ItemType` 相关联。 创建并调用委托的两个实例（整型和双精度型）。  
  
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
  
```Output  
Invoking the integer delegate: i = 123, j = 123  
Invoking the double delegate: m = 0.123, n = 0.123  
```  
  
## <a name="see-also"></a>请参阅  
 [泛型](../windows/generics-cpp-component-extensions.md)