---
title: COle 更新对话类
ms.date: 11/04/2016
f1_keywords:
- COleUpdateDialog
- AFXODLGS/COleUpdateDialog
- AFXODLGS/COleUpdateDialog::COleUpdateDialog
- AFXODLGS/COleUpdateDialog::DoModal
helpviewer_keywords:
- COleUpdateDialog [MFC], COleUpdateDialog
- COleUpdateDialog [MFC], DoModal
ms.assetid: 699ca980-52b1-4cf8-9ab1-ac6767ad5b0e
ms.openlocfilehash: 9e2c7a8d79ebf5e6483a06354b280e474d7b8e61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374841"
---
# <a name="coleupdatedialog-class"></a>COle 更新对话类

用于 OLE“编辑链接”对话框的特例，当你只需要更新文档中现有的链接对象或嵌入对象时才可使用。

## <a name="syntax"></a>语法

```
class COleUpdateDialog : public COleLinksDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COle 更新对话：：COle 更新对话](#coleupdatedialog)|构造 `COleUpdateDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COle更新对话：:Do模态](#domodal)|在更新模式下显示 **"编辑链接"** 对话框。|

## <a name="remarks"></a>备注

有关特定于 OLE 的对话框的详细信息，请参阅 OLE[中的"对话框](../../mfc/dialog-boxes-in-ole.md)"一文。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

[COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)

`COleUpdateDialog`

## <a name="requirements"></a>要求

**标题：** afxodlgs.h

## <a name="coleupdatedialogcoleupdatedialog"></a><a name="coleupdatedialog"></a>COle 更新对话：：COle 更新对话

构造 `COleUpdateDialog` 对象。

```
explicit COleUpdateDialog(
    COleDocument* pDoc,
    BOOL bUpdateLinks = TRUE,
    BOOL bUpdateEmbeddings = FALSE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*pDoc*<br/>
指向包含可能需要更新的链接的文档。

*b更新链接*<br/>
确定链接对象是否要更新的标志。

*b 更新嵌入*<br/>
确定是否要更新嵌入对象的标志。

*pparentwnd*<br/>
指向对话框对象所属的父窗口或所有者窗口对象`CWnd`（类型）。 如果为 NULL，则对话框的父窗口将设置为主应用程序窗口。

### <a name="remarks"></a>备注

此函数仅构造对象`COleUpdateDialog`。 要显示对话框，请调用[DoModal](../../mfc/reference/colelinksdialog-class.md#domodal)。 应使用此类，而不是`COleLinksDialog`仅更新现有链接或嵌入项目。

## <a name="coleupdatedialogdomodal"></a><a name="domodal"></a>COle更新对话：:Do模态

在更新模式下显示"编辑链接"对话框。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

对话框的完成状态。 以下值之一：

- 如果对话框成功返回，则 IDOK。

- 如果当前文档中的链接或嵌入项目不需要更新，则 IDCANCEL。

- 如果发生错误，则 IDABORT。 如果返回 IDABORT，请调用[COleDialog：getLastError](../../mfc/reference/coledialog-class.md#getlasterror)成员函数，以获取有关所发生错误类型的详细信息。 有关可能错误的列表，请参阅 Windows SDK 中的[OleUIEditLinks](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw)函数。

### <a name="remarks"></a>备注

除非用户选择"取消"按钮，否则所有链接和/或嵌入都将更新。

## <a name="see-also"></a>另请参阅

[MFC 样品 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleLinks对话类](../../mfc/reference/colelinksdialog-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleLinks对话类](../../mfc/reference/colelinksdialog-class.md)
