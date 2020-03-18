---
title: CDialogBar 类
ms.date: 11/04/2016
f1_keywords:
- CDialogBar
- AFXEXT/CDialogBar
- AFXEXT/CDialogBar::CDialogBar
- AFXEXT/CDialogBar::Create
helpviewer_keywords:
- CDialogBar [MFC], CDialogBar
- CDialogBar [MFC], Create
ms.assetid: da2f7a30-970c-44e3-87f0-6094bd002cab
ms.openlocfilehash: af84c5239a9cb3cbddb1ab4f0230e5b1a3373573
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425957"
---
# <a name="cdialogbar-class"></a>CDialogBar 类

提供控件条中的 Windows 无模式对话框功能。

## <a name="syntax"></a>语法

```
class CDialogBar : public CControlBar
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CDialogBar：： CDialogBar](#cdialogbar)|构造 `CDialogBar` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDialogBar：： Create](#create)|创建一个 Windows 对话栏并将其附加到 `CDialogBar` 对象上。|

## <a name="remarks"></a>备注

对话栏类似于一个对话框，其中包含用户可在两者之间切换的标准 Windows 控件。 另一个相似性是创建对话框模板来表示对话栏。

创建和使用对话栏类似于创建和使用 `CFormView` 对象。 首先，使用 "[对话框编辑器](../../windows/dialog-editor.md)" 定义样式 WS_CHILD 的对话框模板，而不是其他样式。 模板不能具有 WS_VISIBLE 样式。 在应用程序代码中，调用构造函数以构造 `CDialogBar` 对象，然后调用 `Create` 以创建对话框窗口，并将其附加到 `CDialogBar` 对象。

有关 `CDialogBar`的详细信息，请参阅文章[对话框](../../mfc/dialog-bars.md)和[技术说明 31](../../mfc/tn031-control-bars.md)，控件条。

> [!NOTE]
>  在当前版本中，`CDialogBar` 对象无法承载 Windows 窗体控件。 有关视觉对象C++中 Windows 窗体控件的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CDialogBar`

## <a name="requirements"></a>要求

**标头：** afxext。h

##  <a name="cdialogbar"></a>CDialogBar：： CDialogBar

构造 `CDialogBar` 对象。

```
CDialogBar();
```

##  <a name="create"></a>CDialogBar：： Create

加载 `lpszTemplateName` 或 `nIDTemplate`指定的对话框资源模板，创建对话框窗口，设置其样式，并将其与 `CDialogBar` 对象相关联。

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

### <a name="parameters"></a>parameters

*pParentWnd*<br/>
指向父级 `CWnd` 对象的指针。

*lpszTemplateName*<br/>
一个指针，指向 `CDialogBar` 对象的对话框资源模板的名称。

*nStyle*<br/>
工具栏样式。 支持的其他工具栏样式包括：

- CBRS_TOP 控件条位于框架窗口的顶部。

- CBRS_BOTTOM 控件条位于框架窗口的底部。

- 调整父级大小时，不会重新定位 CBRS_NOALIGN 控件条。

- CBRS_TOOLTIPS 控件条显示工具提示。

- CBRS_SIZE_DYNAMIC 控件条是动态的。

- CBRS_SIZE_FIXED 控制条是固定的。

- CBRS_FLOATING 控件条浮动。

- CBRS_FLYBY 状态栏显示有关按钮的信息。

- 不向用户显示 CBRS_HIDE_INPLACE 控件条。

*nID*<br/>
对话栏的控件 ID。

*nIDTemplate*<br/>
`CDialogBar` 对象的对话框模板的资源 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

如果指定 CBRS_TOP 或 CBRS_BOTTOM 对齐样式，则对话栏的宽度为框架窗口的宽度，其高度为*nIDTemplate*指定的资源的高度。 如果指定 CBRS_LEFT 或 CBRS_RIGHT 对齐样式，则对话栏的高度为框架窗口的高度，其宽度为*nIDTemplate*指定的资源的宽度。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 示例 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CControlBar Class](../../mfc/reference/ccontrolbar-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CFormView 类](../../mfc/reference/cformview-class.md)<br/>
[CControlBar Class](../../mfc/reference/ccontrolbar-class.md)
