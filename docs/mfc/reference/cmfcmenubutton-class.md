---
title: CMFCMenuButton 类
ms.date: 07/15/2019
f1_keywords:
- CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::PreTranslateMessage
- AFXMENUBUTTON/CMFCMenuButton::SizeToContent
- AFXMENUBUTTON/CMFCMenuButton::m_bOSMenu
- AFXMENUBUTTON/CMFCMenuButton::m_bRightArrow
- AFXMENUBUTTON/CMFCMenuButton::m_bStayPressed
- AFXMENUBUTTON/CMFCMenuButton::m_hMenu
- AFXMENUBUTTON/CMFCMenuButton::m_nMenuResult
- AFXMENUBUTTON/CMFCMenuButton::m_bDefaultClick
helpviewer_keywords:
- CMFCMenuButton [MFC], CMFCMenuButton
- CMFCMenuButton [MFC], PreTranslateMessage
- CMFCMenuButton [MFC], SizeToContent
- CMFCMenuButton [MFC], m_bOSMenu
- CMFCMenuButton [MFC], m_bRightArrow
- CMFCMenuButton [MFC], m_bStayPressed
- CMFCMenuButton [MFC], m_hMenu
- CMFCMenuButton [MFC], m_nMenuResult
- CMFCMenuButton [MFC], m_bDefaultClick
ms.assetid: 53d3d459-1e5a-47c5-8b7f-2e61f6af5187
ms.openlocfilehash: 929fc1c8166f249fe3babc724b2c0bcd9cb99676
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369673"
---
# <a name="cmfcmenubutton-class"></a>CMFCMenuButton 类

在用户菜单选项上显示弹出菜单和报表的按钮。

## <a name="syntax"></a>语法

```
class CMFCMenuButton : public CMFCButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC菜单按钮：CMFC菜单按钮](#cmfcmenubutton)|构造 `CMFCMenuButton` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCMenuButton::PreTranslateMessage](#pretranslatemessage)|由框架调用，在发送窗口消息之前进行转换。 （重写 `CMFCButton::PreTranslateMessage`。）|
|[CMFCMenu按钮：：大小到内容](#sizetocontent)|根据按钮的文本和图像大小更改按钮的大小。|

### <a name="data-members"></a>数据成员

|名称|说明|
|----------|-----------------|
|[CMFC菜单按钮：：m_bOSMenu](#m_bosmenu)|指定是显示默认系统弹出菜单还是使用[CContextMenuManager：：TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu)。|
|[CMFC菜单按钮：：m_bRightArrow](#m_brightarrow)|指定弹出菜单是显示在按钮的下方还是右侧。|
|[CMFC菜单按钮：m_bStayPressed](#m_bstaypressed)|指定菜单按钮在用户释放按钮后是否更改其状态。|
|[CMFC菜单按钮：m_hMenu](#m_hmenu)|附加 Windows 菜单的句柄。|
|[CMFC菜单按钮：：m_nMenuResult](#m_nmenuresult)|指示用户从弹出式菜单中选择的项的标识符。|
|[CMFC菜单按钮：：m_bDefaultClick](#m_bdefaultclick)| 允许默认（按钮文本/图像）处理。|

## <a name="remarks"></a>备注

类`CMFCMenuButton`派生自[CMFCButton 类，而 CMFCButton 类](../../mfc/reference/cmfcbutton-class.md)则派生自[CButton 类](../../mfc/reference/cbutton-class.md)。 因此，您可以在代码中使用`CMFCMenuButton`与 使用`CButton`相同的方式使用 。

创建 时`CMFCMenuButton`，必须将句柄传递到关联的弹出式菜单。 接下来，调用 函数`CMFCMenuButton::SizeToContent`。 `CMFCMenuButton::SizeToContent`检查按钮大小是否足以包含指向弹出窗口显示位置的箭头，即按钮下方或右侧。

## <a name="example"></a>示例

下面的示例演示如何设置附加到按钮的菜单的句柄，根据按钮的文本和图像大小调整按钮的大小，以及设置框架显示的弹出式菜单。 此代码段是["新控件"示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#38](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#39](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)

## <a name="requirements"></a>要求

**标题：** afxmenu按钮.h

## <a name="cmfcmenubuttoncmfcmenubutton"></a><a name="cmfcmenubutton"></a>CMFC菜单按钮：CMFC菜单按钮

构造新的[CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)对象。

```
CMFCMenuButton();
```

## <a name="cmfcmenubuttonm_bosmenu"></a><a name="m_bosmenu"></a>CMFC菜单按钮：：m_bOSMenu

一个布尔成员变量，指示框架显示的弹出菜单。

```
BOOL m_bOSMenu;
```

### <a name="remarks"></a>备注

如果`m_bOSMenu`为 TRUE，则框架将调用`TrackPopupMenu`此对象的继承方法。 否则，框架将调用[CContextMenuManager：：跟踪弹出菜单](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu)。

## <a name="cmfcmenubuttonm_brightarrow"></a><a name="m_brightarrow"></a>CMFC菜单按钮：：m_bRightArrow

指示弹出菜单位置的布尔成员变量。

```
BOOL m_bRightArrow;
```

### <a name="remarks"></a>备注

当用户按下菜单按钮时，应用程序将显示一个弹出式菜单。 框架将在按钮下方或按钮右侧显示弹出式菜单。 该按钮还有一个小箭头，指示弹出菜单的显示位置。 如果`m_bRightArrow`为 TRUE，则框架将显示按钮右侧的弹出式菜单。 否则，它会在按钮下显示弹出式菜单。

## <a name="cmfcmenubuttonm_bstaypressed"></a><a name="m_bstaypressed"></a>CMFC菜单按钮：m_bStayPressed

Boolean 成员变量，指示用户从弹出式菜单中进行选择时菜单按钮是否显示按下。

```
BOOL m_bStayPressed;
```

### <a name="remarks"></a>备注

如果`m_bStayPressed`成员为 FALSE，则当使用单击该按钮时，菜单按钮不会按下。 在这种情况下，框架仅显示弹出式菜单。

如果`m_bStayPressed`成员为 TRUE，则当用户单击该按钮时，将按下菜单按钮。 它保持按下，直到用户关闭弹出菜单后，通过选择或取消。

## <a name="cmfcmenubuttonm_hmenu"></a><a name="m_hmenu"></a>CMFC菜单按钮：m_hMenu

附加菜单的句柄。

```
HMENU m_hMenu;
```

### <a name="remarks"></a>备注

当用户单击菜单按钮时，框架将显示此成员变量指示的菜单。

## <a name="cmfcmenubuttonm_nmenuresult"></a><a name="m_nmenuresult"></a>CMFC菜单按钮：：m_nMenuResult

指示用户从弹出式菜单中选择哪个项的整数。

```
int m_nMenuResult;
```

### <a name="remarks"></a>备注

如果用户取消菜单而不进行选择或发生错误，则此成员变量的值为零。

## <a name="cmfcmenubuttonm_bdefaultclick"></a><a name="m_bdefaultclick"></a>CMFC菜单按钮：：m_bDefaultClick

允许默认处理按钮上的文本或图像。

```
BOOL  m_bDefaultClick;
```

### <a name="remarks"></a>备注

将m_bDefaultClick设置为 false 会导致按钮在单击按钮上的任意位置时显示菜单。

## <a name="cmfcmenubuttonm_nmenuresult"></a><a name="m_nmenuresult"></a>CMFC菜单按钮：：m_nMenuResult

指示用户从弹出式菜单中选择哪个项的整数。

```
int m_nMenuResult;
```

### <a name="remarks"></a>备注

## <a name="cmfcmenubuttonpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCMenu按钮：:P重新翻译消息

由框架调用，在发送窗口消息之前进行转换。

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>参数

*pMsg*<br/>
[在]指向包含要处理的消息的[MSG](/windows/win32/api/winuser/ns-winuser-msg)结构。

### <a name="return-value"></a>返回值

如果邮件已翻译且不应发送，则非零;0 如果邮件未翻译，则应调度。

### <a name="remarks"></a>备注

## <a name="cmfcmenubuttonsizetocontent"></a><a name="sizetocontent"></a>CMFCMenu按钮：：大小到内容

根据按钮的文本大小和图像大小更改按钮的大小。

```
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```

### <a name="parameters"></a>参数

*bCalcOnly*<br/>
[在]一个布尔参数，指示此方法是否调整按钮的大小。

### <a name="return-value"></a>返回值

指定按钮新[大小的 CSize](../../atl-mfc-shared/reference/csize-class.md)对象。

### <a name="remarks"></a>备注

如果调用此函数，并且*bCalcOnly*为`SizeToContent`TRUE，则仅计算按钮的新大小。

计算按钮的新大小以适合按钮文本、图像和箭头。 框架还增加了预定义的边距为 10 像素的水平边和 5 像素的垂直边。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton 类](../../mfc/reference/cmfcbutton-class.md)
