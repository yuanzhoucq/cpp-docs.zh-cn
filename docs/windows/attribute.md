---
title: "attribute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.attribute"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__typeof keyword"
  - "custom attributes, creating"
  - "attribute attribute"
  - "attributes [C++], custom"
ms.assetid: 8cb3489f-65c4-44ea-b0aa-3c3c6b15741d
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# attribute
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

允许您创建自定义特性。  
  
## 语法  
  
```  
  
      [ attribute(  
   AllowOn,  
   AllowMultiple=boolean,  
   Inherited=boolean  
) ]  
```  
  
#### 参数  
 *AllowOn*  
 指定自定义特性可应用的语言元素。  默认值为 **系统:: AttributeTargets:: 任何** \(请参见 [系统:: AttributeTargets](https://msdn.microsoft.com/en-us/library/system.attributetargets.aspx)\)。  
  
 `AllowMultiple`  
 指定自定义特性是否可重复适用于构造。  默认值为 **错误**。  
  
 `Inherited`  
 指示属性是否将由子类继承。  编译器提供不支持此功能特别支持;将其属性使用者 \(如反射的工作，\) 保留此信息。  如果 `Inherited` 是 **TRUE**，属性继承。  如果 `AllowMultiple` 是 **TRUE**，属性是名派生的成员将累积;如果 `AllowMultiple` 是 **错误**，属性在继承将重写 \(或替换\)。  如果 `Inherited` 是 **错误**，属性不会继承。  默认值为 **TRUE**。  
  
## 备注  
  
> [!NOTE]
>  `attribute` 属性现在已弃用。  使用公共语言运行时 \(clr\) 特性 System.Attribute 为直接创建用户定义的 attirbutes。  有关更多信息，请参见 [用户定义的特性](../windows/user-defined-attributes-cpp-component-extensions.md)。  
  
 通过将 `attribute` 属性定义 [自定义特性](../windows/custom-attributes-cpp.md) 在托管类或结构的定义。  类的名称是自定义特性。  例如：  
  
```  
[ attribute(Parameter) ]  
public ref class MyAttr {};  
```  
  
 定义调用可应用于函数参数的 MyAttr 的特性。  在中，如果属性用于其他程序集，类必须是公共的。  
  
> [!NOTE]
>  若要防止命名冲突，所有属性隐式名为的 “属性”结尾;在此示例中，特性的名称和类实际上是 MyAttrAttribute，但是，可以互换使用 MyAttr 和 MyAttrAttribute。  
  
 类的公共构造函数定义属性的未命名参数。  重载的构造函数允许指定该特性方式，因此定义以下方式的自定义特性:  
  
```  
// cpp_attr_ref_attribute.cpp  
// compile with: /c /clr  
using namespace System;  
[ attribute(AttributeTargets::Class) ]   // apply attribute to classes  
public ref class MyAttr {  
public:  
   MyAttr() {}   // Constructor with no parameters  
   MyAttr(int arg1) {}   // Constructor with one parameter  
};  
  
[MyAttr]  
ref class ClassA {};   // Attribute with no parameters  
  
[MyAttr(123)]  
ref class ClassB {};   // Attribute with one parameter  
```  
  
 类的公共数据成员和属性是属性的选项命名参数:  
  
```  
// cpp_attr_ref_attribute_2.cpp  
// compile with: /c /clr  
using namespace System;  
[ attribute(AttributeTargets::Class) ]  
ref class MyAttr {  
public:  
   // Property Priority becomes attribute's named parameter Priority  
    property int Priority {  
       void set(int value) {}  
       int get() { return 0;}  
   }  
   // Data member Version becomes attribute's named parameter Version  
   int Version;  
   MyAttr() {}   // constructor with no parameters  
   MyAttr(int arg1) {}   // constructor with one parameter  
};  
  
[MyAttr(123, Version=2)]   
ref class ClassC {};  
```  
  
 有关可能的特性参数类型的列表，请参见 [自定义特性](../windows/custom-attributes-cpp.md)。  
  
 有关特性目标的讨论参见 [用户定义的特性](../windows/user-defined-attributes-cpp-component-extensions.md) 。  
  
 `attribute` 属性指定了一个 `AllowMultiple` 参数自定义属性是否为单使用的或 multiuse \(可多次出现在同一个实体\)。  
  
```  
// cpp_attr_ref_attribute_3.cpp  
// compile with: /c /clr  
using namespace System;  
[ attribute(AttributeTargets::Class, AllowMultiple = true) ]  
ref struct MyAttr {  
   MyAttr(){}  
};   // MyAttr is a multiuse attribute  
  
[MyAttr, MyAttr()]  
ref class ClassA {};  
```  
  
 自定义特性类从 <xref:System.ComponentModel.AttributeCollection.%23ctor%2A>直接或间接派生，从而加快确定元数据的属性定义和容易。  `attribute` 属性暗示从系统的继承:: 属性，因此，显式派生不是必需的:  
  
```  
[ attribute(Class) ]  
ref class MyAttr  
```  
  
 等效于  
  
```  
[ attribute(Class) ]  
ref class MyAttr : System::Attribute   // OK, but redundant.  
```  
  
 `attribute` 是 <xref:System.AttributeUsageAttribute?displayProperty=fullName> \(不是 AttributeAttribute 别名;这是异常给特性的命名规则\)。  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|`ref` **类**， **ref 结构**|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 示例  
  
```  
// cpp_attr_ref_attribute_4.cpp  
// compile with: /c /clr  
using namespace System;  
[attribute(AttributeTargets::Class)]  
ref struct ABC {  
   ABC(Type ^) {}  
};  
  
[ABC(String::typeid)]   // typeid operator yields System::Type ^  
ref class MyClass {};  
```  
  
## 示例  
 命名参数的 `Inherited` 指定在基类应用的自定义特性是否在派生类中镜像显示。  
  
```  
// cpp_attr_ref_attribute_5.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Reflection;  
  
[attribute( AttributeTargets::Method, Inherited=false )]  
ref class BaseOnlyAttribute { };  
  
[attribute( AttributeTargets::Method, Inherited=true )]  
ref class DerivedTooAttribute { };  
  
ref struct IBase {  
public:  
   [BaseOnly, DerivedToo]  
   virtual void meth() {}  
};  
  
// Reflection on Derived::meth will show DerivedTooAttribute   
// but not BaseOnlyAttribute.  
ref class Derived : public IBase {  
public:  
   virtual void meth() override {}  
};  
  
int main() {  
   IBase ^ pIB = gcnew Derived;  
  
   MemberInfo ^ pMI = pIB->GetType( )->GetMethod( "meth" );  
   array<Object ^> ^ pObjs = pMI->GetCustomAttributes( true );  
   Console::WriteLine( pObjs->Length ) ;  
}  
```  
  
  **2**   
## 请参阅  
 [Attributes Alphabetical Reference](../windows/attributes-alphabetical-reference.md)   
 [Custom Attributes](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)