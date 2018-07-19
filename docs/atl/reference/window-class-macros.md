---
title: 窗口类宏 |Microsoft Docs
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
ms.openlocfilehash: 470c1c8e3facbeba909e182b97a8b027dc9e8ca8
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879676"
---
# <a name="window-class-macros"></a>窗口类宏
这些宏定义窗口类实用程序。  
  
|||  
|-|-|  
|[{2&AMP;GT;DECLARE_WND_CLASS&AMP;LT;2](#declare_wnd_class)|可以指定新的窗口类的名称。| 
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|(Visual Studio 2017)可以指定新的窗口类和封闭类的新类将使用其窗口过程的名称。| 
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|可以指定新的窗口类将基于现有窗口类的名称。|  
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|允许您指定的类的参数。|  

## <a name="requirements"></a>要求  
 **标头：** atlwin.h  
   
##  <a name="declare_wnd_class"></a>  {2&AMP;GT;DECLARE_WND_CLASS&AMP;LT;2  
 可以指定新的窗口类的名称。 将此宏放置在 ATL ActiveX 控件的控件类。  
  
```
DECLARE_WND_CLASS( WndClassName )
```  
  
### <a name="parameters"></a>参数  
 *WndClassName*  
 [in]新的窗口类的名称。 如果为 NULL，ATL 将生成的窗口类名称。  
  
### <a name="remarks"></a>备注  
 如果您要使用 /permissive-compiler 选项，然后 {2&gt;declare_wnd_class&lt;2 将会导致编译器错误;请改用 DECLARE_WND_CLASS2。
 
 {2&gt;declare_wnd_class&lt;2 允许您指定获取其信息将由一个新窗口类的名称[CWndClassInfo](cwndclassinfo-class.md)。 {2&gt;declare_wnd_class&lt;2 通过实现以下静态函数定义新的窗口类：  
  
 [!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 {2&gt;declare_wnd_class&lt;2 指定新窗口中的以下样式：  
  
-   CS_HREDRAW  
  
-   CS_VREDRAW  
  
-   CS_DBLCLKS  
  
 {2&gt;declare_wnd_class&lt;2 还指定了默认窗口的背景色。 使用[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)宏，以提供您自己的样式和背景色。  
  
 [CWindowImpl](cwindowimpl-class.md)使用 {2&gt;declare_wnd_class&lt;2 宏来创建基于新的窗口类的窗口。 若要重写此行为，请使用[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)宏，或提供自己的实现[GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo)函数。  

  
 有关使用 ATL 中的窗口的详细信息，请参阅文章[ATL 窗口类](../../atl/atl-window-classes.md)。  

##  <a name="declare_wnd_class2"></a>  DECLARE_WND_CLASS2  
 (Visual Studio 2017)类似于 {2&gt;declare_wnd_class&lt;2，但使用 /permissive-option 编译时可避免依赖名称错误的额外参数。
  
```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```  
  
### <a name="parameters"></a>参数  
 *WndClassName*  
 [in]新的窗口类的名称。 如果为 NULL，ATL 将生成的窗口类名称。 

 *EnclosingClass*  
 [in]包含新的窗口类的窗口类的名称。 不能为 NULL。  
  
### <a name="remarks"></a>备注 
如果使用的 /permissive-option，{2&gt;declare_wnd_class&lt;2 将导致编译错误，因为它包含将依赖名称。 DECLARE_WND_CLASS2 要求显式命名的类，此宏中使用并且不会导致下 /permissive-flag 错误。
否则此宏等同于[{2&gt;declare_wnd_class&lt;2](#declare_wnd_class)。
   
##  <a name="declare_wnd_superclass"></a>  DECLARE_WND_SUPERCLASS  
 允许您指定的类的参数。 将此宏放置在 ATL ActiveX 控件的控件类。  
  
```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```  
  
### <a name="parameters"></a>参数  
 *WndClassName*  
 [in]窗口名称类，将超类*OrigWndClassName*。 如果为 NULL，ATL 将生成的窗口类名称。  
  
 *OrigWndClassName*  
 [in]将现有的窗口类的名称。  
  
### <a name="remarks"></a>备注  
 此宏，可指定将现有的窗口类的超类的窗口类的名称。 [CWndClassInfo](cwndclassinfo-class.md)管理超类别信息。  
  
 DECLARE_WND_SUPERCLASS 实现以下静态函数：  
  
 [!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 默认情况下[CWindowImpl](cwindowimpl-class.md)使用[{2&gt;declare_wnd_class&lt;2](#declare_wnd_class)宏来创建一个窗口，基于一个新的窗口类。 通过指定中的 DECLARE_WND_SUPERCLASS 宏`CWindowImpl`-派生的类，窗口类将基于现有类，但将使用在窗口过程。 这一技术称为创建超类。  
  
 除了使用 {2&gt;declare_wnd_class&lt;2 和 DECLARE_WND_SUPERCLASS 宏，您可以重写[GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo)函数与您自己的实现。  

  
 有关使用 ATL 中的窗口的详细信息，请参阅文章[ATL 窗口类](../../atl/atl-window-classes.md)。  
  
##  <a name="declare_wnd_class_ex"></a>  DECLARE_WND_CLASS_EX  
 可以指定新的窗口类将基于现有窗口类的名称。 将此宏放置在 ATL ActiveX 控件的控件类。  
  
```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```  
  
### <a name="parameters"></a>参数  
 *WndClassName*  
 [in]新的窗口类的名称。 如果为 NULL，ATL 将生成的窗口类名称。  
  
 *style*  
 [in]窗口的样式。  
  
 *背景*  
 [in]窗口的背景色。  
  
### <a name="remarks"></a>备注  
 此宏，可指定新的窗口类，将由其信息的类参数[CWndClassInfo](cwndclassinfo-class.md)。 DECLARE_WND_CLASS_EX 通过实现以下静态函数定义新的窗口类：  
  
 [!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 如果你想要使用的默认样式和背景色，使用[{2&gt;declare_wnd_class&lt;2](#declare_wnd_class)宏。 有关使用 ATL 中的窗口的详细信息，请参阅文章[ATL 窗口类](../../atl/atl-window-classes.md)。  
  
## <a name="see-also"></a>请参阅  
 [宏](atl-macros.md)









