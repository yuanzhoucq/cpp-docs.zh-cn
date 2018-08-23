---
title: 属性 |Microsoft Docs
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
ms.openlocfilehash: 69ec1c9e1b3e30e68bf7199f7a70cb7d329ee040
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603636"
---
# <a name="attribute"></a>attribute

可以创建自定义属性。

## <a name="syntax"></a>语法

```cpp
[ attribute(
   AllowOn,
   AllowMultiple=boolean,
   Inherited=boolean
) ]
```

### <a name="parameters"></a>参数

*AllowOn*  
指定自定义的特性可以应用于的语言元素。 默认值是`System::AttributeTargets::All`(请参阅[System::AttributeTargets](https://msdn.microsoft.com/library/system.attributetargets.aspx))。

*AllowMultiple*  
指定是否可以重复应用自定义属性构造。 默认值为 FALSE。

*继承*  
指示该特性将由子类继承。 编译器不提供特殊支持此功能;它是作业的属性使用者 (`Reflection`，例如) 遵循此信息。 如果*继承*为 TRUE，结果为继承该属性。 如果*AllowMultiple*为 TRUE，如果该属性将派生的成员; 上累积*AllowMultiple*为 FALSE 时，属性将重写 （或替换） 中继承。 如果*继承*为 FALSE 时，该属性不能被继承。 默认值为 TRUE。

## <a name="remarks"></a>备注

> [!NOTE]
> **特性**属性现已弃用。  使用公共语言运行时属性`System.Attribute`到直接来创建用户定义的特性。 有关详细信息，请参阅[用户定义的特性](../windows/user-defined-attributes-cpp-component-extensions.md)。

您定义[自定义特性](../windows/custom-attributes-cpp.md)上来**属性**上托管的类或结构定义的属性。 类的名称是自定义属性。 例如：

```cpp
[ attribute(Parameter) ]
public ref class MyAttr {};
```

定义一个名为属性`MyAttr`，可以应用于函数参数。 类必须是公共的如果该属性将用于在其他程序集。

> [!NOTE]
> 若要防止命名空间冲突，所有特性名称隐式都结尾"属性";在此示例中，属性和类名称实际上是`MyAttrAttribute`，但`MyAttr`和`MyAttrAttribute`可以互换使用。

类的公共构造函数定义特性的未命名的参数。 重载的构造函数允许通过多种方式指定属性，因此是一个自定义属性的定义方法如下：

```cpp
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

类的公共数据成员和属性是属性的可选命名的参数：

```cpp
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

请参阅[用户定义的特性](../windows/user-defined-attributes-cpp-component-extensions.md)特性目标有关的讨论。

**特性**属性具有*AllowMultiple*指定自定义属性是否是一次性使用的参数或 multiuse （可以出现不止一次相同的实体）。

```cpp
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

自定义特性类派生直接或间接从<xref:System.ComponentModel.AttributeCollection.%23ctor%2A>，这样标识快速而简单的元数据中的特性定义。 **特性**属性表示从继承`System::Attribute`，因此不需要显式派生：

```cpp
[ attribute(Class) ]
ref class MyAttr
```

等效于

```cpp
[ attribute(Class) ]
ref class MyAttr : System::Attribute   // OK, but redundant.
```

**特性**是其别名<xref:System.AttributeUsageAttribute?displayProperty=fullName>(不 AttributeAttribute; 这是属性命名规则的例外)。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**ref 类**， **ref 结构**|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。

## <a name="example"></a>示例

```cpp
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

`Inherited`命名的参数指定是否在基类上应用的自定义属性将显示在派生类的反射。

```cpp
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

[按字母顺序的特性参考](../windows/attributes-alphabetical-reference.md)  
[自定义属性](http://msdn.microsoft.com/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)