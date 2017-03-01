---
title: "DHTML 事件映射 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.macros.shared
dev_langs:
- C++
helpviewer_keywords:
- event map macros
- DHTML, event map macros
- macros, DHTML event map
- DHTML events, event map
- DHTML events
ms.assetid: 9a2c8ae7-7216-4a5e-bc60-6b98695be0c6
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
ms.openlocfilehash: 8be59b52e06241651a2f605ab949efffd0e010d3
ms.lasthandoff: 02/24/2017

---
# <a name="dhtml-event-maps"></a>DHTML 事件映射
可以使用以下宏来处理 DHTML 事件。  
  
## <a name="dhtml-event-map-macros"></a>DHTML 事件映射宏  
 可以使用以下宏来处理中的 DHTML 事件[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)的派生类。  
  
|||  
|-|-|  
|[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)|标记 DHTML 事件映射的开始位置。|  
|[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)|标记 DHTML 事件映射的开始位置。|  
|[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)|声明 DHTML 事件映射。|  
|[DHTML_EVENT](#dhtml_event)|用于处理在单个的 HTML 元素的文档级别的事件。|  
|[DHTML_EVENT_AXCONTROL](#dhtml_event_axcontrol)|用于处理由 ActiveX 控件激发的事件。|  
|[DHTML_EVENT_CLASS](#dhtml_event_class)|用于处理在与特定的 CSS 类的所有 HTML 元素的文档级别的事件。|  
|[DHTML_EVENT_ELEMENT](#dhtml_event_element)|用于处理在元素级别的事件。|  
|[DHTML_EVENT_ONAFTERUPDATE](#dhtml_event_onafterupdate)|用于处理**onafterupdate** HTML 元素中的事件。|  
|[DHTML_EVENT_ONBEFOREUPDATE](#dhtml_event_onbeforeupdate)|用于处理**onbeforeupdate** HTML 元素中的事件。|  
|[DHTML_EVENT_ONBLUR](#dhtml_event_onblur)|用于处理**onblur** HTML 元素中的事件。|  
|[DHTML_EVENT_ONCHANGE](#dhtml_event_onchange)|用于处理`onchange`HTML 元素中的事件。|  
|[DHTML_EVENT_ONCLICK](#dhtml_event_onclick)|用于处理**onclick** HTML 元素中的事件。|  
|[DHTML_EVENT_ONDATAAVAILABLE](#dhtml_event_ondataavailable)|用于处理**ondataavailable** HTML 元素中的事件。|  
|[DHTML_EVENT_ONDATASETCHANGED](#dhtml_event_ondatasetchanged)|用于处理**ondatasetchanged** HTML 元素中的事件。|  
|[DHTML_EVENT_ONDATASETCOMPLETE](#dhtml_event_ondatasetcomplete)|用于处理**ondatasetcomplete** HTML 元素中的事件。|  
|[DHTML_EVENT_ONDBLCLICK](#dhtml_event_ondblclick)|用于处理**ondblclick** HTML 元素中的事件。|  
|[DHTML_EVENT_ONDRAGSTART](#dhtml_event_ondragstart)|用于处理**ondragstart** HTML 元素中的事件。|  
|[DHTML_EVENT_ONERRORUPDATE](#dhtml_event_onerrorupdate)|用于处理**onerrorupdate** HTML 元素中的事件。|  
|[DHTML_EVENT_ONFILTERCHANGE](#dhtml_event_onfilterchange)|用于处理**onfilterchange** HTML 元素中的事件。|  
|[DHTML_EVENT_ONFOCUS](#dhtml_event_onfocus)|用于处理**onfocus** HTML 元素中的事件。|  
|[DHTML_EVENT_ONHELP](#dhtml_event_onhelp)|用于处理`onhelp`HTML 元素中的事件。|  
|[DHTML_EVENT_ONKEYDOWN](#dhtml_event_onkeydown)|用于处理**onkeydown** HTML 元素中的事件。|  
|[DHTML_EVENT_ONKEYPRESS](#dhtml_event_onkeypress)|用于处理**onkeypress** HTML 元素中的事件。|  
|[DHTML_EVENT_ONKEYUP](#dhtml_event_onkeyup)|用于处理**onkeyup** HTML 元素中的事件。|  
|[DHTML_EVENT_ONMOUSEDOWN](#dhtml_event_onmousedown)|用于处理**onmousedown** HTML 元素中的事件。|  
|[DHTML_EVENT_ONMOUSEMOVE](#dhtml_event_onmousemove)|用于处理`onmousemove`HTML 元素中的事件。|  
|[DHTML_EVENT_ONMOUSEOUT](#dhtml_event_onmouseout)|用于处理**onmouseout** HTML 元素中的事件。|  
|[DHTML_EVENT_ONMOUSEOVER](#dhtml_event_onmouseover)|用于处理**onmouseover** HTML 元素中的事件。|  
|[DHTML_EVENT_ONMOUSEUP](#dhtml_event_onmouseup)|用于处理**onmouseup** HTML 元素中的事件。|  
|[DHTML_EVENT_ONRESIZE](#dhtml_event_onresize)|用于处理**onresize** HTML 元素中的事件。|  
|[DHTML_EVENT_ONROWENTER](#dhtml_event_onrowenter)|用于处理**onrowenter** HTML 元素中的事件。|  
|[DHTML_EVENT_ONROWEXIT](#dhtml_event_onrowexit)|用于处理**onrowexit** HTML 元素中的事件。|  
|[DHTML_EVENT_ONSELECTSTART](#dhtml_event_onselectstart)|用于处理**onselectstart** HTML 元素中的事件。|  
|[DHTML_EVENT_TAG](#dhtml_event_tag)|用于处理在文档级别的所有元素具有特定的 HTML 标记的事件。|  
|[END_DHTML_EVENT_MAP](#end_dhtml_event_map)|标记 DHTML 事件映射的结尾。|  
  
## <a name="url-event-map-macros"></a>URL 事件映射宏  
 可以使用以下宏来处理中的 DHTML 事件[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)的派生类。  
  
|||  
|-|-|  
|[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)|标记多页 DHTML 和 URL 事件映射的开始位置。|  
|[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)|标记嵌入 DHTML 事件映射的开始位置。|  
|[BEGIN_URL_ENTRIES](#begin_url_entries)|标记的开始 URL 事件输入映射。|  
|[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)|声明多页 DHTML 和 URL 事件映射。|  
|[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)|标记多页 DHTML 和 URL 事件映射的结尾。|  
|[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)|标记嵌入 DHTML 事件映射的结尾。|  
|[END_URL_ENTRIES](#end_url_entries)|标记 URL 事件输入映射的结尾。|  
|[URL_EVENT_ENTRY](#url_event_entry)|将 URL 或 HTML 资源映射到多页对话框中的页。|  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namebegindhtmleventmapa--begindhtmleventmap"></a><a name="begin_dhtml_event_map"></a>BEGIN_DHTML_EVENT_MAP  
 标记的 DHTML 事件映射放入由标识类的源代码文件时开始`className`。  
  
```   
BEGIN_DHTML_EVENT_MAP(className)   
```  
  
### <a name="parameters"></a>参数  
 `className`  
 包含 DHTML 事件映射的类的名称。 此类应直接或间接派生从[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)并且包括[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)在其类定义中的宏。  
  
### <a name="remarks"></a>备注  
 将 DHTML 事件映射添加到您的类将信息提供给**CDHtmlDialog** ，可用来由 HTML 元素或网页与您的类中的处理程序函数中的 ActiveX 控件触发的路由事件。  
  
 位置`BEGIN_DHTML_EVENT_MAP`类的实现 (.cpp) 文件中的宏跟`DHTML_EVENT`宏的事件的类是以处理 (例如，`DHTML_EVENT_ONMOUSEOVER`的鼠标悬停事件)。 使用[END_DHTML_EVENT_MAP](#end_dhtml_event_map)宏来标记事件映射的末尾。 这些宏实现以下函数︰  
  
 `virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namebegindhtmleventmapinlinea--begindhtmleventmapinline"></a><a name="begin_dhtml_event_map_inline"></a>BEGIN_DHTML_EVENT_MAP_INLINE  
 标记的 DHTML 事件映射中的类定义开头`className`。  
  
```   
BEGIN_DHTML_EVENT_MAP_INLINE(className)   
```  
  
### <a name="parameters"></a>参数  
 `className`  
 包含 DHTML 事件映射的类的名称。 此类应直接或间接派生从[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)并且包括[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)在其类定义中的宏。  
  
### <a name="remarks"></a>备注  
 将 DHTML 事件映射添加到您的类将信息提供给**CDHtmlDialog** ，可用来由 HTML 元素或网页与您的类中的处理程序函数中的 ActiveX 控件触发的路由事件。  
  
 位置`BEGIN_DHTML_EVENT_MAP`类的定义 (.h) 文件中的宏跟`DHTML_EVENT`宏的事件的类是以处理 (例如，`DHTML_EVENT_ONMOUSEOVER`的鼠标悬停事件)。 使用[END_DHTML_EVENT_MAP_INLINE](http://msdn.microsoft.com/library/0cfec092-20ee-49f3-bc38-56d6a5572db2)宏来标记事件映射的末尾。 这些宏实现以下函数︰  
  
 `virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  

  
##  <a name="a-namedeclaredhtmleventmapa--declaredhtmleventmap"></a><a name="declare_dhtml_event_map"></a>DECLARE_DHTML_EVENT_MAP  
 声明 DHTML 事件映射中的类定义。  
  
```   
DECLARE_DHTML_EVENT_MAP()   
```  
  
### <a name="remarks"></a>备注  
 此宏的定义中使用，则[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)的派生类。  
  
 使用[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)或[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)来实现该映射。  
  
 [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)声明了以下函数︰  
  
 `virtual const DHtmlEventMapEntry* GetDHtmlEventMap( );`  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventa--dhtmlevent"></a><a name="dhtml_event"></a>DHTML_EVENT  
 （在文档级别） 处理由标识的事件`dispid`建立者标识的 HTML 元素`elemName`。  
  
```   
DHTML_EVENT(dispid, elemName,  memberFxn)   
```  
  
### <a name="parameters"></a>参数  
 `dispid`  
 要处理的事件的 DISPID。  
  
 `elemName`  
 `LPCWSTR`保存来源该事件的 HTML 元素的 ID 或**NULL**来处理文档的事件。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventaxcontrola--dhtmleventaxcontrol"></a><a name="dhtml_event_axcontrol"></a>DHTML_EVENT_AXCONTROL  
 处理该事件由标识`dispid`由标识的 ActiveX 控件激发`controlName`。  
  
```   
DHTML_EVENT_AXCONTROL(dispid, controlName,  memberFxn)  
```  
  
### <a name="parameters"></a>参数  
 `dispid`  
 要处理的事件调度 ID。  
  
 `controlName`  
 `LPCWSTR`保存触发事件的控件的 HTML ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventclassa--dhtmleventclass"></a><a name="dhtml_event_class"></a>DHTML_EVENT_CLASS  
 （在文档级别） 处理由标识的事件`dispid`源自任何 HTML 元素的 CSS 类由标识`elemName`。  
  
```   
DHTML_EVENT_CLASS(dispid, elemName,  memberFxn)   
```  
  
### <a name="parameters"></a>参数  
 `dispid`  
 要处理的事件调度 ID。  
  
 `elemName`  
 `LPCWSTR`持有来源事件的 HTML 元素的 CSS 类。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventelementa--dhtmleventelement"></a><a name="dhtml_event_element"></a>DHTML_EVENT_ELEMENT  
 处理 (由标识的元素在`elemName`) 通过标识事件`dispid`。  
  
```   
DHTML_EVENT_ELEMENT(dispid, elemName,  memberFxn) 
```  
  
### <a name="parameters"></a>参数  
 `dispid`  
 要处理的事件调度 ID。  
  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
 如果使用此宏来处理 nonbubbling 事件，事件源将标识的元素`elemName`。  
  
 如果使用此宏来处理冒泡事件，该元素标识的`elemName`可能不是事件源 (源可能包含的任何元素`elemName`)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventonafterupdatea--dhtmleventonafterupdate"></a><a name="dhtml_event_onafterupdate"></a>DHTML_EVENT_ONAFTERUPDATE  
 （在文档级别） 处理**onafterupdate**事件是由标识的 HTML 元素始发`elemName`。  
  
```   
DHTML_EVENT_ONAFTERUPDATE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventonbeforeupdatea--dhtmleventonbeforeupdate"></a><a name="dhtml_event_onbeforeupdate"></a>DHTML_EVENT_ONBEFOREUPDATE  
 （在文档级别） 处理**onbeforeupdate**事件是由标识的 HTML 元素始发`elemName`。  
  
```   
DHTML_EVENT_ONBEFOREUPDATE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventonblura--dhtmleventonblur"></a><a name="dhtml_event_onblur"></a>DHTML_EVENT_ONBLUR  
 （在元素级别） 处理**onblur**事件。 这是 nonbubbling 事件。  
  
```   
DHTML_EVENT_ONBLUR(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventonchangea--dhtmleventonchange"></a><a name="dhtml_event_onchange"></a>DHTML_EVENT_ONCHANGE  
 （在元素级别） 处理`onchange`事件。 这是 nonbubbling 事件。  
  
```   
DHTML_EVENT_ONCHANGE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventonclicka--dhtmleventonclick"></a><a name="dhtml_event_onclick"></a>DHTML_EVENT_ONCLICK  
 （在文档级别） 处理**onclick**事件是由标识的 HTML 元素始发`elemName`。  
  
```   
DHTML_EVENT_ONCLICK(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventondataavailablea--dhtmleventondataavailable"></a><a name="dhtml_event_ondataavailable"></a>DHTML_EVENT_ONDATAAVAILABLE  
 （在文档级别） 处理**ondataavailable**事件是由标识的 HTML 元素始发`elemName`。  
  
```   
DHTML_EVENT_ONDATAAVAILABLE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventondatasetchangeda--dhtmleventondatasetchanged"></a><a name="dhtml_event_ondatasetchanged"></a>DHTML_EVENT_ONDATASETCHANGED  
 （在文档级别） 处理**ondatasetchanged**事件是由标识的 HTML 元素始发`elemName`。  
  
```   
DHTML_EVENT_ONDATASETCHANGED(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventondatasetcompletea--dhtmleventondatasetcomplete"></a><a name="dhtml_event_ondatasetcomplete"></a>DHTML_EVENT_ONDATASETCOMPLETE  
 （在文档级别） 处理**ondatasetcomplete**事件是由标识的 HTML 元素始发`elemName`。  
  
```   
DHTML_EVENT_ONDATASETCOMPLETE(elemName, memberFxn) 
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventondblclicka--dhtmleventondblclick"></a><a name="dhtml_event_ondblclick"></a>DHTML_EVENT_ONDBLCLICK  
 （在文档级别） 处理**ondblclick**事件是由标识的 HTML 元素始发`elemName`。  
  
```   
DHTML_EVENT_ONDBLCLICK(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventondragstarta--dhtmleventondragstart"></a><a name="dhtml_event_ondragstart"></a>DHTML_EVENT_ONDRAGSTART  
 （在文档级别） 处理**ondragstart**事件是由标识的 HTML 元素始发`elemName`。  
  
```   
DHTML_EVENT_ONDRAGSTART(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventonerrorupdatea--dhtmleventonerrorupdate"></a><a name="dhtml_event_onerrorupdate"></a>DHTML_EVENT_ONERRORUPDATE  
 （在文档级别） 处理**onerrorupdate**事件是由标识的 HTML 元素始发`elemName`。  
  
```   
DHTML_EVENT_ONERRORUPDATE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventonfilterchangea--dhtmleventonfilterchange"></a><a name="dhtml_event_onfilterchange"></a>DHTML_EVENT_ONFILTERCHANGE  
 （在文档级别） 处理**onfilterchange**事件是由标识的 HTML 元素始发`elemName`。  
  
```  
 
DHTML_EVENT_ONFILTERCHANGE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventonfocusa--dhtmleventonfocus"></a><a name="dhtml_event_onfocus"></a>DHTML_EVENT_ONFOCUS  
 （在元素级别） 处理**onfocus**事件。 这是 nonbubbling 事件。  
  
```  
 
DHTML_EVENT_ONFOCUS(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventonhelpa--dhtmleventonhelp"></a><a name="dhtml_event_onhelp"></a>DHTML_EVENT_ONHELP  
 （在文档级别） 处理`onhelp`事件是由标识的 HTML 元素始发`elemName`。  
  
```  
 
DHTML_EVENT_ONHELP(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventonkeydowna--dhtmleventonkeydown"></a><a name="dhtml_event_onkeydown"></a>DHTML_EVENT_ONKEYDOWN  
 （在文档级别） 处理**onkeydown**事件是由标识的 HTML 元素始发`elemName`。  
  
```  
 
DHTML_EVENT_ONKEYDOWN(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventonkeypressa--dhtmleventonkeypress"></a><a name="dhtml_event_onkeypress"></a>DHTML_EVENT_ONKEYPRESS  
 （在文档级别） 处理**onkeypress**事件是由标识的 HTML 元素始发`elemName`。  
  
```  
 
DHTML_EVENT_ONKEYPRESS(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventonkeyupa--dhtmleventonkeyup"></a><a name="dhtml_event_onkeyup"></a>DHTML_EVENT_ONKEYUP  
 （在文档级别） 处理**onkeyup**事件是由标识的 HTML 元素始发`elemName`。  
  
```  
 
DHTML_EVENT_ONKEYUP(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventonmousedowna--dhtmleventonmousedown"></a><a name="dhtml_event_onmousedown"></a>DHTML_EVENT_ONMOUSEDOWN  
 （在文档级别） 处理**onmousedown**事件是由标识的 HTML 元素始发`elemName`。  
  
```  
 
DHTML_EVENT_ONMOUSEDOWN(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventonmousemovea--dhtmleventonmousemove"></a><a name="dhtml_event_onmousemove"></a>DHTML_EVENT_ONMOUSEMOVE  
 （在文档级别） 处理`onmousemove`事件是由标识的 HTML 元素始发`elemName`。  
  
```  
 
DHTML_EVENT_ONMOUSEMOVE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventonmouseouta--dhtmleventonmouseout"></a><a name="dhtml_event_onmouseout"></a>DHTML_EVENT_ONMOUSEOUT  
 （在文档级别） 处理**onmouseout**事件是由标识的 HTML 元素始发`elemName`。  
  
```  
 
DHTML_EVENT_ONMOUSEOUT(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventonmouseovera--dhtmleventonmouseover"></a><a name="dhtml_event_onmouseover"></a>DHTML_EVENT_ONMOUSEOVER  
 （在文档级别） 处理**onmouseover**事件是由标识的 HTML 元素始发`elemName`。  
  
```  
 
DHTML_EVENT_ONMOUSEOVER(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventonmouseupa--dhtmleventonmouseup"></a><a name="dhtml_event_onmouseup"></a>DHTML_EVENT_ONMOUSEUP  
 （在文档级别） 处理**onmouseup**事件是由标识的 HTML 元素始发`elemName`。  
  
```  
 
DHTML_EVENT_ONMOUSEUP(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventonresizea--dhtmleventonresize"></a><a name="dhtml_event_onresize"></a>DHTML_EVENT_ONRESIZE  
 （在元素级别） 处理**onresize**事件。 这是 nonbubbling 事件。  
  
```  
 
DHTML_EVENT_ONRESIZE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventonrowentera--dhtmleventonrowenter"></a><a name="dhtml_event_onrowenter"></a>DHTML_EVENT_ONROWENTER  
 （在文档级别） 处理**onrowenter**事件是由标识的 HTML 元素始发`elemName`。  
  
```  
 
DHTML_EVENT_ONROWENTER(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventonrowexita--dhtmleventonrowexit"></a><a name="dhtml_event_onrowexit"></a>DHTML_EVENT_ONROWEXIT  
 （在文档级别） 处理**onrowexit**事件是由标识的 HTML 元素始发`elemName`。  
  
```  
 
DHTML_EVENT_ONROWEXIT(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventonselectstarta--dhtmleventonselectstart"></a><a name="dhtml_event_onselectstart"></a>DHTML_EVENT_ONSELECTSTART  
 （在文档级别） 处理**onselectstart**事件是由标识的 HTML 元素始发`elemName`。  
  
```  
 
DHTML_EVENT_ONSELECTSTART(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>参数  
 `elemName`  
 `LPCWSTR`保存来源事件的 HTML 元素的 ID。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedhtmleventtaga--dhtmleventtag"></a><a name="dhtml_event_tag"></a>DHTML_EVENT_TAG  
 （在文档级别） 处理由标识的事件`dispid`发起的任何 HTML 元素的标识的 HTML 标记`elemName`。  
  
```   
DHTML_EVENT_TAG(dispid, elemName,  memberFxn)   
```  
  
### <a name="parameters"></a>参数  
 `dispid`  
 要处理的事件调度 ID。  
  
 `elemName`  
 事件来源的 HTML 元素的 HTML 标记。  
  
 `memberFxn`  
 该事件处理程序函数。  
  
### <a name="remarks"></a>备注  
 使用此宏将项添加到[DHTML 事件映射](#begin_dhtml_event_map_inline)在您的类。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-nameenddhtmleventmapa--enddhtmleventmap"></a><a name="end_dhtml_event_map"></a>END_DHTML_EVENT_MAP  
 标记 DHTML 事件映射的结尾。  
  
```   
END_DHTML_EVENT_MAP()   
```  
  
### <a name="remarks"></a>备注  
 必须结合使用[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namebegindhtmlurleventmapa--begindhtmlurleventmap"></a><a name="begin_dhtml_url_event_map"></a>BEGIN_DHTML_URL_EVENT_MAP  
 启动多页对话框 DHTML 和 URL 事件映射的定义。  
  
```  
BEGIN_DHTML_URL_EVENT_MAP()  
 
```  
  
### <a name="remarks"></a>备注  
 放置`BEGIN_DHTML_URL_EVENT_MAP`的实现文件中您[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)的派生类。 按照其与[嵌入 DHTML 事件映射](#begin_embed_dhtml_event_map)和[URL 条目](#begin_url_entries)，然后将其与关闭[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)。 包括[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)类定义中的宏。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&196;](../../mfc/codesnippet/cpp/dhtml-event-maps_1.cpp)]  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namebeginembeddhtmleventmapa--beginembeddhtmleventmap"></a><a name="begin_embed_dhtml_event_map"></a>BEGIN_EMBED_DHTML_EVENT_MAP  
 多页对话框中启动嵌入 DHTML 事件映射的定义。  
  
```  
BEGIN_EMBED_DHTML_EVENT_MAP(className, mapName)  
 
```  
  
### <a name="parameters"></a>参数  
 `className`  
 包含事件映射的类的名称。 此类应直接或间接派生从[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 嵌入的 DHTML 事件映射必须位于[DHTML 和 URL 事件映射](#begin_dhtml_url_event_map))。  
  
 *映射名称*  
 指定此列的事件类型映射页。 这符合*mapName*中[URL_EVENT_ENTRY](#url_event_entry)宏实际定义 URL 或 HTML 资源。  
  
### <a name="remarks"></a>备注  
 由于多页 DHTML 对话框包含多个 HTML 页，其中每个可引发 DHTML 事件，嵌入的事件映射用于将事件映射到每页基础上的处理程序。  
  
 DHTML 和 URL 事件映射中的嵌入的事件映射组成`BEGIN_EMBED_DHTML_EVENT_MAP`宏跟[DHTML_EVENT](dhtml-event-maps.md#dhtml_event)宏和[END_EMBED_DHTML_EVENT_MAP](dhtml-event-maps.md#end_embed_dhtml_event_map)宏。  
  
 每个嵌入的事件映射需要相应[URL 事件输入](#url_event_entry)映射*mapName* (中指定`BEGIN_EMBED_DHTML_EVENT_MAP`) 到 URL 或 HTML 资源。  
  
### <a name="example"></a>示例  
 请参阅中的示例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namebeginurlentriesa--beginurlentries"></a><a name="begin_url_entries"></a>BEGIN_URL_ENTRIES  
 在多页对话框中启动 URL 事件输入映射的定义。  
  
```  
BEGIN_URL_ENTRIES(className)  
 
```  
  
### <a name="parameters"></a>参数  
 `className`  
 包含 URL 事件映射的类的名称。 此类应直接或间接派生从[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 URL 事件输入映射必须位于内部[DHTML 和 URL 事件映射](#begin_dhtml_url_event_map))。  
  
### <a name="remarks"></a>备注  
 由于多页 DHTML 对话框包含多个 HTML 页，URL 事件输入用于映射 Url 或 HTML 的资源添加到相应[嵌入 DHTML 事件映射](#begin_embed_dhtml_event_map)。 放置`URL_EVENT_ENTRY`之间宏`BEGIN_URL_ENTRIES`和[END_URL_ENTRIES](#end_url_entries)宏。  
  
### <a name="example"></a>示例  
 请参阅中的示例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-namedeclaredhtmlurleventmapa--declaredhtmlurleventmap"></a><a name="declare_dhtml_url_event_map"></a>DECLARE_DHTML_URL_EVENT_MAP  
 声明 DHTML 和 URL 事件映射中的类定义。  
  
```  
DECLARE_DHTML_URL_EVENT_MAP()  
 
```  
  
### <a name="remarks"></a>备注  
 此宏的定义中使用，则[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)的派生类。  
  
 DHTML 和 URL 事件映射包含[嵌入 DHTML 事件映射](#begin_embed_dhtml_event_map)和[URL 事件输入](#begin_url_entries)DHTML 事件映射到每页基础上的处理程序。 使用[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)来实现该映射。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-nameenddhtmlurleventmapa--enddhtmlurleventmap"></a><a name="end_dhtml_url_event_map"></a>END_DHTML_URL_EVENT_MAP  
 标记 DHTML 和 URL 事件映射的结尾。  
  
```  
END_DHTML_URL_EVENT_MAP(className)  
 
```  
  
### <a name="parameters"></a>参数  
 `className`  
 包含事件映射的类的名称。 此类应直接或间接派生从[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 这应匹配`className`在相应[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)宏。  
  
### <a name="example"></a>示例  
 请参阅中的示例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-nameendembeddhtmleventmapa--endembeddhtmleventmap"></a><a name="end_embed_dhtml_event_map"></a>END_EMBED_DHTML_EVENT_MAP  
 标记嵌入 DHTML 事件映射的结尾。  
  
```  
END_EMBED_DHTML_EVENT_MAP()  
 
```  
  
### <a name="example"></a>示例  
 请参阅中的示例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-nameendurlentriesa--endurlentries"></a><a name="end_url_entries"></a>END_URL_ENTRIES  
 标记 URL 事件输入映射的结尾。  
  
```  
END_URL_ENTRIES()  
 
```  
  
### <a name="example"></a>示例  
 请参阅中的示例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
  
##  <a name="a-nameurlevententrya--urlevententry"></a><a name="url_event_entry"></a>URL_EVENT_ENTRY  
 将 URL 或 HTML 资源映射到多页对话框中的页。  
  
```  
URL_EVENT_ENTRY(className, url,  mapName)   
```  
  
### <a name="parameters"></a>参数  
 `className`  
 包含 URL 事件映射的类的名称。 此类应直接或间接派生从[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 URL 事件输入映射必须位于内部[DHTML 和 URL 事件映射](#begin_dhtml_url_event_map))。  
  
 *url*  
 面向页面的 URL 或 HTML 资源。  
  
 *映射名称*  
 指定的 URL 的页面*url*。 这符合*mapName*中[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)映射从此页的事件的宏。  
  
### <a name="remarks"></a>备注  
 如果页是一个 HTML 资源， *url*必须为该资源的 ID 号 (即，"123"中，不 123 或 ID_HTMLRES1) 的字符串表示。  
  
 页标识符， *mapName*，即是用于将链接的任意符号嵌入 DHTML 事件映射到 URL 事件输入映射。 对其进行限制 DHTML 和 URL 事件映射到范围内。  
  
### <a name="example"></a>示例  
 请参阅中的示例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。  

  
### <a name="requirements"></a>要求  
  **标头**afxdhtml.h  
    
## <a name="see-also"></a>另请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)

