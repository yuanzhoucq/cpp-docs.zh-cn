---
title: CMFCPropertyGridToolTipCtrl 类
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Create
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Deactivate
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::GetLastRect
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Hide
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::SetTextMargin
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Track
helpviewer_keywords:
- CMFCPropertyGridToolTipCtrl [MFC], CMFCPropertyGridToolTipCtrl
- CMFCPropertyGridToolTipCtrl [MFC], Create
- CMFCPropertyGridToolTipCtrl [MFC], Deactivate
- CMFCPropertyGridToolTipCtrl [MFC], GetLastRect
- CMFCPropertyGridToolTipCtrl [MFC], Hide
- CMFCPropertyGridToolTipCtrl [MFC], SetTextMargin
- CMFCPropertyGridToolTipCtrl [MFC], Track
ms.assetid: 84b436e5-6695-4da0-9569-1a875e087711
ms.openlocfilehash: 94d75f914e5f7928d08dd2a87997ab02c4f16832
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361793"
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>CMFCPropertyGridToolTipCtrl 类

实现[CMFCPropertyGridCtrl 类](../../mfc/reference/cmfcpropertygridctrl-class.md)用于显示工具提示的工具提示控件。

## <a name="syntax"></a>语法

```
class CMFCPropertyGridToolTipCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|||
|-|-|
|名称|说明|
|[CMFC属性网格工具提示：：CMFC属性网格工具提示rl](#cmfcpropertygridtooltipctrl)|构造 `CMFCPropertyGridToolTipCtrl` 对象。|
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|析构函数。|

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|说明|
|[CMFC属性网格工具提示：：创建](#create)|为工具提示控件创建一个窗口。|
|[CMFC属性网格工具提示：:D激活](#deactivate)|停用并隐藏工具提示控件。|
|[CMFC财产网格工具提示：：获取最后](#getlastrect)|返回工具提示控件最后一个位置的坐标。|
|[CMFC属性网格工具提示：：隐藏](#hide)|隐藏工具提示控件。|
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|类[CWinApp](../../mfc/reference/cwinapp-class.md)在窗口消息发送到[翻译消息](/windows/win32/api/winuser/nf-winuser-translatemessage)和[调度消息](/windows/win32/api/winuser/nf-winuser-dispatchmessage)窗口功能之前，用于转换窗口消息。 （重写 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。）|
|[CMFC属性网格工具提示：：设置文本边缘](#settextmargin)|设置工具提示文本与工具提示窗口边框之间的间距。|
|[CMFC财产网格工具提示：：轨道](#track)|显示工具提示控件。|

## <a name="remarks"></a>备注

当指针位于属性名称上时，将显示工具提示。 [CMFC属性GridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)类显示一个工具提示，以便用户可以轻松阅读。 通常，工具提示的位置由指针的位置决定。 通过使用此类，工具提示将显示在属性名称上，类似于自然属性扩展，因此属性名称完全可见。

MFC 会自动创建此控件，并在[CMFC 属性网格Ctrl 类](../../mfc/reference/cmfcpropertygridctrl-class.md)中使用它。

## <a name="example"></a>示例

下面的示例演示如何构造`CMFCPropertyGridToolTipCtrl`类的对象以及如何显示工具提示控件。

[!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFC财产网格工具提示器](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)

## <a name="requirements"></a>要求

**标题：** afx属性网格tooltipctrl.h

## <a name="cmfcpropertygridtooltipctrlcmfcpropertygridtooltipctrl"></a><a name="cmfcpropertygridtooltipctrl"></a>CMFC属性网格工具提示：：CMFC属性网格工具提示rl

构造 `CMFCPropertyGridToolTipCtrl` 对象。

```
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```

## <a name="cmfcpropertygridtooltipctrlcreate"></a><a name="create"></a>CMFC属性网格工具提示：：创建

为工具提示控件创建一个窗口。

```
BOOL Create(CWnd* pWndParent);
```

### <a name="parameters"></a>参数

*pwnd 父级*<br/>
[在]指向父窗口的指针。

### <a name="return-value"></a>返回值

如果成功创建窗口，则为 TRUE;如果成功创建了窗口，则为 TRUE。否则，FALSE。

## <a name="cmfcpropertygridtooltipctrldeactivate"></a><a name="deactivate"></a>CMFC属性网格工具提示：:D激活

停用并隐藏工具提示控件。

```
void Deactivate();
```

### <a name="remarks"></a>备注

此方法将最后一个位置和文本设置为空值，以便将来对[CMFC 属性网格ToolTipCtrl的调用：跟踪](#track)显示工具提示。

## <a name="cmfcpropertygridtooltipctrlgetlastrect"></a><a name="getlastrect"></a>CMFC财产网格工具提示：：获取最后

返回工具提示控件最后一个位置的坐标。

```
void GetLastRect(CRect& rect) const;
```

### <a name="parameters"></a>参数

*矩形*<br/>
[出]包含工具提示控件的最后位置。

## <a name="cmfcpropertygridtooltipctrlhide"></a><a name="hide"></a>CMFC属性网格工具提示：：隐藏

隐藏工具提示控件。

```
void Hide();
```

## <a name="cmfcpropertygridtooltipctrlsettextmargin"></a><a name="settextmargin"></a>CMFC属性网格工具提示：：设置文本边缘

设置工具提示文本与工具提示窗口边框之间的间距。

```
void SetTextMargin(int nTextMargin);
```

### <a name="parameters"></a>参数

*nTextMargin*<br/>
[在]指定工具提示控件文本与工具提示窗口的边框之间的间距。 默认值为 10 像素。

## <a name="cmfcpropertygridtooltipctrltrack"></a><a name="track"></a>CMFC财产网格工具提示：：轨道

显示工具提示控件。

```
void Track(
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>参数

*矩形*<br/>
[在]指定工具提示控件的位置和大小。

*斯特文本*<br/>
[在]指定要在工具提示中显示的文本。

### <a name="remarks"></a>备注

此方法在*rect*指定的位置和大小处显示工具提示控件。 如果自上次调用此方法以来位置、大小和文本未更改，则此方法没有效果。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
