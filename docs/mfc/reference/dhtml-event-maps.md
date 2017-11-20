---
title: "DHTML 事件映射 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.macros.shared
dev_langs: C++
helpviewer_keywords:
- event map macros [MFC]
- DHTML [MFC], event map macros
- macros [MFC], DHTML event map
- DHTML events [MFC], event map
- DHTML events [MFC]
ms.assetid: 9a2c8ae7-7216-4a5e-bc60-6b98695be0c6
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5588f716cfc7aec0caba7fd6943770353e7b2b1e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="dhtml-event-maps"></a>DHTML 事件映射
下面的宏可以用于处理 DHTML 事件。  
  
## <a name="dhtml-event-map-macros"></a>DHTML 事件映射宏  
 可以使用以下宏，以处理在 DHTML 事件[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-派生类。  
  
|||  
|-|-|  
|[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)|标记 DHTML 事件映射的开头。|  
|[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)|标记 DHTML 事件映射的开头。|  
|[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)|声明 DHTML 事件映射。|  
|[DHTML_EVENT](#dhtml_event)|用于处理事件的文档级别的单个 HTML 元素。|  
|[DHTML_EVENT_AXCONTROL](#dhtml_event_axcontrol)|用于处理由 ActiveX 控件激发的事件。|  
|[DHTML_EVENT_CLASS](#dhtml_event_class)|用于处理在与特定的 CSS 类的所有 HTML 元素的文档级别的事件。|  
|[DHTML_EVENT_ELEMENT](#dhtml_event_element)|用于处理在元素级别的事件。|  
|[DHTML_EVENT_ONAFTERUPDATE](#dhtml_event_onafterupdate)|用于处理**onafterupdate**从 HTML 元素的事件。|  
|[DHTML_EVENT_ONBEFOREUPDATE](#dhtml_event_onbeforeupdate)|用于处理**onbeforeupdate**从 HTML 元素的事件。|  
|[DHTML_EVENT_ONBLUR](#dhtml_event_onblur)|用于处理**onblur**从 HTML 元素的事件。|  
|[DHTML_EVENT_ONCHANGE](#dhtml_event_onchange)|用于处理`onchange`从 HTML 元素的事件。|  
|[DHTML_EVENT_ONCLICK](#dhtml_event_onclick)|用于处理**onclick**从 HTML 元素的事件。|  
|[DHTML_EVENT_ONDATAAVAILABLE](#dhtml_event_ondataavailable)|用于处理**ondataavailable**从 HTML 元素的事件。|  
|[DHTML_EVENT_ONDATASETCHANGED](#dhtml_event_ondatasetchanged)|用于处理**ondatasetchanged**从 HTML 元素的事件。|  
|[DHTML_EVENT_ONDATASETCOMPLETE](#dhtml_event_ondatasetcomplete)|用于处理**ondatasetcomplete**从 HTML 元素的事件。|  
|[DHTML_EVENT_ONDBLCLICK](#dhtml_event_ondblclick)|用于处理**ondblclick**从 HTML 元素的事件。|  
|[DHTML_EVENT_ONDRAGSTART](#dhtml_event_ondragstart)|用于处理**ondragstart**从 HTML 元素的事件。|  
|[DHTML_EVENT_ONERRORUPDATE](#dhtml_event_onerrorupdate)|用于处理**onerrorupdate**从 HTML 元素的事件。|  
|[DHTML_EVENT_ONFILTERCHANGE](#dhtml_event_onfilterchange)|用于处理**onfilterchange**从 HTML 元素的事件。|  
|[DHTML_EVENT_ONFOCUS](#dhtml_event_onfocus)|用于处理**onfocus**从 HTML 元素的事件。|  
|[DHTML_EVENT_ONHELP](#dhtml_event_onhelp)|用于处理`onhelp`从 HTML 元素的事件。|  
|[DHTML_EVENT_ONKEYDOWN](#dhtml_event_onkeydown)|用于处理**onkeydown**从 HTML 元素的事件。|  
|[DHTML_EVENT_ONKEYPRESS](#dhtml_event_onkeypress)|用于处理**onkeypress**从 HTML 元素的事件。|  
|[DHTML_EVENT_ONKEYUP](#dhtml_event_onkeyup)|用于处理**onkeyup**从 HTML 元素的事件。|  
|[DHTML_EVENT_ONMOUSEDOWN](#dhtml_event_onmousedown)|用于处理**onmousedown**从 HTML 元素的事件。|  
|[DHTML_EVENT_ONMOUSEMOVE](#dhtml_event_onmousemove)|用于处理`onmousemove`从 HTML 元素的事件。|  
|[DHTML_EVENT_ONMOUSEOUT](#dhtml_event_onmouseout)|用于处理**onmouseout**从 HTML 元素的事件。|  
|[DHTML_EVENT_ONMOUSEOVER](#dhtml_event_onmouseover)|用于处理**onmouseover**从 HTML 元素的事件。|  
|[DHTML_EVENT_ONMOUSEUP](#dhtml_event_onmouseup)|用于处理**onmouseup**从 HTML 元素的事件。|  
|[DHTML_EVENT_ONRESIZE](#dhtml_event_onresize)|用于处理**onresize**从 HTML 元素的事件。|  
|[DHTML_EVENT_ONROWENTER](#dhtml_event_onrowenter)|用于处理**onrowenter**从 HTML 元素的事件。|  
|[DHTML_EVENT_ONROWEXIT](#dhtml_event_onrowexit)|用于处理**onrowexit**从 HTML 元素的事件。|  
|[DHTML_EVENT_ONSELECTSTART](#dhtml_event_onselectstart)|用于处理**onselectstart**从 HTML 元素的事件。|  
|[DHTML_EVENT_TAG](#dhtml_event_tag)|用于处理在具有特定的 HTML 标记的所有元素的文档级别的事件。|  
|[END_DHTML_EVENT_MAP](#end_dhtml_event_map)|将标记 DHTML 事件映射的末尾。|  
|[END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)|将标记 DHTML 事件映射的末尾。 |
  
## <a name="url-event-map-macros"></a>URL 事件映射宏  
 可以使用以下宏，以处理在 DHTML 事件[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-派生类。  
  
|||  
|-|-|  
|[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)|标记多页 DHTML 和 URL 事件映射的开始。|  
|[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)|标记嵌入 DHTML 事件映射的开头。|  
|[BEGIN_URL_ENTRIES](#begin_url_entries)|标记 URL 事件输入映射的开始。|  
|[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)|声明多页 DHTML 和 URL 事件映射。|  
|[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)|将标记多页 DHTML 和 URL 事件映射的末尾。|  
|[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)|标记嵌入 DHTML 事件映射的末尾。|  
|[END_URL_ENTRIES](#end_url_entries)|将标记 URL 事件输入映射的末尾。|  
|[URL_EVENT_ENTRY](#url_event_entry)|将 URL 或 HTML 资源映射到多页对话框中的页。|  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="begin_dhtml_event_map"></a>BEGIN_DHTML_EVENT_MAP  
 标记的 DHTML 事件映射置于由标识的类别的源文件时开始`className`。  
  
```   
BEGIN_DHTML_EVENT_MAP(className)   
```  
  
### <a name="parameters"></a>参数  
 `className`  
 包含 DHTML 事件映射的类名称。 此类应直接或间接派生从[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)和包括[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)在其类定义中的宏。  
  
### <a name="remarks"></a>备注  
 将 DHTML 事件映射添加到你的类将信息提供给**CDHtmlDialog**可用于触发的 HTML 元素或网页到类中的处理程序函数中的 ActiveX 控件的路由事件。  
  
 位置`BEGIN_DHTML_EVENT_MAP`类的实现 (.cpp) 文件中的宏跟`DHTML_EVENT`事件宏类是处理 (例如，`DHTML_EVENT_ONMOUSEOVER`鼠标悬停事件)。 使用[END_DHTML_EVENT_MAP](#end_dhtml_event_map)宏来标记事件映射的末尾。 这些宏实现以下函数：  
  
 `virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="begin_dhtml_event_map_inline"></a>BEGIN_DHTML_EVENT_MAP_INLINE  
 标记的 DHTML 事件映射中的类定义开始`className`。  
  
```   
BEGIN_DHTML_EVENT_MAP_INLINE(className)   
```  
  
### <a name="parameters"></a>参数  
 `className`  
 包含 DHTML 事件映射的类名称。 此类应直接或间接派生从[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)和包括[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)在其类定义中的宏。  
  
### <a name="remarks"></a>备注  
 将 DHTML 事件映射添加到你的类将信息提供给**CDHtmlDialog**可用于触发的 HTML 元素或网页到类中的处理程序函数中的 ActiveX 控件的路由事件。  
  
 位置`BEGIN_DHTML_EVENT_MAP`类的定义 (.h) 文件中的宏跟`DHTML_EVENT`事件宏类是处理 (例如，`DHTML_EVENT_ONMOUSEOVER`鼠标悬停事件)。 使用[END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)宏来标记事件映射的末尾。 这些宏实现以下函数：  
  
 `virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  

  
##  <a name="declare_dhtml_event_map"></a>DECLARE_DHTML_EVENT_MAP  
 声明类定义中的 DHTML 事件映射。  
  
```   
DECLARE_DHTML_EVENT_MAP()   
```  
  
### <a name="remarks"></a>备注  
 此宏的定义中使用，则[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-派生类。  
  
 使用[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)或[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)实现映射。  
  
 [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)声明以下函数：  
  
 `virtual const DHtmlEventMapEntry* GetDHtmlEventMap( );`  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event"></a>DHTML_EVENT  
 （在文档级别中） 处理由标识的事件`dispid`源于标识的 HTML 元素`elemName`。  
  
```   
DHTML_EVENT(dispid, elemName,  memberFxn)   
```  
  
### <a name="parameters"></a>参数  
 `dispid`  
 要处理的事件的 DISPID。  
  
 `elemName`  
 `LPCWSTR`持有外包事件，HTML 元素的 ID 或**NULL**来处理文档事件。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_axcontrol"></a>DHTML_EVENT_AXCONTROL  
 处理由事件`dispid`由 ActiveX 控件触发的`controlName`。  
  
```   
DHTML_EVENT_AXCONTROL(dispid, controlName,  memberFxn)  
```  
  
### <a name="parameters"></a>参数  
 `dispid`  
 要处理的事件调度 ID。  
  
 `controlName`  
 `LPCWSTR`保存激发事件的控件的 HTML ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_class"></a>DHTML_EVENT_CLASS  
 （在文档级别中） 处理由标识的事件`dispid`源自任何 HTML 元素的 CSS 类由标识`elemName`。  
  
```   
DHTML_EVENT_CLASS(dispid, elemName,  memberFxn)   
```  
  
### <a name="parameters"></a>参数  
 `dispid`  
 要处理的事件调度 ID。  
  
 `elemName`  
 `LPCWSTR`持有外包事件的 HTML 元素的 CSS 类。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_element"></a>DHTML_EVENT_ELEMENT  
 处理 (标识的元素在`elemName`) 由标识事件`dispid`。  
  
```   
DHTML_EVENT_ELEMENT(dispid, elemName,  memberFxn) 
```  
  
### <a name="parameters"></a>参数  
 `dispid`  
 要处理的事件调度 ID。  
  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
 如果使用此宏来处理 nonbubbling 事件，事件源将标识的元素`elemName`。  
  
 如果此宏用于处理冒泡事件，该元素由`elemName`可能不是事件源 (源可能包含的任何元素`elemName`)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_onafterupdate"></a>DHTML_EVENT_ONAFTERUPDATE  
 （在文档级别中） 处理**onafterupdate**生成事件的标识的 HTML 元素通过`elemName`。  
  
```   
DHTML_EVENT_ONAFTERUPDATE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_onbeforeupdate"></a>DHTML_EVENT_ONBEFOREUPDATE  
 （在文档级别中） 处理**onbeforeupdate**生成事件的标识的 HTML 元素通过`elemName`。  
  
```   
DHTML_EVENT_ONBEFOREUPDATE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_onblur"></a>DHTML_EVENT_ONBLUR  
 （在元素级别） 处理**onblur**事件。 这是 nonbubbling 事件。  
  
```   
DHTML_EVENT_ONBLUR(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_onchange"></a>DHTML_EVENT_ONCHANGE  
 （在元素级别） 处理`onchange`事件。 这是 nonbubbling 事件。  
  
```   
DHTML_EVENT_ONCHANGE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_onclick"></a>DHTML_EVENT_ONCLICK  
 （在文档级别中） 处理**onclick**生成事件的标识的 HTML 元素通过`elemName`。  
  
```   
DHTML_EVENT_ONCLICK(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_ondataavailable"></a>DHTML_EVENT_ONDATAAVAILABLE  
 （在文档级别中） 处理**ondataavailable**生成事件的标识的 HTML 元素通过`elemName`。  
  
```   
DHTML_EVENT_ONDATAAVAILABLE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_ondatasetchanged"></a>DHTML_EVENT_ONDATASETCHANGED  
 （在文档级别中） 处理**ondatasetchanged**生成事件的标识的 HTML 元素通过`elemName`。  
  
```   
DHTML_EVENT_ONDATASETCHANGED(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_ondatasetcomplete"></a>DHTML_EVENT_ONDATASETCOMPLETE  
 （在文档级别中） 处理**ondatasetcomplete**生成事件的标识的 HTML 元素通过`elemName`。  
  
```   
DHTML_EVENT_ONDATASETCOMPLETE(elemName, memberFxn) 
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_ondblclick"></a>DHTML_EVENT_ONDBLCLICK  
 （在文档级别中） 处理**ondblclick**生成事件的标识的 HTML 元素通过`elemName`。  
  
```   
DHTML_EVENT_ONDBLCLICK(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_ondragstart"></a>DHTML_EVENT_ONDRAGSTART  
 （在文档级别中） 处理**ondragstart**生成事件的标识的 HTML 元素通过`elemName`。  
  
```   
DHTML_EVENT_ONDRAGSTART(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_onerrorupdate"></a>DHTML_EVENT_ONERRORUPDATE  
 （在文档级别中） 处理**onerrorupdate**生成事件的标识的 HTML 元素通过`elemName`。  
  
```   
DHTML_EVENT_ONERRORUPDATE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_onfilterchange"></a>DHTML_EVENT_ONFILTERCHANGE  
 （在文档级别中） 处理**onfilterchange**生成事件的标识的 HTML 元素通过`elemName`。  
  
```  
 
DHTML_EVENT_ONFILTERCHANGE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_onfocus"></a>DHTML_EVENT_ONFOCUS  
 （在元素级别） 处理**onfocus**事件。 这是 nonbubbling 事件。  
  
```  
 
DHTML_EVENT_ONFOCUS(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_onhelp"></a>DHTML_EVENT_ONHELP  
 （在文档级别中） 处理`onhelp`生成事件的标识的 HTML 元素通过`elemName`。  
  
```  
 
DHTML_EVENT_ONHELP(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_onkeydown"></a>DHTML_EVENT_ONKEYDOWN  
 （在文档级别中） 处理**onkeydown**生成事件的标识的 HTML 元素通过`elemName`。  
  
```  
 
DHTML_EVENT_ONKEYDOWN(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_onkeypress"></a>DHTML_EVENT_ONKEYPRESS  
 （在文档级别中） 处理**onkeypress**生成事件的标识的 HTML 元素通过`elemName`。  
  
```  
 
DHTML_EVENT_ONKEYPRESS(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_onkeyup"></a>DHTML_EVENT_ONKEYUP  
 （在文档级别中） 处理**onkeyup**生成事件的标识的 HTML 元素通过`elemName`。  
  
```  
 
DHTML_EVENT_ONKEYUP(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_onmousedown"></a>DHTML_EVENT_ONMOUSEDOWN  
 （在文档级别中） 处理**onmousedown**生成事件的标识的 HTML 元素通过`elemName`。  
  
```  
 
DHTML_EVENT_ONMOUSEDOWN(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_onmousemove"></a>DHTML_EVENT_ONMOUSEMOVE  
 （在文档级别中） 处理`onmousemove`生成事件的标识的 HTML 元素通过`elemName`。  
  
```  
 
DHTML_EVENT_ONMOUSEMOVE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_onmouseout"></a>DHTML_EVENT_ONMOUSEOUT  
 （在文档级别中） 处理**onmouseout**生成事件的标识的 HTML 元素通过`elemName`。  
  
```  
 
DHTML_EVENT_ONMOUSEOUT(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_onmouseover"></a>DHTML_EVENT_ONMOUSEOVER  
 （在文档级别中） 处理**onmouseover**生成事件的标识的 HTML 元素通过`elemName`。  
  
```  
 
DHTML_EVENT_ONMOUSEOVER(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_onmouseup"></a>DHTML_EVENT_ONMOUSEUP  
 （在文档级别中） 处理**onmouseup**生成事件的标识的 HTML 元素通过`elemName`。  
  
```  
 
DHTML_EVENT_ONMOUSEUP(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_onresize"></a>DHTML_EVENT_ONRESIZE  
 （在元素级别） 处理**onresize**事件。 这是 nonbubbling 事件。  
  
```  
 
DHTML_EVENT_ONRESIZE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_onrowenter"></a>DHTML_EVENT_ONROWENTER  
 （在文档级别中） 处理**onrowenter**生成事件的标识的 HTML 元素通过`elemName`。  
  
```  
 
DHTML_EVENT_ONROWENTER(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_onrowexit"></a>DHTML_EVENT_ONROWEXIT  
 （在文档级别中） 处理**onrowexit**生成事件的标识的 HTML 元素通过`elemName`。  
  
```  
 
DHTML_EVENT_ONROWEXIT(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_onselectstart"></a>DHTML_EVENT_ONSELECTSTART  
 （在文档级别中） 处理**onselectstart**生成事件的标识的 HTML 元素通过`elemName`。  
  
```  
 
DHTML_EVENT_ONSELECTSTART(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存外包事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="dhtml_event_tag"></a>DHTML_EVENT_TAG  
 （在文档级别中） 处理由标识的事件`dispid`源自任何 HTML 元素由标识的 HTML 标记`elemName`。  
  
```   
DHTML_EVENT_TAG(dispid, elemName,  memberFxn)   
```  
  
### <a name="parameters"></a>参数  
 `dispid`  
 要处理的事件调度 ID。  
  
 `elemName`  
 源事件的 HTML 元素的 HTML 标记。  
  
 `memberFxn`  
 事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏添加到一个条目[DHTML 事件映射](#begin_dhtml_event_map_inline)类中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="end_dhtml_event_map"></a>END_DHTML_EVENT_MAP  
 将标记 DHTML 事件映射的末尾。  
  
```   
END_DHTML_EVENT_MAP()   
```  
  
### <a name="remarks"></a>备注  
 必须与结合使用[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="begin_dhtml_url_event_map"></a>BEGIN_DHTML_URL_EVENT_MAP  
 在多页对话框中启动 DHTML 和 URL 事件映射的定义。  
  
```  
BEGIN_DHTML_URL_EVENT_MAP()  
 
```  
  
### <a name="remarks"></a>备注  
 Put`BEGIN_DHTML_URL_EVENT_MAP`的实现文件中您[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-派生类。 与在其后[嵌入 DHTML 事件映射](#begin_embed_dhtml_event_map)和[URL 条目](#begin_url_entries)，然后关闭其与[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)。 包括[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)在类定义的宏。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#196](../../mfc/codesnippet/cpp/dhtml-event-maps_1.cpp)]  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="begin_embed_dhtml_event_map"></a>BEGIN_EMBED_DHTML_EVENT_MAP  
 在多页对话框中启动嵌入 DHTML 事件映射的定义。  
  
```  
BEGIN_EMBED_DHTML_EVENT_MAP(className, mapName)  
 
```  
  
### <a name="parameters"></a>参数  
 `className`  
 包含事件映射的类名称。 此类应直接或间接派生从[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 嵌入的 DHTML 事件映射必须位于[DHTML 和 URL 事件映射](#begin_dhtml_url_event_map))。  
  
 *映射名称*  
 指定其事件映射此页。 这符合*映射名称*中[URL_EVENT_ENTRY](#url_event_entry)宏实际定义 URL 或 HTML 资源。  
  
### <a name="remarks"></a>备注  
 因为多页 DHTML 对话框包含多个 HTML 页，其中每个可以引发 DHTML 事件，嵌入的事件映射用于将事件映射到每页基础上的处理程序。  
  
 在 DHTML 和 URL 事件映射内的嵌入的事件映射组成`BEGIN_EMBED_DHTML_EVENT_MAP`宏跟[DHTML_EVENT](#dhtml_event)宏和[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)宏。  
  
 每个嵌入的事件映射需要相应[URL 事件项](#url_event_entry)映射*映射名称*(中指定`BEGIN_EMBED_DHTML_EVENT_MAP`) 到 URL 或 HTML 资源。  
  
### <a name="example"></a>示例  
 请参阅中的示例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="begin_url_entries"></a>BEGIN_URL_ENTRIES  
 在多页对话框中启动 URL 事件输入映射的定义。  
  
```  
BEGIN_URL_ENTRIES(className)  
 
```  
  
### <a name="parameters"></a>参数  
 `className`  
 包含 URL 事件映射的类的名称。 此类应直接或间接派生从[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 URL 事件输入映射必须位于内部[DHTML 和 URL 事件映射](#begin_dhtml_url_event_map))。  
  
### <a name="remarks"></a>备注  
 由于多页 DHTML 对话框包含多个 HTML 页，URL 事件输入用于将 Url 或 HTML 映射到对应的资源[嵌入 DHTML 事件映射](#begin_embed_dhtml_event_map)。 Put`URL_EVENT_ENTRY`宏之间`BEGIN_URL_ENTRIES`和[END_URL_ENTRIES](#end_url_entries)宏。  
  
### <a name="example"></a>示例  
 请参阅中的示例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="declare_dhtml_url_event_map"></a>DECLARE_DHTML_URL_EVENT_MAP  
 声明类定义中的 DHTML 和 URL 事件映射。  
  
```  
DECLARE_DHTML_URL_EVENT_MAP()  
 
```  
  
### <a name="remarks"></a>备注  
 此宏的定义中使用，则[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-派生类。  
  
 DHTML 和 URL 事件映射包含[嵌入 DHTML 事件映射](#begin_embed_dhtml_event_map)和[URL 事件输入](#begin_url_entries)DHTML 事件映射到每页基础上的处理程序。 使用[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)实现映射。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="end_dhtml_url_event_map"></a>END_DHTML_URL_EVENT_MAP  
 标记 DHTML 和 URL 事件映射的末尾。  
  
```  
END_DHTML_URL_EVENT_MAP(className)  
 
```  
  
### <a name="parameters"></a>参数  
 `className`  
 包含事件映射的类名称。 此类应直接或间接派生从[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 这应匹配`className`在相应[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)宏。  
  
### <a name="example"></a>示例  
 请参阅中的示例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="end_embed_dhtml_event_map"></a>END_EMBED_DHTML_EVENT_MAP  
 标记嵌入 DHTML 事件映射的末尾。  
  
```  
END_EMBED_DHTML_EVENT_MAP()  
 
```  
  
### <a name="example"></a>示例  
 请参阅中的示例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="end_url_entries"></a>END_URL_ENTRIES  
 将标记 URL 事件输入映射的末尾。  
  
```  
END_URL_ENTRIES()  
 
```  
  
### <a name="example"></a>示例  
 请参阅中的示例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="url_event_entry"></a>URL_EVENT_ENTRY  
 将 URL 或 HTML 资源映射到多页对话框中的页。  
  
```  
URL_EVENT_ENTRY(className, url,  mapName)   
```  
  
### <a name="parameters"></a>参数  
 `className`  
 包含 URL 事件映射的类的名称。 此类应直接或间接派生从[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 URL 事件输入映射必须位于内部[DHTML 和 URL 事件映射](#begin_dhtml_url_event_map))。  
  
 *url*  
 页面 URL 或 HTML 资源。  
  
 *映射名称*  
 指定的页的 URL 是*url*。 这符合*映射名称*中[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)映射此页中的事件的宏。  
  
### <a name="remarks"></a>备注  
 如果该页的 HTML 资源， *url*必须是资源的 ID 号 (即，"123"，不 123 或 ID_HTMLRES1) 的字符串表示。  
  
 页标识符，*映射名称*，即是用于将链接的任意符号嵌入 DHTML 事件映射到 URL 事件输入映射。 它在 DHTML 和 URL 事件映射到的作用域中的限制。  
  
### <a name="example"></a>示例  
 请参阅中的示例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。  

  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  

##  <a name="end_dhtml_event_map_inline"></a>END_DHTML_EVENT_MAP_INLINE
将标记 DHTML 事件映射的末尾。  
   
### <a name="syntax"></a>语法    
```
END_DHTML_EVENT_MAP_INLINE( )    
```  
   
### <a name="remarks"></a>备注  
 必须与结合使用[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)。  
   
### <a name="requirements"></a>要求  
 **标头：** afxdhtml.h  
   
### <a name="see-also"></a>另请参阅  
 [宏和全局函数](mfc-macros-and-globals.md)   
