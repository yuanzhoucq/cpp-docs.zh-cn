---
title: 'Platform:: object 类 |Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Object::Object
- VCCORLIB/Platform::Object::Equals
- VCCORLIB/Platform::Object::GetHashCode
- VCCORLIB/Platform::Object::ReferenceEquals
- VCCORLIB/Platform::ToString
- VCCORLIB/Platform::GetType
dev_langs:
- C++
helpviewer_keywords:
- Object class
ms.assetid: 709e84a8-0bff-471b-bc14-63e424080b5a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 19c302f08485b6db89ea2a6b66106244ed95b48c
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601733"
---
# <a name="platformobject-class"></a>Platform::Object 类
提供 ref 类和 ref 结构在 Windows 运行时应用中的通用行为。 所有 ref 类和 ref 结构实例都可以隐式转换为 Platform::Object^，并且可以重写其虚拟 ToString 方法。  
  
## <a name="syntax"></a>语法  
  
```cpp  
public ref class Object : Object  
```  
  
### <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[Object::Object](#ctor)|初始化该对象类的新实例。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Object:: equals](#equals)|确定指定的对象是否等于当前对象。|  
|[Object::GetHashCode](#gethashcode)|返回此实例的哈希代码。|  
|[Object:: referenceequals](#referenceequals)|确定指定对象实例是否为同一实例。|  
|[ToString](#tostring)|返回表示当前对象的字符串。 可重写。|  
|[GetType](#gettype)|获取描述当前实例的 [Platform::Type](../cppcx/platform-type-class.md) 。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `Object`  
  
 `Object`  
  
### <a name="requirements"></a>要求  
 **标头：** vccorlib.h  
  
 **命名空间：** Platform  

  
## <a name="equals"></a> Object:: equals 方法
确定指定的对象是否等于当前对象。  
  
### <a name="syntax"></a>语法  
  
```cpp  
  
bool Equals(  
    Object^ obj  
)  
```  
  
### <a name="parameters"></a>参数  
 obj  
 要比较的对象。  
  
### <a name="return-value"></a>返回值  
 如果对象相等，则为`true` ；否则为 `false`。  
  


## <a name="gethashcode"></a>  Object:: gethashcode 方法
返回此实例的 `IUnknown`* 标识值（如果它是 COM 对象）或计算所得的哈希值（如果它不是 COM 对象）。  
  
### <a name="syntax"></a>语法  
  
```cpp  
public:int GetHashCode()  
```  
  
### <a name="return-value"></a>返回值  
 唯一标识此对象的数值。  
  
### <a name="remarks"></a>备注  
 可以在映射中使用 GetHashCode 创建对象的键。 可以通过使用比较哈希代码[object:: equals](#equals)。 如果代码路径极为重要，并且 `GetHashCode` 和 `Equals` 不足够快，则可以下降到基础 COM 层并执行本机 `IUnknown` 指针比较。  
  


## <a name="gettype"></a>  Object:: gettype 方法
返回[platform:: type](../cppcx/platform-type-class.md)描述一个对象的运行时类型的对象。  
  
### <a name="syntax"></a>语法  
  
```cpp  
Object::GetType()  
```  

  
### <a name="property-valuereturn-value"></a>属性值/返回值  
 一个[platform:: type](../cppcx/platform-type-class.md)描述对象的运行时类型的对象。  
  
### <a name="remarks"></a>备注  
 静态[type:: gettypecode](../cppcx/platform-type-class.md#gettypecode)可用于获取[platform:: typecode 枚举](../cppcx/platform-typecode-enumeration.md)值，该值表示当前类型。 这对于内置类型通常很有用。 除了任何 ref 类的类型代码[platform:: string](../cppcx/platform-string-class.md)是对象 (1)。  
  
 [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx)作为 Windows 组件和应用之间传递类型信息的独立于语言的方法在 Windows Api 中使用类。 T[platform:: type 类](../cppcx/platform-type-class.md)之间进行转换有运算符`Type`和`TypeName`。  
  
 使用[typeid](../windows/typeid-cpp-component-extensions.md)运算符可返回`Platform::Type`对象的类名，例如，XAML 页面之间导航时：  
  
```  
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);  
```  
  
## <a name="see-also"></a>请参阅  
 [Platform:: type 类](../cppcx/platform-type-class.md)   
 [平台命名空间](../cppcx/platform-namespace-c-cx.md)   
 [类型系统](../cppcx/type-system-c-cx.md
  
## <a name="ctor"></a>  Object:: object 构造函数
初始化该对象类的新实例。  
  
### <a name="syntax"></a>语法  
  
```cpp  
public:Object()  
```  

## <a name="referenceequals"></a>  Object:: referenceequals 方法
确定指定对象实例是否为同一实例。  
  
### <a name="syntax"></a>语法  
  
```cpp  
public:static bool ReferenceEquals(  Object^ obj1,   Object^ obj2)  
```  
  
### <a name="parameters"></a>参数  
 obj1  
 要比较的第一个对象。  
  
 obj2  
 要比较的第二个对象。  
  
### <a name="return-value"></a>返回值  
 如果两个对象相同，则为 `true`；否则为 `false`。  
 
## <a name="tostring"></a>  Object:: tostring 方法 (C + + /cli CX)
返回表示当前对象的字符串。  
  
### <a name="syntax"></a>语法  
  
```cpp  
public:  
virtual String^ ToString()  
```  
  
### <a name="return-value"></a>返回值  
 表示当前对象的字符串。 您可以重写此方法以便在 ref 类或结构中提供自定义的字符串消息：  
  
```cpp  
public ref class Tree sealed  
{  
public:  
    Tree(){}  
    virtual Platform::String^ ToString() override  
    {  
      return "I’m a Tree";  
    };  
};  
```  
## <a name="see-also"></a>请参阅  
 [平台 Namespace](platform-namespace-c-cx.md)