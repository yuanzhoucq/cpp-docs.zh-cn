---
title: "事件接收器映射 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- event sink maps
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
caps.latest.revision: 14
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
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 33bf66d18b499787a34b2da501bb3e8ead255459
ms.lasthandoff: 02/24/2017

---
# <a name="event-sink-maps"></a>事件接收器映射
当嵌入 OLE 控件触发事件时，控件的容器将使用 MFC 提供的名为“事件接收器映射”的机制接收事件。 此事件接收器映射为每个特定事件指定处理程序函数，以及这些事件的参数。 事件接收器映射的详细信息，请参阅文章[ActiveX 控件容器](../../mfc/activex-control-containers.md)。  
  
### <a name="event-sink-maps"></a>事件接收器映射  
  
|||  
|-|-|  
|[BEGIN_EVENTSINK_MAP](#begin_eventsink_map)|启动事件接收器映射的定义。|  
|[DECLARE_EVENTSINK_MAP](#declare_eventsink_map)|声明事件接收器映射。|  
|[END_EVENTSINK_MAP](#end_eventsink_map)|结束事件接收器映射的定义。|  
|[ON_EVENT](#on_event)|为特定事件定义事件处理程序。|  
|[ON_EVENT_RANGE](#on_event_range)|为一组 OLE 控件触发的特定事件定义事件处理程序。|  
|[ON_EVENT_REFLECT](#on_event_reflect)|在控件的容器处理控件触发的事件之前接收这些事件。|  
|[ON_PROPNOTIFY](#on_propnotify)|定义处理程序来处理来自 OLE 控件的属性通知。|  
|[ON_PROPNOTIFY_RANGE](#on_propnotify_range)|定义处理程序来处理来自一组 OLE 控件的属性通知。|  
|[ON_PROPNOTIFY_REFLECT](#on_propnotify_reflect)|在控件的容器处理控件发送的属性通知之前接收这些通知。|  
  
##  <a name="a-namebegineventsinkmapa--begineventsinkmap"></a><a name="begin_eventsink_map"></a>BEGIN_EVENTSINK_MAP  
 开始事件接收器映射的定义。  
  
```   
BEGIN_EVENTSINK_MAP(theClass, baseClass)  
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 指定此列类型的事件接收器映射的控件类的名称。  
  
 `baseClass`  
 指定 `theClass` 的基类的名称。  
  
### <a name="remarks"></a>备注  
 在定义您的类的成员函数的实现 (.cpp) 文件，启动事件接收器映射与`BEGIN_EVENTSINK_MAP`宏，然后添加宏条目为每个事件通知，并完成事件接收器映射与`END_EVENTSINK_MAP`宏。  
  
 事件接收器映射和 OLE 控件容器的详细信息，请参阅文章[ActiveX 控件容器](../../mfc/activex-control-containers.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdisp.h  
  
##  <a name="a-namedeclareeventsinkmapa--declareeventsinkmap"></a><a name="declare_eventsink_map"></a>DECLARE_EVENTSINK_MAP  
 OLE 容器可以提供事件接收器映射来指定将接收通知您的容器的事件。  
  
```   
DECLARE_EVENTSINK_MAP()   
```  
  
### <a name="remarks"></a>备注  
 使用`DECLARE_EVENTSINK_MAP`宏在类声明的末尾。 然后，在。CPP 文件中定义的成员函数的类，请使用`BEGIN_EVENTSINK_MAP`宏，宏项，为每个事件、 通知和`END_EVENTSINK_MAP`宏声明事件接收器列表的末尾。  
  
 事件接收器映射的详细信息，请参阅文章[ActiveX 控件容器](../../mfc/activex-control-containers.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxwin.h  
  
##  <a name="a-nameendeventsinkmapa--endeventsinkmap"></a><a name="end_eventsink_map"></a>END_EVENTSINK_MAP  
 结束事件接收器映射的定义。  
  
```   
END_EVENTSINK_MAP()   
```  
  
### <a name="requirements"></a>要求  
  **标头**afxdisp.h  
  
##  <a name="a-nameoneventa--onevent"></a><a name="on_event"></a>ON_EVENT  
 使用`ON_EVENT`由 OLE 控件触发宏来定义事件的事件处理程序函数。  
  
```   
ON_EVENT(theClass, id, dispid, pfnHandler,  vtsParams) 
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 此事件接收器映射所属的类。  
  
 `id`  
 OLE 控件的控件 ID。  
  
 `dispid`  
 由该控件激发的事件调度 ID。  
  
 `pfnHandler`  
 指向成员函数处理该事件的指针。 此函数应具有**BOOL**返回类型，并且与该事件的参数相匹配的参数类型 (请参阅`vtsParams`)。 该函数应返回**TRUE**来表示该事件处理，否则为**FALSE**。  
  
 `vtsParams`  
 一系列**VTS_**指定事件的参数的类型的常量。 这些是如调度映射条目中使用的同一个常量`DISP_FUNCTION`。  
  
### <a name="remarks"></a>备注  
 `vtsParams`参数是以空格分隔的值列表**VTS_**常量。 一个或多个由空格 （而不是逗号） 分隔这些值指定函数的参数列表。 例如：  
  
 [!code-cpp[NVC_MFCAutomation #&11;](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 指定包含后跟一个短整数列表**BOOL**。  
  
 有关列表的**VTS_**常量，请参阅[EVENT_CUSTOM](event-maps.md#event_custom)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdisp.h  
  
##  <a name="a-nameoneventrangea--oneventrange"></a><a name="on_event_range"></a>ON_EVENT_RANGE  
 使用`ON_EVENT_RANGE`由任何具有连续的 Id 范围中的控件 ID 的 OLE 控件触发宏来定义事件的事件处理程序函数。  
  
```   
ON_EVENT_RANGE(theClass, idFirst, idLast, dispid, pfnHandler,  vtsParams)   
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 此事件接收器映射所属的类。  
  
 `idFirst`  
 在范围内的第一个 OLE 控件的控件 ID。  
  
 `idLast`  
 在范围内的最后一个 OLE 控件的控件 ID。  
  
 `dispid`  
 由该控件激发的事件调度 ID。  
  
 `pfnHandler`  
 指向成员函数处理该事件的指针。 此函数应具有**BOOL**返回类型，类型的第一个参数**UINT** （适用于控件 ID) 和与该事件的参数相匹配的其他参数类型 (请参阅`vtsParams`)。 该函数应返回**TRUE**来表示该事件处理，否则为**FALSE**。  
  
 `vtsParams`  
 一系列**VTS_**指定事件的参数的类型的常量。 第一个常量的类型应为**VTS_I4**，为控件 id。 这些是如调度映射条目中使用的同一个常量`DISP_FUNCTION`。  
  
### <a name="remarks"></a>备注  
 `vtsParams`参数是以空格分隔的值列表**VTS_**常量。 一个或多个由空格 （而不是逗号） 分隔这些值指定函数的参数列表。 例如：  
  
 [!code-cpp[NVC_MFCAutomation #&11;](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 指定包含后跟一个短整数列表**BOOL**。  
  
 有关列表的**VTS_**常量，请参阅[EVENT_CUSTOM](event-maps.md#event_custom)。  
  
### <a name="example"></a>示例  
 下面的示例演示一个事件处理程序，三个控件实现的 MouseDown 事件 (`IDC_MYCTRL1`通过`IDC_MYCTRL3`)。 事件处理程序函数， `OnRangeMouseDown`，在对话框类的头文件中声明 ( `CMyDlg`) 为︰  
  
 [!code-cpp[NVC_MFCAutomation #&12;](../../mfc/codesnippet/cpp/event-sink-maps_2.h)]  
  
 下面的代码是在对话框类的实现文件中定义的。  
  
 [!code-cpp[NVC_MFCAutomation #&13;](../../mfc/codesnippet/cpp/event-sink-maps_3.cpp)]  
  
### <a name="requirements"></a>要求  
  **标头**afxdisp.h  
  
##  <a name="a-nameoneventreflecta--oneventreflect"></a><a name="on_event_reflect"></a>ON_EVENT_REFLECT  
 `ON_EVENT_REFLECT`宏，使用在事件接收器映射 OLE 控件的包装器类时接收之前它们均由该控件的容器处理控件触发的事件。  
  
```   
ON_EVENT_REFLECT(theClass,  dispid, pfnHandler,  vtsParams) 
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 此事件接收器映射所属的类。  
  
 dispid  
 由该控件激发的事件调度 ID。  
  
 `pfnHandler`  
 指向成员函数处理该事件的指针。 此函数应具有**BOOL**返回类型和与该事件的参数相匹配的参数类型 (请参阅`vtsParams`)。 该函数应返回**TRUE**来表示该事件处理，否则为**FALSE**。  
  
 `vtsParams`  
 一系列**VTS_**指定事件的参数的类型的常量。 这些是如调度映射条目中使用的同一个常量`DISP_FUNCTION`。  
  
### <a name="remarks"></a>备注  
 `vtsParams`参数是以空格分隔的值列表**VTS_**常量。  
  
 一个或多个由空格 （而不是逗号） 分隔这些值指定函数的参数列表。 例如：  
  
 [!code-cpp[NVC_MFCAutomation #&11;](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 指定包含后跟一个短整数列表**BOOL**。  
  
 有关列表的**VTS_**常量，请参阅[EVENT_CUSTOM](event-maps.md#event_custom)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdisp.h  
  
##  <a name="a-nameonpropnotifya--onpropnotify"></a><a name="on_propnotify"></a>ON_PROPNOTIFY  
 使用`ON_PROPNOTIFY`宏来定义一个事件接收器映射条目，来处理来自 OLE 控件的属性通知。  
  
```   
ON_PROPNOTIFY(theClass, id, dispid, pfnRequest, pfnChanged)  
 
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 此事件接收器映射所属的类。  
  
 `id`  
 OLE 控件的控件 ID。  
  
 `dispid`  
 在通知中所涉及的属性的调度 ID。  
  
 `pfnRequest`  
 处理的成员函数指针**OnRequestEdit**此属性的通知。 此函数应具有**BOOL**返回类型和一个**BOOL\* **参数。 此函数应将参数设置为**TRUE**以允许要更改的属性和**FALSE**不允许。 该函数应返回**TRUE**以指示通知的处理; 否则为**FALSE**。  
  
 `pfnChanged`  
 处理的成员函数指针**OnChanged**此属性的通知。 此函数应该拥有**BOOL**返回类型和一个**UINT**参数。 该函数应返回**TRUE**以指示通知的处理; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 `vtsParams`参数是以空格分隔的值列表**VTS_**常量。 一个或多个由空格 （而不是逗号） 分隔这些值指定函数的参数列表。 例如:   
  
 [!code-cpp[NVC_MFCAutomation #&11;](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 指定包含后跟一个短整数列表**BOOL**。  
  
 有关列表的**VTS_**常量，请参阅[EVENT_CUSTOM](event-maps.md#event_custom)。  
  
##  <a name="a-nameonpropnotifyrangea--onpropnotifyrange"></a><a name="on_propnotify_range"></a>ON_PROPNOTIFY_RANGE  
 使用`ON_PROPNOTIFY_RANGE`宏来定义用于处理来自任何具有连续的 Id 范围中的控件 ID 的 OLE 控件的属性通知事件接收器映射项。  
  
```  
 
ON_PROPNOTIFY_RANGE(theClass, idFirst, idLast, dispid, pfnRequest, pfnChanged)  
 
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 此事件接收器映射所属的类。  
  
 `idFirst`  
 在范围内的第一个 OLE 控件的控件 ID。  
  
 `idLast`  
 在范围内的最后一个 OLE 控件的控件 ID。  
  
 `dispid`  
 在通知中所涉及的属性的调度 ID。  
  
 `pfnRequest`  
 处理的成员函数指针**OnRequestEdit**此属性的通知。 此函数应具有**BOOL**返回类型和**UINT**和**BOOL\* **参数。 该函数应将参数设置为**TRUE**以允许要更改的属性和**FALSE**不允许。 该函数应返回**TRUE**以指示通知的处理; 否则为**FALSE**。  
  
 `pfnChanged`  
 处理的成员函数指针**OnChanged**此属性的通知。 此函数应该拥有**BOOL**返回类型和一个**UINT**参数。 该函数应返回**TRUE**以指示通知的处理; 否则为**FALSE**。  
  
### <a name="requirements"></a>要求  
  **标头**afxdisp.h  
  
##  <a name="a-nameonpropnotifyreflecta--onpropnotifyreflect"></a><a name="on_propnotify_reflect"></a>ON_PROPNOTIFY_REFLECT  
 `ON_PROPNOTIFY_REFLECT`宏，当使用在事件接收器映射 OLE 控件的包装器类的属性通知接收之前它们均由该控件的容器处理由控件发送。  
  
```  
 
ON_PROPNOTIFY_REFLECT(theClass, dispid, pfnRequest, pfnChanged)  
 
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 此事件接收器映射所属的类。  
  
 `dispid`  
 在通知中所涉及的属性的调度 ID。  
  
 `pfnRequest`  
 处理的成员函数指针**OnRequestEdit**此属性的通知。 此函数应具有**BOOL**返回类型和一个**BOOL\* **参数。 此函数应将参数设置为**TRUE**以允许要更改的属性和**FALSE**不允许。 该函数应返回**TRUE**以指示通知的处理; 否则为**FALSE**。  
  
 `pfnChanged`  
 处理的成员函数指针**OnChanged**此属性的通知。 此函数应该拥有**BOOL**返回类型和任何参数。 该函数应返回**TRUE**以指示通知的处理; 否则为**FALSE**。  
  
### <a name="requirements"></a>要求  
  **标头**afxdisp.h  
    
## <a name="see-also"></a>另请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)

