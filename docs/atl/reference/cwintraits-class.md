---
title: CWinTraits 类
ms.date: 11/04/2016
f1_keywords:
- CWinTraits
- ATLWIN/ATL::CWinTraits
- ATLWIN/ATL::CWinTraits::GetWndExStyle
- ATLWIN/ATL::CWinTraits::GetWndStyle
helpviewer_keywords:
- CMDIChildWinTraits class
- window styles, default values for ATL
- CWinTraits class
- CFrameWinTraits class
- CControlWinTraits class
ms.assetid: f78f486e-6d9c-42c6-8e86-371e05aa7e59
ms.openlocfilehash: fd73f733e4eff21da92937d1e1b0cce21552a48c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330302"
---
# <a name="cwintraits-class"></a>CWinTraits 类

此类提供了一种用于标准化创建窗口对象时使用的样式的方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <DWORD t_dwStyle = 0, DWORD t_dwExStyle = 0>  class CWinTraits
```

#### <a name="parameters"></a>参数

*t_dwStyle*<br/>
默认标准窗口样式。

*t_dwExStyle*<br/>
默认扩展窗口样式。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CWinTraits：获取WndEx样式](#getwndexstyle)|（静态）检索`CWinTraits`对象的扩展样式。|
|[CWinTraits：获取温德风格](#getwndstyle)|（静态）检索`CWinTraits`对象的标准样式。|

## <a name="remarks"></a>备注

此[窗口特征类](../../atl/understanding-window-traits.md)提供了一种用于标准化用于创建 ATL 窗口对象的样式的简单方法。 将此类的专门化用作[CWindowImpl](../../atl/reference/cwindowimpl-class.md)或其他 ATL 窗口类的模板参数，以指定用于该窗口类实例的默认标准和扩展样式。

如果要提供默认窗口样式，仅当对[CWindowImpl：：create](../../atl/reference/cwindowimpl-class.md#create)调用时未指定其他样式时，才使用此模板。

ATL 为此模板的三个预定义专门化功能为常用的窗口样式组合：

- `CControlWinTraits`

   专为标准控制窗口而设计。 使用以下标准样式：WS_CHILD、WS_VISIBLE、WS_CLIPCHILDREN和WS_CLIPSIBLINGS。 没有扩展样式。

- `CFrameWinTraits`

   专为标准框架窗口而设计。 使用的标准样式包括：WS_OVERLAPPEDWINDOW、WS_CLIPCHILDREN 和WS_CLIPSIBLINGS。 使用的扩展样式包括：WS_EX_APPWINDOW和WS_EX_WINDOWEDGE。

- `CMDIChildWinTraits`

   专为标准 MDI 子窗口而设计。 使用的标准样式包括：WS_OVERLAPPEDWINDOW、WS_CHILD、WS_VISIBLE、WS_CLIPCHILDREN和WS_CLIPSIBLINGS。 使用的扩展样式包括：WS_EX_MDICHILD。

如果要确保为窗口类的所有实例设置某些样式，同时允许基于每个实例设置其他样式，请使用[CWinTraitsOR。](../../atl/reference/cwintraitsor-class.md)

## <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="cwintraitsgetwndstyle"></a><a name="getwndstyle"></a>CWinTraits：获取温德风格

调用此函数以检索`CWinTraits`对象的标准样式。

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
用于创建窗口的标准样式。 如果*dwStyle*为 0，则返回`t_dwStyle`模板样式值 （ ） 。 如果*dwStyle*是非零，则返回*dwStyle。*

### <a name="return-value"></a>返回值

对象的标准窗口样式。

## <a name="cwintraitsgetwndexstyle"></a><a name="getwndexstyle"></a>CWinTraits：获取WndEx样式

调用此函数以检索`CWinTraits`对象的扩展样式。

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>参数

*dwExStyle*<br/>
用于创建窗口的扩展样式。 如果*dwExStyle*为 0，则返回`t_dwExStyle`模板样式值 （ ） 。 如果*dwExStyle*是非零，则返回*dwExStyle。*

### <a name="return-value"></a>返回值

对象的扩展窗口样式。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)<br/>
[了解窗口特征](../../atl/understanding-window-traits.md)
