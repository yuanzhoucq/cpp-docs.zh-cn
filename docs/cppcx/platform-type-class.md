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
ms.openlocfilehash: 2c73967d287ade86e2657af70592845d2cc2085e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87185029"
---
# <a name="platformtype-class"></a>Platform::Type 类

包含有关类型的运行时信息，尤其是字符串名称和类型代码。 通过对任何对象调用[object：： GetType](../cppcx/platform-object-class.md#gettype) ，或对类或结构名称使用[typeid](../extensions/typeid-cpp-component-extensions.md)运算符来获得。

## <a name="syntax"></a>语法

```cpp
public ref class Platform::Type :
    Platform::Object, Platform::Details::IEquatable,
    Platform::Details::IPrintable
```

### <a name="remarks"></a>备注

`Type`类在必须通过使用 **`if`** **`switch`** 根据对象的运行时类型进行分支的或语句来直接处理的应用程序中很有用。 描述类型类别的类型代码是使用[type：： GetTypeCode](#gettypecode)成员函数检索的。

## <a name="public-methods"></a>公共方法

|||
|-|-|
|[Type::GetTypeCode 方法](#gettypecode)|返回对象的 [Platform::TypeCode 枚举](../cppcx/platform-typecode-enumeration.md) 值。|
|[Type：： ToString 方法](#tostring)|返回在其元数据中指定的类型的名称。|

## <a name="public-properties"></a>公共属性

|||
|-|-|
|[类型：： FullName](#fullname)|返回表示类型的完全限定名称的 [Platform::String 类](../cppcx/platform-string-class.md)^，并使用 . （点）作为分隔符，而不是：：（双冒号）-例如 `MyNamespace.MyClass` 。|

## <a name="conversion-operators"></a>转换运算符

|||
|-|-|
|[运算符类型 ^](../cppcx/operator-type-hat.md)|实现从 `Windows::UI::Xaml::Interop::TypeName` 到 `Platform::Type`的转换。|
|[运算符 Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)|实现从 `Platform::Type` 到 `Windows::UI::Xaml::Interop::TypeName`的转换。|

### <a name="requirements"></a>要求

**支持的最低客户端：** Windows 8

**支持的最低服务器：** Windows Server 2012

**命名空间：** Platform

**Metadata：** platform.string

## <a name="typefullname-property"></a><a name="fullname"></a>Type：： FullName 属性

检索窗体中当前类型的完全限定名称 `Namespace.Type` 。

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

## <a name="typegettypecode-method"></a><a name="gettypecode"></a>Type：： GetTypeCode 方法

检索内置类型数值类型类别。

### <a name="syntax"></a>语法

```cpp
Platform::TypeCode GetTypeCode();
```

### <a name="return-value"></a>返回值

Platform::TypeCode 枚举值之一。

### <a name="remarks"></a>备注

GetTypeCode （）成员方法的等效项是 **`typeid`** 属性。

## <a name="typetostring-method"></a><a name="tostring"></a>Type：： ToString 方法

检索类型的名称。

### <a name="syntax"></a>语法

```cpp
Platform::String^ ToString();
```

### <a name="return-value"></a>返回值

在其元数据中指定的类型的名称。

## <a name="see-also"></a>另请参阅

[Platform 命名空间](../cppcx/platform-namespace-c-cx.md)
