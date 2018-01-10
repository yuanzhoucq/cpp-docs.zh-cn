---
title: "CWinTraits 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinTraits
- ATLWIN/ATL::CWinTraits
- ATLWIN/ATL::CWinTraits::GetWndExStyle
- ATLWIN/ATL::CWinTraits::GetWndStyle
dev_langs: C++
helpviewer_keywords:
- CMDIChildWinTraits class
- window styles, default values for ATL
- CWinTraits class
- CFrameWinTraits class
- CControlWinTraits class
ms.assetid: f78f486e-6d9c-42c6-8e86-371e05aa7e59
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5c5e71f969f86aee419a0ff9d3701f4d43be5c32
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cwintraits-class"></a>CWinTraits 类
此类提供的方法来标准化时创建的窗口对象使用的样式。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template <DWORD t_dwStyle = 0, DWORD t_dwExStyle = 0>  class CWinTraits
```  
  
#### <a name="parameters"></a>参数  
 `t_dwStyle`  
 默认标准的窗口样式。  
  
 `t_dwExStyle`  
 默认扩展的窗口样式。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CWinTraits::GetWndExStyle](#getwndexstyle)|（静态）检索的扩展的样式`CWinTraits`对象。|  
|[CWinTraits::GetWndStyle](#getwndstyle)|（静态）检索的标准样式`CWinTraits`对象。|  
  
## <a name="remarks"></a>备注  
 这[窗口特征](../../atl/understanding-window-traits.md)类提供标准化用于创建 ATL 窗口对象的样式的简单方法。 作为模板参数传递给使用此类专用化[CWindowImpl](../../atl/reference/cwindowimpl-class.md)或另一个 ATL 的窗口类来指定用于默认标准和扩展样式窗口类的实例。  
  
 当你想要提供仅在不指定的调用中的任何其他样式时将使用的窗口样式的默认使用此模板[CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create)。  
  
 ATL 提供三个预定义的专用化的窗口样式的常用组合此模板：  
  
 `CControlWinTraits`  
 设计标准控件窗口。 使用以下标准样式： **WS_CHILD**， **WS_VISIBLE**， **WS_CLIPCHILDREN**，和**WS_CLIPSIBLINGS**。 没有扩展的样式。  
  
 `CFrameWinTraits`  
 适用于标准框架窗口。 使用的标准样式包括： **WS_OVERLAPPEDWINDOW**， **WS_CLIPCHILDREN**，和**WS_CLIPSIBLINGS**。 使用的扩展的样式包括： **WS_EX_APPWINDOW**和**WS_EX_WINDOWEDGE**。  
  
 `CMDIChildWinTraits`  
 设计标准的 MDI 子窗口。 使用的标准样式包括： **WS_OVERLAPPEDWINDOW**， **WS_CHILD**， **WS_VISIBLE**， **WS_CLIPCHILDREN**，和**WS_CLIPSIBLINGS**。 使用的扩展的样式包括： **WS_EX_MDICHILD**。  
  
 如果你想要确保时允许基于每个实例，设置其他样式窗口类的所有实例使用此选项设置特定的样式[CWinTraitsOR](../../atl/reference/cwintraitsor-class.md)相反。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlwin.h  
  
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
 对象的扩展的窗口样式。  
  
## <a name="see-also"></a>请参阅  
 [类成员](http://msdn.microsoft.com/en-us/dbe6a147-3f01-4aea-a3fb-fe6ebadc31f8)   
 [类概述](../../atl/atl-class-overview.md)   
 [了解窗口特征](../../atl/understanding-window-traits.md)
