---
title: "CWinTraitsOR 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR::GetWndExStyle
- ATLWIN/ATL::CWinTraitsOR::GetWndStyle
dev_langs: C++
helpviewer_keywords:
- CWinTraitsOR class
- window styles, default values for ATL
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 14796948369b92c9137dc7e02a8399910d46997c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cwintraitsor-class"></a>CWinTraitsOR 类
此类提供的方法来标准化时创建的窗口对象使用的样式。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template <DWORD t_dwStyle = 0,
          DWORD t_dwExStyle = 0, 
          class TWinTraits = CControlWinTraits>
class CWinTraitsOR
```  
  
#### <a name="parameters"></a>参数  
 `t_dwStyle`  
 默认窗口样式。  
  
 `t_dwExStyle`  
 默认扩展的窗口样式。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CWinTraitsOR::GetWndExStyle](#getwndexstyle)|检索的扩展的样式`CWinTraitsOR`对象。|  
|[CWinTraitsOR::GetWndStyle](#getwndstyle)|检索的标准样式`CWinTraitsOR`对象。|  
  
## <a name="remarks"></a>备注  
 这[窗口特征](../../atl/understanding-window-traits.md)类提供标准化用于创建 ATL 窗口对象的样式的简单方法。 作为模板参数传递给使用此类专用化[CWindowImpl](../../atl/reference/cwindowimpl-class.md)或 ATL 的窗口类，以指定的最小的一套标准和扩展样式，以用于另一个窗口类的实例。  
  
 使用此模板的专用化，如果你想要确保特定的样式设置窗口类的所有实例同时允许其他样式设置上的调用中按实例逐一[CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create)。  
  
 如果你想要提供默认值，仅当对的调用中不指定任何其他样式时将使用的窗口样式`CWindowImpl::Create`，使用[CWinTraits](../../atl/reference/cwintraits-class.md)相反。  
  
## <a name="requirements"></a>要求  
 **标头：** atlwin.h  
  
##  <a name="getwndstyle"></a>CWinTraitsOR::GetWndStyle  
 调用此函数可检索 （使用逻辑 OR 运算符） 的标准样式的组合`CWinTraits`对象和指定的默认样式`t_dwStyle`。  
  
```
static DWORD GetWndStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 用于创建窗口的样式。  
  
### <a name="return-value"></a>返回值  
 传入的样式的组合`dwStyle`和默认值的指定`t_dwStyle`，使用逻辑 OR 运算符。  
  
##  <a name="getwndexstyle"></a>CWinTraitsOR::GetWndExStyle  
 调用此函数可检索的扩展样式的组合 （使用逻辑 OR 运算符）`CWinTraits`对象和指定的默认样式`t_dwStyle`。  
  
```
static DWORD GetWndExStyle(DWORD dwExStyle);
```  
  
### <a name="parameters"></a>参数  
 `dwExStyle`  
 用于创建窗口的扩展的样式。  
  
### <a name="return-value"></a>返回值  
 传入的扩展样式的组合`dwExStyle`和默认的指定`t_dwExStyle`，使用逻辑 OR 运算符  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)   
 [了解窗口特征](../../atl/understanding-window-traits.md)

