---
title: Platform::Type 类
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Type::GetTypeCode
- VCCORLIB/Platform::Type::FullName
helpviewer_keywords:
- Platform::Type Class
ms.assetid: d6b03f1e-b240-49b9-a08e-53a460030475
ms.openlocfilehash: 7463a2518e6ec5cc84f59db05cfaf60e43eb9fde
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322090"
---
# <a name="platformtype-class"></a>Platform::Type 类

包含有关类型的运行时信息，尤其是字符串名称和类型代码。 通过调用[Object：：getType](../cppcx/platform-object-class.md#gettype)在任何对象上或使用类或结构名称上的[typeid](../extensions/typeid-cpp-component-extensions.md)运算符获得。

## <a name="syntax"></a>语法

```cpp
public ref class Platform::Type :
    Platform::Object, Platform::Details::IEquatable,
    Platform::Details::IPrintable
```

### <a name="remarks"></a>备注

对于必须使用基于对象的运行时类型进行分支的 `Type` 或 `if` 语句来直接处理的应用程序， `switch` 类非常有用。 使用[Type：：GetTypeCode](#gettypecode)成员函数检索描述类型类别的类型代码。

## <a name="public-methods"></a>公共方法

|||
|-|-|
|[Type::GetTypeCode 方法](#gettypecode)|返回对象的 [Platform::TypeCode 枚举](../cppcx/platform-typecode-enumeration.md) 值。|
|[类型：：到字符串方法](#tostring)|返回其元数据中指定的类型的名称。|

## <a name="public-properties"></a>公共属性

|||
|-|-|
|[类型：全名](#fullname)|返回表示类型的完全限定名称的 [Platform::String 类](../cppcx/platform-string-class.md)^，并使用 . （点）作为分隔符，而不是 ：： （双冒号） * 例如`MyNamespace.MyClass`。|

## <a name="conversion-operators"></a>转换运算符

|||
|-|-|
|[运算符类型*](../cppcx/operator-type-hat.md)|实现从 `Windows::UI::Xaml::Interop::TypeName` 到 `Platform::Type`的转换。|
|[运算符 Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)|实现从 `Platform::Type` 到 `Windows::UI::Xaml::Interop::TypeName`的转换。|

### <a name="requirements"></a>要求

**受支持的最小客户端：** 视窗 8

**受支持的服务器最少：** 视窗服务器 2012

**命名空间：** Platform

**元数据：** 平台.winmd

## <a name="typefullname-property"></a><a name="fullname"></a>类型：：全名属性

检索窗体`Namespace.Type`中当前类型的完全限定名称。

### <a name="syntax"></a>语法

```cpp
String^ FullName();
```

### <a name="return-value"></a>返回值

类型的名称。

### <a name="example"></a>示例

```cpp
//  namespace is TestApp
MainPage::MainPage()
{
    InitializeComponent();
    Type^ t = this->GetType();
    auto s = t->FullName; // returns "TestApp.MainPage"
    auto s2 = t->ToString(); //also returns "TestApp.MainPage"
}
```

## <a name="typegettypecode-method"></a><a name="gettypecode"></a>类型：获取类型代码方法

检索内置类型数值类型类别。

### <a name="syntax"></a>语法

```cpp
Platform::TypeCode GetTypeCode();
```

### <a name="return-value"></a>返回值

Platform::TypeCode 枚举值之一。

### <a name="remarks"></a>备注

GetTypeCode() 成员方法等效于 `typeid` 属性。

## <a name="typetostring-method"></a><a name="tostring"></a>类型：：到字符串方法

检索类型的名称。

### <a name="syntax"></a>语法

```cpp
Platform::String^ ToString();
```

### <a name="return-value"></a>返回值

在其元数据中指定的类型的名称。

## <a name="see-also"></a>另请参阅

[Platform 命名空间](../cppcx/platform-namespace-c-cx.md)
