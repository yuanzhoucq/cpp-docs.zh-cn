---
title: DDX_DHtml 帮助器宏 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFXDHTML/DDX_DHtml_ElementValue
- AFXDHTML/DDX_DHtml_ElementInnerText
- AFXDHTML/DDX_DHtml_ElementInnerHtml
- AFXDHTML/DDX_DHtml_Anchor_Href
- AFXDHTML/DDX_DHtml_Anchor_Target
- AFXDHTML/DDX_DHtml_Img_Src
- AFXDHTML/DDX_DHtml_Frame_Src
- AFXDHTML/DDX_DHtml_IFrame_Src
dev_langs:
- C++
helpviewer_keywords:
- macros [MFC], exchanging data with HMTL pages
- DDX macros [MFC]
- HTML pages [MFC], helper macros
- DDX (dialog data exchange), DHtml helper macros
- macros [MFC], DDX_DHtml helpers
ms.assetid: c46302d2-ea43-4fea-bfc2-6f590d99f267
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb2e9d2494463b502fda85c03fa1b861e1182cfc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="ddxdhtml-helper-macros"></a>DDX_DHtml 帮助器宏
DDX_DHtml 帮助器宏让您轻松访问的 HTML 页上的控件的常用属性。  
  
### <a name="data-exchange-macros"></a>数据交换宏  
  
|||  
|-|-|  
|[DDX_DHtml_ElementValue](#ddx_dhtml_elementvalue)|设置或检索所选控件的值属性。|  
|[DDX_DHtml_ElementInnerText](#ddx_dhtml_elementinnertext)|设置或检索的当前元素的开始和结束标记之间的文本。|  
|[DDX_DHtml_ElementInnerHtml](#ddx_dhtml_elementinnerhtml)|设置或检索的当前元素的开始和结束标记之间的 HTML。|  
|[DDX_DHtml_Anchor_Href](#ddx_dhtml_anchor_href)|设置或检索的目标 URL 或定位点。|  
|[DDX_DHtml_Anchor_Target](#ddx_dhtml_anchor_target)|设置或检索的目标窗口或框架。|  
|[DDX_DHtml_Img_Src](#ddx_dhtml_img_src)|设置或检索图像或文档中的视频剪辑的名称。|  
|[DDX_DHtml_Frame_Src](#ddx_dhtml_frame_src)|设置或检索关联的帧的 URL。|  
|[DDX_DHtml_IFrame_Src](#ddx_dhtml_iframe_src)|设置或检索关联的帧的 URL。|  
  
## <a name="requirements"></a>要求  
 **标头：** afxdhtml.h  

## <a name="ddx_dhtml_anchor_href"></a> DDX_DHtml_Anchor_Href
设置或检索的目标 URL 或定位点。  
  
  
  
```  
DDX_DHtml_Anchor_Href(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>参数  
 `dx`  
 指向的指针[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。  
  
 `name`  
 为 HTML 控件的 ID 参数指定的值。  
  
 `var`  
 要交换的值。  
  
## <a name="remarks"></a>备注  
 此宏将调用[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函数使用 DISPID_IHTMLANCHORELEMENT_HREF 调度 id。

## <a name="ddx_dhtml_anchor_target"></a>  DDX_DHtml_Anchor_Target
 设置或检索的目标窗口或框架。  
    
```  
DDX_DHtml_Anchor_Target(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>参数  
 `dx`  
 指向的指针[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。  
  
 `name`  
 为 HTML 控件的 ID 参数指定的值。  
  
 `var`  
 要交换的值。  
  
## <a name="remarks"></a>备注  
 此宏将调用[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函数使用 DISPID_IHTMLANCHORELEMENT_TARGET 调度 id。  

## <a name="ddx_dhtml_elementinnerhtml"></a>  DDX_DHtml_ElementInnerHtml
 设置或检索的当前元素的开始和结束标记之间的 HTML。  
  
  
  
```  
DDX_DHtml_ElementInnerHtml(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>参数  
 `dx`  
 指向的指针[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。  
  
 `name`  
 为 HTML 控件的 ID 参数指定的值。  
  
 `var`  
 要交换的值。  
  
## <a name="remarks"></a>备注  
 此宏将调用[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函数使用 DISPID_IHTMLELEMENT_INNERHTML 调度 id。  
  

## <a name="ddx_dhtml_elementinnertext"></a>  DDX_DHtml_ElementInnerText
设置或检索的当前元素的开始和结束标记之间的文本。  
  
  
  
```  
DDX_DHtml_ElementInnerText(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>参数  
 `dx`  
 指向的指针[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。  
  
 `name`  
 为 HTML 控件的 ID 参数指定的值。  
  
 `var`  
 要交换的值。  
  
## <a name="remarks"></a>备注  
 此宏将调用[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函数使用 DISPID_IHTMLELEMENT_INNERTEXT 调度 id。 

## <a name="ddx_dhtml_elementvalue"></a> DDX_DHtml_ElementValue  
设置或检索所选控件的值属性。  
 
```  
DDX_DHtml_ElementValue(
    CDataExchange* dx,  
    LPCTSTR name,
    var)  
```  
  
#### <a name="parameters"></a>参数  
 `dx`  
 指向的指针[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。  
  
 `name`  
 为 HTML 控件的 ID 参数指定的值。  
  
 `var`  
 要交换的值。 请参阅*值*中[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)。  
  
## <a name="remarks"></a>备注  
 当在具有 Value 属性的控件上运行，此宏将只会成功。 具有值属性的控件包括编辑框、 列表框和组合框。  
  
 此宏将调用[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函数使用 DISPID_A_VALUE 调度 id。  

## <a name="ddx_dhtml_frame_src"></a> DDX_DHtml_Frame_Src
设置或检索关联的帧的 URL。  
  
```  
DDX_DHtml_Frame_Src(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>参数  
 `dx`  
 指向的指针[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。  
  
 `name`  
 为 HTML 控件的 ID 参数指定的值。  
  
 `var`  
 要交换的值。  
  
## <a name="remarks"></a>备注  
 此宏将调用[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函数使用 DISPID_IHTMLFRAMEBASE_SRC 调度 id。  

## <a name="ddx_dhtml_iframe_src"></a> DDX_DHtml_IFrame_Src
设置或检索关联的帧的 URL。  
  
  
  
```  
DDX_DHtml_IFrame_Src(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>参数  
 `dx`  
 指向的指针[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。  
  
 `name`  
 为 HTML 控件的 ID 参数指定的值。  
  
 `var`  
 要交换的值。  
  
## <a name="remarks"></a>备注  
 此宏将调用[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函数使用 DISPID_IHTMLFRAMEBASE_SRC 调度 id。 

## <a name="ddx_dhtml_img_src"></a>DDX_DHtml_Img_Src
获取或检索图像或文档中的视频剪辑的名称。  
  
```  
DDX_DHtml_Img_Src(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>参数  
 `dx`  
 指向的指针[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。  
  
 `name`  
 为 HTML 控件的 ID 参数指定的值。  
  
 `var`  
 要交换的值。  
  
## <a name="remarks"></a>备注  
 使用时`DDX_DHtml_Img_Src`宏要检索图像元素，Internet Explorer 映像对象的 src 属性将返回图像源的完全转义的 URL。 例如，如果你使用`DDX_DHtml_Img_Src`宏以将图像元素的 src 属性设置为字符串"一些有趣图中，"Internet Explorer 时检索该属性，将返回字符串"res://d:\myapplication\myapp.exe/some%20interesting %20picture。"  
  
 此宏将调用[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函数使用 DISPID_IHTMLIMGELEMENT_SRC 调度 id。  

  
## <a name="see-also"></a>请参阅  
 [CDHtmlDialog 类](../../mfc/reference/cdhtmldialog-class.md)
