---
title: CWinTraitsOR 类
ms.date: 11/04/2016
f1_keywords:
- CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR::GetWndExStyle
- ATLWIN/ATL::CWinTraitsOR::GetWndStyle
helpviewer_keywords:
- CWinTraitsOR class
- window styles, default values for ATL
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
ms.openlocfilehash: 825f79190c6f68cd1372154e4e02f430f545aa48
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330287"
---
# <a name="cwintraitsor-class"></a>CWinTraitsOR 类

此类提供了一种用于标准化创建窗口对象时使用的样式的方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <DWORD t_dwStyle = 0,
          DWORD t_dwExStyle = 0,
          class TWinTraits = CControlWinTraits>
class CWinTraitsOR
```

#### <a name="parameters"></a>参数

*t_dwStyle*<br/>
默认窗口样式。

*t_dwExStyle*<br/>
默认扩展窗口样式。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CWinTraitsOR：获取WndEx样式](#getwndexstyle)|检索`CWinTraitsOR`对象的扩展样式。|
|[CWinTraitsOR：获得温德风格](#getwndstyle)|检索`CWinTraitsOR`对象的标准样式。|

## <a name="remarks"></a>备注

此[窗口特征类](../../atl/understanding-window-traits.md)提供了一种用于标准化用于创建 ATL 窗口对象的样式的简单方法。 将此类的专门化用作[CWindowImpl](../../atl/reference/cwindowimpl-class.md)或其他 ATL 窗口类的模板参数，以指定要用于该窗口类实例的最小标准和扩展样式集。

如果要确保为窗口类的所有实例设置某些样式，同时允许在调用[CWindowImpl：：Create](../../atl/reference/cwindowimpl-class.md#create)中按实例设置其他样式，请使用此模板的专用化。

如果要提供默认窗口样式，仅当调用 中`CWindowImpl::Create`未指定其他样式时才会使用，请改用[CWinTraits。](../../atl/reference/cwintraits-class.md)

## <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="cwintraitsorgetwndstyle"></a><a name="getwndstyle"></a>CWinTraitsOR：获得温德风格

调用此函数以检索`CWinTraits`对象的标准样式和*t_dwStyle*指定的默认样式的组合（使用逻辑 OR 运算符）。

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
用于创建窗口的样式。

### <a name="return-value"></a>返回值

使用 逻辑 OR 运算符在*dwStyle*中传递的样式`t_dwStyle`和 指定的默认样式的组合。

## <a name="cwintraitsorgetwndexstyle"></a><a name="getwndexstyle"></a>CWinTraitsOR：获取WndEx样式

调用此函数以检索`CWinTraits`对象扩展样式和 指定的`t_dwStyle`默认样式的组合（使用逻辑 OR 运算符）。

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>参数

*dwExStyle*<br/>
用于创建窗口的扩展样式。

### <a name="return-value"></a>返回值

使用 逻辑 OR 运算符在*dwExStyle*中传递的扩展`t_dwExStyle`样式和指定的默认样式的组合

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)<br/>
[了解窗口特征](../../atl/understanding-window-traits.md)
