---
title: CCommonDialog 类
ms.date: 11/04/2016
f1_keywords:
- CCommonDialog
- AFXDLGS/CCommonDialog
- AFXDLGS/CCommonDialog::CCommonDialog
helpviewer_keywords:
- CCommonDialog [MFC], CCommonDialog
ms.assetid: 1f68d65f-a0fd-4778-be22-ebbe51a95f95
ms.openlocfilehash: 853a4756df3b70f4f33deb7159b4d1aee610092c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369449"
---
# <a name="ccommondialog-class"></a>CCommonDialog 类

封装 Windows 公共对话框功能的类的基类。

## <a name="syntax"></a>语法

```
class CCommonDialog : public CDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C 公共对话：C 公共对话](#ccommondialog)|构造 `CCommonDialog` 对象。|

## <a name="remarks"></a>备注

以下类封装了 Windows 通用对话框的功能：

- [CFileDialog](../../mfc/reference/cfiledialog-class.md)

- [CFontDialog](../../mfc/reference/cfontdialog-class.md)

- [CColorDialog](../../mfc/reference/ccolordialog-class.md)

- [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)

- [CPrintDialog](../../mfc/reference/cprintdialog-class.md)

- [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md)

- [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)

- [COleDialog](../../mfc/reference/coledialog-class.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`CCommonDialog`

## <a name="requirements"></a>要求

**标题：** afxdlgs.h

## <a name="ccommondialogccommondialog"></a><a name="ccommondialog"></a>C 公共对话：C 公共对话

构造 `CCommonDialog` 对象。

```
explicit CCommonDialog(CWnd* pParentWnd);
```

### <a name="parameters"></a>参数

*pparentwnd*<br/>
指向对话框对象所属的父窗口或所有者窗口对象[（CWnd](../../mfc/reference/cwnd-class.md)类型）。 如果为 NULL，则对话框对象的父窗口将设置为主应用程序窗口。

### <a name="remarks"></a>备注

有关详细信息[，请参阅 CDialog：CDialog。](../../mfc/reference/cdialog-class.md#cdialog)

## <a name="see-also"></a>另请参阅

[CDialog 类](../../mfc/reference/cdialog-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[文件对话类](../../mfc/reference/cfiledialog-class.md)<br/>
[CFontDialog 类](../../mfc/reference/cfontdialog-class.md)<br/>
[CColorDialog 类](../../mfc/reference/ccolordialog-class.md)<br/>
[CPageSetupDialog 类](../../mfc/reference/cpagesetupdialog-class.md)<br/>
[CPrintDialog 类](../../mfc/reference/cprintdialog-class.md)<br/>
[CFindReplaceDialog 类](../../mfc/reference/cfindreplacedialog-class.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)
