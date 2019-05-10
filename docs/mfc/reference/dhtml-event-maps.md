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
ms.openlocfilehash: 5ae37acd3e0b0c2636e6a3e985490a2feab8fa34
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322808"
---
# <a name="dhtml-event-maps"></a>DHTML 事件映射

下列宏可以用于处理 DHTML 事件。

## <a name="dhtml-event-map-macros"></a>DHTML 事件映射宏

下列宏可用于处理中的 DHTML 事件[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-派生的类。

|||
|-|-|
|[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)|标记 DHTML 事件映射的开头。|
|[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)|标记 DHTML 事件映射的开头。|
|[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)|声明 DHTML 事件映射。|
|[DHTML_EVENT](#dhtml_event)|用于处理在单个的 HTML 元素的文档级别的事件。|
|[DHTML_EVENT_AXCONTROL](#dhtml_event_axcontrol)|用于处理由 ActiveX 控件激发的事件。|
|[DHTML_EVENT_CLASS](#dhtml_event_class)|用于处理在使用特定的 CSS 类的所有 HTML 元素的文档级别的事件。|
|[DHTML_EVENT_ELEMENT](#dhtml_event_element)|用于处理在元素级别的事件。|
|[DHTML_EVENT_ONAFTERUPDATE](#dhtml_event_onafterupdate)|用于处理`onafterupdate`HTML 元素中的事件。|
|[DHTML_EVENT_ONBEFOREUPDATE](#dhtml_event_onbeforeupdate)|用于处理`onbeforeupdate`HTML 元素中的事件。|
|[DHTML_EVENT_ONBLUR](#dhtml_event_onblur)|用于处理`onblur`HTML 元素中的事件。|
|[DHTML_EVENT_ONCHANGE](#dhtml_event_onchange)|用于处理`onchange`HTML 元素中的事件。|
|[DHTML_EVENT_ONCLICK](#dhtml_event_onclick)|用于处理`onclick`HTML 元素中的事件。|
|[DHTML_EVENT_ONDATAAVAILABLE](#dhtml_event_ondataavailable)|用于处理`ondataavailable`HTML 元素中的事件。|
|[DHTML_EVENT_ONDATASETCHANGED](#dhtml_event_ondatasetchanged)|用于处理`ondatasetchanged`HTML 元素中的事件。|
|[DHTML_EVENT_ONDATASETCOMPLETE](#dhtml_event_ondatasetcomplete)|用于处理`ondatasetcomplete`HTML 元素中的事件。|
|[DHTML_EVENT_ONDBLCLICK](#dhtml_event_ondblclick)|用于处理`ondblclick`HTML 元素中的事件。|
|[DHTML_EVENT_ONDRAGSTART](#dhtml_event_ondragstart)|用于处理`ondragstart`HTML 元素中的事件。|
|[DHTML_EVENT_ONERRORUPDATE](#dhtml_event_onerrorupdate)|用于处理`onerrorupdate`HTML 元素中的事件。|
|[DHTML_EVENT_ONFILTERCHANGE](#dhtml_event_onfilterchange)|用于处理`onfilterchange`HTML 元素中的事件。|
|[DHTML_EVENT_ONFOCUS](#dhtml_event_onfocus)|用于处理`onfocus`HTML 元素中的事件。|
|[DHTML_EVENT_ONHELP](#dhtml_event_onhelp)|用于处理`onhelp`HTML 元素中的事件。|
|[DHTML_EVENT_ONKEYDOWN](#dhtml_event_onkeydown)|用于处理`onkeydown`HTML 元素中的事件。|
|[DHTML_EVENT_ONKEYPRESS](#dhtml_event_onkeypress)|用于处理`onkeypress`HTML 元素中的事件。|
|[DHTML_EVENT_ONKEYUP](#dhtml_event_onkeyup)|用于处理`onkeyup`HTML 元素中的事件。|
|[DHTML_EVENT_ONMOUSEDOWN](#dhtml_event_onmousedown)|用于处理`onmousedown`HTML 元素中的事件。|
|[DHTML_EVENT_ONMOUSEMOVE](#dhtml_event_onmousemove)|用于处理`onmousemove`HTML 元素中的事件。|
|[DHTML_EVENT_ONMOUSEOUT](#dhtml_event_onmouseout)|用于处理`onmouseout`HTML 元素中的事件。|
|[DHTML_EVENT_ONMOUSEOVER](#dhtml_event_onmouseover)|用于处理`onmouseover`HTML 元素中的事件。|
|[DHTML_EVENT_ONMOUSEUP](#dhtml_event_onmouseup)|用于处理`onmouseup`HTML 元素中的事件。|
|[DHTML_EVENT_ONRESIZE](#dhtml_event_onresize)|用于处理`onresize`HTML 元素中的事件。|
|[DHTML_EVENT_ONROWENTER](#dhtml_event_onrowenter)|用于处理`onrowenter`HTML 元素中的事件。|
|[DHTML_EVENT_ONROWEXIT](#dhtml_event_onrowexit)|用于处理`onrowexit`HTML 元素中的事件。|
|[DHTML_EVENT_ONSELECTSTART](#dhtml_event_onselectstart)|用于处理`onselectstart`HTML 元素中的事件。|
|[DHTML_EVENT_TAG](#dhtml_event_tag)|用于处理在具有特定的 HTML 标记的所有元素的文档级别的事件。|
|[END_DHTML_EVENT_MAP](#end_dhtml_event_map)|标记 DHTML 事件映射的末尾。|
|[END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)|标记 DHTML 事件映射的末尾。 |

## <a name="url-event-map-macros"></a>URL 事件映射宏

下列宏可用于处理中的 DHTML 事件[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-派生的类。

|||
|-|-|
|[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)|标记多页 DHTML 和 URL 事件映射的开头。|
|[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)|标记嵌入 DHTML 事件映射的开头。|
|[BEGIN_URL_ENTRIES](#begin_url_entries)|标记 URL 事件输入映射的开头。|
|[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)|声明多页 DHTML 和 URL 事件映射。|
|[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)|标记多页 DHTML 和 URL 事件映射的末尾。|
|[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)|标记嵌入 DHTML 事件映射的末尾。|
|[END_URL_ENTRIES](#end_url_entries)|标记 URL 事件输入映射的末尾。|
|[URL_EVENT_ENTRY](#url_event_entry)|将 URL 或 HTML 资源映射到多页对话框中的页。|

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="begin_dhtml_event_map"></a>  BEGIN_DHTML_EVENT_MAP

标记的 DHTML 事件映射放入由标识的类的源文件时开始`className`。

```
BEGIN_DHTML_EVENT_MAP(className)
```

### <a name="parameters"></a>参数

*className*<br/>
包含 DHTML 事件映射的类的名称。 此类应直接或间接派生[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)和包含[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)其类定义中的宏。

### <a name="remarks"></a>备注

将 DHTML 事件映射添加到您的类将信息提供给`CDHtmlDialog`，可用于触发的 HTML 元素或 ActiveX 控件在网页与类中的处理程序函数中的路由事件。

将 BEGIN_DHTML_EVENT_MAP 宏放在后跟 DHTML_EVENT 宏的类是以处理的事件的类的实现 (.cpp) 文件 (例如，鼠标悬停事件的 DHTML_EVENT_ONMOUSEOVER)。 使用[END_DHTML_EVENT_MAP](#end_dhtml_event_map)宏来标记事件映射的结尾。 这些宏实现以下函数：

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="begin_dhtml_event_map_inline"></a>  BEGIN_DHTML_EVENT_MAP_INLINE

表示的 DHTML 事件映射中的类定义开头*className*。

```
BEGIN_DHTML_EVENT_MAP_INLINE(className)
```

### <a name="parameters"></a>参数

*className*<br/>
包含 DHTML 事件映射的类的名称。 此类应直接或间接派生[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)和包含[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)其类定义中的宏。

### <a name="remarks"></a>备注

将 DHTML 事件映射添加到您的类将信息提供给`CDHtmlDialog`，可用于触发的 HTML 元素或 ActiveX 控件在网页与类中的处理程序函数中的路由事件。

BEGIN_DHTML_EVENT_MAP 宏置于后跟 DHTML_EVENT 宏的类是要处理的事件的类定义 (.h) 文件 (例如，鼠标悬停事件的 DHTML_EVENT_ONMOUSEOVER)。 使用[END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)宏来标记事件映射的结尾。 这些宏实现以下函数：

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="declare_dhtml_event_map"></a>  DECLARE_DHTML_EVENT_MAP

声明的 DHTML 事件映射中的类定义。

```
DECLARE_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>备注

此宏的定义中使用，则[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-派生的类。

使用[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)或[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)实现映射。

[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)声明以下函数：

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap( );`

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event"></a>  DHTML_EVENT

（在文档级别） 处理由标识的事件*dispid*由标识的 HTML 元素产生*elemName*。

```
DHTML_EVENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>参数

*dispid*<br/>
要处理的事件的 DISPID。

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR 或为 NULL，以处理文档事件。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_axcontrol"></a>  DHTML_EVENT_AXCONTROL

处理标识的事件*dispid*由标识的 ActiveX 控件激发*controlName*。

```
DHTML_EVENT_AXCONTROL(dispid, controlName,  memberFxn)
```

### <a name="parameters"></a>参数

*dispid*<br/>
要处理的事件的调度 ID。

*controlName*<br/>
保存触发此事件的控件的 HTML ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_class"></a>  DHTML_EVENT_CLASS

（在文档级别） 处理由标识的事件*dispid*标识的 CSS 类的任何 HTML 元素源自*elemName*。

```
DHTML_EVENT_CLASS(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>参数

*dispid*<br/>
要处理的事件的调度 ID。

*elemName*<br/>
保存事件溯源的 HTML 元素的 CSS 类 LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_element"></a>  DHTML_EVENT_ELEMENT

处理 (在标识的元素*elemName*) 由标识事件*dispid*。

```
DHTML_EVENT_ELEMENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>参数

*dispid*<br/>
要处理的事件的调度 ID。

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

如果使用此宏来处理 nonbubbling 事件，事件源将标识的元素*elemName*。

如果使用此宏来处理浮升事件，该元素由*elemName*可能不是事件的源 (数据源可能包含的任何元素*elemName*)。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_onafterupdate"></a>  DHTML_EVENT_ONAFTERUPDATE

（在文档级别） 处理`onafterupdate`事件的标识的 HTML 元素源自*elemName*。

```
DHTML_EVENT_ONAFTERUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_onbeforeupdate"></a>  DHTML_EVENT_ONBEFOREUPDATE

（在文档级别） 处理`onbeforeupdate`事件的标识的 HTML 元素源自*elemName*。

```
DHTML_EVENT_ONBEFOREUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_onblur"></a>  DHTML_EVENT_ONBLUR

（在元素级别） 处理`onblur`事件。 这是 nonbubbling 事件。

```
DHTML_EVENT_ONBLUR(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_onchange"></a>  DHTML_EVENT_ONCHANGE

（在元素级别） 处理`onchange`事件。 这是 nonbubbling 事件。

```
DHTML_EVENT_ONCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_onclick"></a>  DHTML_EVENT_ONCLICK

（在文档级别） 处理`onclick`事件的标识的 HTML 元素源自*elemName*。

```
DHTML_EVENT_ONCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_ondataavailable"></a>  DHTML_EVENT_ONDATAAVAILABLE

（在文档级别） 处理`ondataavailable`事件的标识的 HTML 元素源自*elemName*。

```
DHTML_EVENT_ONDATAAVAILABLE(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_ondatasetchanged"></a>  DHTML_EVENT_ONDATASETCHANGED

（在文档级别） 处理`ondatasetchanged`事件的标识的 HTML 元素源自*elemName*。

```
DHTML_EVENT_ONDATASETCHANGED(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_ondatasetcomplete"></a>  DHTML_EVENT_ONDATASETCOMPLETE

（在文档级别） 处理`ondatasetcomplete`事件源自的标识的 HTML 元素`elemName`。

```
DHTML_EVENT_ONDATASETCOMPLETE(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_ondblclick"></a>  DHTML_EVENT_ONDBLCLICK

（在文档级别） 处理`ondblclick`事件的标识的 HTML 元素源自*elemName*。

```
DHTML_EVENT_ONDBLCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_ondragstart"></a>  DHTML_EVENT_ONDRAGSTART

（在文档级别） 处理`ondragstart`事件的标识的 HTML 元素源自*elemName*。

```
DHTML_EVENT_ONDRAGSTART(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_onerrorupdate"></a>  DHTML_EVENT_ONERRORUPDATE

（在文档级别） 处理`onerrorupdate`事件的标识的 HTML 元素源自*elemName*。

```
DHTML_EVENT_ONERRORUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_onfilterchange"></a>  DHTML_EVENT_ONFILTERCHANGE

（在文档级别） 处理`onfilterchange`事件的标识的 HTML 元素源自*elemName*。

```

DHTML_EVENT_ONFILTERCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_onfocus"></a>  DHTML_EVENT_ONFOCUS

（在元素级别） 处理`onfocus`事件。 这是 nonbubbling 事件。

```

DHTML_EVENT_ONFOCUS(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_onhelp"></a>  DHTML_EVENT_ONHELP

（在文档级别） 处理`onhelp`事件的标识的 HTML 元素源自*elemName*。

```

DHTML_EVENT_ONHELP(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_onkeydown"></a>  DHTML_EVENT_ONKEYDOWN

（在文档级别） 处理`onkeydown`事件的标识的 HTML 元素源自*elemName*。

```

DHTML_EVENT_ONKEYDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_onkeypress"></a>  DHTML_EVENT_ONKEYPRESS

（在文档级别） 处理`onkeypress`事件的标识的 HTML 元素源自*elemName*。

```

DHTML_EVENT_ONKEYPRESS(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_onkeyup"></a>  DHTML_EVENT_ONKEYUP

（在文档级别） 处理`onkeyup`事件的标识的 HTML 元素源自*elemName*。

```

DHTML_EVENT_ONKEYUP(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_onmousedown"></a>  DHTML_EVENT_ONMOUSEDOWN

（在文档级别） 处理`onmousedown`事件的标识的 HTML 元素源自*elemName*。

```

DHTML_EVENT_ONMOUSEDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_onmousemove"></a>  DHTML_EVENT_ONMOUSEMOVE

（在文档级别） 处理`onmousemove`事件的标识的 HTML 元素源自*elemName*。

```

DHTML_EVENT_ONMOUSEMOVE(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_onmouseout"></a>  DHTML_EVENT_ONMOUSEOUT

（在文档级别） 处理`onmouseout`事件的标识的 HTML 元素源自*elemName*。

```

DHTML_EVENT_ONMOUSEOUT(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_onmouseover"></a>  DHTML_EVENT_ONMOUSEOVER

（在文档级别） 处理`onmouseover`事件的标识的 HTML 元素源自*elemName*。

```

DHTML_EVENT_ONMOUSEOVER(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_onmouseup"></a>  DHTML_EVENT_ONMOUSEUP

（在文档级别） 处理`onmouseup`事件的标识的 HTML 元素源自*elemName*。

```

DHTML_EVENT_ONMOUSEUP(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_onresize"></a>  DHTML_EVENT_ONRESIZE

（在元素级别） 处理`onresize`事件。 这是 nonbubbling 事件。

```

DHTML_EVENT_ONRESIZE(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_onrowenter"></a>  DHTML_EVENT_ONROWENTER

（在文档级别） 处理`onrowenter`事件的标识的 HTML 元素源自*elemName*。

```

DHTML_EVENT_ONROWENTER(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_onrowexit"></a>  DHTML_EVENT_ONROWEXIT

（在文档级别） 处理`onrowexit`事件的标识的 HTML 元素源自*elemName*。

```

DHTML_EVENT_ONROWEXIT(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_onselectstart"></a>  DHTML_EVENT_ONSELECTSTART

（在文档级别） 处理`onselectstart`事件的标识的 HTML 元素源自*elemName*。

```

DHTML_EVENT_ONSELECTSTART(elemName, memberFxn)
```

### <a name="parameters"></a>参数

*elemName*<br/>
保存事件溯源的 HTML 元素的 ID LPCWSTR。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="dhtml_event_tag"></a>  DHTML_EVENT_TAG

（在文档级别） 处理由标识的事件`dispid`标识的 HTML 标记的任何 HTML 元素源自*elemName*。

```
DHTML_EVENT_TAG(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>参数

*dispid*<br/>
要处理的事件的调度 ID。

*elemName*<br/>
事件溯源的 HTML 元素的 HTML 标记。

*memberFxn*<br/>
事件处理程序函数。

### <a name="remarks"></a>备注

使用此宏将添加一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)在类中。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="end_dhtml_event_map"></a>  END_DHTML_EVENT_MAP

标记 DHTML 事件映射的末尾。

```
END_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>备注

必须与结合使用[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="begin_dhtml_url_event_map"></a>  BEGIN_DHTML_URL_EVENT_MAP

在多页对话框中启动 DHTML 和 URL 事件映射的定义。

```
BEGIN_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>备注

实现文件中放入 BEGIN_DHTML_URL_EVENT_MAP 你[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-派生的类。 按照其与[嵌入 DHTML 事件映射](#begin_embed_dhtml_event_map)并[URL 条目](#begin_url_entries)，然后将其与关闭[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)。 包括[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)类定义中的宏。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#196](../../mfc/codesnippet/cpp/dhtml-event-maps_1.cpp)]

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="begin_embed_dhtml_event_map"></a>  BEGIN_EMBED_DHTML_EVENT_MAP

在多页对话框中，启动嵌入 DHTML 事件映射的定义。

```
BEGIN_EMBED_DHTML_EVENT_MAP(className, mapName)
```

### <a name="parameters"></a>参数

*className*<br/>
包含事件映射的类的名称。 此类应直接或间接派生[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 嵌入的 DHTML 事件映射必须位于[DHTML 和 URL 事件映射](#begin_dhtml_url_event_map))。

*mapName*<br/>
指定其事件将此映射的页。 这与匹配*mapName*中[URL_EVENT_ENTRY](#url_event_entry)宏实际上定义 URL 或 HTML 资源。

### <a name="remarks"></a>备注

由于多页 DHTML 对话框包含多个 HTML 页，其中每个可以引发 DHTML 事件，因此将使用嵌入的事件映射将事件映射到基于每个页面上的处理程序。

DHTML 和 URL 事件映射内的嵌入的事件映射包含后跟一个 BEGIN_EMBED_DHTML_EVENT_MAP 宏[DHTML_EVENT](#dhtml_event)宏和一个[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)宏。

每个嵌入的事件映射需要相应[URL 事件条目](#url_event_entry)映射*mapName* （BEGIN_EMBED_DHTML_EVENT_MAP 中指定） 对 URL 或 HTML 资源。

### <a name="example"></a>示例

请参阅中的示例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="begin_url_entries"></a>  BEGIN_URL_ENTRIES

在多页对话框中启动 URL 事件输入映射的定义。

```
BEGIN_URL_ENTRIES(className)
```

### <a name="parameters"></a>参数

*className*<br/>
包含 URL 事件映射的类的名称。 此类应直接或间接派生[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 URL 事件输入映射必须位于[DHTML 和 URL 事件映射](#begin_dhtml_url_event_map))。

### <a name="remarks"></a>备注

由于多页 DHTML 对话框包含多个 HTML 页，因此将使用 URL 事件输入映射 Url 或 HTML 的资源添加到对应[嵌入 DHTML 事件映射](#begin_embed_dhtml_event_map)。 放置之间 BEGIN_URL_ENTRIES URL_EVENT_ENTRY 宏和[END_URL_ENTRIES](#end_url_entries)宏。

### <a name="example"></a>示例

请参阅中的示例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="declare_dhtml_url_event_map"></a>  DECLARE_DHTML_URL_EVENT_MAP

声明类定义中的 DHTML 和 URL 事件映射。

```
DECLARE_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>备注

此宏的定义中使用，则[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-派生的类。

DHTML 和 URL 事件映射包含[嵌入 DHTML 事件映射](#begin_embed_dhtml_event_map)并[URL 事件输入](#begin_url_entries)DHTML 事件映射到基于每个页面上的处理程序。 使用[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)实现映射。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="end_dhtml_url_event_map"></a>  END_DHTML_URL_EVENT_MAP

标记 DHTML 和 URL 事件映射的末尾。

```
END_DHTML_URL_EVENT_MAP(className)
```

### <a name="parameters"></a>参数

*className*<br/>
包含事件映射的类的名称。 此类应直接或间接派生[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 这应与匹配*className*中的相应[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)宏。

### <a name="example"></a>示例

请参阅中的示例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="end_embed_dhtml_event_map"></a>  END_EMBED_DHTML_EVENT_MAP

标记嵌入 DHTML 事件映射的末尾。

```
END_EMBED_DHTML_EVENT_MAP()
```

### <a name="example"></a>示例

请参阅中的示例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="end_url_entries"></a>  END_URL_ENTRIES

标记 URL 事件输入映射的末尾。

```
END_URL_ENTRIES()
```

### <a name="example"></a>示例

请参阅中的示例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="url_event_entry"></a>  URL_EVENT_ENTRY

将 URL 或 HTML 资源映射到多页对话框中的页。

```
URL_EVENT_ENTRY(className, url,  mapName)
```

### <a name="parameters"></a>参数

*className*<br/>
包含 URL 事件映射的类的名称。 此类应直接或间接派生[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 URL 事件输入映射必须位于[DHTML 和 URL 事件映射](#begin_dhtml_url_event_map))。

*url*<br/>
页面 URL 或 HTML 资源。

*mapName*<br/>
指定其 URL 的页面*url*。 这与匹配*mapName*中[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)宏映射此页中的事件。

### <a name="remarks"></a>备注

如果该页的 HTML 资源， *url*必须是资源的 ID 号 (即，"123"，不 123 或 ID_HTMLRES1) 的字符串表示形式。

页标识符*mapName*，是用于链接的任意符号嵌入 DHTML 事件映射到 URL 事件输入映射。 它在 DHTML 和 URL 事件映射到的作用域中的限制。

### <a name="example"></a>示例

请参阅中的示例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。

### <a name="requirements"></a>要求

  **标头**afxdhtml.h

##  <a name="end_dhtml_event_map_inline"></a>END_DHTML_EVENT_MAP_INLINE

标记 DHTML 事件映射的末尾。

### <a name="syntax"></a>语法

```
END_DHTML_EVENT_MAP_INLINE( )
```

### <a name="remarks"></a>备注

必须与结合使用[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)。

### <a name="requirements"></a>要求

**标头：** afxdhtml.h

## <a name="see-also"></a>请参阅

[宏和全局函数](mfc-macros-and-globals.md)
