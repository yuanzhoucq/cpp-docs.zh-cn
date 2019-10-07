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
ms.openlocfilehash: d7c23cbda0a5af4dc3fa6b2d9f59497acc9bf5ff
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505214"
---
# <a name="cmfcmenubutton-class"></a>CMFCMenuButton 类

在用户菜单选项上显示弹出菜单和报表的按钮。

## <a name="syntax"></a>语法

```
class CMFCMenuButton : public CMFCButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCMenuButton：： CMFCMenuButton](#cmfcmenubutton)|构造 `CMFCMenuButton` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCMenuButton::PreTranslateMessage](#pretranslatemessage)|由框架调用，用于在调度窗口消息之前对其进行转换。 （重写 `CMFCButton::PreTranslateMessage`。）|
|[CMFCMenuButton::SizeToContent](#sizetocontent)|根据按钮的文本和图像大小更改按钮的大小。|

### <a name="data-members"></a>数据成员

|名称|描述|
|----------|-----------------|
|[CMFCMenuButton::m_bOSMenu](#m_bosmenu)|指定是显示默认系统弹出菜单还是使用[CContextMenuManager：： TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu)。|
|[CMFCMenuButton::m_bRightArrow](#m_brightarrow)|指定是否在按钮的下方或右侧显示弹出菜单。|
|[CMFCMenuButton::m_bStayPressed](#m_bstaypressed)|指定菜单按钮在用户释放按钮后是否更改其状态。|
|[CMFCMenuButton::m_hMenu](#m_hmenu)|附加的 Windows 菜单的句柄。|
|[CMFCMenuButton::m_nMenuResult](#m_nmenuresult)|指示用户从弹出菜单中选择的项的标识符。|
|[CMFCMenuButton::m_bDefaultClick](#m_bdefaultclick)| 允许处理默认值（按钮文本/图像）。|

## <a name="remarks"></a>备注

该类派生自[CMFCButton 类](../../mfc/reference/cmfcbutton-class.md)，后者又派生自[CButton 类。](../../mfc/reference/cbutton-class.md) `CMFCMenuButton` 因此，您可以使用`CMFCMenuButton`与使用`CButton`相同的方法在代码中使用。

创建`CMFCMenuButton`时，必须将句柄传入关联的弹出菜单。 接下来，调用函数`CMFCMenuButton::SizeToContent`。 `CMFCMenuButton::SizeToContent`检查按钮大小是否足以包含一个箭头，该箭头指向弹出窗口将出现的位置（即，在按钮的下方或右侧）。

## <a name="example"></a>示例

下面的示例演示如何设置附加到按钮的菜单的句柄，根据按钮的文本和图像大小调整按钮的大小，以及设置框架显示的弹出菜单。 此代码片段是[新控件示例](../../overview/visual-cpp-samples.md)的一部分。

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

**标头：** afxmenubutton

##  <a name="cmfcmenubutton"></a>CMFCMenuButton：： CMFCMenuButton

构造一个新的[CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)对象。

```
CMFCMenuButton();
```

##  <a name="m_bosmenu"></a>CMFCMenuButton：： m_bOSMenu

布尔成员变量，指示框架显示的弹出菜单。

```
BOOL m_bOSMenu;
```

### <a name="remarks"></a>备注

如果`m_bOSMenu`为 TRUE，则框架将为此`TrackPopupMenu`对象调用继承的方法。 否则，框架将调用[CContextMenuManager：： TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu)。

##  <a name="m_brightarrow"></a>CMFCMenuButton：： m_bRightArrow

布尔成员变量，指示弹出菜单的位置。

```
BOOL m_bRightArrow;
```

### <a name="remarks"></a>备注

当用户按下菜单按钮时，应用程序会显示一个弹出菜单。 该框架将在按钮或按钮的右侧显示弹出菜单。 该按钮还具有一个指示弹出菜单显示位置的小箭头。 如果`m_bRightArrow`为 TRUE，则框架将在按钮右侧显示弹出菜单。 否则，它会在按钮下显示弹出菜单。

##  <a name="m_bstaypressed"></a>CMFCMenuButton：： m_bStayPressed

布尔成员变量，指示当用户从弹出菜单中进行选择时，菜单按钮是否显示为按下状态。

```
BOOL m_bStayPressed;
```

### <a name="remarks"></a>备注

`m_bStayPressed`如果成员为 FALSE，则当使用单击按钮时，菜单按钮不会被按下。 在这种情况下，框架只显示弹出菜单。

`m_bStayPressed`如果成员为 TRUE，则当用户单击按钮时，菜单按钮将变为按下状态。 在用户关闭弹出菜单之后，可以通过选择或取消来保持按下状态。

##  <a name="m_hmenu"></a>CMFCMenuButton：： m_hMenu

附加菜单的句柄。

```
HMENU m_hMenu;
```

### <a name="remarks"></a>备注

当用户单击菜单按钮时，框架会显示此成员变量所指示的菜单。

##  <a name="m_nmenuresult"></a>CMFCMenuButton：： m_nMenuResult

一个整数，指示用户从弹出菜单中选择的项。

```
int m_nMenuResult;
```

### <a name="remarks"></a>备注

如果用户取消菜单而不进行选择或出现错误，则此成员变量的值为零。

##  <a name="m_bdefaultclick"></a>CMFCMenuButton：： m_bDefaultClick

允许在按钮上默认处理文本或图像。

```
BOOL  m_bDefaultClick;
```

### <a name="remarks"></a>备注

如果将 m_bDefaultClick 设置为 false，则在单击该按钮上的任意位置时，按钮将显示该菜单。

##  <a name="m_nmenuresult"></a>CMFCMenuButton：： m_nMenuResult

一个整数，指示用户从弹出菜单中选择的项。

```
int m_nMenuResult;
```

### <a name="remarks"></a>备注

##  <a name="pretranslatemessage"></a>CMFCMenuButton：:P reTranslateMessage

由框架调用，用于在调度窗口消息之前对其进行转换。

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>参数

*pMsg*<br/>
中指向包含要处理的[消息的消息结构。](/windows/win32/api/winuser/ns-winuser-msg)

### <a name="return-value"></a>返回值

如果消息已转换且不应被调度，则为非零值;如果消息未翻译并且应被调度，则为0。

### <a name="remarks"></a>备注

##  <a name="sizetocontent"></a>CMFCMenuButton：： System.windows.window.sizetocontent

根据按钮的文本大小和图像大小更改按钮大小。

```
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```

### <a name="parameters"></a>参数

*bCalcOnly*<br/>
中布尔型参数，指示此方法是否调整按钮大小。

### <a name="return-value"></a>返回值

一个[CSize](../../atl-mfc-shared/reference/csize-class.md)对象，指定按钮的新大小。

### <a name="remarks"></a>备注

如果调用此函数并且*bCalcOnly*为 TRUE， `SizeToContent`则将只计算按钮的新大小。

此按钮的新大小将计算为适合按钮文本、图像和箭头。 该框架还为水平边缘和垂直边缘添加了10个像素的预定义边距和5个像素。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton 类](../../mfc/reference/cmfcbutton-class.md)
