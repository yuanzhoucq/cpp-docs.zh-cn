---
title: 窗口类宏 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlwin/ATL::DECLARE_WND_CLASS
- atlwin/ATL::DECLARE_WND_SUPERCLASS
- atlwin/ATL::DECLARE_WND_CLASS_EX
dev_langs:
- C++
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f0490eedb412e43f2ae99c4034648880be5f32a9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="window-class-macros"></a>窗口类宏
这些宏定义窗口类实用程序。  
  
|||  
|-|-|  
|[DECLARE_WND_CLASS](#declare_wnd_class)|使用此选项可以指定新的窗口类的名称。| 
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|(Visual Studio 2017)使用此选项可以指定一个新的窗口类以及封闭类的新类将使用其窗口过程的名称。| 
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|使用此选项可指定新的窗口类将基于现有窗口类的名称。|  
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|允许你指定的类的参数。|  

## <a name="requirements"></a>要求  
 **标头：** atlwin.h  
   
##  <a name="declare_wnd_class"></a>  DECLARE_WND_CLASS  
 使用此选项可以指定新的窗口类的名称。 将此宏放在 ATL ActiveX 控件的控件类。  
  
```
DECLARE_WND_CLASS( WndClassName )
```  
  
### <a name="parameters"></a>参数  
 `WndClassName`  
 [in]新的窗口类的名称。 如果**NULL**，ATL 将生成一个窗口类名称。  
  
### <a name="remarks"></a>备注  
 如果使用 /permissive-compiler 选项，通过然后 DECLARE_WND_CLASS 将导致编译器错误;请改用 DECLARE_WND_CLASS2。
 
 DECLARE_WND_CLASS 允许你指定的名称将由其信息的新窗口类[CWndClassInfo](cwndclassinfo-class.md)。 `DECLARE_WND_CLASS` 通过实现以下静态函数定义新的窗口类：  
  
 [!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 `DECLARE_WND_CLASS` 指定新的窗口中的以下样式：  
  
-   CS_HREDRAW  
  
-   CS_VREDRAW  
  
-   CS_DBLCLKS  
  
 `DECLARE_WND_CLASS` 此外指定的默认窗口的背景色。 使用[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)宏来提供你自己的样式和背景色。  
  
 [CWindowImpl](cwindowimpl-class.md)使用`DECLARE_WND_CLASS`宏创建窗口基于新的窗口类。 若要重写此行为，使用[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)宏，或提供您自己的实现[GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo)函数。  

  
 有关使用 ATL 中的窗口的详细信息，请参阅文章[ATL 窗口类](../../atl/atl-window-classes.md)。  

##  <a name="declare_wnd_class2"></a>  DECLARE_WND_CLASS2  
 (Visual Studio 2017)类似于 DECLARE_WND_CLASS，但使用 /permissive-option 编译时，可避免依赖名称错误的额外参数。
  
```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```  
  
### <a name="parameters"></a>参数  
 `WndClassName`  
 [in]新的窗口类的名称。 如果**NULL**，ATL 将生成一个窗口类名称。 

 `EnclosingClass`  
 [in]窗口类所属的新的窗口类的名称。 不能为**NULL**。  
  
### <a name="remarks"></a>备注 
如果你使用的 /permissive-option，DECLARE_WND_CLASS 将导致编译错误，因为它包含依赖名称。 DECLARE_WND_CLASS2 要求你显式将此宏用于中，并且不会导致在 /permissive-flag 错误类。
否则此宏等同于[DECLARE_WND_CLASS](#declare_wnd_class)。
   
##  <a name="declare_wnd_superclass"></a>  DECLARE_WND_SUPERCLASS  
 允许你指定的类的参数。 将此宏放在 ATL ActiveX 控件的控件类。  
  
```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```  
  
### <a name="parameters"></a>参数  
 `WndClassName`  
 [in]窗口名称类，将超类`OrigWndClassName`。 如果**NULL**，ATL 将生成一个窗口类名称。  
  
 `OrigWndClassName`  
 [in]现有窗口类的名称。  
  
### <a name="remarks"></a>备注  
 此宏，可指定的窗口类，将超类现有窗口类的名称。 [CWndClassInfo](cwndclassinfo-class.md)管理超类的信息。  
  
 `DECLARE_WND_SUPERCLASS` 实现以下静态函数：  
  
 [!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 默认情况下， [CWindowImpl](cwindowimpl-class.md)使用[DECLARE_WND_CLASS](#declare_wnd_class)宏创建窗口基于新的窗口类。 通过指定`DECLARE_WND_SUPERCLASS`中的宏`CWindowImpl`-派生类，窗口类将基于现有类，但将使用你的窗口过程。 这种技术称为创建超类。  
  
 除了使用`DECLARE_WND_CLASS`和`DECLARE_WND_SUPERCLASS`宏，可以重写[GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo)具有自己的实现函数。  

  
 有关使用 ATL 中的窗口的详细信息，请参阅文章[ATL 窗口类](../../atl/atl-window-classes.md)。  
  
##  <a name="declare_wnd_class_ex"></a>  DECLARE_WND_CLASS_EX  
 使用此选项可指定新的窗口类将基于现有窗口类的名称。 将此宏放在 ATL ActiveX 控件的控件类。  
  
```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```  
  
### <a name="parameters"></a>参数  
 `WndClassName`  
 [in]新的窗口类的名称。 如果**NULL**，ATL 将生成一个窗口类名称。  
  
 `style`  
 [in]窗口的样式。  
  
 *背景*  
 [in]窗口的背景色。  
  
### <a name="remarks"></a>备注  
 此宏允许你指定的类参数的一个新的窗口类，其信息将由[CWndClassInfo](cwndclassinfo-class.md)。 `DECLARE_WND_CLASS_EX` 通过实现以下静态函数定义新的窗口类：  
  
 [!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 如果你想要使用的默认样式和背景色，使用[DECLARE_WND_CLASS](#declare_wnd_class)宏。 有关使用 ATL 中的窗口的详细信息，请参阅文章[ATL 窗口类](../../atl/atl-window-classes.md)。  
  
## <a name="see-also"></a>请参阅  
 [宏](atl-macros.md)









