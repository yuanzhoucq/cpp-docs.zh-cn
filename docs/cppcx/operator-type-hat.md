---
title: 运算符 Type^
ms.date: 12/30/2016
ms.assetid: b24ffc83-0780-4f9a-8ee0-f5725db339d1
ms.openlocfilehash: 5b2c0b83533af62aa96fdc4b53f5762c6ca748a4
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422164"
---
# <a name="operator-type"></a>运算符 Type^

实现从 [Windows::UI::Xaml::Interop::TypeName](/uwp/api/windows.ui.xaml.interop.typename) 到 `Platform::Type`的转换。

## <a name="syntax"></a>语法

```cpp
Operator Type^(Windows::UI::Xaml::Interop::TypeName typeName);
```

### <a name="return-value"></a>返回值

给定 `Platform::Type` Windows::UI::Xaml::Interop::TypeName [时返回](/uwp/api/windows.ui.xaml.interop.typename)。

### <a name="remarks"></a>备注

`TypeName` 是表示类型信息的中性语言 Windows 运行时结构。 [Platform::Type](../cppcx/platform-type-class.md) 特定于 C++，无法通过应用程序二进制接口 (ABI) 传递。 下面是 `TypeName`在 [Navigate](/uwp/api/windows.ui.xaml.controls.frame.navigate) 函数中的一种用法：

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

### <a name="example"></a>示例

下一示例演示如何在 `TypeName` 和 `Type`之间转换。

```

// Convert from Type to TypeName
TypeName tn = TypeName(MainPage::typeid);

// Convert back from TypeName to Type
Type^ tx2 = (Type^)(tn);
```

## <a name="net-framework-equivalent"></a>.NET Framework 等效项

.NET framework 程序项目`TypeName`作为 <xref:System.Type>

### <a name="requirements"></a>要求

## <a name="see-also"></a>请参阅

[运算符 Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)<br/>
[Platform::Type 类](../cppcx/platform-type-class.md)