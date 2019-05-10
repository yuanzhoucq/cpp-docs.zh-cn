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
ms.openlocfilehash: 435c91082fa901f0bc9726316f0358fc5a669b29
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396192"
---
# <a name="cfolderpickerdialog-class"></a>CFolderPickerDialog 类

CFolderPickerDialog 类实现文件夹选取器模式下的 CFileDialog。

## <a name="syntax"></a>语法

```
class CFolderPickerDialog : public CFileDialog;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CFolderPickerDialog::~CFolderPickerDialog](#_dtorcfolderpickerdialog)|析构函数。|
|[CFolderPickerDialog::CFolderPickerDialog](#cfolderpickerdialog)|构造函数。|

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

**标头：** afxdlgs.h

##  <a name="cfolderpickerdialog"></a>  CFolderPickerDialog::CFolderPickerDialog

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

*dwFlags*<br/>
可用于自定义对话框中的一个或多个标志的组合。

*pParentWnd*<br/>
指向对话框对象的父级或所有者窗口的指针。

*dwSize*<br/>
OPENFILENAME 结构的大小。

### <a name="remarks"></a>备注

##  <a name="_dtorcfolderpickerdialog"></a>  CFolderPickerDialog:: ~ CFolderPickerDialog

析构函数。

```
virtual ~CFolderPickerDialog();
```

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
