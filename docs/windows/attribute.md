---
title: 属性 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.attribute
dev_langs:
- C++
helpviewer_keywords:
- __typeof keyword
- custom attributes, creating
- attribute attribute
- attributes [C++], custom
ms.assetid: 8cb3489f-65c4-44ea-b0aa-3c3c6b15741d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9826b689e2b8a640efe66e8625b97b3cec347acf
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33862057"
---
# <a name="attribute"></a>属性
允许你创建的自定义特性。  
  
## <a name="syntax"></a>语法  
  
```  
  
      [ attribute(  
   AllowOn,  
   AllowMultiple=boolean,  
   Inherited=boolean  
) ]  
```  
  
#### <a name="parameters"></a>参数  
 *AllowOn*  
 指定自定义特性可以应用的语言元素。 默认值是**System::AttributeTargets::All** (请参阅[System::AttributeTargets](https://msdn.microsoft.com/en-us/library/system.attributetargets.aspx))。  
  
 `AllowMultiple`  
 指定是否可以重复应用自定义属性到一个构造。 默认值是**FALSE**。  
  
 `Inherited`  
 指示是否该特性将由子类继承。 编译器不提供特殊支持此功能;它是属性使用者 （例如反射） 的工作以遵守此信息。 如果`Inherited`是**TRUE**，继承属性。 如果`AllowMultiple`是**TRUE**，该属性将累积派生成员; 上，如果`AllowMultiple`是**FALSE**，该属性将重写 （或替换） 中继承。 如果`Inherited`是**FALSE**，该属性不能被继承。 默认值是**TRUE**。  
  
## <a name="remarks"></a>备注  
  
> [!NOTE]
>  `attribute`属性现已弃用。  使用直接到公共语言运行时属性 System.Attribute 创建用户定义的特性。  有关详细信息，请参阅[用户定义的特性](../windows/user-defined-attributes-cpp-component-extensions.md)。  
  
 你定义[自定义特性](../windows/custom-attributes-cpp.md)放置`attribute`上托管的类或结构定义的属性。 类的名称是自定义特性。 例如：  
  
```  
[ attribute(Parameter) ]  
public ref class MyAttr {};  
```  
  
 定义一个称为 MyAttr 可以应用于函数参数的属性。 类必须是公共的如果该属性将在其他程序集中使用。  
  
> [!NOTE]
>  若要防止命名空间冲突，所有的属性名称隐式结尾"属性";在此示例中，属性和类的名称是实际 MyAttrAttribute，但可以互换使用 MyAttr 和 MyAttrAttribute。  
  
 类的公共构造函数定义该特性的未命名的参数。 重载的构造函数允许指定特性，因此是的自定义特性定义按以下方式通过多种方式：  
  
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
  
 类的公共数据成员和属性是该特性的可选命名的参数：  
  
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
  
 有关可能属性参数类型的列表，请参阅[自定义特性](../windows/custom-attributes-cpp.md)。  
  
 请参阅[用户定义的特性](../windows/user-defined-attributes-cpp-component-extensions.md)有关特性目标的讨论。  
  
 `attribute`属性具有`AllowMultiple`指定自定义属性是否为一次性使用的参数或 multiuse （可以多次出现相同的实体）。  
  
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
  
 自定义特性类派生直接或间接从<xref:System.ComponentModel.AttributeCollection.%23ctor%2A>，这样标识快速而简单的元数据中的属性定义。 `attribute`特性意味着从 system:: attribute，继承，因此不需要显式派生：  
  
```  
[ attribute(Class) ]  
ref class MyAttr  
```  
  
 等效于  
  
```  
[ attribute(Class) ]  
ref class MyAttr : System::Attribute   // OK, but redundant.  
```  
  
 `attribute` 是的别名<xref:System.AttributeUsageAttribute?displayProperty=fullName>(不 AttributeAttribute; 这是属性命名规则的例外)。  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|`ref` **类**， **ref 结构**|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="example"></a>示例  
  
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
  
## <a name="example"></a>示例  
 `Inherited`命名自变量指定是否在基类上应用的自定义特性将显示在派生类的反射。  
  
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
  
```Output  
2  
```  
  
## <a name="see-also"></a>请参阅  
 [按字母顺序排列的特性参考](../windows/attributes-alphabetical-reference.md)   
 [自定义特性](http://msdn.microsoft.com/en-us/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)