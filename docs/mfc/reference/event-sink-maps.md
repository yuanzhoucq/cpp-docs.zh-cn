---
title: 事件接收器映射
ms.date: 11/04/2016
helpviewer_keywords:
- event sink maps [MFC]
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
ms.openlocfilehash: 731ed2403aae3332e81702673d1181e9e52399a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365721"
---
# <a name="event-sink-maps"></a>事件接收器映射

当嵌入 OLE 控件触发事件时，控件的容器将使用 MFC 提供的名为“事件接收器映射”的机制接收事件。 此事件接收器映射为每个特定事件指定处理程序函数，以及这些事件的参数。 有关事件接收器映射的详细信息，请参阅文章[ActiveX 控制容器](../../mfc/activex-control-containers.md)。

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

## <a name="begin_eventsink_map"></a><a name="begin_eventsink_map"></a>BEGIN_EVENTSINK_MAP

开始定义事件接收器映射。

```
BEGIN_EVENTSINK_MAP(theClass, baseClass)
```

### <a name="parameters"></a>参数

*类*<br/>
指定其事件接收器映射为该控件类的名称。

*基类*<br/>
指定*类*的基类的名称。

### <a name="remarks"></a>备注

在定义类成员函数的实现 （.cpp） 文件中，使用BEGIN_EVENTSINK_MAP宏启动事件接收器映射，然后为要通知的每个事件添加宏条目，然后使用END_EVENTSINK_MAP宏完成事件接收器映射。

有关事件接收器映射和 OLE 控制容器的详细信息，请参阅文章[ActiveX 控制容器](../../mfc/activex-control-containers.md)。

### <a name="requirements"></a>要求

  **标题**afxdisp.h

## <a name="declare_eventsink_map"></a><a name="declare_eventsink_map"></a>DECLARE_EVENTSINK_MAP

OLE 容器可以提供事件接收器映射，以指定容器将收到通知的事件。

```
DECLARE_EVENTSINK_MAP()
```

### <a name="remarks"></a>备注

在类声明末尾使用DECLARE_EVENTSINK_MAP宏。 然后，在 中。用于定义类的成员函数的 CPP 文件，使用要通知的每个事件的BEGIN_EVENTSINK_MAP宏、宏条目，以及END_EVENTSINK_MAP宏来声明事件接收器列表的结束。

有关事件接收器映射的详细信息，请参阅文章[ActiveX 控制容器](../../mfc/activex-control-containers.md)。

### <a name="requirements"></a>要求

  **头**afxwin.h

## <a name="end_eventsink_map"></a><a name="end_eventsink_map"></a>END_EVENTSINK_MAP

结束事件接收器映射的定义。

```
END_EVENTSINK_MAP()
```

### <a name="requirements"></a>要求

  **标题**afxdisp.h

## <a name="on_event"></a><a name="on_event"></a>ON_EVENT

使用ON_EVENT宏为由 OLE 控件触发的事件定义事件处理程序函数。

```
ON_EVENT(theClass, id, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>参数

*类*<br/>
此事件接收器映射所属的类。

*id*<br/>
OLE 控件的控制 ID。

*不一部分*<br/>
控件触发的事件的调度 ID。

*普芬汉德勒*<br/>
指向处理事件的成员函数的指针。 此函数应具有 BOOL 返回类型和匹配事件参数的参数类型（请参阅*vtsParams）。* 该函数应返回 TRUE 以指示事件已处理;因此，应返回 TRUE，以指示事件已处理。否则 FALSE。

*vtsParams*<br/>
指定事件参数类型的**VTS_** 常量序列。 这些是调度映射条目（如DISP_FUNCTION）中使用的相同常量。

### <a name="remarks"></a>备注

*vtsParams*参数是**VTS_常量**中由空间分隔的值列表。 一个或多个这些值由空格（不是逗号）分隔，指定函数的参数列表。 例如：

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

指定包含短整数后跟 BOOL 的列表。

有关**VTS_** 常量的列表，请参阅[EVENT_CUSTOM](event-maps.md#event_custom)。

### <a name="requirements"></a>要求

  **标题**afxdisp.h

## <a name="on_event_range"></a><a name="on_event_range"></a>ON_EVENT_RANGE

使用ON_EVENT_RANGE宏为任何 OLE 控件触发的事件定义事件处理程序函数，该控件在连续 ID 范围内具有控件 ID。

```
ON_EVENT_RANGE(theClass, idFirst, idLast, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>参数

*类*<br/>
此事件接收器映射所属的类。

*idFirst*<br/>
范围内第一个 OLE 控件的控制 ID。

*idLast*<br/>
范围内最后一个 OLE 控件的控制 ID。

*不一部分*<br/>
控件触发的事件的调度 ID。

*普芬汉德勒*<br/>
指向处理事件的成员函数的指针。 此函数应具有 BOOL 返回类型、UINT 类型（用于控件 ID）的第一个参数，以及与事件参数匹配的其他参数类型（请参阅*vtsParams）。* 该函数应返回 TRUE 以指示事件已处理;因此，应返回 TRUE，以指示事件已处理。否则 FALSE。

*vtsParams*<br/>
指定事件参数类型的**VTS_** 常量序列。 对于控件 ID，第一个常量应为VTS_I4类型。 这些是调度映射条目（如DISP_FUNCTION）中使用的相同常量。

### <a name="remarks"></a>备注

*vtsParams*参数是**VTS_常量**中由空间分隔的值列表。 一个或多个这些值由空格（不是逗号）分隔，指定函数的参数列表。 例如：

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

指定包含短整数后跟 BOOL 的列表。

有关**VTS_** 常量的列表，请参阅[EVENT_CUSTOM](event-maps.md#event_custom)。

### <a name="example"></a>示例

下面的示例演示了为三个控件（IDC_MYCTRL1 通过IDC_MYCTRL3）为鼠标关闭事件实现的事件处理程序。 事件处理程序函数`OnRangeMouseDown`， 在对话框类 （ `CMyDlg`） 的标头文件中声明为：

[!code-cpp[NVC_MFCAutomation#12](../../mfc/codesnippet/cpp/event-sink-maps_2.h)]

下面的代码在对话框类的实现文件中定义。

[!code-cpp[NVC_MFCAutomation#13](../../mfc/codesnippet/cpp/event-sink-maps_3.cpp)]

### <a name="requirements"></a>要求

  **标题**afxdisp.h

## <a name="on_event_reflect"></a><a name="on_event_reflect"></a>ON_EVENT_REFLECT

ON_EVENT_REFLECT宏在 OLE 控件的包装类的事件接收器映射中使用时，在控件的容器处理事件之前接收控件触发的事件。

```
ON_EVENT_REFLECT(theClass,  dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>参数

*类*<br/>
此事件接收器映射所属的类。

*不一部分*<br/>
控件触发的事件的调度 ID。

*普芬汉德勒*<br/>
指向处理事件的成员函数的指针。 此函数应具有与事件参数匹配的 BOOL 返回类型和参数类型（请参阅*vtsParams）。* 该函数应返回 TRUE 以指示事件已处理;因此，应返回 TRUE，以指示事件已处理。否则 FALSE。

*vtsParams*<br/>
指定事件参数类型的**VTS_** 常量序列。 这些是调度映射条目（如DISP_FUNCTION）中使用的相同常量。

### <a name="remarks"></a>备注

*vtsParams*参数是**VTS_常量**中由空间分隔的值列表。

一个或多个这些值由空格（不是逗号）分隔，指定函数的参数列表。 例如：

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

指定包含短整数后跟 BOOL 的列表。

有关**VTS_** 常量的列表，请参阅[EVENT_CUSTOM](event-maps.md#event_custom)。

### <a name="requirements"></a>要求

  **标题**afxdisp.h

## <a name="on_propnotify"></a><a name="on_propnotify"></a>ON_PROPNOTIFY

使用ON_PROPNOTIFY宏定义事件接收器映射条目，用于处理来自 OLE 控件的属性通知。

```
ON_PROPNOTIFY(theClass, id, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>参数

*类*<br/>
此事件接收器映射所属的类。

*id*<br/>
OLE 控件的控制 ID。

*不一部分*<br/>
通知中涉及的属性的调度 ID。

*pfn请求*<br/>
指向处理此属性`OnRequestEdit`通知的成员函数的指针。 此功能应具有 BOOL 返回类型和**BOOL**<strong>\*</strong>参数。 此函数应将参数设置为 TRUE，以允许属性更改，FALSE 不允许。 该函数应返回 TRUE 以指示已处理通知;否则 FALSE。

*pfn改变*<br/>
指向处理此属性`OnChanged`通知的成员函数的指针。 该函数应具有 BOOL 返回类型和 UINT 参数。 该函数应返回 TRUE 以指示已处理通知;否则 FALSE。

### <a name="remarks"></a>备注

*vtsParams*参数是**VTS_常量**中由空间分隔的值列表。 一个或多个这些值由空格（不是逗号）分隔，指定函数的参数列表。 例如：

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

指定包含短整数后跟 BOOL 的列表。

有关**VTS_** 常量的列表，请参阅[EVENT_CUSTOM](event-maps.md#event_custom)。

## <a name="on_propnotify_range"></a><a name="on_propnotify_range"></a>ON_PROPNOTIFY_RANGE

使用ON_PROPNOTIFY_RANGE宏定义事件接收器映射条目，用于处理来自任何 OLE 控件的属性通知，该控件具有连续 ID 范围内的控制 ID。

```

ON_PROPNOTIFY_RANGE(theClass, idFirst, idLast, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>参数

*类*<br/>
此事件接收器映射所属的类。

*idFirst*<br/>
范围内第一个 OLE 控件的控制 ID。

*idLast*<br/>
范围内最后一个 OLE 控件的控制 ID。

*不一部分*<br/>
通知中涉及的属性的调度 ID。

*pfn请求*<br/>
指向处理此属性`OnRequestEdit`通知的成员函数的指针。 此函数应具有`BOOL`返回类型和`UINT`和`BOOL*`参数。 该函数应将参数设置为 TRUE，以允许属性更改，FALSE 将不允许。 该函数应返回 TRUE 以指示已处理通知;否则 FALSE。

*pfn改变*<br/>
指向处理此属性`OnChanged`通知的成员函数的指针。 函数应具有`BOOL`返回类型和参数`UINT`。 该函数应返回 TRUE 以指示已处理通知;否则 FALSE。

### <a name="requirements"></a>要求

  **标题**afxdisp.h

## <a name="on_propnotify_reflect"></a><a name="on_propnotify_reflect"></a>ON_PROPNOTIFY_REFLECT

ON_PROPNOTIFY_REFLECT宏在 OLE 控件的包装类的事件接收器映射中使用时，接收控件在控件的容器处理之前发送的属性通知。

```

ON_PROPNOTIFY_REFLECT(theClass, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>参数

*类*<br/>
此事件接收器映射所属的类。

*不一部分*<br/>
通知中涉及的属性的调度 ID。

*pfn请求*<br/>
指向处理此属性`OnRequestEdit`通知的成员函数的指针。 此功能应具有 BOOL 返回类型和**BOOL**<strong>\*</strong>参数。 此函数应将参数设置为 TRUE，以允许属性更改，FALSE 不允许。 该函数应返回 TRUE 以指示已处理通知;否则 FALSE。

*pfn改变*<br/>
指向处理此属性`OnChanged`通知的成员函数的指针。 该函数应具有 BOOL 返回类型，但没有参数。 该函数应返回 TRUE 以指示已处理通知;否则 FALSE。

### <a name="requirements"></a>要求

  **标题**afxdisp.h

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
