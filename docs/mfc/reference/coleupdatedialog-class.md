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
ms.openlocfilehash: 150e78b7880a61343db21c3c787ffdd1f0b734a5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503170"
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
|[COleUpdateDialog::DoModal](#domodal)|在更新模式下显示 "**编辑链接**" 对话框。|

## <a name="remarks"></a>备注

有关特定于 OLE 的对话框的详细信息, 请参阅[ole 中](../../mfc/dialog-boxes-in-ole.md)的文章对话框。

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

**标头:** afxodlgs

##  <a name="coleupdatedialog"></a>COleUpdateDialog::COleUpdateDialog

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
确定是否要更新链接对象的标志。

*bUpdateEmbeddings*<br/>
确定是否要更新嵌入对象的标志。

*pParentWnd*<br/>
指向对话框对象所属的父对象或所有者窗口对象`CWnd`(类型为)。 如果为 NULL, 则对话框的父窗口将设置为主应用程序窗口。

### <a name="remarks"></a>备注

此函数仅`COleUpdateDialog`构造对象。 若要显示该对话框, 请调用[DoModal](../../mfc/reference/colelinksdialog-class.md#domodal)。 `COleLinksDialog`如果只想更新现有的链接或嵌入项, 则应使用此类, 而不是。

##  <a name="domodal"></a>COleUpdateDialog::D oModal

在更新模式下显示 "编辑链接" 对话框。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

对话框的完成状态。 以下值之一：

- 如果对话框成功返回, 则为 IDOK。

- 如果当前文档中没有任何链接或嵌入项需要更新, 则为 IDCANCEL。

- 如果发生错误, 则为 IDABORT。 如果返回 IDABORT, 则调用[COleDialog:: GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)成员函数以获取有关发生的错误类型的详细信息。 有关可能的错误的列表, 请参阅 Windows SDK 中的[OleUIEditLinks](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw)函数。

### <a name="remarks"></a>备注

除非用户选择 "取消" 按钮, 否则将更新所有链接和/或嵌入。

## <a name="see-also"></a>请参阅

[MFC 示例 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleLinksDialog 类](../../mfc/reference/colelinksdialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleLinksDialog 类](../../mfc/reference/colelinksdialog-class.md)
