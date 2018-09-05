---
title: CWinTraitsOR 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR::GetWndExStyle
- ATLWIN/ATL::CWinTraitsOR::GetWndStyle
dev_langs:
- C++
helpviewer_keywords:
- CWinTraitsOR class
- window styles, default values for ATL
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e837e15f934e53f7b1d06a94efb4a320f2e8407
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757889"
---
# <a name="cwintraitsor-class"></a>CWinTraitsOR 类

此类提供方法来标准化创建窗口对象时所用的样式。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template <DWORD t_dwStyle = 0,
          DWORD t_dwExStyle = 0, 
          class TWinTraits = CControlWinTraits>
class CWinTraitsOR
```

#### <a name="parameters"></a>参数

*t_dwStyle*  
默认窗口样式。

*t_dwExStyle*  
默认扩展的窗口样式。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CWinTraitsOR::GetWndExStyle](#getwndexstyle)|检索的扩展的样式`CWinTraitsOR`对象。|
|[CWinTraitsOR::GetWndStyle](#getwndstyle)|检索的标准样式`CWinTraitsOR`对象。|

## <a name="remarks"></a>备注

这[窗口特征](../../atl/understanding-window-traits.md)类提供了简单的方法来标准化用创建 ATL 窗口对象的样式。 使用此类专用化作为模板参数[CWindowImpl](../../atl/reference/cwindowimpl-class.md)或另一个 ATL 的窗口类来指定要用于的标准和扩展样式的最小集的窗口类的实例。

如果你想要确保特定的样式设置的所有实例的窗口类同时允许其他样式设置对的调用中根据每个实例，请使用此模板的专用化[CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create)。

如果你想要提供默认值，仅当没有其他样式指定在调用时将使用的窗口样式`CWindowImpl::Create`，使用[CWinTraits](../../atl/reference/cwintraits-class.md)相反。

## <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="getwndstyle"></a>  CWinTraitsOR::GetWndStyle

调用此函数可检索 （使用逻辑 OR 运算符） 的标准样式的组合`CWinTraits`对象和指定的默认样式*t_dwStyle*。

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>参数

*dwStyle*  
用于创建窗口的样式。

### <a name="return-value"></a>返回值

传入的样式的组合*dwStyle*和与指定的默认`t_dwStyle`，使用逻辑 OR 运算符。

##  <a name="getwndexstyle"></a>  CWinTraitsOR::GetWndExStyle

调用此函数可检索 （使用逻辑 OR 运算符） 的扩展样式的组合`CWinTraits`对象和指定的默认样式`t_dwStyle`。

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>参数

*dwExStyle*  
用于创建窗口的扩展的样式。

### <a name="return-value"></a>返回值

传入的扩展样式的组合*dwExStyle*和默认的由指定`t_dwExStyle`，使用逻辑 OR 运算符

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)   
[了解窗口特征](../../atl/understanding-window-traits.md)

