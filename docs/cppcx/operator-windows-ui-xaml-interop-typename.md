---
title: 运算符 Windows::UI::Xaml::Interop::TypeName
ms.date: 12/30/2016
ms.assetid: a65a105e-7e3a-452f-932f-2cdaf00fbba5
ms.openlocfilehash: 5acf17b7c87a71259dba6579d8ee69e0eea86fa5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161584"
---
# <a name="operator-windowsuixamlinteroptypename"></a>运算符 Windows::UI::Xaml::Interop::TypeName

实现从 `Platform::Type` 到 [Windows::UI::Xaml::Interop::TypeName](/uwp/api/windows.ui.xaml.interop.typename)的转换。

## <a name="syntax"></a>语法

```cpp
Operator TypeName(Platform::Type^ type);
```

### <a name="return-value"></a>返回值

给定 [时返回](/uwp/api/windows.ui.xaml.interop.typename) Windows::UI::Xaml::Interop::TypeName `Platform::Type^`。

### <a name="remarks"></a>备注

`TypeName` 是表示类型信息的中性语言 Windows 运行时结构。 [Platform::Type](../cppcx/platform-type-class.md) 特定于 C++，无法通过应用程序二进制接口 (ABI) 传递。 下面是 `TypeName`在 [Navigate](/uwp/api/windows.ui.xaml.controls.frame.navigate) 函数中的一种用法：

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

### <a name="example"></a>示例

下一示例演示如何在 `TypeName` 和 `Type`之间转换。

```

// Convert from Type to TypeName
Windows::UI::Xaml::Interop::TypeName tn = TypeName(MainPage::typeid);

// Convert back from TypeName to Type
Type^ tx2 = (Type^)(tn);
```

## <a name="net-framework-equivalent"></a>.NET Framework 等效项

.NET Framework 程序将 `TypeName` 投影为 [System.Type](assetId:///System.Type?qualifyHint=False&autoUpgrade=True)的转换。

### <a name="requirements"></a>要求

## <a name="see-also"></a>请参阅

[运算符 Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)<br/>
[Platform::Type 类](../cppcx/platform-type-class.md)
