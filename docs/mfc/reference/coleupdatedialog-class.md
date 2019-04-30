---
title: COleUpdateDialog 类
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
ms.openlocfilehash: b8e580130b025f07b8f85a624b7f5a224a00e49e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62373591"
---
# <a name="coleupdatedialog-class"></a>COleUpdateDialog 类

用于 OLE“编辑链接”对话框的特例，当你只需要更新文档中现有的链接对象或嵌入对象时才可使用。

## <a name="syntax"></a>语法

```
class COleUpdateDialog : public COleLinksDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COleUpdateDialog::COleUpdateDialog](#coleupdatedialog)|构造 `COleUpdateDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleUpdateDialog::DoModal](#domodal)|显示**编辑链接**更新模式中的对话框。|

## <a name="remarks"></a>备注

有关特定于 OLE 的对话框的详细信息，请参阅文章[OLE 中的对话框](../../mfc/dialog-boxes-in-ole.md)。

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

**标头：** afxodlgs.h

##  <a name="coleupdatedialog"></a>  COleUpdateDialog::COleUpdateDialog

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

*bUpdateLinks*<br/>
确定是否要更新链接的对象的标志。

*bUpdateEmbeddings*<br/>
确定是否要更新嵌入的对象的标志。

*pParentWnd*<br/>
指向父或所有者窗口对象 (类型的`CWnd`) 对话框对象属于的。 如果它为 NULL，父窗口的对话框的将设置为应用程序主窗口。

### <a name="remarks"></a>备注

此函数将构造仅`COleUpdateDialog`对象。 若要显示的对话框，请调用[DoModal](../../mfc/reference/colelinksdialog-class.md#domodal)。 应使用此类以代替`COleLinksDialog`当你想要更新仅现有链接或嵌入的项。

##  <a name="domodal"></a>  COleUpdateDialog::DoModal

编辑链接对话框框中显示更新模式。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

对话框中的完成状态。 以下值之一：

- IDOK 如果对话框的成功返回。

- IDCANCEL 如果没有当前文档中的链接或嵌入项，则需要更新。

- IDABORT 是否发生错误。 如果返回 IDABORT，调用[COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)成员函数以获取有关发生的错误类型的详细信息。 有关可能的错误的列表，请参阅[OleUIEditLinks](/windows/desktop/api/oledlg/nf-oledlg-oleuieditlinksa) Windows SDK 中的函数。

### <a name="remarks"></a>备注

除非用户选择取消按钮更新所有链接和/或嵌入内容。

## <a name="see-also"></a>请参阅

[MFC 示例 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleLinksDialog 类](../../mfc/reference/colelinksdialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleLinksDialog 类](../../mfc/reference/colelinksdialog-class.md)
