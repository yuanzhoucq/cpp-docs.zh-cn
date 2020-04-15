---
title: CFolderPickerDialog 类
ms.date: 03/27/2019
f1_keywords:
- CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog::CFolderPickerDialog
helpviewer_keywords:
- CFolderPickerDialog [MFC], CFolderPickerDialog
ms.assetid: 8db01684-dd1d-4e9c-989e-07a2318a8156
ms.openlocfilehash: ed3dc151060519bce216cf4a2f3d6559d6b8937e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373851"
---
# <a name="cfolderpickerdialog-class"></a>CFolderPickerDialog 类

CFolderPickerDialog 类在文件夹选取器模式下实现 CFileDialog。

## <a name="syntax"></a>语法

```
class CFolderPickerDialog : public CFileDialog;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[夹子拾取者对话：：~CFOLDERPicker对话](#_dtorcfolderpickerdialog)|析构函数。|
|[夹子选取器对话框：：CfolderPicker对话](#cfolderpickerdialog)|构造函数。|

## <a name="remarks"></a>备注

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[CFileDialog](../../mfc/reference/cfiledialog-class.md)

`CFolderPickerDialog`

## <a name="requirements"></a>要求

**标题：** afxdlgs.h

## <a name="cfolderpickerdialogcfolderpickerdialog"></a><a name="cfolderpickerdialog"></a>夹子选取器对话框：：CfolderPicker对话

构造函数。

```
explicit CFolderPickerDialog(
    LPCTSTR lpszFolder = NULL,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL,
    DWORD dwSize = 0);
```

### <a name="parameters"></a>参数

*lpszFolder*<br/>
初始文件夹。

dwFlags**<br/>
允许您自定义对话框的一个或多个标志的组合。

*pparentwnd*<br/>
指向对话框对象的父窗口或所有者窗口的指针。

*dwSize*<br/>
OPENFILENAME 结构的大小。

### <a name="remarks"></a>备注

## <a name="cfolderpickerdialogcfolderpickerdialog"></a><a name="_dtorcfolderpickerdialog"></a>夹子拾取者对话：：~CFOLDERPicker对话

析构函数。

```
virtual ~CFolderPickerDialog();
```

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
