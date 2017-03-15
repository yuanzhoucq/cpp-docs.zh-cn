---
title: "CWndClassInfo 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWndClassInfo
dev_langs:
- C++
helpviewer_keywords:
- CWndClassInfo class
ms.assetid: c36fe7e1-75f1-4cf5-a06f-9f59c43fe6fb
caps.latest.revision: 22
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
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: f036d79c7a9420e083eb86023c5cbf98906cc1cc
ms.lasthandoff: 02/24/2017

---
# <a name="cwndclassinfo-class"></a>CWndClassInfo 类
此类提供用于注册窗口类信息的方法。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
class CWndClassInfo
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|||  
|-|-|  
|[注册](#register)|注册窗口类。|  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|[m_atom](#m_atom)|唯一地标识已注册的窗口类。|  
|[m_bSystemCursor](#m_bsystemcursor)|指定的光标资源引用系统光标或引用包含在模块资源中的游标。|  
|[m_lpszCursorID](#m_lpszcursorid)|指定的光标资源的名称。|  
|[m_lpszOrigName](#m_lpszorigname)|包含现有窗口类的名称。|  
|[m_szAutoName](#m_szautoname)|保存的窗口类的 ATL 生成的名称。|  
|[m_wc](#m_wc)|维护中的窗口类信息**WNDCLASSEX**结构。|  
|[pWndProc](#pwndproc)|指向现有窗口类的窗口过程。|  
  
## <a name="remarks"></a>备注  
 `CWndClassInfo`管理窗口类的信息。 通常使用`CWndClassInfo`通过三个宏之一`DECLARE_WND_CLASS`， `DECLARE_WND_CLASS_EX`，或`DECLARE_WND_SUPERCLASS`，如下面的表中所述︰  
  
|宏|描述|  
|-----------|-----------------|  
|[DECLARE_WND_CLASS](http://msdn.microsoft.com/library/55247a72-fb9e-4bde-87f3-747c08076971)|`CWndClassInfo`注册一个新的窗口类的信息。|  
|[DECLARE_WND_CLASS_EX](http://msdn.microsoft.com/library/0672c144-f2aa-4f6a-ae16-566e3a1f5411)|`CWndClassInfo`注册一个新的窗口类，其中包括类参数的信息。|  
|[DECLARE_WND_SUPERCLASS](http://msdn.microsoft.com/library/650337b6-4973-41e5-8c36-55f90327bdcd)|`CWndClassInfo`注册的窗口类，基于现有类，但使用不同的窗口过程的信息。 这种技术称为创建超类。|  
  
 默认情况下， [CWindowImpl](../../atl/reference/cwindowimpl-class.md)包括`DECLARE_WND_CLASS`宏来创建一个窗口基于新的窗口类。 DECLARE_WND_CLASS 控件提供了默认样式和背景色。 如果您想要指定的样式和背景色自己，派生您的类从`CWindowImpl`并且包括`DECLARE_WND_CLASS_EX`在类定义的宏。  
  
 如果您想要创建基于现有的窗口类的窗口，派生您的类从`CWindowImpl`并且包括`DECLARE_WND_SUPERCLASS`在类定义的宏。 例如:   
  
 [!code-cpp[NVC_ATL_Windowing #&43;](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]  
  
 有关窗口类的详细信息，请参阅[窗口类](http://msdn.microsoft.com/library/windows/desktop/ms632596)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 有关使用 ATL 中的窗口的详细信息，请参阅文章[ATL 窗口类](../../atl/atl-window-classes.md)。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlwin.h  
  
##  <a name="a-namematoma--cwndclassinfomatom"></a><a name="m_atom"></a>CWndClassInfo::m_atom  
 包含已注册的窗口类的唯一标识符。  
  
```
ATOM m_atom;
```  
  
##  <a name="a-namembsystemcursora--cwndclassinfombsystemcursor"></a><a name="m_bsystemcursor"></a>CWndClassInfo::m_bSystemCursor  
 如果**TRUE**，在注册窗口类时，将加载的系统光标资源。  
  
```
BOOL m_bSystemCursor;
```  
  
### <a name="remarks"></a>备注  
 否则，将加载包含在模块中的光标资源。  
  
 `CWndClassInfo`使用`m_bSystemCursor`仅当[DECLARE_WND_CLASS](http://msdn.microsoft.com/library/55247a72-fb9e-4bde-87f3-747c08076971) (中的默认设置[CWindowImpl](../../atl/reference/cwindowimpl-class.md)) 或[DECLARE_WND_CLASS_EX](http://msdn.microsoft.com/library/0672c144-f2aa-4f6a-ae16-566e3a1f5411)指定宏。 在这种情况下，`m_bSystemCursor`初始化为**TRUE**。 有关详细信息，请参阅[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概述。  
  
##  <a name="a-namemlpszcursorida--cwndclassinfomlpszcursorid"></a><a name="m_lpszcursorid"></a>CWndClassInfo::m_lpszCursorID  
 在低序位字和零的高序位字中指定的光标资源的名称或资源标识符。  
  
```
LPCTSTR m_lpszCursorID;
```  
  
### <a name="remarks"></a>备注  
 注册窗口类时，由标识光标的句柄`m_lpszCursorID`检索并将其存储的[m_wc](#m_wc)。  
  
 `CWndClassInfo`使用`m_lpszCursorID`仅当[DECLARE_WND_CLASS](http://msdn.microsoft.com/library/55247a72-fb9e-4bde-87f3-747c08076971) (中的默认设置[CWindowImpl](../../atl/reference/cwindowimpl-class.md)) 或[DECLARE_WND_CLASS_EX](http://msdn.microsoft.com/library/0672c144-f2aa-4f6a-ae16-566e3a1f5411)指定宏。 在这种情况下，`m_lpszCursorID`初始化为**IDC_ARROW**。 有关详细信息，请参阅[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概述。  
  
##  <a name="a-namemlpszorignamea--cwndclassinfomlpszorigname"></a><a name="m_lpszorigname"></a>CWndClassInfo::m_lpszOrigName  
 包含现有窗口类的名称。  
  
```
LPCTSTR m_lpszOrigName;
```  
  
### <a name="remarks"></a>备注  
 `CWndClassInfo`使用`m_lpszOrigName`仅包括[DECLARE_WND_SUPERCLASS](http://msdn.microsoft.com/library/650337b6-4973-41e5-8c36-55f90327bdcd)在类定义的宏。 在这种情况下，`CWndClassInfo`寄存器窗口类根据消息由名为的类`m_lpszOrigName`。 有关详细信息，请参阅[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概述。  
  
##  <a name="a-namemszautonamea--cwndclassinfomszautoname"></a><a name="m_szautoname"></a>CWndClassInfo::m_szAutoName  
 保留的窗口类的名称。  
  
```
TCHAR m_szAutoName[13];
```  
  
### <a name="remarks"></a>备注  
 `CWndClassInfo`使用`m_szAutoName`才**NULL**为传递`WndClassName`参数[DECLARE_WND_CLASS](http://msdn.microsoft.com/library/55247a72-fb9e-4bde-87f3-747c08076971)、 [DECLARE_WND_CLASS_EX](http://msdn.microsoft.com/library/0672c144-f2aa-4f6a-ae16-566e3a1f5411)或[DECLARE_WND_SUPERCLASS](http://msdn.microsoft.com/library/650337b6-4973-41e5-8c36-55f90327bdcd)。 注册窗口类时，ATL 将构造的名称。  
  
##  <a name="a-namemwca--cwndclassinfomwc"></a><a name="m_wc"></a>CWndClassInfo::m_wc  
 维护中的窗口类信息[WNDCLASSEX](http://msdn.microsoft.com/library/windows/desktop/ms633577)结构。  
  
```
WNDCLASSEX m_wc;
```  
  
### <a name="remarks"></a>备注  
 如果已指定[DECLARE_WND_CLASS](http://msdn.microsoft.com/library/55247a72-fb9e-4bde-87f3-747c08076971) (中的默认设置[CWindowImpl](../../atl/reference/cwindowimpl-class.md)) 或[DECLARE_WND_CLASS_EX](http://msdn.microsoft.com/library/0672c144-f2aa-4f6a-ae16-566e3a1f5411)宏，`m_wc`包含新的窗口类的相关信息。  
  
 如果已指定[DECLARE_WND_SUPERCLASS](http://msdn.microsoft.com/library/650337b6-4973-41e5-8c36-55f90327bdcd)宏，`m_wc`包含有关超类信息 — 的窗口类，基于现有类，但使用不同的窗口过程。 [m_lpszOrigName](#m_lpszorigname)和[pWndProc](#pwndproc)分别保存现有窗口类的名称和窗口过程。  
  
##  <a name="a-namepwndproca--cwndclassinfopwndproc"></a><a name="pwndproc"></a>CWndClassInfo::pWndProc  
 指向现有窗口类的窗口过程。  
  
```
WNDPROC pWndProc;
```  
  
### <a name="remarks"></a>备注  
 `CWndClassInfo`使用`pWndProc`仅包括[DECLARE_WND_SUPERCLASS](http://msdn.microsoft.com/library/650337b6-4973-41e5-8c36-55f90327bdcd)在类定义的宏。 在这种情况下，`CWndClassInfo`注册的窗口类，基于现有类，但使用不同的窗口过程。 现有窗口类的窗口过程将保存在`pWndProc`。 有关详细信息，请参阅[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概述。  
  
##  <a name="a-nameregistera--cwndclassinforegister"></a><a name="register"></a>CWndClassInfo::Register  
 由调用[CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create)注册窗口类，如果尚未注册。  
  
```
ATOM Register(WNDPROC* pProc);
```  
  
### <a name="parameters"></a>参数  
 `pProc`  
 [out]指定现有窗口类的原始窗口过程。  
  
### <a name="return-value"></a>返回值  
 如果成功，atom 唯一标识要注册的窗口类。 否则为 0。  
  
### <a name="remarks"></a>备注  
 如果已指定[DECLARE_WND_CLASS](http://msdn.microsoft.com/library/55247a72-fb9e-4bde-87f3-747c08076971) (中的默认设置[CWindowImpl](../../atl/reference/cwindowimpl-class.md)) 或[DECLARE_WND_CLASS_EX](http://msdn.microsoft.com/library/0672c144-f2aa-4f6a-ae16-566e3a1f5411)宏，`Register`注册新的窗口类。 在这种情况下，`pProc`不使用参数。  
  
 如果已指定[DECLARE_WND_SUPERCLASS](http://msdn.microsoft.com/library/650337b6-4973-41e5-8c36-55f90327bdcd)宏，`Register`注册超类 — 的窗口类，基于现有类，但使用不同的窗口过程。 现有窗口类的窗口过程返回在`pProc`。  
  
## <a name="see-also"></a>另请参阅  
 [CComControl 类](../../atl/reference/ccomcontrol-class.md)   
 [类概述](../../atl/atl-class-overview.md)
