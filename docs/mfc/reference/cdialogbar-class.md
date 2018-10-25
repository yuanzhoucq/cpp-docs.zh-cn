---
title: CDialogBar 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDialogBar
- AFXEXT/CDialogBar
- AFXEXT/CDialogBar::CDialogBar
- AFXEXT/CDialogBar::Create
dev_langs:
- C++
helpviewer_keywords:
- CDialogBar [MFC], CDialogBar
- CDialogBar [MFC], Create
ms.assetid: da2f7a30-970c-44e3-87f0-6094bd002cab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dad3f7309d36f7233d871ea47a859c4e572140f6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065455"
---
# <a name="cdialogbar-class"></a>CDialogBar 类

提供控件条中的 Windows 无模式对话框功能。

## <a name="syntax"></a>语法

```
class CDialogBar : public CControlBar
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CDialogBar::CDialogBar](#cdialogbar)|构造 `CDialogBar` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDialogBar::Create](#create)|创建 Windows 对话栏并将其附加到`CDialogBar`对象。|

## <a name="remarks"></a>备注

对话栏类似于一个对话框，其中包含用户可以使用 tab 键之间的标准 Windows 控件。 另一种相似性就创建对话框模板来表示对话栏。

创建和使用对话栏是类似于创建和使用`CFormView`对象。 首先，使用[对话框编辑器](../../windows/dialog-editor.md)定义样式 WS_CHILD 的对话框模板和任何其他样式。 该模板不能 WS_VISIBLE 的样式。 在应用程序代码中，调用构造函数来构造`CDialogBar`对象，然后调用`Create`若要创建对话栏窗口，然后将其附加到`CDialogBar`对象。

有关详细信息`CDialogBar`，请参阅文章[对话栏](../../mfc/dialog-bars.md)并[技术说明 31](../../mfc/tn031-control-bars.md)，控件条。

> [!NOTE]
>  在当前版本中，`CDialogBar`对象不能承载 Windows 窗体控件。 有关 Visual c + + 的 Windows 窗体控件的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CDialogBar`

## <a name="requirements"></a>要求

**标头：** afxext.h

##  <a name="cdialogbar"></a>  CDialogBar::CDialogBar

构造 `CDialogBar` 对象。

```
CDialogBar();
```

##  <a name="create"></a>  CDialogBar::Create

加载指定的对话框资源模板`lpszTemplateName`或`nIDTemplate`、 创建对话栏窗口中，设置其样式，并将其与`CDialogBar`对象。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    LPCTSTR lpszTemplateName,
    UINT nStyle,
    UINT nID);

virtual BOOL Create(
    CWnd* pParentWnd,
    UINT nIDTemplate,
    UINT nStyle,
    UINT nID);
```

### <a name="parameters"></a>参数

*pParentWnd*<br/>
指向父`CWnd`对象。

*lpszTemplateName*<br/>
指向的目录名称`CDialogBar`对象的对话框资源模板。

*nStyle*<br/>
Styl toolbar。 支持的其他工具栏样式是：

- CBRS_TOP 控件条是在框架窗口的顶部。

- CBRS_BOTTOM 控件条是在框架窗口的底部。

- 父级重设大小时，CBRS_NOALIGN 控件栏不会重新定位。

- CBRS_TOOLTIPS 控件栏会显示工具提示。

- CBRS_SIZE_DYNAMIC 控件栏是动态的。

- CBRS_SIZE_FIXED 控件条被固定。

- 浮动 CBRS_FLOATING 控件条。

- CBRS_FLYBY 状态栏会显示按钮的信息。

- 不会向用户显示 CBRS_HIDE_INPLACE 控件条。

*nID*<br/>
对话栏控件 ID。

*nIDTemplate*<br/>
资源 ID`CDialogBar`对象的对话框模板。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

如果指定 CBRS_TOP 或 CBRS_BOTTOM 对齐样式，对话栏的宽度是框架窗口的窗体的高度是由指定的资源*nIDTemplate*。 如果指定 CBRS_LEFT 或 CBRS_RIGHT 对齐方式、 对话栏的高度为的框架窗口，其宽度为指定的资源的*nIDTemplate*。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]

## <a name="see-also"></a>请参阅

[MFC 示例 CTRLBARS](../../visual-cpp-samples.md)<br/>
[CControlBar 类](../../mfc/reference/ccontrolbar-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CFormView 类](../../mfc/reference/cformview-class.md)<br/>
[CControlBar 类](../../mfc/reference/ccontrolbar-class.md)
