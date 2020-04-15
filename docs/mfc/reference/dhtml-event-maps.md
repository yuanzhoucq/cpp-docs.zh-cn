---
title: DHTML 事件映射
ms.date: 11/04/2016
f1_keywords:
- vc.macros.shared
helpviewer_keywords:
- event map macros [MFC]
- DHTML [MFC], event map macros
- macros [MFC], DHTML event map
- DHTML events [MFC], event map
- DHTML events [MFC]
ms.assetid: 9a2c8ae7-7216-4a5e-bc60-6b98695be0c6
ms.openlocfilehash: 30c755b2901374cffab3ce91d0683811ef6624b6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365809"
---
# <a name="dhtml-event-maps"></a>DHTML 事件映射

以下宏可用于处理 DHTML 事件。

## <a name="dhtml-event-map-macros"></a>DHTML 事件映射宏

以下宏可用于处理[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)派生类中的 DHTML 事件。

|||
|-|-|
|[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)|标记 DHTML 事件映射的开始。|
|[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)|标记 DHTML 事件映射的开始。|
|[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)|声明 DHTML 事件映射。|
|[DHTML_EVENT](#dhtml_event)|用于在单个 HTML 元素的文档级别处理事件。|
|[DHTML_EVENT_AXCONTROL](#dhtml_event_axcontrol)|用于处理由 ActiveX 控件触发的事件。|
|[DHTML_EVENT_CLASS](#dhtml_event_class)|用于处理具有特定 CSS 类的所有 HTML 元素的文档级别的事件。|
|[DHTML_EVENT_ELEMENT](#dhtml_event_element)|用于在元素级别处理事件。|
|[DHTML_EVENT_ONAFTERUPDATE](#dhtml_event_onafterupdate)|用于从 HTML`onafterupdate`元素处理事件。|
|[DHTML_EVENT_ONBEFOREUPDATE](#dhtml_event_onbeforeupdate)|用于从 HTML`onbeforeupdate`元素处理事件。|
|[DHTML_EVENT_ONBLUR](#dhtml_event_onblur)|用于从 HTML`onblur`元素处理事件。|
|[DHTML_EVENT_ONCHANGE](#dhtml_event_onchange)|用于从 HTML`onchange`元素处理事件。|
|[DHTML_EVENT_ONCLICK](#dhtml_event_onclick)|用于从 HTML`onclick`元素处理事件。|
|[DHTML_EVENT_ONDATAAVAILABLE](#dhtml_event_ondataavailable)|用于从 HTML`ondataavailable`元素处理事件。|
|[DHTML_EVENT_ONDATASETCHANGED](#dhtml_event_ondatasetchanged)|用于从 HTML`ondatasetchanged`元素处理事件。|
|[DHTML_EVENT_ONDATASETCOMPLETE](#dhtml_event_ondatasetcomplete)|用于从 HTML`ondatasetcomplete`元素处理事件。|
|[DHTML_EVENT_ONDBLCLICK](#dhtml_event_ondblclick)|用于从 HTML`ondblclick`元素处理事件。|
|[DHTML_EVENT_ONDRAGSTART](#dhtml_event_ondragstart)|用于从 HTML`ondragstart`元素处理事件。|
|[DHTML_EVENT_ONERRORUPDATE](#dhtml_event_onerrorupdate)|用于从 HTML`onerrorupdate`元素处理事件。|
|[DHTML_EVENT_ONFILTERCHANGE](#dhtml_event_onfilterchange)|用于从 HTML`onfilterchange`元素处理事件。|
|[DHTML_EVENT_ONFOCUS](#dhtml_event_onfocus)|用于从 HTML`onfocus`元素处理事件。|
|[DHTML_EVENT_ONHELP](#dhtml_event_onhelp)|用于从 HTML`onhelp`元素处理事件。|
|[DHTML_EVENT_ONKEYDOWN](#dhtml_event_onkeydown)|用于从 HTML`onkeydown`元素处理事件。|
|[DHTML_EVENT_ONKEYPRESS](#dhtml_event_onkeypress)|用于从 HTML`onkeypress`元素处理事件。|
|[DHTML_EVENT_ONKEYUP](#dhtml_event_onkeyup)|用于从 HTML`onkeyup`元素处理事件。|
|[DHTML_EVENT_ONMOUSEDOWN](#dhtml_event_onmousedown)|用于从 HTML`onmousedown`元素处理事件。|
|[DHTML_EVENT_ONMOUSEMOVE](#dhtml_event_onmousemove)|用于从 HTML`onmousemove`元素处理事件。|
|[DHTML_EVENT_ONMOUSEOUT](#dhtml_event_onmouseout)|用于从 HTML`onmouseout`元素处理事件。|
|[DHTML_EVENT_ONMOUSEOVER](#dhtml_event_onmouseover)|用于从 HTML`onmouseover`元素处理事件。|
|[DHTML_EVENT_ONMOUSEUP](#dhtml_event_onmouseup)|用于从 HTML`onmouseup`元素处理事件。|
|[DHTML_EVENT_ONRESIZE](#dhtml_event_onresize)|用于从 HTML`onresize`元素处理事件。|
|[DHTML_EVENT_ONROWENTER](#dhtml_event_onrowenter)|用于从 HTML`onrowenter`元素处理事件。|
|[DHTML_EVENT_ONROWEXIT](#dhtml_event_onrowexit)|用于从 HTML`onrowexit`元素处理事件。|
|[DHTML_EVENT_ONSELECTSTART](#dhtml_event_onselectstart)|用于从 HTML`onselectstart`元素处理事件。|
|[DHTML_EVENT_TAG](#dhtml_event_tag)|用于处理具有特定 HTML 标记的所有元素的文档级别的事件。|
|[END_DHTML_EVENT_MAP](#end_dhtml_event_map)|标记 DHTML 事件映射的末尾。|
|[END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)|标记 DHTML 事件映射的末尾。 |

## <a name="url-event-map-macros"></a>URL 事件映射宏

以下宏可用于处理[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)派生类中的 DHTML 事件。

|||
|-|-|
|[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)|标记多页 DHTML 和 URL 事件映射的开始。|
|[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)|标记嵌入 DHTML 事件映射的开始。|
|[BEGIN_URL_ENTRIES](#begin_url_entries)|标记 URL 事件条目映射的开始。|
|[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)|声明多页 DHTML 和 URL 事件映射。|
|[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)|标记多页 DHTML 和 URL 事件映射的结尾。|
|[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)|标记嵌入 DHTML 事件映射的末尾。|
|[END_URL_ENTRIES](#end_url_entries)|标记 URL 事件条目映射的末尾。|
|[URL_EVENT_ENTRY](#url_event_entry)|将 URL 或 HTML 资源映射到多页对话框中的页面。|

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="begin_dhtml_event_map"></a><a name="begin_dhtml_event_map"></a>BEGIN_DHTML_EVENT_MAP

在 源文件中放置 由 标识`className`的类时，标记 DHTML 事件映射的开头。

```cpp
BEGIN_DHTML_EVENT_MAP(className)
```

### <a name="parameters"></a>参数

*类名称*<br/>
包含 DHTML 事件映射的类的名称。 此类应直接或间接地派生自[CDHtmlDialog，](../../mfc/reference/cdhtmldialog-class.md)并在其类定义中包含[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)宏。

### <a name="remarks"></a>备注

向类添加 DHTML 事件映射以向其`CDHtmlDialog`提供信息，这些信息可用于将网页中的 HTML 元素或 ActiveX 控件触发的事件路由到类中的处理程序函数。

将BEGIN_DHTML_EVENT_MAP宏放在类的实现 （.cpp） 文件中，然后DHTML_EVENT宏，用于该类要处理的事件（例如，DHTML_EVENT_ONMOUSEOVER鼠标悬停事件）。 使用[END_DHTML_EVENT_MAP](#end_dhtml_event_map)宏标记事件映射的结尾。 这些宏实现以下功能：

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="begin_dhtml_event_map_inline"></a><a name="begin_dhtml_event_map_inline"></a>BEGIN_DHTML_EVENT_MAP_INLINE

在*类名称*的类定义中标记 DHTML 事件映射的开头。

```cpp
BEGIN_DHTML_EVENT_MAP_INLINE(className)
```

### <a name="parameters"></a>参数

*类名称*<br/>
包含 DHTML 事件映射的类的名称。 此类应直接或间接地派生自[CDHtmlDialog，](../../mfc/reference/cdhtmldialog-class.md)并在其类定义中包含[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)宏。

### <a name="remarks"></a>备注

向类添加 DHTML 事件映射以向其`CDHtmlDialog`提供信息，这些信息可用于将网页中的 HTML 元素或 ActiveX 控件触发的事件路由到类中的处理程序函数。

将BEGIN_DHTML_EVENT_MAP宏放在类的定义 （.h） 文件中，然后将DHTML_EVENT宏放在类要处理的事件（例如，鼠标悬停事件DHTML_EVENT_ONMOUSEOVER）。 使用[END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)宏标记事件映射的结尾。 这些宏实现以下功能：

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="declare_dhtml_event_map"></a><a name="declare_dhtml_event_map"></a>DECLARE_DHTML_EVENT_MAP

在类定义中声明 DHTML 事件映射。

```cpp
DECLARE_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>备注

此宏将用于[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)派生类的定义。

使用[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)或[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)实现地图。

[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)声明以下函数：

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap( );`

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event"></a><a name="dhtml_event"></a>DHTML_EVENT

句柄（在文档级别）由*elemName*标识的 HTML 元素标识的*未pid*事件源自。

```cpp
DHTML_EVENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>参数

*不一部分*<br/>
要处理的事件的 DISPID。

*埃莱姆纳*<br/>
持有 HTML 元素的 ID 以处理文档事件的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_axcontrol"></a><a name="dhtml_event_axcontrol"></a>DHTML_EVENT_AXCONTROL

处理由*控件名称*标识的 ActiveX 控件触发*的不pid*触发的事件。

```cpp
DHTML_EVENT_AXCONTROL(dispid, controlName,  memberFxn)
```

### <a name="parameters"></a>参数

*不一部分*<br/>
要处理的事件的调度 ID。

*控件名称*<br/>
持有触发事件的控件的 HTML ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_class"></a><a name="dhtml_event_class"></a>DHTML_EVENT_CLASS

句柄（在文档级别）由任何 HTML 元素使用*elemName*标识的 CSS 类发起的 *"无源*"标识的事件。

```cpp
DHTML_EVENT_CLASS(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>参数

*不一部分*<br/>
要处理的事件的调度 ID。

*埃莱姆纳*<br/>
持有 HTML 元素的 CSS 类的 LPCWSTR，该元素源为事件。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_element"></a><a name="dhtml_event_element"></a>DHTML_EVENT_ELEMENT

句柄（在*elemName*标识的元素）由*dispid*标识的事件。

```cpp
DHTML_EVENT_ELEMENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>参数

*不一部分*<br/>
要处理的事件的调度 ID。

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

如果此宏用于处理非冒泡事件，则事件源将是*elemName*标识的元素。

如果此宏用于处理冒泡事件，*则 elemName*标识的元素可能不是事件的来源（源可能是*elemName*包含的任何元素）。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_onafterupdate"></a><a name="dhtml_event_onafterupdate"></a>DHTML_EVENT_ONAFTERUPDATE

句柄（在文档级别），`onafterupdate`事件由*elemName*标识的 HTML 元素发起。

```cpp
DHTML_EVENT_ONAFTERUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_onbeforeupdate"></a><a name="dhtml_event_onbeforeupdate"></a>DHTML_EVENT_ONBEFOREUPDATE

句柄（在文档级别），`onbeforeupdate`事件由*elemName*标识的 HTML 元素发起。

```cpp
DHTML_EVENT_ONBEFOREUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_onblur"></a><a name="dhtml_event_onblur"></a>DHTML_EVENT_ONBLUR

处理（在元素级别）事件`onblur`。 这是一个非冒泡事件。

```cpp
DHTML_EVENT_ONBLUR(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_onchange"></a><a name="dhtml_event_onchange"></a>DHTML_EVENT_ONCHANGE

处理（在元素级别）事件`onchange`。 这是一个非冒泡事件。

```cpp
DHTML_EVENT_ONCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_onclick"></a><a name="dhtml_event_onclick"></a>DHTML_EVENT_ONCLICK

句柄（在文档级别），`onclick`事件由*elemName*标识的 HTML 元素发起。

```cpp
DHTML_EVENT_ONCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_ondataavailable"></a><a name="dhtml_event_ondataavailable"></a>DHTML_EVENT_ONDATAAVAILABLE

句柄（在文档级别），`ondataavailable`事件由*elemName*标识的 HTML 元素发起。

```cpp
DHTML_EVENT_ONDATAAVAILABLE(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_ondatasetchanged"></a><a name="dhtml_event_ondatasetchanged"></a>DHTML_EVENT_ONDATASETCHANGED

句柄（在文档级别），`ondatasetchanged`事件由*elemName*标识的 HTML 元素发起。

```cpp
DHTML_EVENT_ONDATASETCHANGED(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_ondatasetcomplete"></a><a name="dhtml_event_ondatasetcomplete"></a>DHTML_EVENT_ONDATASETCOMPLETE

句柄（在文档级别），`ondatasetcomplete`由 标识`elemName`的 HTML 元素发起的事件。

```cpp
DHTML_EVENT_ONDATASETCOMPLETE(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_ondblclick"></a><a name="dhtml_event_ondblclick"></a>DHTML_EVENT_ONDBLCLICK

句柄（在文档级别），`ondblclick`事件由*elemName*标识的 HTML 元素发起。

```cpp
DHTML_EVENT_ONDBLCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_ondragstart"></a><a name="dhtml_event_ondragstart"></a>DHTML_EVENT_ONDRAGSTART

句柄（在文档级别），`ondragstart`事件由*elemName*标识的 HTML 元素发起。

```cpp
DHTML_EVENT_ONDRAGSTART(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_onerrorupdate"></a><a name="dhtml_event_onerrorupdate"></a>DHTML_EVENT_ONERRORUPDATE

句柄（在文档级别），`onerrorupdate`事件由*elemName*标识的 HTML 元素发起。

```cpp
DHTML_EVENT_ONERRORUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_onfilterchange"></a><a name="dhtml_event_onfilterchange"></a>DHTML_EVENT_ONFILTERCHANGE

句柄（在文档级别），`onfilterchange`事件由*elemName*标识的 HTML 元素发起。

```cpp
DHTML_EVENT_ONFILTERCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_onfocus"></a><a name="dhtml_event_onfocus"></a>DHTML_EVENT_ONFOCUS

处理（在元素级别）事件`onfocus`。 这是一个非冒泡事件。

```cpp
DHTML_EVENT_ONFOCUS(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_onhelp"></a><a name="dhtml_event_onhelp"></a>DHTML_EVENT_ONHELP

句柄（在文档级别），`onhelp`事件由*elemName*标识的 HTML 元素发起。

```cpp
DHTML_EVENT_ONHELP(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_onkeydown"></a><a name="dhtml_event_onkeydown"></a>DHTML_EVENT_ONKEYDOWN

句柄（在文档级别），`onkeydown`事件由*elemName*标识的 HTML 元素发起。

```cpp
DHTML_EVENT_ONKEYDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_onkeypress"></a><a name="dhtml_event_onkeypress"></a>DHTML_EVENT_ONKEYPRESS

句柄（在文档级别），`onkeypress`事件由*elemName*标识的 HTML 元素发起。

```cpp
DHTML_EVENT_ONKEYPRESS(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_onkeyup"></a><a name="dhtml_event_onkeyup"></a>DHTML_EVENT_ONKEYUP

句柄（在文档级别），`onkeyup`事件由*elemName*标识的 HTML 元素发起。

```cpp
DHTML_EVENT_ONKEYUP(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_onmousedown"></a><a name="dhtml_event_onmousedown"></a>DHTML_EVENT_ONMOUSEDOWN

句柄（在文档级别），`onmousedown`事件由*elemName*标识的 HTML 元素发起。

```cpp
DHTML_EVENT_ONMOUSEDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_onmousemove"></a><a name="dhtml_event_onmousemove"></a>DHTML_EVENT_ONMOUSEMOVE

句柄（在文档级别），`onmousemove`事件由*elemName*标识的 HTML 元素发起。

```cpp
DHTML_EVENT_ONMOUSEMOVE(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_onmouseout"></a><a name="dhtml_event_onmouseout"></a>DHTML_EVENT_ONMOUSEOUT

句柄（在文档级别），`onmouseout`事件由*elemName*标识的 HTML 元素发起。

```cpp
DHTML_EVENT_ONMOUSEOUT(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_onmouseover"></a><a name="dhtml_event_onmouseover"></a>DHTML_EVENT_ONMOUSEOVER

句柄（在文档级别），`onmouseover`事件由*elemName*标识的 HTML 元素发起。

```cpp
DHTML_EVENT_ONMOUSEOVER(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_onmouseup"></a><a name="dhtml_event_onmouseup"></a>DHTML_EVENT_ONMOUSEUP

句柄（在文档级别），`onmouseup`事件由*elemName*标识的 HTML 元素发起。

```cpp
DHTML_EVENT_ONMOUSEUP(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_onresize"></a><a name="dhtml_event_onresize"></a>DHTML_EVENT_ONRESIZE

处理（在元素级别）事件`onresize`。 这是一个非冒泡事件。

```cpp
DHTML_EVENT_ONRESIZE(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_onrowenter"></a><a name="dhtml_event_onrowenter"></a>DHTML_EVENT_ONROWENTER

句柄（在文档级别），`onrowenter`事件由*elemName*标识的 HTML 元素发起。

```cpp
DHTML_EVENT_ONROWENTER(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_onrowexit"></a><a name="dhtml_event_onrowexit"></a>DHTML_EVENT_ONROWEXIT

句柄（在文档级别），`onrowexit`事件由*elemName*标识的 HTML 元素发起。

```cpp
DHTML_EVENT_ONROWEXIT(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_onselectstart"></a><a name="dhtml_event_onselectstart"></a>DHTML_EVENT_ONSELECTSTART

句柄（在文档级别），`onselectstart`事件由*elemName*标识的 HTML 元素发起。

```cpp
DHTML_EVENT_ONSELECTSTART(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*埃莱姆纳*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="dhtml_event_tag"></a><a name="dhtml_event_tag"></a>DHTML_EVENT_TAG

句柄（在文档级别）由`dispid`任何 HTML 元素使用*elemName*标识的 HTML 标记标识的事件。

```cpp
DHTML_EVENT_TAG(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>参数

*不一部分*<br/>
要处理的事件的调度 ID。

*埃莱姆纳*<br/>
源事件的 HTML 元素的 HTML 标记。

*成员Fxn*<br/>
事件的处理程序函数。

### <a name="remarks"></a>备注

使用此宏可向类中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加条目。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="end_dhtml_event_map"></a><a name="end_dhtml_event_map"></a>END_DHTML_EVENT_MAP

标记 DHTML 事件映射的末尾。

```cpp
END_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>备注

必须与[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)一起使用。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="begin_dhtml_url_event_map"></a><a name="begin_dhtml_url_event_map"></a>BEGIN_DHTML_URL_EVENT_MAP

在多页对话框中启动 DHTML 和 URL 事件映射的定义。

```cpp
BEGIN_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>备注

将BEGIN_DHTML_URL_EVENT_MAP放在[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)派生类的实现文件中。 使用[嵌入的 DHTML 事件映射](#begin_embed_dhtml_event_map)和[URL 条目](#begin_url_entries)进行操作，然后用[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)将其关闭。 将[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)宏包含在类定义中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#196](../../mfc/codesnippet/cpp/dhtml-event-maps_1.cpp)]

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="begin_embed_dhtml_event_map"></a><a name="begin_embed_dhtml_event_map"></a>BEGIN_EMBED_DHTML_EVENT_MAP

在多页对话框中启动嵌入 DHTML 事件映射的定义。

```cpp
BEGIN_EMBED_DHTML_EVENT_MAP(className, mapName)
```

### <a name="parameters"></a>参数

*类名称*<br/>
包含事件映射的类的名称。 此类应直接或间接派生自[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 嵌入的 DHTML 事件映射必须位于[DHTML 和 URL 事件映射](#begin_dhtml_url_event_map)中。

*地图名称*<br/>
指定事件映射为其事件的页面。 这与[URL_EVENT_ENTRY](#url_event_entry)宏中实际定义 URL 或 HTML 资源的*地图名称*相匹配。

### <a name="remarks"></a>备注

由于多页 DHTML 对话框由多个 HTML 页面组成，每个页面都可以引发 DHTML 事件，因此嵌入的事件映射用于将事件映射到每个页面的处理程序。

DHTML 和 URL 事件映射中的嵌入事件映射由BEGIN_EMBED_DHTML_EVENT_MAP宏组成，后跟[DHTML_EVENT](#dhtml_event)宏和[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)宏。

每个嵌入的事件映射都需要一个相应的[URL 事件条目](#url_event_entry)，以将*mapName（BEGIN_EMBED_DHTML_EVENT_MAP*中指定）映射到 URL 或 HTML 资源。

### <a name="example"></a>示例

请参阅[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)中的示例。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="begin_url_entries"></a><a name="begin_url_entries"></a>BEGIN_URL_ENTRIES

在多页对话框中启动 URL 事件输入映射的定义。

```cpp
BEGIN_URL_ENTRIES(className)
```

### <a name="parameters"></a>参数

*类名称*<br/>
包含 URL 事件映射的类的名称。 此类应直接或间接派生自[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 URL 事件条目映射必须位于[DHTML 和 URL 事件映射](#begin_dhtml_url_event_map)中。

### <a name="remarks"></a>备注

由于多页 DHTML 对话框由多个 HTML 页面组成，因此 URL 事件条目用于将 URL 或 HTML 资源映射到相应的[嵌入式 DHTML 事件映射](#begin_embed_dhtml_event_map)。 将URL_EVENT_ENTRY宏放在BEGIN_URL_ENTRIES和[END_URL_ENTRIES](#end_url_entries)宏之间。

### <a name="example"></a>示例

请参阅[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)中的示例。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="declare_dhtml_url_event_map"></a><a name="declare_dhtml_url_event_map"></a>DECLARE_DHTML_URL_EVENT_MAP

在类定义中声明 DHTML 和 URL 事件映射。

```cpp
DECLARE_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>备注

此宏将用于[CMultiPageDHtmlDialog-](../../mfc/reference/cmultipagedhtmldialog-class.md)派生类的定义。

DHTML 和 URL 事件映射包含嵌入的[DHTML 事件映射](#begin_embed_dhtml_event_map)和[URL 事件条目](#begin_url_entries)，用于按页将 DHTML 事件映射到处理程序。 使用[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)实现映射。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="end_dhtml_url_event_map"></a><a name="end_dhtml_url_event_map"></a>END_DHTML_URL_EVENT_MAP

标记 DHTML 和 URL 事件映射的结尾。

```cpp
END_DHTML_URL_EVENT_MAP(className)
```

### <a name="parameters"></a>参数

*类名称*<br/>
包含事件映射的类的名称。 此类应直接或间接派生自[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 这应该匹配相应[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)宏中的*类名称*。

### <a name="example"></a>示例

请参阅[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)中的示例。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="end_embed_dhtml_event_map"></a><a name="end_embed_dhtml_event_map"></a>END_EMBED_DHTML_EVENT_MAP

标记嵌入 DHTML 事件映射的末尾。

```cpp
END_EMBED_DHTML_EVENT_MAP()
```

### <a name="example"></a>示例

请参阅[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)中的示例。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="end_url_entries"></a><a name="end_url_entries"></a>END_URL_ENTRIES

标记 URL 事件条目映射的末尾。

```cpp
END_URL_ENTRIES()
```

### <a name="example"></a>示例

请参阅[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)中的示例。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="url_event_entry"></a><a name="url_event_entry"></a>URL_EVENT_ENTRY

将 URL 或 HTML 资源映射到多页对话框中的页面。

```cpp
URL_EVENT_ENTRY(className, url,  mapName)
```

### <a name="parameters"></a>参数

*类名称*<br/>
包含 URL 事件映射的类的名称。 此类应直接或间接派生自[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 URL 事件条目映射必须位于[DHTML 和 URL 事件映射](#begin_dhtml_url_event_map)中。

*url*<br/>
页面的 URL 或 HTML 资源。

*地图名称*<br/>
指定其 URL 为*URL*的页面。 这与[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)宏中的*地图名称*匹配，该宏映射此页中的事件。

### <a name="remarks"></a>备注

如果页面是 HTML 资源，*则 URL*必须是资源 ID 号（即"123"，而不是 123 或 ID_HTMLRES1）的字符串表示形式。

页面标识符*mapName*是一个任意符号，用于将嵌入的 DHTML 事件映射链接到 URL 事件条目映射。 它在范围上仅限于 DHTML 和 URL 事件映射。

### <a name="example"></a>示例

请参阅[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)中的示例。

### <a name="requirements"></a>要求

  **头**afxdhtml.h

## <a name="end_dhtml_event_map_inline"></a><a name="end_dhtml_event_map_inline"></a>END_DHTML_EVENT_MAP_INLINE

标记 DHTML 事件映射的末尾。

### <a name="syntax"></a>语法

```cpp
END_DHTML_EVENT_MAP_INLINE( )
```

### <a name="remarks"></a>备注

必须与[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)一起使用。

### <a name="requirements"></a>要求

**标题：** afxdhtml.h

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](mfc-macros-and-globals.md)
