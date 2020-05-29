---
title: C 多页DHtml对话类
ms.date: 03/27/2019
f1_keywords:
- CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog::CMultiPageDHtmlDialog
helpviewer_keywords:
- CMultiPageDHtmlDialog [MFC], CMultiPageDHtmlDialog
ms.assetid: 971accc1-824d-4df4-b4c1-b1a20e0f7e4f
ms.openlocfilehash: 89e4830c3b5c6cb663ca2d2935adaaae3f356958
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319656"
---
# <a name="cmultipagedhtmldialog-class"></a>C 多页DHtml对话类

多页对话框按顺序显示多个 HTML 页并处理每页中的事件。

## <a name="syntax"></a>语法

```
class CMultiPageDHtmlDialog : public CDHtmlDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C 多页Html对话：：C多页DHtml对话](#cmultipagedhtmldialog)|构造多页（向导样式）DHTML对话框对象。|
|[C 多页Html对话：：_c多页DHtml对话](#_dtorcmultipagedhtmldialog)|销毁多页 DHTML 对话框对象。|

## <a name="remarks"></a>备注

执行此操作的机制是[DHTML 和 URL 事件映射](dhtml-event-maps.md)，其中包含每个页面的嵌入事件映射。

## <a name="example"></a>示例

此多页对话框假定三个 HTML 资源定义类似于向导的简单功能。 第一页有一个 **"下一步**"按钮，第二个按钮为 **"Prev"** 和 **"下一步**"按钮，第三页具有 **"Prev"** 按钮。 按下其中一个按钮时，处理程序函数将调用[CDHtmlDialog：：LoadFromResource](../../mfc/reference/cdhtmldialog-class.md#loadfromresource)以加载相应的新页面。

类声明的相关部分（在 CMyMultiPageDlg.h 中）：

[!code-cpp[NVC_MFCDocView#181](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_1.h)]

类实现的相关部分（在 CMyMultipageDlg.cpp 中）：

[!code-cpp[NVC_MFCDocView#182](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CDHtmlSinkHandlerBase2`

`CDHtmlSinkHandlerBase1`

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDHtmlSinkHandler`

[CWnd](../../mfc/reference/cwnd-class.md)

`CDHtmlEventSink`

[CDialog](../../mfc/reference/cdialog-class.md)

[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)

`CMultiPageDHtmlDialog`

## <a name="requirements"></a>要求

**标题：** afxdhtml.h

## <a name="cmultipagedhtmldialogcmultipagedhtmldialog"></a><a name="cmultipagedhtmldialog"></a>C 多页Html对话：：C多页DHtml对话

构造多页（向导样式）DHTML对话框对象。

```
CMultiPageDHtmlDialog(
    LPCTSTR lpszTemplateName,
    LPCTSTR szHtmlResID = NULL,
    CWnd* pParentWnd = NULL);

CMultiPageDHtmlDialog(
    UINT nIDTemplate,
    UINT nHtmlResID = 0,
    CWnd* pParentWnd = NULL);

CMultiPageDHtmlDialog();
```

### <a name="parameters"></a>参数

*lpszTemplate 名称*<br/>
作为对话框模板资源名称的 null 终止字符串。

*什奇雷斯ID*<br/>
作为 HTML 资源名称的 null 终止字符串。

*pparentwnd*<br/>
指向对话框对象所属的父窗口或所有者窗口对象的指针[（CWnd](../../mfc/reference/cwnd-class.md)类型）。 如果为 NULL，则对话框对象的父窗口将设置为主应用程序窗口。

*nIDTemplate*<br/>
包含对话框模板资源的 ID 号。

*nHtmlResID*<br/>
包含 HTML 资源的 ID 号。

## <a name="cmultipagedhtmldialogcmultipagedhtmldialog"></a><a name="_dtorcmultipagedhtmldialog"></a>C 多页Html对话：：_c多页DHtml对话

销毁多页 DHTML 对话框对象。

```
virtual ~CMultiPageDHtmlDialog();
```

## <a name="see-also"></a>另请参阅

[CDHtml对话类](../../mfc/reference/cdhtmldialog-class.md)
