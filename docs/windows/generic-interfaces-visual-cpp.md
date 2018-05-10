---
title: 泛型接口 （Visual c + +） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- generic interfaces
- interfaces, generic [C++}
ms.assetid: f3da788a-ba83-4db7-9dcf-9b95a8fb9d1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8e16a2ab8a1ee0c9255f394d033bda2a7afc2b7e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="generic-interfaces-visual-c"></a>泛型接口 (Visual C++)
应用于对类类型参数的限制都应用于类型参数在接口上的那些相同 (请参阅[泛型类 (C + + /cli CLI)](../windows/generic-classes-cpp-cli.md))。  
  
 控制函数重载的规则都相同的泛型类或泛型接口中的函数。  
  
 显式接口成员的实现以使用 （请参阅下面的示例） 的简单接口类型的相同方式处理构造的接口类型。  
  
 在接口上的详细信息，请参阅[接口类](../windows/interface-class-cpp-component-extensions.md)。  
  
## <a name="syntax"></a>语法  
  
```  
[attributes] generic <class-key type-parameter-identifier[, ...]>  
[type-parameter-constraints-clauses][accesibility-modifiers] interface class identifier [: base-list] {   interface-body} [declarators] ;  
```  
  
## <a name="remarks"></a>备注  
 *属性*（可选）  
 附加的声明信息。 有关特性和特性类的详细信息，请参阅“特性”。  
  
 *类别键*  
 **类**或**typename**  
  
 `type-parameter-identifier(s)`  
 以逗号分隔标识符列表。  
  
 `type-parameter-constraints-clauses`  
 中指定的形式[泛型类型参数的约束 (C + + /cli CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md)  
  
 *可访问性修饰符*（可选）  
 可访问性修饰符 (例如**公钥 / 私钥**)。  
  
 *identifier*  
 接口名称。  
  
 *基列表*（可选）  
 包含一个或多个显式基接口用逗号分隔的列表。  
  
 *接口体内*  
 接口成员的声明。  
  
 *声明符*（可选）  
 基于此类型的变量的声明。  
  
## <a name="example"></a>示例  
 下面的示例演示如何声明并实例化一个泛型接口。 在示例中，泛型接口`IList<ItemType>`声明。 它由两个泛型类，然后实现`List1<ItemType>`和`List2<ItemType>`，具有不同的实现。  
  
```  
// generic_interface.cpp  
// compile with: /clr  
using namespace System;  
  
// An exception to be thrown by the List when  
// attempting to access elements beyond the  
// end of the list.  
ref class ElementNotFoundException : Exception {};  
  
// A generic List interface  
generic <typename ItemType>  
public interface class IList {  
   ItemType MoveFirst();  
   bool Add(ItemType item);  
   bool AtEnd();  
   ItemType Current();  
   void MoveNext();  
};  
  
// A linked list implementation of IList  
generic <typename ItemType>  
public ref class List1 : public IList<ItemType> {  
   ref class Node {  
      ItemType m_item;  
  
   public:  
      ItemType get_Item() { return m_item; };  
      void set_Item(ItemType value) { m_item = value; };  
  
      Node^ next;  
  
      Node(ItemType item) {  
         m_item = item;  
         next = nullptr;  
      }  
   };  
  
   Node^ first;  
   Node^ last;  
   Node^ current;  
  
   public:  
   List1() {  
      first = nullptr;  
      last = first;  
      current = first;  
   }  
  
   virtual ItemType MoveFirst() {  
      current = first;  
      if (first != nullptr)  
        return first->get_Item();  
      else  
         return ItemType();  
   }  
  
   virtual bool Add(ItemType item) {  
      if (last != nullptr) {   
         last->next = gcnew Node(item);  
         last = last->next;  
      }  
      else {  
         first = gcnew Node(item);  
         last = first;  
         current = first;  
      }  
      return true;  
   }  
  
   virtual bool AtEnd() {  
      if (current == nullptr )  
        return true;  
      else   
        return false;  
   }  
  
   virtual ItemType Current() {  
       if (current != nullptr)  
         return current->get_Item();  
       else  
         throw gcnew ElementNotFoundException();  
   }  
  
   virtual void MoveNext() {  
      if (current != nullptr)  
       current = current->next;  
      else  
        throw gcnew ElementNotFoundException();  
   }  
};  
  
// An array implementation of IList  
generic <typename ItemType>  
ref class List2 : public IList<ItemType> {  
   array<ItemType>^ item_array;  
   int count;  
   int current;  
  
   public:  
  
   List2() {  
      // not yet possible to declare an  
      // array of a generic type parameter  
      item_array = gcnew array<ItemType>(256);  
      count = current = 0;  
   }  
  
   virtual ItemType MoveFirst() {  
      current = 0;  
      return item_array[0];  
   }  
  
   virtual bool Add(ItemType item) {  
      if (count < 256)  
         item_array[count++] = item;  
      else  
        return false;  
      return true;  
   }  
  
   virtual bool AtEnd() {  
      if (current >= count)  
        return true;  
      else  
        return false;  
   }  
  
   virtual ItemType Current() {  
      if (current < count)  
        return item_array[current];  
      else  
        throw gcnew ElementNotFoundException();  
   }  
  
   virtual void MoveNext() {  
      if (current < count)   
         ++current;  
      else  
         throw gcnew ElementNotFoundException();  
   }  
};  
  
// Add elements to the list and display them.  
generic <typename ItemType>  
void AddStringsAndDisplay(IList<ItemType>^ list, ItemType item1, ItemType item2) {  
   list->Add(item1);  
   list->Add(item2);  
   for (list->MoveFirst(); ! list->AtEnd(); list->MoveNext())  
     Console::WriteLine(list->Current());  
}  
  
int main() {  
   // Instantiate both types of list.  
  
   List1<String^>^ list1 = gcnew List1<String^>();  
   List2<String^>^ list2 = gcnew List2<String^>();  
  
   // Use the linked list implementation of IList.  
   AddStringsAndDisplay<String^>(list1, "Linked List", "List1");  
  
   // Use the array implementation of the IList.  
   AddStringsAndDisplay<String^>(list2, "Array List", "List2");  
}  
```  
  
```Output  
Linked List  
List1  
Array List  
List2  
```  
  
## <a name="example"></a>示例  
 此示例声明一个泛型接口， `IMyGenIface`，和两个非泛型接口，`IMySpecializedInt`和`ImySpecializedString`的专用化`IMyGenIface`。 由两个类，然后实现两个专用的接口`MyIntClass`和`MyStringClass`。 该示例演示如何专用化的泛型接口，实例化泛型和非泛型接口，并在接口上调用显式实现的成员。  
  
```  
// generic_interface2.cpp  
// compile with: /clr  
// Specializing and implementing generic interfaces.  
using namespace System;  
  
generic <class ItemType>  
public interface class IMyGenIface {  
   void Initialize(ItemType f);  
};  
  
public interface class IMySpecializedInt: public IMyGenIface<int> {  
   void Display();  
};  
  
public interface class IMySpecializedString: public IMyGenIface<String^> {  
   void Display();  
};  
  
public ref class MyIntClass: public IMySpecializedInt {  
   int myField;  
  
public:   
   virtual void Initialize(int f) {  
      myField = f;  
   }  
  
   virtual void Display() {  
      Console::WriteLine("The integer field contains: {0}", myField);  
   }      
};  
  
public ref struct MyStringClass: IMySpecializedString {      
   String^ myField;  
  
public:  
   virtual void Initialize(String^ f) {  
      myField = f;  
    }  
  
   virtual void Display() {  
      Console::WriteLine("The String field contains: {0}", myField);  
   }  
};  
  
int main() {  
   // Instantiate the generic interface.  
   IMyGenIface<int>^ myIntObj = gcnew MyIntClass();  
  
   // Instantiate the specialized interface "IMySpecializedInt."  
   IMySpecializedInt^ mySpIntObj = (IMySpecializedInt^) myIntObj;  
  
   // Instantiate the generic interface.  
   IMyGenIface<String^>^ myStringObj = gcnew MyStringClass();  
  
   // Instantiate the specialized interface "IMySpecializedString."  
   IMySpecializedString^ mySpStringObj =   
            (IMySpecializedString^) myStringObj;  
  
   // Call the explicitly implemented interface members.  
   myIntObj->Initialize(1234);  
   mySpIntObj->Display();  
  
   myStringObj->Initialize("My string");  
   mySpStringObj->Display();  
}  
```  
  
```Output  
The integer field contains: 1234  
The String field contains: My string  
```  
  
## <a name="see-also"></a>请参阅  
 [泛型](../windows/generics-cpp-component-extensions.md)