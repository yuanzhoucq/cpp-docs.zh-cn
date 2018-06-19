---
title: CWndClassInfo 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CWndClassInfo
- ATLWIN/ATL::CWndClassInfo
- ATLWIN/ATL::Register
- ATLWIN/ATL::m_atom
- ATLWIN/ATL::m_bSystemCursor
- ATLWIN/ATL::m_lpszCursorID
- ATLWIN/ATL::m_lpszOrigName
- ATLWIN/ATL::m_szAutoName
- ATLWIN/ATL::m_wc
- ATLWIN/ATL::pWndProc
dev_langs:
- C++
helpviewer_keywords:
- CWndClassInfo class
ms.assetid: c36fe7e1-75f1-4cf5-a06f-9f59c43fe6fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 878d6065f3a158ac4404620205ef9c60912d89ca
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365759"
---
# <a name="cwndclassinfo-class"></a>CWndClassInfo 类
此类提供注册窗口类信息的方法。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
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
|[m_atom](#m_atom)|唯一标识已注册的窗口类。|  
|[m_bSystemCursor](#m_bsystemcursor)|指定的光标资源引用系统光标或引用的模块资源中包含的游标。|  
|[m_lpszCursorID](#m_lpszcursorid)|指定的光标资源的名称。|  
|[m_lpszOrigName](#m_lpszorigname)|包含现有窗口类的名称。|  
|[m_szAutoName](#m_szautoname)|包含的窗口类 ATL 生成的名称。|  
|[m_wc](#m_wc)|维护中的窗口类信息**WNDCLASSEX**结构。|  
|[pWndProc](#pwndproc)|指向现有窗口类的窗口过程。|  
  
## <a name="remarks"></a>备注  
 `CWndClassInfo` 管理窗口类的信息。 通常使用`CWndClassInfo`通过三个宏之一`DECLARE_WND_CLASS`， `DECLARE_WND_CLASS_EX`，或`DECLARE_WND_SUPERCLASS`下, 表中所述：  
  
|宏|描述|  
|-----------|-----------------|  
|[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)|`CWndClassInfo` 注册新的窗口类的信息。|  
|[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)|`CWndClassInfo` 注册一个新的窗口类，包括类参数的信息。|  
|[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)|`CWndClassInfo` 注册的窗口类，基于现有类，但使用不同的窗口过程的信息。 这种技术称为创建超类。|  
  
 默认情况下， [CWindowImpl](../../atl/reference/cwindowimpl-class.md)包括`DECLARE_WND_CLASS`宏创建窗口基于新的窗口类。 DECLARE_WND_CLASS 提供控件的默认样式和背景色。 如果你想要指定的样式和背景色自己，派生您的类从`CWindowImpl`和包括`DECLARE_WND_CLASS_EX`在类定义的宏。  
  
 如果你想要创建窗口基于现有窗口类，派生您的类从`CWindowImpl`和包括`DECLARE_WND_SUPERCLASS`在类定义的宏。 例如：  
  
 [!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]  
  
 窗口类的详细信息，请参阅[窗口类](http://msdn.microsoft.com/library/windows/desktop/ms632596)Windows SDK 中。  
  
 有关使用 ATL 中的窗口的详细信息，请参阅文章[ATL 窗口类](../../atl/atl-window-classes.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** atlwin.h  
  
##  <a name="m_atom"></a>  CWndClassInfo::m_atom  
 包含已注册的窗口类的唯一标识符。  
  
```
ATOM m_atom;
```  
  
##  <a name="m_bsystemcursor"></a>  CWndClassInfo::m_bSystemCursor  
 如果**TRUE**，在注册窗口类时，将加载系统光标资源。  
  
```
BOOL m_bSystemCursor;
```  
  
### <a name="remarks"></a>备注  
 否则，将加载包含在模块中的光标资源。  
  
 `CWndClassInfo` 使用`m_bSystemCursor`仅当[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (中的默认值[CWindowImpl](../../atl/reference/cwindowimpl-class.md)) 或[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)指定宏。 在这种情况下，`m_bSystemCursor`初始化为**TRUE**。 有关详细信息，请参阅[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概述。  
  
##  <a name="m_lpszcursorid"></a>  CWndClassInfo::m_lpszCursorID  
 指定在低序位字和零的高序位字中的光标资源的名称或资源标识符。  
  
```
LPCTSTR m_lpszCursorID;
```  
  
### <a name="remarks"></a>备注  
 注册窗口类时，由标识光标的句柄`m_lpszCursorID`存储并检索[m_wc](#m_wc)。  
  
 `CWndClassInfo` 使用`m_lpszCursorID`仅当[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (中的默认值[CWindowImpl](../../atl/reference/cwindowimpl-class.md)) 或[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)指定宏。 在这种情况下，`m_lpszCursorID`初始化为**IDC_ARROW**。 有关详细信息，请参阅[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概述。  
  
##  <a name="m_lpszorigname"></a>  CWndClassInfo::m_lpszOrigName  
 包含现有窗口类的名称。  
  
```
LPCTSTR m_lpszOrigName;
```  
  
### <a name="remarks"></a>备注  
 `CWndClassInfo` 使用`m_lpszOrigName`仅包括[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)在类定义的宏。 在这种情况下，`CWndClassInfo`寄存器窗口类基于命名的类`m_lpszOrigName`。 有关详细信息，请参阅[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概述。  
  
##  <a name="m_szautoname"></a>  CWndClassInfo::m_szAutoName  
 包含的窗口类的名称。  
  
```
TCHAR m_szAutoName[13];
```  
  
### <a name="remarks"></a>备注  
 `CWndClassInfo` 使用`m_szAutoName`才**NULL**为传递`WndClassName`参数[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)、 [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)或[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)。 注册窗口类时，ATL 将构造的名称。  
  
##  <a name="m_wc"></a>  CWndClassInfo::m_wc  
 维护中的窗口类信息[WNDCLASSEX](http://msdn.microsoft.com/library/windows/desktop/ms633577)结构。  
  
```
WNDCLASSEX m_wc;
```  
  
### <a name="remarks"></a>备注  
 如果已指定[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (中的默认值[CWindowImpl](../../atl/reference/cwindowimpl-class.md)) 或[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)宏，`m_wc`包含有关的信息新的窗口类。  
  
 如果已指定[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏，`m_wc`包含有关超类信息 — 的窗口类，基于现有类，但使用不同的窗口过程。 [m_lpszOrigName](#m_lpszorigname)和[pWndProc](#pwndproc)分别保存现有窗口类的名称和窗口过程。  
  
##  <a name="pwndproc"></a>  CWndClassInfo::pWndProc  
 指向现有窗口类的窗口过程。  
  
```
WNDPROC pWndProc;
```  
  
### <a name="remarks"></a>备注  
 `CWndClassInfo` 使用`pWndProc`仅包括[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)在类定义的宏。 在这种情况下，`CWndClassInfo`注册的窗口类，基于现有类，但使用不同的窗口过程。 现有窗口类的窗口过程将保存在`pWndProc`。 有关详细信息，请参阅[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概述。  
  
##  <a name="register"></a>  CWndClassInfo::Register  
 由调用[CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create)以注册窗口类，如果尚未注册。  
  
```
ATOM Register(WNDPROC* pProc);
```  
  
### <a name="parameters"></a>参数  
 `pProc`  
 [out]指定现有窗口类的原始窗口过程。  
  
### <a name="return-value"></a>返回值  
 如果成功，atom 唯一标识要注册的窗口类。 否则为为 0。  
  
### <a name="remarks"></a>备注  
 如果已指定[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (中的默认值[CWindowImpl](../../atl/reference/cwindowimpl-class.md)) 或[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)宏，`Register`注册新的窗口类。 在这种情况下，`pProc`未使用参数。  
  
 如果已指定[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏，`Register`注册超类-的窗口类，基于现有类，但使用不同的窗口过程。 在中返回现有窗口类的窗口过程`pProc`。  
  
## <a name="see-also"></a>请参阅  
 [CComControl 类](../../atl/reference/ccomcontrol-class.md)   
 [类概述](../../atl/atl-class-overview.md)