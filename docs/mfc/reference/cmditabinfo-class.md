---
title: CMDITab信息类
ms.date: 11/04/2016
f1_keywords:
- CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo::Serialize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bAutoColor
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bDocumentMenu
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bEnableTabSwap
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bFlatFrame
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCloseButton
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCustomTooltips
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabIcons
- AFXMDICLIENTAREAWND/CMDITabInfo::m_nTabBorderSize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_style
- AFXMDICLIENTAREAWND/CMDITabInfo::m_tabLocation
helpviewer_keywords:
- CMDITabInfo [MFC], Serialize
- CMDITabInfo [MFC], m_bAutoColor
- CMDITabInfo [MFC], m_bDocumentMenu
- CMDITabInfo [MFC], m_bEnableTabSwap
- CMDITabInfo [MFC], m_bFlatFrame
- CMDITabInfo [MFC], m_bTabCloseButton
- CMDITabInfo [MFC], m_bTabCustomTooltips
- CMDITabInfo [MFC], m_bTabIcons
- CMDITabInfo [MFC], m_nTabBorderSize
- CMDITabInfo [MFC], m_style
- CMDITabInfo [MFC], m_tabLocation
ms.assetid: 988ae1b7-4f7f-4239-b88f-7e28b3291c5e
ms.openlocfilehash: 0d230d2a3401ab556adc1183f4c4210ec6ff3c29
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370032"
---
# <a name="cmditabinfo-class"></a>CMDITab信息类

该`CMDITabInfo`类用于将参数传递给[CMDIFrameWndEx：：启用MDITabbed组](../../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups)方法。 设置此类的成员以控制 MDI 选项卡式组的行为。

## <a name="syntax"></a>语法

```
class CMDITabInfo
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|`CMDITabInfo::CMDITabInfo`|默认构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMDITab信息：序列化](#serialize)|从存档读取该对象或将该对象写入存档。|

### <a name="data-members"></a>数据成员

|名称|说明|
|----------|-----------------|
|[CMDITab信息：m_bActiveTabCloseButton;](#m_bactivetabclosebutton_)|指定"**关闭**"按钮是否显示在活动选项卡的标签上。|
|[CMDITab信息：m_bAutoColor](#m_bautocolor)|指定是否为 MDI 选项卡着色。|
|[CMDITab信息：m_bDocumentMenu](#m_bdocumentmenu)|指定选项卡组是显示显示打开的文档列表的弹出菜单还是显示滚动按钮。|
|[CMDITab信息：m_bEnableTabSwap](#m_benabletabswap)|指定用户是否可以通过拖动交换选项卡的位置。|
|[CMDITab信息：m_bFlatFrame](#m_bflatframe)|指定选项卡是否具有平面框架。|
|[CMDITab信息：m_bTabCloseButton](#m_btabclosebutton)|指定每个选项卡标签是否显示 **"关闭"** 按钮。|
|[CMDITab信息：m_bTabCustomTooltips](#m_btabcustomtooltips)|指定是否启用了自定义工具提示。|
|[CMDITab信息：m_bTabIcons](#m_btabicons)|指定是否在 MDI 选项卡上显示图标。|
|[CMDITab信息：m_nTabBorderSize](#m_ntabbordersize)|指定每个选项卡窗口的边框大小。|
|[CMDITab信息：m_style](#m_style)|指定选项卡标签的样式。|
|[CMDITab信息：m_tabLocation](#m_tablocation)|指定选项卡标签是位于页面的顶部还是底部。|

## <a name="remarks"></a>备注

此类指定框架创建的 MDI 选项卡组的参数。

## <a name="example"></a>示例

下面的示例演示如何在类中`CMDITabInfo`设置各种成员变量的值。

[!code-cpp[NVC_MFC_MDITab#1](../../mfc/reference/codesnippet/cpp/cmditabinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CMDITabInfo](../../mfc/reference/cmditabinfo-class.md)

## <a name="requirements"></a>要求

**标题：** afxmdiclient 区域wnd.h

## <a name="cmditabinfom_bactivetabclosebutton"></a><a name="m_bactivetabclosebutton_"></a>CMDITab信息：m_bActiveTabCloseButton;

指定"**关闭**"按钮是否显示在活动选项卡的标签上。

```
BOOL m_bActiveTabCloseButton;
```

### <a name="remarks"></a>备注

如果为 TRUE，则活动选项卡的标签将显示"**关闭"** 按钮。 "**关闭**"按钮将从选项卡区域的右上角删除。 否则，活动选项卡的标签将不会显示 **"关闭"** 按钮。 "**关闭**"按钮将显示在选项卡区域的右上角。

## <a name="cmditabinfom_bautocolor"></a><a name="m_bautocolor"></a>CMDITab信息：m_bAutoColor

指定每个 MDI 选项卡是否具有自己的颜色。

```
BOOL m_bAutoColor;
```

### <a name="remarks"></a>备注

如果为 TRUE，则每个选项卡将有自己的颜色。 颜色集由 MFC 库管理。 否则，选项卡显示为白色。 默认值是 FALSE。

## <a name="cmditabinfom_bdocumentmenu"></a><a name="m_bdocumentmenu"></a>CMDITab信息：m_bDocumentMenu

指定每个选项卡是否显示一个弹出菜单，该菜单在选项卡区域的右边缘显示打开的文档列表。

```
BOOL m_bDocumentMenu;
```

### <a name="remarks"></a>备注

如果为 TRUE，则每个选项卡窗口都会显示一个弹出菜单，该菜单在选项卡区域的右边缘显示打开的文档的列表;如果为 TRUE，则显示一个弹出窗口。如果为 TRUE，则显示选项卡区域右侧打开的文档列表。否则，选项卡窗口将显示选项卡区域右边缘的滚动按钮。 默认值是 FALSE。

## <a name="cmditabinfom_benabletabswap"></a><a name="m_benabletabswap"></a>CMDITab信息：m_bEnableTabSwap

指定用户是否可以通过拖动交换选项卡的位置。

```
BOOL m_bEnableTabSwap;
```

### <a name="remarks"></a>备注

如果为 TRUE，则用户可以通过拖动选项卡来更改选项卡位置。 否则，用户无法更改选项卡位置。 默认值为 TRUE。

## <a name="cmditabinfom_bflatframe"></a><a name="m_bflatframe"></a>CMDITab信息：m_bFlatFrame

指定每个选项卡窗口是否具有平面框架。

```
BOOL m_bFlatFrame;
```

## <a name="cmditabinfom_btabclosebutton"></a><a name="m_btabclosebutton"></a>CMDITab信息：m_bTabCloseButton

指定每个选项卡窗口是否显示 **"关闭"** 按钮。

```
BOOL m_bTabCloseButton;
```

### <a name="remarks"></a>备注

如果为 TRUE，则每个选项卡窗口都会在选项卡的右边缘显示 **"关闭**"按钮。否则，不显示 **"关闭**"按钮。 默认值为 TRUE。

## <a name="cmditabinfom_btabcustomtooltips"></a><a name="m_btabcustomtooltips"></a>CMDITab信息：m_bTabCustomTooltips

指定选项卡是否显示工具提示。

```
BOOL m_bTabCustomTooltips;
```

### <a name="remarks"></a>备注

如果为 TRUE，则应用程序向主帧发送AFX_WM_ON_GET_TAB_TOOLTIP消息。 您可以使用ON_REGISTERED_MESSAGE宏来处理此消息。

## <a name="cmditabinfom_btabicons"></a><a name="m_btabicons"></a>CMDITab信息：m_bTabIcons

指定是否在 MDI 选项卡上显示图标。

```
BOOL m_bTabIcons;
```

### <a name="remarks"></a>备注

如果为 TRUE，则每个 MDI 选项卡上都会显示图标。否则，图标不会显示在选项卡上。 默认值是 FALSE。

## <a name="cmditabinfom_ntabbordersize"></a><a name="m_ntabbordersize"></a>CMDITab信息：m_nTabBorderSize

指定每个选项卡窗口的边框大小（以像素为单位）。

```
int m_nTabBorderSize;
```

### <a name="remarks"></a>备注

[CMFCVisualManager：getMDITabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize)返回默认值。

## <a name="cmditabinfom_style"></a><a name="m_style"></a>CMDITab信息：m_style

指定选项卡标签的样式。

```
CMFCTabCtrl::Style m_style
```

### <a name="remarks"></a>备注

为选项卡标签指定以下样式之一：

|||
|-|-|
|STYLE_3D|3D 样式。  |
|STYLE_3D_ONENOTE|微软 OneNote 样式。  |
|STYLE_3D_VS2005|微软视觉工作室2005年风格。  |
|STYLE_3D_SCROLLED|带矩形选项卡标签的 3D 样式。  |
|STYLE_FLAT_SHARED_HORZ_SCROLL|具有共享水平滚动条的平面样式。  |
|STYLE_3D_ROUNDED_SCROLL|带圆形标签的 3D 样式。  |

## <a name="cmditabinfom_tablocation"></a><a name="m_tablocation"></a>CMDITab信息：m_tabLocation

指定选项卡标签是位于页面的顶部还是底部。

```
CMFCTabCtrl::Location m_tabLocation;
```

### <a name="remarks"></a>备注

应用于选项卡，以下位置标志之一：

- LOCATION_BOTTOM：选项卡标签位于页面底部。

- LOCATION_TOP：选项卡标签位于页面顶部

## <a name="cmditabinfoserialize"></a><a name="serialize"></a>CMDITab信息：序列化

从存档或存档读取或写入此对象。

```
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>参数

*ar*<br/>
[在]要序列化的[CArchive 类](../../mfc/reference/carchive-class.md)对象。

## <a name="see-also"></a>另请参阅

[CMDIFrameWndEx 类](../../mfc/reference/cmdiframewndex-class.md)<br/>
[MDI 选项卡式组](../../mfc/mdi-tabbed-groups.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
