---
title: "窗口类宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
caps.latest.revision: 16
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 8cdedc5cfac9d49df812ae6fcfcc548201b1edb5
ms.openlocfilehash: f32926b6efd4ffb9c0541c0574a479c13dac01df
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="window-class-macros"></a>窗口类宏
这些宏定义窗口类实用程序。  
  
|||  
|-|-|  
|[DECLARE_WND_CLASS](#declare_wnd_class)|可以指定新的窗口类的名称。| 
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|（visual Studio 于 2017 年）允许您指定的名称以及新的窗口类在封闭类的新类将使用其窗口过程。| 
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|可以指定新的窗口类将基于现有窗口类的名称。|  
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|允许您指定的类的参数。|  

## <a name="requirements"></a>要求  
 **标头︰** atlwin.h  
   
##  <a name="declare_wnd_class"></a>DECLARE_WND_CLASS  
 可以指定新的窗口类的名称。 将此宏放在 ATL ActiveX 控件的控件类。  
  
```
DECLARE_WND_CLASS( WndClassName )
```  
  
### <a name="parameters"></a>参数  
 `WndClassName`  
 [in]新的窗口类的名称。 如果**NULL**，ATL 将生成一个窗口类名。  
  
### <a name="remarks"></a>备注  
 如果您要使用 /permissive-compiler 选项，然后 DECLARE_WND_CLASS 将会导致编译器错误;请改用 DECLARE_WND_CLASS2。
 
 DECLARE_WND_CLASS 允许您指定的名称获取其信息将由一个新窗口类[CWndClassInfo](cwndclassinfo-class.md)。 `DECLARE_WND_CLASS`通过实现以下静态函数定义新的窗口类︰  
  
 [!code-cpp[NVC_ATL_Windowing #&127;](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 `DECLARE_WND_CLASS`指定新的窗口中的下列样式︰  
  
-   CS_HREDRAW  
  
-   CS_VREDRAW  
  
-   CS_DBLCLKS  
  
 `DECLARE_WND_CLASS`此外指定了默认窗口的背景色。 使用[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)宏来提供您自己的样式和背景色。  
  
 [CWindowImpl](cwindowimpl-class.md)使用`DECLARE_WND_CLASS`宏来创建一个窗口基于新的窗口类。 若要重写此行为，请使用[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)宏，或提供您自己的实现[GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo)函数。  

  
 有关使用 ATL 中的窗口的详细信息，请参阅文章[ATL 窗口类](../../atl/atl-window-classes.md)。  

##  <a name="declare_wnd_class2"></a>DECLARE_WND_CLASS2  
 （visual Studio 于 2017 年）类似于 DECLARE_WND_CLASS，但使用 /permissive-option 编译时，可以避免依赖名称错误的额外参数。
  
```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```  
  
### <a name="parameters"></a>参数  
 `WndClassName`  
 [in]新的窗口类的名称。 如果**NULL**，ATL 将生成一个窗口类名。 

 `EnclosingClass`  
 [in]包含新的窗口类的窗口类的名称。 不能为**NULL**。  
  
### <a name="remarks"></a>备注 
如果使用 /permissive-option，DECLARE_WND_CLASS 将导致编译错误，因为它包含依赖名称。 DECLARE_WND_CLASS2 要求您显式命名的类，此宏中使用，而不会导致在 /permissive-flag 错误。
否则该宏等同于[DECLARE_WND_CLASS](#declare_wnd_class)。
   
##  <a name="declare_wnd_superclass"></a>DECLARE_WND_SUPERCLASS  
 允许您指定的类的参数。 将此宏放在 ATL ActiveX 控件的控件类。  
  
```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```  
  
### <a name="parameters"></a>参数  
 `WndClassName`  
 [in]窗口的名称的类，将超类`OrigWndClassName`。 如果**NULL**，ATL 将生成一个窗口类名。  
  
 `OrigWndClassName`  
 [in]现有窗口类的名称。  
  
### <a name="remarks"></a>备注  
 此宏，可指定的窗口类，将超类现有窗口类的名称。 [CWndClassInfo](cwndclassinfo-class.md)管理超类的信息。  
  
 `DECLARE_WND_SUPERCLASS`实现以下静态函数︰  
  
 [!code-cpp[NVC_ATL_Windowing #&127;](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 默认情况下， [CWindowImpl](cwindowimpl-class.md)使用[DECLARE_WND_CLASS](#declare_wnd_class)宏来创建一个窗口基于新的窗口类。 通过指定`DECLARE_WND_SUPERCLASS`中的宏`CWindowImpl`的派生类中，窗口类将基于现有类，但将使用您的窗口过程。 这种技术称为创建超类。  
  
 除了使用`DECLARE_WND_CLASS`和`DECLARE_WND_SUPERCLASS`宏，可以重写[GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo)函数使用您自己的实现。  

  
 有关使用 ATL 中的窗口的详细信息，请参阅文章[ATL 窗口类](../../atl/atl-window-classes.md)。  
  
##  <a name="declare_wnd_class_ex"></a>DECLARE_WND_CLASS_EX  
 可以指定新的窗口类将基于现有窗口类的名称。 将此宏放在 ATL ActiveX 控件的控件类。  
  
```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```  
  
### <a name="parameters"></a>参数  
 `WndClassName`  
 [in]新的窗口类的名称。 如果**NULL**，ATL 将生成一个窗口类名。  
  
 `style`  
 [in]窗口的样式。  
  
 *背景*  
 [in]窗口的背景色。  
  
### <a name="remarks"></a>备注  
 此宏，可以指定一个新的窗口类，将由其信息的类参数[CWndClassInfo](cwndclassinfo-class.md)。 `DECLARE_WND_CLASS_EX`通过实现以下静态函数定义新的窗口类︰  
  
 [!code-cpp[NVC_ATL_Windowing #&127;](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 如果您想要使用的默认样式和背景色，使用[DECLARE_WND_CLASS](#declare_wnd_class)宏。 有关使用 ATL 中的窗口的详细信息，请参阅文章[ATL 窗口类](../../atl/atl-window-classes.md)。  
  
## <a name="see-also"></a>另请参阅  
 [宏](atl-macros.md)










