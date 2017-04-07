---
title: "CWinTraits 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinTraits
- ATLWIN/ATL::CWinTraits
- ATLWIN/ATL::CWinTraits::GetWndExStyle
- ATLWIN/ATL::CWinTraits::GetWndStyle
dev_langs:
- C++
helpviewer_keywords:
- CMDIChildWinTraits class
- window styles, default values for ATL
- CWinTraits class
- CFrameWinTraits class
- CControlWinTraits class
ms.assetid: f78f486e-6d9c-42c6-8e86-371e05aa7e59
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: abd62b916f976721bf85fc4bb2a94ffaf5b217ea
ms.lasthandoff: 02/24/2017

---
# <a name="cwintraits-class"></a>CWinTraits 类
此类提供方法来标准化时创建窗口对象使用的样式。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
template <DWORD t_dwStyle = 0, DWORD t_dwExStyle = 0>  class CWinTraits
```  
  
#### <a name="parameters"></a>参数  
 `t_dwStyle`  
 默认标准的窗口样式。  
  
 `t_dwExStyle`  
 扩展窗口样式的默认值。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CWinTraits::GetWndExStyle](#getwndexstyle)|（静态）检索的扩展的样式`CWinTraits`对象。|  
|[CWinTraits::GetWndStyle](#getwndstyle)|（静态）检索的标准样式`CWinTraits`对象。|  
  
## <a name="remarks"></a>备注  
 这[窗口特性](../../atl/understanding-window-traits.md)类提供了简单的方法，来标准化用于创建 ATL 窗口对象的样式。 专用化此类用作模板参数[CWindowImpl](../../atl/reference/cwindowimpl-class.md)或另一个 ATL 的窗口类指定使用的默认标准和扩展样式窗口类的实例。  
  
 当您想要提供将仅在对的调用中不指定的任何其他样式时使用的窗口样式的默认使用此模板[CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create)。  
  
 ATL 提供三个预定义的模板的专用化此常用组合的窗口样式︰  
  
 `CControlWinTraits`  
 为标准控件窗口设计。 使用以下标准样式︰ **WS_CHILD**， **WS_VISIBLE**， **WS_CLIPCHILDREN**，和**WS_CLIPSIBLINGS**。 没有扩展的样式。  
  
 `CFrameWinTraits`  
 为标准的框架窗口而设计。 使用的标准样式包括︰ **WS_OVERLAPPEDWINDOW**， **WS_CLIPCHILDREN**，和**WS_CLIPSIBLINGS**。 使用的扩展的样式包括︰ **WS_EX_APPWINDOW**和**WS_EX_WINDOWEDGE**。  
  
 `CMDIChildWinTraits`  
 为标准的 MDI 子窗口设计。 使用的标准样式包括︰ **WS_OVERLAPPEDWINDOW**， **WS_CHILD**， **WS_VISIBLE**， **WS_CLIPCHILDREN**，和**WS_CLIPSIBLINGS**。 使用的扩展的样式包括︰ **WS_EX_MDICHILD**。  
  
 如果您想要确保特定的样式设置为同时允许基于每个实例，设置其他样式的窗口类的所有实例都使用[CWinTraitsOR](../../atl/reference/cwintraitsor-class.md)相反。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlwin.h  
  
##  <a name="getwndstyle"></a>CWinTraits::GetWndStyle  
 调用此函数可检索的标准样式`CWinTraits`对象。  
  
```
static DWORD GetWndStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 用于创建窗口的标准样式。 如果`dwStyle`为 0，模板样式值 ( `t_dwStyle`) 返回。 如果`dwStyle`不为零，`dwStyle`返回。  
  
### <a name="return-value"></a>返回值  
 对象的标准的窗口样式。  
  
##  <a name="getwndexstyle"></a>CWinTraits::GetWndExStyle  
 调用此函数可检索的扩展的样式`CWinTraits`对象。  
  
```
static DWORD GetWndExStyle(DWORD dwExStyle);
```  
  
### <a name="parameters"></a>参数  
 `dwExStyle`  
 用于创建窗口的扩展的样式。 如果`dwExStyle`为 0，模板样式值 ( `t_dwExStyle`) 返回。 如果`dwExStyle`不为零，`dwExStyle`返回。  
  
### <a name="return-value"></a>返回值  
 对象扩展的窗口样式。  
  
## <a name="see-also"></a>另请参阅  
 [类成员](http://msdn.microsoft.com/en-us/dbe6a147-3f01-4aea-a3fb-fe6ebadc31f8)   
 [类概述](../../atl/atl-class-overview.md)   
 [了解窗口特性](../../atl/understanding-window-traits.md)

