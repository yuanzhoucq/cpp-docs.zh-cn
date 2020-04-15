---
title: CMFCKeyMapDialog 类
ms.date: 11/04/2016
f1_keywords:
- CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::DoModal
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::FormatItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::GetCommandKeys
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnInsertItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnPrintHeader
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnPrintItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnSetColumns
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::PrintKeyMap
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::SetColumnsWidth
helpviewer_keywords:
- CMFCKeyMapDialog [MFC], CMFCKeyMapDialog
- CMFCKeyMapDialog [MFC], DoModal
- CMFCKeyMapDialog [MFC], FormatItem
- CMFCKeyMapDialog [MFC], GetCommandKeys
- CMFCKeyMapDialog [MFC], OnInsertItem
- CMFCKeyMapDialog [MFC], OnPrintHeader
- CMFCKeyMapDialog [MFC], OnPrintItem
- CMFCKeyMapDialog [MFC], OnSetColumns
- CMFCKeyMapDialog [MFC], PrintKeyMap
- CMFCKeyMapDialog [MFC], SetColumnsWidth
ms.assetid: 5feb4942-d636-462d-a162-0104dd320f4e
ms.openlocfilehash: 22aa006ce214ca720192bb761e2ff2b35a64fce3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374411"
---
# <a name="cmfckeymapdialog-class"></a>CMFCKeyMapDialog 类

类`CMFCKeyMapDialog`支持将命令映射到键盘上的键的控件。

## <a name="syntax"></a>语法

```
class CMFCKeyMapDialog : public CDialogEx
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC键映射对话：：CMFC键映射对话](#cmfckeymapdialog)|构造 `CMFCKeyMapDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC键映射对话：:Do模态](#domodal)|显示键盘映射对话框。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CMFC键映射对话：：格式项目](#formatitem)|由框架调用以生成描述密钥映射的字符串。 默认情况下，字符串包含命令名称、使用的快捷键和快捷键说明。|
|[CMFC键映射对话：：获取命令密钥](#getcommandkeys)|检索包含与指定命令关联的快捷键列表的字符串。|
|[CMFC键映射对话：：插入项目](#oninsertitem)|在将新项目插入支持键盘映射控件的内部列表控件之前，由框架调用。|
|[CMFC键映射对话：：在打印标题上](#onprintheader)|由框架调用在新页面上打印键盘映射的标头。|
|[CMFC键映射对话：：在打印项目](#onprintitem)|由框架调用以打印键盘映射项。|
|[CMFC键映射对话：：打开列](#onsetcolumns)|框架调用，为支持键盘映射控件的内部列表控件中的列设置标题。|
|[CMFC键映射对话：:PrintKeyMap](#printkeymap)|当用户单击 **"打印"** 按钮时，由框架调用。|
|[CMFC键映射对话：：设置列宽度](#setcolumnswidth)|由框架调用，以设置支持键盘映射控件的内部列表控件中的列的宽度。|

## <a name="remarks"></a>备注

使用`CMFCKeyMapDialog`类实现可调整大小的键盘映射对话框。 该对话框使用列表视图控件来显示键盘快捷键及其关联的命令。

要在应用程序中`CMFCKeyMapDialog`使用 类，请将指向主框架窗口的指针作为参数传递给`CMFCKeyMapDialog`构造函数。 然后调用`DoModal`方法以启动模态对话框。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCKeyMapDialog](../../mfc/reference/cmfckeymapdialog-class.md)

## <a name="requirements"></a>要求

**标题：** afxkeymapdialog.h

## <a name="cmfckeymapdialogcmfckeymapdialog"></a><a name="cmfckeymapdialog"></a>CMFC键映射对话：：CMFC键映射对话

构造 `CMFCKeyMapDialog` 对象。

```
CMFCKeyMapDialog(
    CFrameWnd* pWndParentFrame,
    BOOL bEnablePrint=FALSE);
```

### <a name="parameters"></a>参数

*pwnd 父框架*<br/>
[在]指向对象的父窗口的`CMFCKeyMapDialog`指针。

*bEnablePrint*<br/>
[在]如果可以打印快捷键列表，则为 TRUE;否则，FALSE。 默认值为 FALSE。

### <a name="remarks"></a>备注

### <a name="example"></a>示例

下面的示例演示如何构造`CMFCKeyMapDialog`类的对象。 此示例是[可视化工作室演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#21](../../mfc/codesnippet/cpp/cmfckeymapdialog-class_1.cpp)]

## <a name="cmfckeymapdialogdomodal"></a><a name="domodal"></a>CMFC键映射对话：:Do模态

显示键盘映射对话框。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

传递给[CDialog：：结束对话](../../mfc/reference/cdialog-class.md#enddialog)方法的已签名整数，如 IDOK 或 IDCANCEL。 该方法依次关闭对话框。 有关详细信息，请参阅[CDialog：:Do 模态](../../mfc/reference/cdialog-class.md#domodal)。

### <a name="remarks"></a>备注

键盘映射对话框允许您选择和分配快捷键到各种类别的命令。 此外，您可以将选定的快捷键及其说明复制到剪贴板。

## <a name="cmfckeymapdialogformatitem"></a><a name="formatitem"></a>CMFC键映射对话：：格式项目

由框架调用以生成描述密钥映射的字符串。 默认情况下，字符串包含命令名称、使用的快捷键和快捷键说明。

```
virtual CString FormatItem(int nItem) const;
```

### <a name="parameters"></a>参数

*nItem*<br/>
[在]键映射内部列表中项的零基索引。

### <a name="return-value"></a>返回值

包含`CString`格式化项文本的对象。

### <a name="remarks"></a>备注

## <a name="cmfckeymapdialoggetcommandkeys"></a><a name="getcommandkeys"></a>CMFC键映射对话：：获取命令密钥

检索字符串值。 该字符串包含与指定命令关联的快捷键列表。

```
virtual CString GetCommandKeys(UINT uiCmdID) const;
```

### <a name="parameters"></a>参数

*乌伊CmdID*<br/>
[在]命令 ID。

### <a name="return-value"></a>返回值

与指定命令关联的快捷键的分号分隔 （';'' 列表）。

### <a name="remarks"></a>备注

## <a name="cmfckeymapdialogoninsertitem"></a><a name="oninsertitem"></a>CMFC键映射对话：：插入项目

在将新项目插入支持键盘映射控件的内部列表控件之前，由框架调用。

```
virtual void OnInsertItem(
    CMFCToolBarButton* pButton,
    int nItem);
```

### <a name="parameters"></a>参数

*pButton*<br/>
[在]指向工具栏按钮的指针，用于将键盘键组合映射到命令名称和说明。 键映射项存储在内部列表控件中。

*nItem*<br/>
[在]一个基于零的索引，用于指定在内部列表控件中插入新键映射项的位置。

### <a name="remarks"></a>备注

## <a name="cmfckeymapdialogonprintheader"></a><a name="onprintheader"></a>CMFC键映射对话：：在打印标题上

由框架调用在新页面上打印键盘映射的标头。

```
virtual int OnPrintHeader(
    CDC& dc,
    int nPage,
    int cx) const;
```

### <a name="parameters"></a>参数

*直流*<br/>
[在]打印机的设备上下文。

*nPage*<br/>
[在]要打印的页码。

*残雪*<br/>
[在]标题的水平偏移（以像素为单位）。

### <a name="return-value"></a>返回值

如果成功，则打印文本的高度。 有关详细信息，请参阅[CDC：:DrawText](../../mfc/reference/cdc-class.md#drawtext)的返回值部分。

### <a name="remarks"></a>备注

框架使用此方法打印键盘映射。 默认情况下，此方法打印页码、应用程序名称和对话框标题。

## <a name="cmfckeymapdialogonprintitem"></a><a name="onprintitem"></a>CMFC键映射对话：：在打印项目

由框架调用以打印键盘映射项。

```
virtual int OnPrintItem(
    CDC& dc,
    int nItem,
    int y,
    int cx,
    BOOL bCalcHeight) const;
```

### <a name="parameters"></a>参数

*直流*<br/>
[在]打印机的设备上下文。

*nItem*<br/>
[在]要打印的项的零基索引。

*Y*<br/>
[在]页面顶部和项目位置之间的垂直偏移。

*残雪*<br/>
[在]页面左侧和项目位置之间的水平偏移。

*bCalcHeight*<br/>
[在]TRUE 以计算打印项目的最佳高度;FALSE 可截截打印项，使其适合默认空间。

### <a name="return-value"></a>返回值

打印项目的高度。

### <a name="remarks"></a>备注

框架调用此方法来打印键映射对话框项。 默认情况下，此方法打印项的命令名称、快捷键和命令说明。

## <a name="cmfckeymapdialogonsetcolumns"></a><a name="onsetcolumns"></a>CMFC键映射对话：：打开列

框架调用，为支持键盘映射控件的内部列表控件中的列设置标题。

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>备注

默认情况下，此方法从三个资源获取列的标题。 命令列标题来自IDS_AFXBARRES_COMMAND，键列标题来自IDS_AFXBARRES_KEYS，描述列标题来自IDS_AFXBARRES_DESCRIPTION。

## <a name="cmfckeymapdialogprintkeymap"></a><a name="printkeymap"></a>CMFC键映射对话：:PrintKeyMap

当用户单击 **"打印"** 按钮时，由框架调用。

```
virtual void PrintKeyMap();
```

### <a name="remarks"></a>备注

该方法`PrintKeyMap`打印键映射。 它启动新的打印作业，然后反复调用[CMFCKeyMapDialog：：在打印标题](#onprintheader)和[CMFCKeyMapDialog：：在打印项目](#onprintitem)方法，直到打印所有键映射。

## <a name="cmfckeymapdialogsetcolumnswidth"></a><a name="setcolumnswidth"></a>CMFC键映射对话：：设置列宽度

由框架调用，以设置支持键盘映射控件的内部列表控件中的列的宽度。

```
virtual void SetColumnsWidth();
```

### <a name="remarks"></a>备注

此方法将内部列表控件的列设置为默认宽度。 首先，计算快捷键列的宽度。 然后，剩余宽度的三分之一分配给命令列，其余三分之二分配给描述列。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CKeyboardManager 类](../../mfc/reference/ckeyboardmanager-class.md)
