---
title: DDX_DHtml Helper 宏
ms.date: 11/04/2016
f1_keywords:
- AFXDHTML/DDX_DHtml_ElementValue
- AFXDHTML/DDX_DHtml_ElementInnerText
- AFXDHTML/DDX_DHtml_ElementInnerHtml
- AFXDHTML/DDX_DHtml_Anchor_Href
- AFXDHTML/DDX_DHtml_Anchor_Target
- AFXDHTML/DDX_DHtml_Img_Src
- AFXDHTML/DDX_DHtml_Frame_Src
- AFXDHTML/DDX_DHtml_IFrame_Src
helpviewer_keywords:
- macros [MFC], exchanging data with HMTL pages
- DDX macros [MFC]
- HTML pages [MFC], helper macros
- DDX (dialog data exchange), DHtml helper macros
- macros [MFC], DDX_DHtml helpers
ms.assetid: c46302d2-ea43-4fea-bfc2-6f590d99f267
ms.openlocfilehash: 90c80dbc5c8b6788f3afad3cf77d796139fbd946
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866652"
---
# <a name="ddx_dhtml-helper-macros"></a>DDX_DHtml Helper 宏

DDX_DHtml helper 宏允许在 HTML 页上轻松访问控件的常用属性。

### <a name="data-exchange-macros"></a>数据交换宏

|||
|-|-|
|[DDX_DHtml_ElementValue](#ddx_dhtml_elementvalue)|设置或检索选定控件的值属性。|
|[DDX_DHtml_ElementInnerText](#ddx_dhtml_elementinnertext)|设置或检索当前元素的开始标记和结束标记之间的文本。|
|[DDX_DHtml_ElementInnerHtml](#ddx_dhtml_elementinnerhtml)|设置或检索当前元素的开始标记和结束标记之间的 HTML。|
|[DDX_DHtml_Anchor_Href](#ddx_dhtml_anchor_href)|设置或检索目标 URL 或定位点。|
|[DDX_DHtml_Anchor_Target](#ddx_dhtml_anchor_target)|设置或检索目标窗口或框架。|
|[DDX_DHtml_Img_Src](#ddx_dhtml_img_src)|设置或检索文档中图像或视频剪辑的名称。|
|[DDX_DHtml_Frame_Src](#ddx_dhtml_frame_src)|设置或检索关联帧的 URL。|
|[DDX_DHtml_IFrame_Src](#ddx_dhtml_iframe_src)|设置或检索关联帧的 URL。|

## <a name="requirements"></a>要求

**标头：** afxdhtml

## <a name="ddx_dhtml_anchor_href"></a>DDX_DHtml_Anchor_Href

设置或检索目标 URL 或定位点。

```
DDX_DHtml_Anchor_Href(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>parameters

*dx*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。

name<br/>
为 HTML 控件的 ID 参数指定的值。

*var*<br/>
要交换的值。

## <a name="remarks"></a>备注

此宏使用 DISPID_IHTMLANCHORELEMENT_HREF 调度 ID 调用[CDHtmlDialog：:D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函数。

## <a name="ddx_dhtml_anchor_target"></a>DDX_DHtml_Anchor_Target

设置或检索目标窗口或框架。

```
DDX_DHtml_Anchor_Target(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>parameters

*dx*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。

name<br/>
为 HTML 控件的 ID 参数指定的值。

*var*<br/>
要交换的值。

## <a name="remarks"></a>备注

此宏使用 DISPID_IHTMLANCHORELEMENT_TARGET 调度 ID 调用[CDHtmlDialog：:D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函数。

## <a name="ddx_dhtml_elementinnerhtml"></a>DDX_DHtml_ElementInnerHtml

设置或检索当前元素的开始标记和结束标记之间的 HTML。

```
DDX_DHtml_ElementInnerHtml(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>parameters

*dx*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。

name<br/>
为 HTML 控件的 ID 参数指定的值。

*var*<br/>
要交换的值。

## <a name="remarks"></a>备注

此宏使用 DISPID_IHTMLELEMENT_INNERHTML 调度 ID 调用[CDHtmlDialog：:D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函数。

## <a name="ddx_dhtml_elementinnertext"></a>DDX_DHtml_ElementInnerText

设置或检索当前元素的开始标记和结束标记之间的文本。

```
DDX_DHtml_ElementInnerText(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>parameters

*dx*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。

name<br/>
为 HTML 控件的 ID 参数指定的值。

*var*<br/>
要交换的值。

## <a name="remarks"></a>备注

此宏使用 DISPID_IHTMLELEMENT_INNERTEXT 调度 ID 调用[CDHtmlDialog：:D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函数。

## <a name="ddx_dhtml_elementvalue"></a>DDX_DHtml_ElementValue

设置或检索选定控件的值属性。

```
DDX_DHtml_ElementValue(
    CDataExchange* dx,
    LPCTSTR name,
    var)
```

#### <a name="parameters"></a>parameters

*dx*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。

name<br/>
为 HTML 控件的 ID 参数指定的值。

*var*<br/>
要交换的值。 请参阅[CDHtmlDialog：:D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)中的*值*。

## <a name="remarks"></a>备注

仅当在具有值属性的控件上运行时，此宏才会成功。 具有值属性的控件包括编辑框、列表框和组合框。

此宏使用 DISPID_A_VALUE 调度 ID 调用[CDHtmlDialog：:D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函数。

## <a name="ddx_dhtml_frame_src"></a>DDX_DHtml_Frame_Src

设置或检索关联帧的 URL。

```
DDX_DHtml_Frame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>parameters

*dx*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。

name<br/>
为 HTML 控件的 ID 参数指定的值。

*var*<br/>
要交换的值。

## <a name="remarks"></a>备注

此宏使用 DISPID_IHTMLFRAMEBASE_SRC 调度 ID 调用[CDHtmlDialog：:D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函数。

## <a name="ddx_dhtml_iframe_src"></a>DDX_DHtml_IFrame_Src

设置或检索关联帧的 URL。

```
DDX_DHtml_IFrame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>parameters

*dx*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。

name<br/>
为 HTML 控件的 ID 参数指定的值。

*var*<br/>
要交换的值。

## <a name="remarks"></a>备注

此宏使用 DISPID_IHTMLFRAMEBASE_SRC 调度 ID 调用[CDHtmlDialog：:D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函数。

## <a name="ddx_dhtml_img_src"></a>DDX_DHtml_Img_Src

获取或检索文档中图像或视频剪辑的名称。

```
DDX_DHtml_Img_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>parameters

*dx*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。

name<br/>
为 HTML 控件的 ID 参数指定的值。

*var*<br/>
要交换的值。

## <a name="remarks"></a>备注

使用 DDX_DHtml_Img_Src 宏检索 IMAGE 元素的 Src 属性时，Internet Explorer 图像对象将返回图像源的完全转义 URL。 例如，如果使用 DDX_DHtml_Img_Src 宏将 IMAGE 元素的 Src 属性设置为 "一些有趣的图片"，则在检索该属性时，Internet Explorer 将返回字符串 "res：//d： \ myapplication \ myapp/一些 %2 0 有趣的 %2 0 图片"。

此宏使用 DISPID_IHTMLIMGELEMENT_SRC 调度 ID 调用[CDHtmlDialog：:D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函数。

## <a name="see-also"></a>另请参阅

[CDHtmlDialog 类](../../mfc/reference/cdhtmldialog-class.md)
