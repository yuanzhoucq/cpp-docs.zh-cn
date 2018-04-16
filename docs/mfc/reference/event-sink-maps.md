---
title: "事件接收器映射 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- event sink maps [MFC]
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 309474220f081a0eca67d0f83ead21c59eb649e5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
  
##  <a name="begin_eventsink_map"></a>BEGIN_EVENTSINK_MAP  
 开始事件接收器映射的定义。  
  
```   
BEGIN_EVENTSINK_MAP(theClass, baseClass)  
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 指定其事件接收器映射的控件类的名称。  
  
 `baseClass`  
 指定 `theClass` 的基类的名称。  
  
### <a name="remarks"></a>备注  
 在实现 (.cpp) 文件中定义你的类的成员函数，启动事件接收器映射与`BEGIN_EVENTSINK_MAP`宏，然后添加宏条目为每个事件接收通知的并完成对事件接收器地图`END_EVENTSINK_MAP`宏。  
  
 事件接收器映射和 OLE 控件容器的详细信息，请参阅文章[ActiveX 控件容器](../../mfc/activex-control-containers.md)。  
  
### <a name="requirements"></a>惠?  
  **标头**afxdisp.h  
  
##  <a name="declare_eventsink_map"></a>DECLARE_EVENTSINK_MAP  
 OLE 容器可以提供事件接收器映射来指定将接收通知你的容器的事件。  
  
```   
DECLARE_EVENTSINK_MAP()   
```  
  
### <a name="remarks"></a>备注  
 使用`DECLARE_EVENTSINK_MAP`宏在类声明的末尾。 然后，在。类的函数定义的成员的 CPP 文件，请使用`BEGIN_EVENTSINK_MAP`宏，为每个事件通知，宏项和`END_EVENTSINK_MAP`宏来声明事件接收器列表的末尾。  
  
 事件接收器映射的详细信息，请参阅文章[ActiveX 控件容器](../../mfc/activex-control-containers.md)。  
  
### <a name="requirements"></a>惠?  
  **标头**afxwin.h  
  
##  <a name="end_eventsink_map"></a>END_EVENTSINK_MAP  
 结束事件接收器映射的定义。  
  
```   
END_EVENTSINK_MAP()   
```  
  
### <a name="requirements"></a>惠?  
  **标头**afxdisp.h  
  
##  <a name="on_event"></a>ON_EVENT  
 使用`ON_EVENT`由 OLE 控件激发的宏来定义事件的事件处理程序函数。  
  
```   
ON_EVENT(theClass, id, dispid, pfnHandler,  vtsParams) 
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 此事件接收器映射所属的类。  
  
 `id`  
 OLE 控件的控件 ID。  
  
 `dispid`  
 控件触发的事件的调度 ID。  
  
 `pfnHandler`  
 对处理事件的成员函数的指针。 此函数应具有**BOOL**返回类型，并且与事件的参数匹配的参数类型 (请参阅`vtsParams`)。 该函数应返回**TRUE**来指示事件是否处理; 否则为**FALSE**。  
  
 `vtsParams`  
 序列**VTS_**指定事件的参数类型的常量。 这些是如调度映射条目中使用的相同常量`DISP_FUNCTION`。  
  
### <a name="remarks"></a>备注  
 `vtsParams`自变量是空格分隔的值从列表**VTS_**常量。 一个或多个用空格 （而不是逗号） 分隔这些值指定函数的参数列表。 例如:  
  
 [!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 指定列表包含跟短整数**BOOL**。  
  
 有关的列表**VTS_**常量，请参阅[EVENT_CUSTOM](event-maps.md#event_custom)。  
  
### <a name="requirements"></a>惠?  
  **标头**afxdisp.h  
  
##  <a name="on_event_range"></a>ON_EVENT_RANGE  
 使用`ON_EVENT_RANGE`由具有连续 Id 的范围中的控件 ID 任何 OLE 控件激发的宏来定义事件的事件处理程序函数。  
  
```   
ON_EVENT_RANGE(theClass, idFirst, idLast, dispid, pfnHandler,  vtsParams)   
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 此事件接收器映射所属的类。  
  
 `idFirst`  
 范围中第一个 OLE 控件的控件 ID。  
  
 `idLast`  
 在范围内的最后一个 OLE 控件的控件 ID。  
  
 `dispid`  
 控件触发的事件的调度 ID。  
  
 `pfnHandler`  
 对处理事件的成员函数的指针。 此函数应具有**BOOL**返回类型，类型的第一个参数**UINT** （有关控件 ID) 和事件的参数匹配的其他参数类型 (请参阅`vtsParams`)。 该函数应返回**TRUE**来指示事件是否处理; 否则为**FALSE**。  
  
 `vtsParams`  
 序列**VTS_**指定事件的参数类型的常量。 第一个常量的类型应该是**VTS_I4**，有关控件 id。 这些是如调度映射条目中使用的相同常量`DISP_FUNCTION`。  
  
### <a name="remarks"></a>备注  
 `vtsParams`自变量是空格分隔的值从列表**VTS_**常量。 一个或多个用空格 （而不是逗号） 分隔这些值指定函数的参数列表。 例如:  
  
 [!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 指定列表包含跟短整数**BOOL**。  
  
 有关的列表**VTS_**常量，请参阅[EVENT_CUSTOM](event-maps.md#event_custom)。  
  
### <a name="example"></a>示例  
 下面的示例演示一个事件处理程序中的，对于 MouseDown 事件，三个控件实现 (`IDC_MYCTRL1`通过`IDC_MYCTRL3`)。 事件处理程序函数， `OnRangeMouseDown`，在对话框类的标头文件中声明 ( `CMyDlg`) 为：  
  
 [!code-cpp[NVC_MFCAutomation#12](../../mfc/codesnippet/cpp/event-sink-maps_2.h)]  
  
 下面的代码是在对话框类的实现文件中定义的。  
  
 [!code-cpp[NVC_MFCAutomation#13](../../mfc/codesnippet/cpp/event-sink-maps_3.cpp)]  
  
### <a name="requirements"></a>惠?  
  **标头**afxdisp.h  
  
##  <a name="on_event_reflect"></a>ON_EVENT_REFLECT  
 `ON_EVENT_REFLECT`宏，当使用在事件接收器映射的 OLE 控件的包装器类，接收之前它们均由该控件的容器处理控件触发的事件。  
  
```   
ON_EVENT_REFLECT(theClass,  dispid, pfnHandler,  vtsParams) 
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 此事件接收器映射所属的类。  
  
 dispid  
 控件触发的事件的调度 ID。  
  
 `pfnHandler`  
 对处理事件的成员函数的指针。 此函数应具有**BOOL**返回类型和事件的参数匹配的参数类型 (请参阅`vtsParams`)。 该函数应返回**TRUE**来指示事件是否处理; 否则为**FALSE**。  
  
 `vtsParams`  
 序列**VTS_**指定事件的参数类型的常量。 这些是如调度映射条目中使用的相同常量`DISP_FUNCTION`。  
  
### <a name="remarks"></a>备注  
 `vtsParams`自变量是空格分隔的值从列表**VTS_**常量。  
  
 一个或多个用空格 （而不是逗号） 分隔这些值指定函数的参数列表。 例如:  
  
 [!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 指定列表包含跟短整数**BOOL**。  
  
 有关的列表**VTS_**常量，请参阅[EVENT_CUSTOM](event-maps.md#event_custom)。  
  
### <a name="requirements"></a>惠?  
  **标头**afxdisp.h  
  
##  <a name="on_propnotify"></a>ON_PROPNOTIFY  
 使用`ON_PROPNOTIFY`宏来定义用于处理来自 OLE 控件的属性通知的事件接收器映射条目。  
  
```   
ON_PROPNOTIFY(theClass, id, dispid, pfnRequest, pfnChanged)  
 
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 此事件接收器映射所属的类。  
  
 `id`  
 OLE 控件的控件 ID。  
  
 `dispid`  
 属性所涉及的通知调度 ID。  
  
 `pfnRequest`  
 指向成员函数处理**OnRequestEdit**此属性的通知。 此函数应具有**BOOL**返回类型和**BOOL\*** 参数。 此函数应将参数设置为**TRUE**以允许要更改的属性和**FALSE**禁止。 该函数应返回**TRUE**来指示通知是否处理; 否则为**FALSE**。  
  
 `pfnChanged`  
 指向成员函数处理**OnChanged**此属性的通知。 此函数应该拥有**BOOL**返回类型和**UINT**参数。 该函数应返回**TRUE**以指示通知的处理; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 `vtsParams`自变量是空格分隔的值从列表**VTS_**常量。 一个或多个用空格 （而不是逗号） 分隔这些值指定函数的参数列表。 例如:  
  
 [!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 指定列表包含跟短整数**BOOL**。  
  
 有关的列表**VTS_**常量，请参阅[EVENT_CUSTOM](event-maps.md#event_custom)。  
  
##  <a name="on_propnotify_range"></a>ON_PROPNOTIFY_RANGE  
 使用`ON_PROPNOTIFY_RANGE`宏来定义用于处理来自任何具有连续 Id 的范围中的控件 ID 的 OLE 控件的属性通知的事件接收器映射条目。  
  
```  
 
ON_PROPNOTIFY_RANGE(theClass, idFirst, idLast, dispid, pfnRequest, pfnChanged)  
 
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 此事件接收器映射所属的类。  
  
 `idFirst`  
 范围中第一个 OLE 控件的控件 ID。  
  
 `idLast`  
 在范围内的最后一个 OLE 控件的控件 ID。  
  
 `dispid`  
 属性所涉及的通知调度 ID。  
  
 `pfnRequest`  
 指向成员函数处理**OnRequestEdit**此属性的通知。 此函数应具有**BOOL**返回类型和**UINT**和**BOOL\*** 参数。 该函数应将参数设置为**TRUE**以允许要更改的属性和**FALSE**禁止。 该函数应返回**TRUE**以指示通知的处理; 否则为**FALSE**。  
  
 `pfnChanged`  
 指向成员函数处理**OnChanged**此属性的通知。 此函数应该拥有**BOOL**返回类型和**UINT**参数。 该函数应返回**TRUE**以指示通知的处理; 否则为**FALSE**。  
  
### <a name="requirements"></a>惠?  
  **标头**afxdisp.h  
  
##  <a name="on_propnotify_reflect"></a>ON_PROPNOTIFY_REFLECT  
 `ON_PROPNOTIFY_REFLECT`宏，当使用在事件接收器映射的 OLE 控件的包装器类，它接收之前它们均由该控件的容器处理由控件发送的属性通知。  
  
```  
 
ON_PROPNOTIFY_REFLECT(theClass, dispid, pfnRequest, pfnChanged)  
 
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 此事件接收器映射所属的类。  
  
 `dispid`  
 属性所涉及的通知调度 ID。  
  
 `pfnRequest`  
 指向成员函数处理**OnRequestEdit**此属性的通知。 此函数应具有**BOOL**返回类型和**BOOL\*** 参数。 此函数应将参数设置为**TRUE**以允许要更改的属性和**FALSE**禁止。 该函数应返回**TRUE**来指示通知是否处理; 否则为**FALSE**。  
  
 `pfnChanged`  
 指向成员函数处理**OnChanged**此属性的通知。 此函数应该拥有**BOOL**返回类型和任何参数。 该函数应返回**TRUE**来指示通知是否处理; 否则为**FALSE**。  
  
### <a name="requirements"></a>惠?  
  **标头**afxdisp.h  
    
## <a name="see-also"></a>请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
