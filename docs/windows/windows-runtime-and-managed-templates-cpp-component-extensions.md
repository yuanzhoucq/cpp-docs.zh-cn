---
title: "Windows 运行时和托管模板（C++ 组件扩展） | Microsoft Docs"
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
  - "模板, 用 CLR 类型"
ms.assetid: cf59d16b-5514-448b-9a95-e0b4fcb616a6
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows 运行时和托管模板（C++ 组件扩展）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用不同的模板类型参数，可以定义运行时模板 Windows 或公共语言运行时 \(CLR\) 类型的原型，然后实例化该类型的变体。  
  
## 所有运行时  
 您可以依据值或引用类型的模板。有关创建自定义配置类型的更多信息，请参见[类和结构 \(托管\)](../windows/classes-and-structs-cpp-component-extensions.md)。  
  
 有关部署项目模板的更多信息，请参见[类模板](../cpp/class-templates.md)。  
  
## Windows Runtime — Windows 运行时  
 \(此语言功能没有只适用于 Windows 运行时的备注。）  
  
### 要求  
 编译器选项：**\/ZW**  
  
## 公共语言运行时  
 有一些限制托管代码创建类类型的模板，如以下代码示例中演示。  
  
### 要求  
 编译器选项：**\/clr**  
  
### 示例  
 **示例**  
  
 实例化与宿主的类型模板参数的泛型类型是可行的，但是，无法实例化泛型类型模板参数的托管模板。这是因为，泛型类型在运行时解析。有关详细信息，请参阅[型和模板](../windows/generics-and-templates-visual-cpp.md)。  
  
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
  
 泛型类型或函数中托管模板不能嵌套。  
  
```cpp  
// managed_templates_2.cpp  
// compile with: /clr /c  
  
template<class T> public ref class R {  
   generic<class T> ref class W {};   // C2959  
};  
```  
  
 **示例**  
  
 不能访问包含在 C\+\+\/CLI 语言语法中引用的程序集中定义的模板，但是，您可以使用反射。如果模板进行实例化，其在元数据中未发出。如果模板实例化，因此，只有引用的成员函数将出现在元数据中。  
  
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
  
 可以更改一类的托管修饰符在部分专用化或类模板的显式专用化的。  
  
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
  
## 请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)