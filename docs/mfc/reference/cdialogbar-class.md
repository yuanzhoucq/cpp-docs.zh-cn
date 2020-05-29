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
ms.openlocfilehash: cf9a2658807959108b3bb0af672d4c1835b58bc5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375674"
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
|[C对话栏：CDialog栏](#cdialogbar)|构造 `CDialogBar` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDialog栏：创建](#create)|创建 Windows 对话框栏并将其附加到`CDialogBar`对象。|

## <a name="remarks"></a>备注

对话框栏类似于对话框，因为它包含用户可以在中间选项卡的标准 Windows 控件。 另一个相似之处是创建一个对话框模板来表示对话框栏。

创建和使用对话框栏类似于创建和使用`CFormView`对象。 首先，使用[对话框编辑器](../../windows/dialog-editor.md)定义具有样式WS_CHILD没有其他样式的对话框模板。 模板不能具有样式WS_VISIBLE。 在应用程序代码中，调用构造函数构造对象，`CDialogBar`然后调用`Create`以创建对话框栏窗口并将其附加到`CDialogBar`对象。

有关 的详细信息`CDialogBar`，请参阅文章[对话框条](../../mfc/dialog-bars.md)[和技术说明 31](../../mfc/tn031-control-bars.md)，控制栏。

> [!NOTE]
> 在当前版本中，`CDialogBar`对象无法承载 Windows 窗体控件。 有关可视化C++中的 Windows 窗体控件的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[C控制栏](../../mfc/reference/ccontrolbar-class.md)

`CDialogBar`

## <a name="requirements"></a>要求

**标题：** afxext.h

## <a name="cdialogbarcdialogbar"></a><a name="cdialogbar"></a>C对话栏：CDialog栏

构造 `CDialogBar` 对象。

```
CDialogBar();
```

## <a name="cdialogbarcreate"></a><a name="create"></a>CDialog栏：创建

加载 或`lpszTemplateName``nIDTemplate`指定的对话框资源模板，创建对话框栏窗口，设置其样式，并将其与`CDialogBar`对象关联。

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

*pparentwnd*<br/>
指向父`CWnd`对象的指针。

*lpszTemplate 名称*<br/>
指向`CDialogBar`对象的对话框资源模板名称的指针。

*nStyle*<br/>
工具栏样式。 支持的其他工具栏样式包括：

- CBRS_TOP控制栏位于框架窗口的顶部。

- CBRS_BOTTOM控制栏位于框架窗口的底部。

- CBRS_NOALIGN调整父控件栏的大小时，不会重新定位。

- CBRS_TOOLTIPS控制栏显示工具提示。

- CBRS_SIZE_DYNAMIC控制栏是动态的。

- CBRS_SIZE_FIXED控制栏已固定。

- CBRS_FLOATING控制栏是浮动的。

- CBRS_FLYBY 状态栏显示有关按钮的信息。

- CBRS_HIDE_INPLACE控件栏不向用户显示。

*nID*<br/>
对话框栏的控制 ID。

*nIDTemplate*<br/>
`CDialogBar`对象的对话框模板的资源 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

如果指定CBRS_TOP或CBRS_BOTTOM对齐样式，则对话框栏的宽度是框架窗口的宽度，其高度是*nIDTemplate*指定的资源。 如果指定CBRS_LEFT或CBRS_RIGHT对齐样式，则对话框栏的高度是框架窗口的高度，其宽度是*nIDTemplate*指定的资源的高度。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 样品 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CControlBar Class](../../mfc/reference/ccontrolbar-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CFormView 类](../../mfc/reference/cformview-class.md)<br/>
[CControlBar Class](../../mfc/reference/ccontrolbar-class.md)
