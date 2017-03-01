---
title: "CWinTraitsOR 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CWinTraitsOR
- ATL::CWinTraitsOR
- CWinTraitsOR
dev_langs:
- C++
helpviewer_keywords:
- CWinTraitsOR class
- window styles, default values for ATL
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
caps.latest.revision: 20
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
ms.openlocfilehash: cd077c7f79c3099d0e825a48233e7a8b269c0d04
ms.lasthandoff: 02/24/2017

---
# <a name="cwintraitsor-class"></a>CWinTraitsOR 类
此类提供方法来标准化时创建窗口对象使用的样式。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
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
 扩展窗口样式的默认值。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CWinTraitsOR::GetWndExStyle](#getwndexstyle)|检索的扩展的样式`CWinTraitsOR`对象。|  
|[CWinTraitsOR::GetWndStyle](#getwndstyle)|检索的标准样式`CWinTraitsOR`对象。|  
  
## <a name="remarks"></a>备注  
 这[窗口特性](../../atl/understanding-window-traits.md)类提供了简单的方法，来标准化用于创建 ATL 窗口对象的样式。 专用化此类用作模板参数[CWindowImpl](../../atl/reference/cwindowimpl-class.md)或 ATL 的窗口类，以指定的最小的一套标准和扩展样式，以用于另一个窗口类的实例。  
  
 如果你想要确保特定的样式设置为窗口类的所有实例同时允许其他样式来设置对的调用中基于每个实例，请使用此模板的专用化[CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create)。  
  
 如果你想要提供默认值仅对的调用中不指定的任何其他样式时，将使用的窗口样式`CWindowImpl::Create`，使用[CWinTraits](../../atl/reference/cwintraits-class.md)相反。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlwin.h  
  
##  <a name="a-namegetwndstylea--cwintraitsorgetwndstyle"></a><a name="getwndstyle"></a>CWinTraitsOR::GetWndStyle  
 调用此函数可检索 （使用逻辑 OR 运算符） 的标准样式的组合`CWinTraits`对象，并由指定的默认样式`t_dwStyle`。  
  
```
static DWORD GetWndStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 用于创建窗口的样式。  
  
### <a name="return-value"></a>返回值  
 在传递的样式组合`dwStyle`和与指定的默认`t_dwStyle`，使用逻辑 OR 运算符。  
  
##  <a name="a-namegetwndexstylea--cwintraitsorgetwndexstyle"></a><a name="getwndexstyle"></a>CWinTraitsOR::GetWndExStyle  
 调用此函数可检索的扩展样式的组合 （使用逻辑 OR 运算符）`CWinTraits`对象，并由指定的默认样式`t_dwStyle`。  
  
```
static DWORD GetWndExStyle(DWORD dwExStyle);
```  
  
### <a name="parameters"></a>参数  
 `dwExStyle`  
 用于创建窗口的扩展的样式。  
  
### <a name="return-value"></a>返回值  
 传入的扩展样式组合`dwExStyle`和默认值是由指定`t_dwExStyle`，使用逻辑 OR 运算符  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)   
 [了解窗口特性](../../atl/understanding-window-traits.md)


