---
title: Platform::Object 类
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Object::Object
- VCCORLIB/Platform::Object::Equals
- VCCORLIB/Platform::Object::GetHashCode
- VCCORLIB/Platform::Object::ReferenceEquals
- VCCORLIB/Platform::ToString
- VCCORLIB/Platform::GetType
helpviewer_keywords:
- Object class
ms.assetid: 709e84a8-0bff-471b-bc14-63e424080b5a
ms.openlocfilehash: 8267d42e67ddf703b4a3a681509b92978e7de8bb
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422776"
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
|[Object::Equals](#equals)|确定指定的对象是否等于当前对象。|
|[Object::GetHashCode](#gethashcode)|返回此实例的哈希代码。|
|[Object::ReferenceEquals](#referenceequals)|确定指定对象实例是否为同一实例。|
|[ToString](#tostring)|返回表示当前对象的字符串。 可重写。|
|[GetType](#gettype)|获取描述当前实例的 [Platform::Type](../cppcx/platform-type-class.md) 。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`Object`

`Object`

### <a name="requirements"></a>要求

**标头：** vccorlib.h

**命名空间：** 平台

## <a name="equals"></a> Object:: equals 方法

确定指定的对象是否等于当前对象。

### <a name="syntax"></a>语法

```cpp
bool Equals(
    Object^ obj
)
```

### <a name="parameters"></a>参数

*obj*<br/>
要比较的对象。

### <a name="return-value"></a>返回值

**true**如果对象相等，否则**false**。

## <a name="gethashcode"></a>  Object:: gethashcode 方法

返回此实例的 `IUnknown`* 标识值（如果它是 COM 对象）或计算所得的哈希值（如果它不是 COM 对象）。

### <a name="syntax"></a>语法

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>返回值

唯一标识此对象的数值。

### <a name="remarks"></a>备注

可以在映射中使用 GetHashCode 创建对象的键。 可以通过使用比较哈希代码[object:: equals](#equals)。 如果代码路径极为重要，并且 `GetHashCode` 和 `Equals` 不足够快，则可以下降到基础 COM 层并执行本机 `IUnknown` 指针比较。

## <a name="gettype"></a>  Object:: gettype 方法

返回[platform:: type](../cppcx/platform-type-class.md)描述一个对象的运行时类型的对象。

### <a name="syntax"></a>语法

```cpp
Object::GetType();
```

### <a name="property-valuereturn-value"></a>属性值/返回值

一个[platform:: type](../cppcx/platform-type-class.md)描述对象的运行时类型的对象。

### <a name="remarks"></a>备注

静态[type:: gettypecode](../cppcx/platform-type-class.md#gettypecode)可用于获取[platform:: typecode 枚举](../cppcx/platform-typecode-enumeration.md)值，该值表示当前类型。 这对于内置类型通常很有用。 除了任何 ref 类的类型代码[platform:: string](../cppcx/platform-string-class.md)是对象 (1)。

[Windows::UI::Xaml::Interop::TypeName](/uwp/api/windows.ui.xaml.interop.typename)作为 Windows 组件和应用之间传递类型信息的独立于语言的方法在 Windows Api 中使用类。 T[platform:: type 类](../cppcx/platform-type-class.md)之间进行转换有运算符`Type`和`TypeName`。

使用[typeid](../windows/typeid-cpp-component-extensions.md)运算符可返回`Platform::Type`对象的类名，例如，XAML 页面之间导航时：

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

## <a name="ctor"></a>  Object:: object 构造函数

初始化该对象类的新实例。

### <a name="syntax"></a>语法

```cpp
public:Object();
```

## <a name="referenceequals"></a>  Object:: referenceequals 方法

确定指定对象实例是否为同一实例。

### <a name="syntax"></a>语法

```cpp
public:static bool ReferenceEquals(  Object^ obj1,   Object^ obj2);
```

### <a name="parameters"></a>参数

*obj1*<br/>
要比较的第一个对象。

*obj2*<br/>
要比较的第二个对象。

### <a name="return-value"></a>返回值

**true**如果两个对象都相同; 否则为**false**。

## <a name="tostring"></a>  Object:: tostring 方法 (C + + /cli CX)

返回表示当前对象的字符串。

### <a name="syntax"></a>语法

```cpp
public:
virtual String^ ToString();
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

[平台 Namespace](platform-namespace-c-cx.md)<br/>
[Platform::Type 类](platform-type-class.md)<br/>
[类型系统](type-system-c-cx.md)
