---
title: 事件接收器映射
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.maps
helpviewer_keywords:
- event sink maps [MFC]
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
ms.openlocfilehash: 8e33636253b269692f87f99980b9da0cd60867ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322353"
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

##  <a name="begin_eventsink_map"></a>  BEGIN_EVENTSINK_MAP

开始事件接收器映射的定义。

```
BEGIN_EVENTSINK_MAP(theClass, baseClass)
```

### <a name="parameters"></a>参数

*theClass*<br/>
指定的事件接收器将此映射的控件类的名称。

*baseClass*<br/>
指定的类的基类名称*类*。

### <a name="remarks"></a>备注

在实现 (.cpp) 文件中定义您的类的成员函数，事件接收器映射开始 BEGIN_EVENTSINK_MAP 宏，然后添加宏条目为每个事件通知，并完成事件接收器映射与 END_EVENTSINK_MAP 宏保持一致。

事件接收器映射和 OLE 控件容器的详细信息，请参阅文章[ActiveX 控件容器](../../mfc/activex-control-containers.md)。

### <a name="requirements"></a>要求

  **标头**afxdisp.h

##  <a name="declare_eventsink_map"></a>  DECLARE_EVENTSINK_MAP

OLE 容器可以提供事件接收器映射来指定你的容器将通知的事件。

```
DECLARE_EVENTSINK_MAP()
```

### <a name="remarks"></a>备注

在类声明的末尾使用 DECLARE_EVENTSINK_MAP 宏。 然后，在。定义类的成员函数 CPP 文件的每个事件通知和 END_EVENTSINK_MAP 宏来声明事件接收器列表的末尾使用 BEGIN_EVENTSINK_MAP 宏，宏条目。

事件接收器映射的详细信息，请参阅文章[ActiveX 控件容器](../../mfc/activex-control-containers.md)。

### <a name="requirements"></a>要求

  **标头**afxwin.h

##  <a name="end_eventsink_map"></a>  END_EVENTSINK_MAP

结束事件接收器映射的定义。

```
END_EVENTSINK_MAP()
```

### <a name="requirements"></a>要求

  **标头**afxdisp.h

##  <a name="on_event"></a>  ON_EVENT

ON_EVENT 宏用于定义由 OLE 控件触发事件的事件处理程序函数。

```
ON_EVENT(theClass, id, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>参数

*theClass*<br/>
此事件接收器映射所属的类。

*id*<br/>
OLE 控件的控件 ID。

*dispid*<br/>
控件触发的事件的调度 ID。

*pfnHandler*<br/>
指向成员函数处理该事件。 此函数应具有返回类型和参数类型匹配的事件参数的一个布尔值 (请参阅*vtsParams*)。 该函数应返回 TRUE 以指示已处理的事件;否则为 FALSE。

*vtsParams*<br/>
一系列**VTS_** 常量用于指定事件的参数的类型。 这些是如 DISP_FUNCTION 调度映射条目中使用的同一个常量。

### <a name="remarks"></a>备注

*VtsParams*参数是以空格分隔的值列表**VTS_** 常量。 一个或多个由空格 （而不是逗号） 分隔这些值指定函数的参数列表。 例如：

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

指定包含短整型跟一个布尔值的列表。

有关一系列**VTS_** 常量，请参阅[EVENT_CUSTOM](event-maps.md#event_custom)。

### <a name="requirements"></a>要求

  **标头**afxdisp.h

##  <a name="on_event_range"></a>  ON_EVENT_RANGE

ON_EVENT_RANGE 宏用于定义由任何具有连续 Id 的范围内的控件 ID 的 OLE 控件触发事件的事件处理程序函数。

```
ON_EVENT_RANGE(theClass, idFirst, idLast, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>参数

*theClass*<br/>
此事件接收器映射所属的类。

*idFirst*<br/>
范围中的第一个 OLE 控件的控件 ID。

*idLast*<br/>
在范围内的最后一个 OLE 控件的控件 ID。

*dispid*<br/>
控件触发的事件的调度 ID。

*pfnHandler*<br/>
指向成员函数处理该事件。 此函数应具有类型、 类型 （对于控件 ID)，UINT 和其他参数类型事件的参数相匹配的第一个参数返回一个布尔值 (请参阅*vtsParams*)。 该函数应返回 TRUE 以指示已处理的事件;否则为 FALSE。

*vtsParams*<br/>
一系列**VTS_** 常量用于指定事件的参数的类型。 第一个常量应是类型 VTS_I4，为控件 id。 这些是如 DISP_FUNCTION 调度映射条目中使用的同一个常量。

### <a name="remarks"></a>备注

*VtsParams*参数是以空格分隔的值列表**VTS_** 常量。 一个或多个由空格 （而不是逗号） 分隔这些值指定函数的参数列表。 例如：

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

指定包含短整型跟一个布尔值的列表。

有关一系列**VTS_** 常量，请参阅[EVENT_CUSTOM](event-maps.md#event_custom)。

### <a name="example"></a>示例

下面的示例演示一个事件处理程序实现三个控件的鼠标按下事件 (通过 IDC_MYCTRL3 IDC_MYCTRL1)。 事件处理程序函数， `OnRangeMouseDown`，在对话框类的头文件中声明 ( `CMyDlg`) 为：

[!code-cpp[NVC_MFCAutomation#12](../../mfc/codesnippet/cpp/event-sink-maps_2.h)]

在对话框类的实现文件中定义下面的代码。

[!code-cpp[NVC_MFCAutomation#13](../../mfc/codesnippet/cpp/event-sink-maps_3.cpp)]

### <a name="requirements"></a>要求

  **标头**afxdisp.h

##  <a name="on_event_reflect"></a>  ON_EVENT_REFLECT

ON_EVENT_REFLECT 宏，使用在事件接收器映射的 OLE 控件的包装类时接收之前它们由该控件的容器处理控件触发的事件。

```
ON_EVENT_REFLECT(theClass,  dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>参数

*theClass*<br/>
此事件接收器映射所属的类。

*dispid*<br/>
控件触发的事件的调度 ID。

*pfnHandler*<br/>
指向成员函数处理该事件。 此函数应具有返回类型和参数类型匹配的事件参数的一个布尔值 (请参阅*vtsParams*)。 该函数应返回 TRUE 以指示已处理的事件;否则为 FALSE。

*vtsParams*<br/>
一系列**VTS_** 常量用于指定事件的参数的类型。 这些是如 DISP_FUNCTION 调度映射条目中使用的同一个常量。

### <a name="remarks"></a>备注

*VtsParams*参数是以空格分隔的值列表**VTS_** 常量。

一个或多个由空格 （而不是逗号） 分隔这些值指定函数的参数列表。 例如：

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

指定包含短整型跟一个布尔值的列表。

有关一系列**VTS_** 常量，请参阅[EVENT_CUSTOM](event-maps.md#event_custom)。

### <a name="requirements"></a>要求

  **标头**afxdisp.h

##  <a name="on_propnotify"></a>  ON_PROPNOTIFY

ON_PROPNOTIFY 宏用于定义一个事件接收器映射条目，用于处理来自 OLE 控件的属性通知。

```
ON_PROPNOTIFY(theClass, id, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>参数

*theClass*<br/>
此事件接收器映射所属的类。

*id*<br/>
OLE 控件的控件 ID。

*dispid*<br/>
在通知中所涉及的属性的调度 ID。

*pfnRequest*<br/>
指向成员函数处理`OnRequestEdit`此属性的通知。 此函数应具有一个布尔值，返回类型和一个**BOOL** <strong>\*</strong>参数。 此函数应将参数设置为 TRUE 以允许更改属性，则为 FALSE，则不允许。 该函数应返回 TRUE 以指示已处理通知;否则为 FALSE。

*pfnChanged*<br/>
指向成员函数处理`OnChanged`此属性的通知。 该函数应具有一个布尔值，返回类型和 UINT 参数。 该函数应返回 TRUE 以指示已处理通知;否则为 FALSE。

### <a name="remarks"></a>备注

*VtsParams*参数是以空格分隔的值列表**VTS_** 常量。 一个或多个由空格 （而不是逗号） 分隔这些值指定函数的参数列表。 例如：

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

指定包含短整型跟一个布尔值的列表。

有关一系列**VTS_** 常量，请参阅[EVENT_CUSTOM](event-maps.md#event_custom)。

##  <a name="on_propnotify_range"></a>  ON_PROPNOTIFY_RANGE

ON_PROPNOTIFY_RANGE 宏用于定义一个事件接收器映射条目，用于处理来自任何具有连续 Id 的范围内的控件 ID 的 OLE 控件的属性通知。

```

ON_PROPNOTIFY_RANGE(theClass, idFirst, idLast, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>参数

*theClass*<br/>
此事件接收器映射所属的类。

*idFirst*<br/>
范围中的第一个 OLE 控件的控件 ID。

*idLast*<br/>
在范围内的最后一个 OLE 控件的控件 ID。

*dispid*<br/>
在通知中所涉及的属性的调度 ID。

*pfnRequest*<br/>
指向成员函数处理`OnRequestEdit`此属性的通知。 此函数应具有`BOOL`返回类型和`UINT`和`BOOL*`参数。 该函数应将参数设置为 TRUE 以允许更改属性，则为 FALSE，则不允许。 该函数应返回 TRUE 以指示已处理通知;否则为 FALSE。

*pfnChanged*<br/>
指向成员函数处理`OnChanged`此属性的通知。 此函数应该拥有`BOOL`返回类型和一个`UINT`参数。 该函数应返回 TRUE 以指示已处理通知;否则为 FALSE。

### <a name="requirements"></a>要求

  **标头**afxdisp.h

##  <a name="on_propnotify_reflect"></a>  ON_PROPNOTIFY_REFLECT

ON_PROPNOTIFY_REFLECT 宏，使用在事件接收器映射的 OLE 控件的包装类时接收之前它们由该控件的容器处理由控件发送的属性通知。

```

ON_PROPNOTIFY_REFLECT(theClass, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>参数

*theClass*<br/>
此事件接收器映射所属的类。

*dispid*<br/>
在通知中所涉及的属性的调度 ID。

*pfnRequest*<br/>
指向成员函数处理`OnRequestEdit`此属性的通知。 此函数应具有一个布尔值，返回类型和一个**BOOL** <strong>\*</strong>参数。 此函数应将参数设置为 TRUE 以允许更改属性，则为 FALSE，则不允许。 该函数应返回 TRUE 以指示已处理通知;否则为 FALSE。

*pfnChanged*<br/>
指向成员函数处理`OnChanged`此属性的通知。 该函数应具有一个布尔值，返回类型和任何参数。 该函数应返回 TRUE 以指示已处理通知;否则为 FALSE。

### <a name="requirements"></a>要求

  **标头**afxdisp.h

## <a name="see-also"></a>请参阅

[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
