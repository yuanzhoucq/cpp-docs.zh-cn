---
title: CHtmlEditCtrl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::Create
- AFXHTML/CHtmlEditCtrl::GetDHtmlDocument
- AFXHTML/CHtmlEditCtrl::GetStartDocument
dev_langs:
- C++
helpviewer_keywords:
- CHtmlEditCtrl [MFC], CHtmlEditCtrl
- CHtmlEditCtrl [MFC], Create
- CHtmlEditCtrl [MFC], GetDHtmlDocument
- CHtmlEditCtrl [MFC], GetStartDocument
ms.assetid: 0fc4a238-b05f-4874-9edc-6a6701f064d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ab9a94663e2c374c0671afc6d4d093559ae1a69
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412390"
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

|名称|描述|
|----------|-----------------|
|[CHtmlEditCtrl::CHtmlEditCtrl](#chtmleditctrl)|构造 `CHtmlEditCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CHtmlEditCtrl::Create](#create)|创建 WebBrowser ActiveX 控件，并将其附加到`CHtmlEditCtrl`对象。 此函数自动使 WebBrowser ActiveX 控件进入编辑模式。|
|[CHtmlEditCtrl::GetDHtmlDocument](#getdhtmldocument)|检索[IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx)所包含的 web 浏览器控件中当前加载该文档上的接口。|
|[CHtmlEditCtrl::GetStartDocument](#getstartdocument)|检索默认文档包含的 WebBrowser 控件中加载的 URL。|

## <a name="remarks"></a>备注

在创建后，托管的 WebBrowser 控件自动将进入编辑模式。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHtmlEditCtrl`

## <a name="requirements"></a>要求

**标头：** afxhtml.h

##  <a name="chtmleditctrl"></a>  CHtmlEditCtrl::CHtmlEditCtrl

构造 `CHtmlEditCtrl` 对象。

```
CHtmlEditCtrl();
```

##  <a name="create"></a>  CHtmlEditCtrl::Create

创建 WebBrowser ActiveX 控件，并将其附加到`CHtmlEditCtrl`对象。 WebBrowser ActiveX 控件自动导航到默认文档，然后置于编辑模式，此函数。

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

*lpszWindowName*<br/>
未使用此参数。

*dwStyle*<br/>
未使用此参数。

*rect*<br/>
指定控件的大小和位置。

*pParentWnd*<br/>
指定控件的父窗口。 它不能为 NULL。

*nID*<br/>
指定控件的 id。

*pContext*<br/>
未使用此参数。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

##  <a name="getdhtmldocument"></a>  CHtmlEditCtrl::GetDHtmlDocument

检索[IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx)所包含的 web 浏览器控件中当前加载该文档上的接口

```
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;
```

### <a name="parameters"></a>参数

*ppDocument*<br/>
文档界面中。

##  <a name="getstartdocument"></a>  CHtmlEditCtrl::GetStartDocument

检索默认文档包含的 WebBrowser 控件中加载的 URL。

```
virtual LPCTSTR GetStartDocument();
```

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)

