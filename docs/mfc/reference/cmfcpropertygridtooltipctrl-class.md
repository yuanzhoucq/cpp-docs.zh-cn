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
ms.openlocfilehash: f1b6f626b5f9844c73cd2225a7d6311f5b2f7d4f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505097"
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>CMFCPropertyGridToolTipCtrl 类

实现[CMFCPropertyGridCtrl 类](../../mfc/reference/cmfcpropertygridctrl-class.md)用来显示工具提示的 tooltip 控件。

## <a name="syntax"></a>语法

```
class CMFCPropertyGridToolTipCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|||
|-|-|
|名称|描述|
|[CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl](#cmfcpropertygridtooltipctrl)|构造 `CMFCPropertyGridToolTipCtrl` 对象。|
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|析构函数。|

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|描述|
|[CMFCPropertyGridToolTipCtrl::Create](#create)|为 tooltip 控件创建窗口。|
|[CMFCPropertyGridToolTipCtrl::Deactivate](#deactivate)|停用并隐藏 tooltip 控件。|
|[CMFCPropertyGridToolTipCtrl::GetLastRect](#getlastrect)|返回 tooltip 控件的最后一个位置的坐标。|
|[CMFCPropertyGridToolTipCtrl::Hide](#hide)|隐藏 tooltip 控件。|
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|在将窗口消息发送到 [TranslateMessage](../../mfc/reference/cwinapp-class.md) 和 [DispatchMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) Windows 函数之前，由 [CWinApp](/windows/win32/api/winuser/nf-winuser-dispatchmessage) 类用于对此消息进行转换。 （重写 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。）|
|[CMFCPropertyGridToolTipCtrl::SetTextMargin](#settextmargin)|设置工具提示文本和工具提示窗口边框之间的间距。|
|[CMFCPropertyGridToolTipCtrl::Track](#track)|显示 tooltip 控件。|

## <a name="remarks"></a>备注

当指针停留在属性名称上时, 将显示工具提示。 [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)类将显示一个工具提示, 以便用户可以轻松阅读。 通常, 工具提示的位置由指针的位置确定。 使用此类时, 工具提示将显示在属性名称上并类似于自然的属性扩展, 因此属性名称完全可见。

MFC 会自动创建此控件并在[CMFCPropertyGridCtrl 类](../../mfc/reference/cmfcpropertygridctrl-class.md)中使用它。

## <a name="example"></a>示例

下面的示例演示如何构造`CMFCPropertyGridToolTipCtrl`类的对象, 以及如何显示 tooltip 控件。

[!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)

## <a name="requirements"></a>要求

**标头:** afxpropertygridtooltipctrl

##  <a name="cmfcpropertygridtooltipctrl"></a>CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl

构造 `CMFCPropertyGridToolTipCtrl` 对象。

```
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```

##  <a name="create"></a>CMFCPropertyGridToolTipCtrl:: Create

为 tooltip 控件创建窗口。

```
BOOL Create(CWnd* pWndParent);
```

### <a name="parameters"></a>参数

*pWndParent*<br/>
中指向父窗口的指针。

### <a name="return-value"></a>返回值

如果已成功创建窗口, 则为 TRUE;否则为 FALSE。

##  <a name="deactivate"></a>CMFCPropertyGridToolTipCtrl::D eactivate

停用并隐藏 tooltip 控件。

```
void Deactivate();
```

### <a name="remarks"></a>备注

此方法将最后一个位置和文本设置为空值, 以便以后对[CMFCPropertyGridToolTipCtrl:: Track](#track)的调用显示工具提示。

##  <a name="getlastrect"></a>CMFCPropertyGridToolTipCtrl::GetLastRect

返回 tooltip 控件的最后一个位置的坐标。

```
void GetLastRect(CRect& rect) const;
```

### <a name="parameters"></a>参数

*rect*<br/>
弄包含 tooltip 控件的最后一个位置。

##  <a name="hide"></a>CMFCPropertyGridToolTipCtrl:: Hide

隐藏 tooltip 控件。

```
void Hide();
```

##  <a name="settextmargin"></a>CMFCPropertyGridToolTipCtrl::SetTextMargin

设置工具提示文本和工具提示窗口边框之间的间距。

```
void SetTextMargin(int nTextMargin);
```

### <a name="parameters"></a>参数

*nTextMargin*<br/>
中指定 tooltip 控件文本和工具提示窗口的边框之间的间距。 默认值为10像素。

##  <a name="track"></a>CMFCPropertyGridToolTipCtrl:: Track

显示 tooltip 控件。

```
void Track(
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>参数

*rect*<br/>
中指定 tooltip 控件的位置和大小。

*strText*<br/>
中指定要在工具提示中显示的文本。

### <a name="remarks"></a>备注

此方法在由*rect*指定的位置和大小显示 tooltip 控件。 如果自上次调用此方法以来位置、大小和文本尚未更改, 则此方法不起作用。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
