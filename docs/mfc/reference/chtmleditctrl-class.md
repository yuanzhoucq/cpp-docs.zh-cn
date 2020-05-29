---
title: CHtmlEditCtrl 类
ms.date: 11/04/2016
f1_keywords:
- CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::Create
- AFXHTML/CHtmlEditCtrl::GetDHtmlDocument
- AFXHTML/CHtmlEditCtrl::GetStartDocument
helpviewer_keywords:
- CHtmlEditCtrl [MFC], CHtmlEditCtrl
- CHtmlEditCtrl [MFC], Create
- CHtmlEditCtrl [MFC], GetDHtmlDocument
- CHtmlEditCtrl [MFC], GetStartDocument
ms.assetid: 0fc4a238-b05f-4874-9edc-6a6701f064d9
ms.openlocfilehash: 05063c62e9f7a5d88d3fecde842f979725200f98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366846"
---
# <a name="chtmleditctrl-class"></a>CHtmlEditCtrl 类

提供 MFC 窗口中的 WebBrowser ActiveX 控件功能。

## <a name="syntax"></a>语法

```
class CHtmlEditCtrl: public CWnd,
    public CHtmlEditCtrlBase<CHtmlEditCtrl>
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CHtmlEditCtrl：：CHtmlEditCtrl](#chtmleditctrl)|构造 `CHtmlEditCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CHtml编辑Ctrl：创建](#create)|创建 Web 浏览器 ActiveX 控件并将其附加到`CHtmlEditCtrl`对象。 此功能会自动将 Web 浏览器 ActiveX 控件置于编辑模式。|
|[CHtml编辑Ctrl：获取DHtml文档](#getdhtmldocument)|检索当前在包含的 Web 浏览器控件中加载的文档上的[IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\))界面。|
|[CHtmlEditCtrl：：获取开始文件](#getstartdocument)|检索默认文档的 URL 以加载到包含的 Web 浏览器控件中。|

## <a name="remarks"></a>备注

托管 Web 浏览器控件在创建后会自动进入编辑模式。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHtmlEditCtrl`

## <a name="requirements"></a>要求

**标头：** afxhtml.h

## <a name="chtmleditctrlchtmleditctrl"></a><a name="chtmleditctrl"></a>CHtmlEditCtrl：：CHtmlEditCtrl

构造 `CHtmlEditCtrl` 对象。

```
CHtmlEditCtrl();
```

## <a name="chtmleditctrlcreate"></a><a name="create"></a>CHtml编辑Ctrl：创建

创建 Web 浏览器 ActiveX 控件并将其附加到`CHtmlEditCtrl`对象。 WebBrowser ActiveX 控件会自动导航到默认文档，然后由此功能置于编辑模式。

```
virtual BOOL Create(
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>参数

*lpsz窗口名称*<br/>
未使用此参数。

*dwStyle*<br/>
未使用此参数。

*矩形*<br/>
指定控件的大小和位置。

*pparentwnd*<br/>
指定控件的父窗口。 值不得为 NULL。

*nID*<br/>
指定控件的 ID。

*pContext*<br/>
未使用此参数。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

## <a name="chtmleditctrlgetdhtmldocument"></a><a name="getdhtmldocument"></a>CHtml编辑Ctrl：获取DHtml文档

检索当前在包含的 Web 浏览器控件中加载的文档上的[IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\))界面

```
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;
```

### <a name="parameters"></a>参数

*ppDocument*<br/>
文档接口。

## <a name="chtmleditctrlgetstartdocument"></a><a name="getstartdocument"></a>CHtmlEditCtrl：：获取开始文件

检索默认文档的 URL 以加载到包含的 Web 浏览器控件中。

```
virtual LPCTSTR GetStartDocument();
```

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)
