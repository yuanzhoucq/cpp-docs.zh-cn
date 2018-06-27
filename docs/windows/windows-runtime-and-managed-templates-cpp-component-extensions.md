---
title: Windows 运行时和托管的模板 （c + + 组件扩展） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- templates, with CLR types
ms.assetid: cf59d16b-5514-448b-9a95-e0b4fcb616a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e9053b101428ac26e96446d9c6756ec5de35e06c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891358"
---
# <a name="windows-runtime-and-managed-templates-c-component-extensions"></a>Windows 运行时和托管模板（C++ 组件扩展）
使用模板可以定义 Windows 运行时或公共语言运行时类型的原型，然后使用不同模板类型参数实例化该类型的变体。  
  
## <a name="all-runtimes"></a>所有运行时  
 您可以依据值类型或引用类型创建模板。  有关创建值或引用类型的详细信息，请参阅[类和结构](../windows/classes-and-structs-cpp-component-extensions.md)。  
  
 有关标准 c + + 类模板的详细信息，请参阅[类模板](../cpp/class-templates.md)。  
  
## <a name="windows-runtime"></a>Windows 运行时  
 (此语言功能没有只适用于 Windows 运行时的备注。）  
  
### <a name="requirements"></a>要求  
 编译器选项： **/ZW**  
  
## <a name="common-language-runtime"></a>公共语言运行时  
 根据托管类型创建类模板会有一些限制，如以下代码示例所示。  
  
### <a name="requirements"></a>要求  
 编译器选项： **/clr**  
  
### <a name="examples"></a>示例  
 **示例**  
  
 使用托管类型模板参数实例化泛型类型是可行的，但是无法使用泛型类型模板参数实例化托管模板。  这是因为泛型类型在运行时解析。  有关详细信息，请参阅[泛型和模板 （Visual c + +）](../windows/generics-and-templates-visual-cpp.md)。  
  
```cpp  
// managed_templates.cpp  
// compile with: /clr /c  
  
generic<class T>   
ref class R;   
  
template<class T>   
ref class Z {  
   // Instantiate a generic with a template parameter.  
   R<T>^ r;    // OK  
};  
  
generic<class T>   
ref class R {  
   // Cannot instantiate a template with a generic parameter.  
   Z<T>^ z;   // C3231  
};  
```  
  
 **示例**  
  
 泛型类型或函数不能嵌套在托管模板中。  
  
```cpp  
// managed_templates_2.cpp  
// compile with: /clr /c  
  
template<class T> public ref class R {  
   generic<class T> ref class W {};   // C2959  
};  
```  
  
 **示例**  
  
 不能访问在使用 C++/CLI 语言语法的引用程序集中定义的模板，但是可以使用反射。  如果模板未实例化，则元数据中不会发出该模板。  如果模板已实例化，则元数据中仅显示引用的成员函数。  
  
```cpp  
// managed_templates_3.cpp  
// compile with: /clr  
  
// Will not appear in metadata.  
template<class T> public ref class A {};  
  
// Will appear in metadata as a specialized type.  
template<class T> public ref class R {  
public:  
   // Test is referenced, will appear in metadata  
   void Test() {}  
  
   // Test2 is not referenced, will not appear in metadata  
   void Test2() {}  
};  
  
// Will appear in metadata.  
generic<class T> public ref class G { };  
  
public ref class S { };  
  
int main() {  
   R<int>^ r = gcnew R<int>;  
   r->Test();  
}  
```  
  
 **示例**  
  
 可以在类模板的部分专用化或显式专用化中更改类的托管修饰符。  
  
```cpp  
// managed_templates_4.cpp  
// compile with: /clr /c  
  
// class template  
// ref class  
template <class T>  
ref class A {};  
  
// partial template specialization  
// value type  
template <class T>  
value class A <T *> {};  
  
// partial template specialization  
// interface  
template <class T>   
interface class A<T%> {};  
  
// explicit template specialization  
// native class  
template <>  
class A <int> {};  
  
```  
  
## <a name="see-also"></a>请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)