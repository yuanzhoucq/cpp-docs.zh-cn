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
ms.openlocfilehash: 77313f8c4dcc87fa9de852afe2d60e614f8fc3a3
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423668"
---
# <a name="platformobject-class"></a>Platform::Object 类

在 Windows 运行时应用程序中提供 ref 类和 ref 结构的常见行为。 所有 ref 类和 ref 结构实例都可以隐式转换为 Platform::Object^，并且可以重写其虚拟 ToString 方法。

## <a name="syntax"></a>语法

```cpp
public ref class Object : Object
```

### <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[Object：： Object](#ctor)|初始化该对象类的新实例。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[Object：： Equals](#equals)|确定指定对象是否等于当前对象。|
|[Object：： GetHashCode](#gethashcode)|返回此实例的哈希代码。|
|[Object：： ReferenceEquals](#referenceequals)|确定指定对象实例是否为同一实例。|
|[ToString](#tostring)|返回表示当前对象的字符串。 可重写。|
|[GetType](#gettype)|获取描述当前实例的 [Platform::Type](../cppcx/platform-type-class.md) 。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`Object`

`Object`

### <a name="requirements"></a>要求

**标头：** vccorlib.h

**命名空间：** Platform

## <a name="equals"></a>Object：： Equals 方法

确定指定对象是否等于当前对象。

### <a name="syntax"></a>语法

```cpp
bool Equals(
    Object^ obj
)
```

### <a name="parameters"></a>parameters

obj<br/>
要比较的对象。

### <a name="return-value"></a>返回值

如果对象相等，**则为 true** ; 否则为**false**。

## <a name="gethashcode"></a>Object：： GetHashCode 方法

返回此实例的 `IUnknown`* 标识值（如果它是 COM 对象）或计算所得的哈希值（如果它不是 COM 对象）。

### <a name="syntax"></a>语法

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>返回值

唯一标识此对象的数值。

### <a name="remarks"></a>备注

可以在映射中使用 GetHashCode 创建对象的键。 您可以通过使用[Object：： Equals](#equals)来比较哈希代码。 如果代码路径极为重要，并且 `GetHashCode` 和 `Equals` 不足够快，则可以下降到基础 COM 层并执行本机 `IUnknown` 指针比较。

## <a name="gettype"></a>Object：： GetType 方法

返回描述对象的运行时类型的[Platform：： Type](../cppcx/platform-type-class.md)对象。

### <a name="syntax"></a>语法

```cpp
Object::GetType();
```

### <a name="property-valuereturn-value"></a>属性值/返回值

描述对象的运行时类型的[Platform：： Type](../cppcx/platform-type-class.md)对象。

### <a name="remarks"></a>备注

静态[类型：： GetTypeCode](../cppcx/platform-type-class.md#gettypecode)可用于获取表示当前类型的[Platform：： TypeCode 枚举](../cppcx/platform-typecode-enumeration.md)值。 这对于内置类型通常很有用。 任何 ref 类（ [Platform：： String](../cppcx/platform-string-class.md)除外）的类型代码均为 Object （1）。

Windows [：： UI：： Xaml：： Interop：： TypeName](/uwp/api/windows.ui.xaml.interop.typename)类在 windows api 中用作在 windows 组件和应用之间传递类型信息的独立于语言的方式。 T[Platform：： Type 类](../cppcx/platform-type-class.md)具有在 `Type` 和 `TypeName`之间进行转换的运算符。

使用[typeid](../extensions/typeid-cpp-component-extensions.md)运算符可返回类名称的 `Platform::Type` 对象，例如在 XAML 页面之间导航时：

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

## <a name="ctor"></a>Object：： Object 构造函数

初始化该对象类的新实例。

### <a name="syntax"></a>语法

```cpp
public:Object();
```

## <a name="referenceequals"></a>Object：： ReferenceEquals 方法

确定指定对象实例是否为同一实例。

### <a name="syntax"></a>语法

```cpp
public:static bool ReferenceEquals(  Object^ obj1,   Object^ obj2);
```

### <a name="parameters"></a>parameters

*obj1*<br/>
要比较的第一个对象。

*obj2*<br/>
要比较的第二个对象。

### <a name="return-value"></a>返回值

如果两个对象相同，则为**true** ;否则**为 false**。

## <a name="tostring"></a>Object：： ToString 方法（C++/cx）

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

## <a name="see-also"></a>另请参阅

[平台命名空间](platform-namespace-c-cx.md)<br/>
[Platform::Type 类](platform-type-class.md)<br/>
[类型系统](type-system-c-cx.md)
