---
title: CHtmlEditView 类
ms.date: 11/04/2016
f1_keywords:
- CHtmlEditView
- AFXHTML/CHtmlEditView
- AFXHTML/CHtmlEditView::CHtmlEditView
- AFXHTML/CHtmlEditView::Create
- AFXHTML/CHtmlEditView::GetDHtmlDocument
- AFXHTML/CHtmlEditView::GetStartDocument
helpviewer_keywords:
- CHtmlEditView [MFC], CHtmlEditView
- CHtmlEditView [MFC], Create
- CHtmlEditView [MFC], GetDHtmlDocument
- CHtmlEditView [MFC], GetStartDocument
ms.assetid: 166c8ba8-3fb5-4dd7-a9ea-5bca662d00f6
ms.openlocfilehash: 1254a3412846cdebd1d9accb91d27d0afbc4ef8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352083"
---
# <a name="chtmleditview-class"></a>CHtmlEditView 类

提供 MFC 文档/视图体系结构上下文中的 Web 浏览器编辑平台功能。

## <a name="syntax"></a>语法

```
class CHtmlEditView : public CHtmlView, public CHtmlEditCtrlBase<CHtmlEditView>
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[Html编辑视图：CHtmlEditView](#chtmleditview)|构造 `CHtmlEditView` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CHtmlEditView：创建](#create)|创建新窗口对象。|
|[CHtml编辑视图：获取Html文档](#getdhtmldocument)|返回`IHTMLDocument2`当前文档上的接口。|
|[CHtmlEditView：获取开始文件](#getstartdocument)|检索此视图的默认文档的名称。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

[CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)

[CHtmlView](../../mfc/reference/chtmlview-class.md)

`CHtmlEditView`

## <a name="requirements"></a>要求

**标头：** afxhtml.h

## <a name="chtmleditviewchtmleditview"></a><a name="chtmleditview"></a>Html编辑视图：CHtmlEditView

构造 `CHtmlEditView` 对象。

```
CHtmlEditView();
```

## <a name="chtmleditviewcreate"></a><a name="create"></a>CHtmlEditView：创建

创建新窗口对象。

```
virtual BOOL Create(
    LPCTSTR lpszClassName,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>参数

*lpszClass名称*<br/>
指向命名 Windows 类的 null 端接字符串。 类名称可以是注册到[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)全局函数或`RegisterClass`Windows 函数的任何名称。 如果为 NULL，则使用预定义的默认[CFramewnd](../../mfc/reference/cframewnd-class.md)属性。

*lpsz窗口名称*<br/>
指向表示窗口名称的 null 端接字符串。

*dwStyle*<br/>
指定窗口样式属性。 默认情况下，将设置WS_VISIBLE和WS_CHILD Windows 样式。

*矩形*<br/>
对[RECT](/previous-versions/dd162897\(v=vs.85\))结构的引用，指定窗口的大小和位置。 *rectDefault*值允许 Windows 指定新窗口的大小和位置。

*pparentwnd*<br/>
指向控件的父窗口的指针。

*nID*<br/>
视图的 ID 号。 默认情况下，设置为AFX_IDW_PANE_FIRST。

*pContext*<br/>
指向[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)的指针。 默认情况下为 NULL。

### <a name="remarks"></a>备注

此方法还将调用包含的`Navigate`WebBrowser 方法来加载默认文档（请参阅[CHtmlEditView：：getStartDocument）。](#getstartdocument)

## <a name="chtmleditviewgetdhtmldocument"></a><a name="getdhtmldocument"></a>CHtml编辑视图：获取Html文档

返回`IHTMLDocument2`当前文档上的接口。

```
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;
```

### <a name="parameters"></a>参数

*ppDocument*<br/>
[IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\))接口。

## <a name="chtmleditviewgetstartdocument"></a><a name="getstartdocument"></a>CHtmlEditView：获取开始文件

检索此视图的默认文档的名称。

```
virtual LPCTSTR GetStartDocument();
```

## <a name="see-also"></a>另请参阅

[HTML编辑示例](../../overview/visual-cpp-samples.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
