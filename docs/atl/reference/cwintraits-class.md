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
ms.openlocfilehash: 840433ffb325a4f181848371306607b62373e75a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280455"
---
# <a name="cwintraits-class"></a>CWinTraits 类

此类提供方法来标准化创建窗口对象时所用的样式。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template <DWORD t_dwStyle = 0, DWORD t_dwExStyle = 0>  class CWinTraits
```

#### <a name="parameters"></a>参数

*t_dwStyle*<br/>
默认标准的窗口样式。

*t_dwExStyle*<br/>
默认扩展的窗口样式。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CWinTraits::GetWndExStyle](#getwndexstyle)|（静态）检索的扩展的样式`CWinTraits`对象。|
|[CWinTraits::GetWndStyle](#getwndstyle)|（静态）检索的标准样式`CWinTraits`对象。|

## <a name="remarks"></a>备注

这[窗口特征](../../atl/understanding-window-traits.md)类提供了简单的方法来标准化用创建 ATL 窗口对象的样式。 使用此类专用化作为模板参数[CWindowImpl](../../atl/reference/cwindowimpl-class.md)或另一个 ATL 的窗口类来指定有关所用的默认标准和扩展样式的窗口类的实例。

使用此模板时想要提供默认值，仅当没有其他样式指定在调用时将使用的窗口样式[CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create)。

ATL 提供了三个预定义的专用化的窗口样式的常用组合此模板：

- `CControlWinTraits`

   面向标准控件窗口。 使用以下标准样式：WS_CHILD、 WS_VISIBLE、 WS_CLIPCHILDREN 和 WS_CLIPSIBLINGS。 没有扩展的样式。

- `CFrameWinTraits`

   为标准的框架窗口设计。 所用的标准样式包括：WS_OVERLAPPEDWINDOW、 WS_CLIPCHILDREN 和 WS_CLIPSIBLINGS。 所用的扩展的样式包括：WS_EX_APPWINDOW 和 WS_EX_WINDOWEDGE。

- `CMDIChildWinTraits`

   适用于标准的 MDI 子窗口。 所用的标准样式包括：WS_OVERLAPPEDWINDOW、 WS_CHILD、 WS_VISIBLE，WS_CLIPCHILDREN 和 WS_CLIPSIBLINGS。 所用的扩展的样式包括：WS_EX_MDICHILD.

如果你想要确保同时允许根据每个实例，设置其他样式的窗口类的所有实例使用此选项设置特定的样式[CWinTraitsOR](../../atl/reference/cwintraitsor-class.md)相反。

## <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="getwndstyle"></a>  CWinTraits::GetWndStyle

调用此函数可检索的标准样式`CWinTraits`对象。

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
用于创建窗口的标准样式。 如果*dwStyle*为 0，模板样式值 (`t_dwStyle`) 返回。 如果*dwStyle*为非零值， *dwStyle*返回。

### <a name="return-value"></a>返回值

对象的标准的窗口样式。

##  <a name="getwndexstyle"></a>  CWinTraits::GetWndExStyle

调用此函数可检索的扩展的样式`CWinTraits`对象。

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>参数

*dwExStyle*<br/>
用于创建窗口的扩展的样式。 如果*dwExStyle*为 0，模板样式值 (`t_dwExStyle`) 返回。 如果*dwExStyle*为非零值， *dwExStyle*返回。

### <a name="return-value"></a>返回值

对象扩展的窗口样式。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)<br/>
[了解窗口特征](../../atl/understanding-window-traits.md)
