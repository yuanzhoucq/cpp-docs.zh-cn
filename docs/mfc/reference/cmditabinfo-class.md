---
title: CMDITabInfo 类
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
ms.openlocfilehash: b9b45142d0fb1d53ccecad31ace7ad1a6dd4ee40
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50524704"
---
# <a name="cmditabinfo-class"></a>CMDITabInfo 类

`CMDITabInfo`类用于将参数传递给[cmdiframewndex:: Enablemditabbedgroups](../../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups)方法。 设置此类的成员以控制 MDI 选项卡式组的行为。

## <a name="syntax"></a>语法

```
class CMDITabInfo
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|`CMDITabInfo::CMDITabInfo`|默认构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMDITabInfo::Serialize](#serialize)|从存档读取该对象或将该对象写入存档。|

### <a name="data-members"></a>数据成员

|name|描述|
|----------|-----------------|
|[CMDITabInfo::m_bActiveTabCloseButton;](#m_bactivetabclosebutton_)|指定是否**关闭**按钮会显示在活动选项卡的标签。|
|[CMDITabInfo::m_bAutoColor](#m_bautocolor)|指定是否颜色 MDI 选项卡。|
|[CMDITabInfo::m_bDocumentMenu](#m_bdocumentmenu)|指定选项卡组是否显示弹出菜单的显示打开的文档列表或显示滚动按钮。|
|[CMDITabInfo::m_bEnableTabSwap](#m_benabletabswap)|指定用户是否可以通过拖动交换的选项卡的位置。|
|[CMDITabInfo::m_bFlatFrame](#m_bflatframe)|指定选项卡是否具有平面的帧。|
|[CMDITabInfo::m_bTabCloseButton](#m_btabclosebutton)|指定是否显示每个选项卡标签**关闭**按钮。|
|[CMDITabInfo::m_bTabCustomTooltips](#m_btabcustomtooltips)|指定是否启用自定义工具提示。|
|[CMDITabInfo::m_bTabIcons](#m_btabicons)|指定是否在 MDI 选项卡上显示图标。|
|[CMDITabInfo::m_nTabBorderSize](#m_ntabbordersize)|指定每个选项卡窗口的边框大小。|
|[CMDITabInfo::m_style](#m_style)|指定选项卡标签的样式。|
|[CMDITabInfo::m_tabLocation](#m_tablocation)|指定的选项卡标签是否位于顶部或底部的页。|

## <a name="remarks"></a>备注

此类指定 MDI 选项卡组，则框架将创建的参数。

## <a name="example"></a>示例

下面的示例演示如何设置中的各种成员变量的值`CMDITabInfo`类。

[!code-cpp[NVC_MFC_MDITab#1](../../mfc/reference/codesnippet/cpp/cmditabinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CMDITabInfo](../../mfc/reference/cmditabinfo-class.md)

## <a name="requirements"></a>要求

**标头：** afxmdiclientareawnd.h

##  <a name="m_bactivetabclosebutton_"></a>  CMDITabInfo::m_bActiveTabCloseButton;

指定是否**关闭**按钮会显示在活动选项卡的标签。

```
BOOL m_bActiveTabCloseButton;
```

### <a name="remarks"></a>备注

如果为 TRUE，将显示活动选项卡的标签**关闭**按钮。 **关闭**将从右上角的选项卡区域删除按钮。 否则，活动选项卡的标签将不会显示**关闭**按钮。 **关闭**按钮将显示在选项卡区域的右上角。

##  <a name="m_bautocolor"></a>  CMDITabInfo::m_bAutoColor

指定每个 MDI 选项卡是否具有其自己的颜色。

```
BOOL m_bAutoColor;
```

### <a name="remarks"></a>备注

如果为 TRUE，每个选项卡将具有其自己的颜色。 由 MFC 库管理的一组颜色。 否则，选项卡中显示为空白。 默认值是 FALSE。

##  <a name="m_bdocumentmenu"></a>  CMDITabInfo::m_bDocumentMenu

指定是否每个选项卡显示弹出菜单显示打开的文档选项卡区域的右边缘的列表。

```
BOOL m_bDocumentMenu;
```

### <a name="remarks"></a>备注

如果为 TRUE，每个选项卡 windows 将显示弹出菜单显示打开的文档选项卡区域; 的右边缘的列表否则，该选项卡窗口选项卡区域的右边缘显示滚动按钮。 默认值是 FALSE。

##  <a name="m_benabletabswap"></a>  CMDITabInfo::m_bEnableTabSwap

指定用户是否可以通过拖动交换的选项卡的位置。

```
BOOL m_bEnableTabSwap;
```

### <a name="remarks"></a>备注

如果为 TRUE，用户可以通过拖动选项卡更改选项卡位置。 否则，用户不能更改的选项卡位置。 默认值为 TRUE。

##  <a name="m_bflatframe"></a>  CMDITabInfo::m_bFlatFrame

指定每个选项卡窗口是否具有平面的帧。

```
BOOL m_bFlatFrame;
```

##  <a name="m_btabclosebutton"></a>  CMDITabInfo::m_bTabCloseButton

指定是否显示每个选项卡窗口**关闭**按钮。

```
BOOL m_bTabCloseButton;
```

### <a name="remarks"></a>备注

如果为 TRUE，每个选项卡窗口会显示**关闭**右边缘的选项卡上的按钮。否则为**关闭**按钮不会显示。 默认值为 TRUE。

##  <a name="m_btabcustomtooltips"></a>  CMDITabInfo::m_bTabCustomTooltips

指定的选项卡是否显示工具提示。

```
BOOL m_bTabCustomTooltips;
```

### <a name="remarks"></a>备注

如果为 TRUE，该应用程序将 AFX_WM_ON_GET_TAB_TOOLTIP 消息发送到主框架。 可以通过使用 ON_REGISTERED_MESSAGE 宏来处理此消息。

##  <a name="m_btabicons"></a>  CMDITabInfo::m_bTabIcons

指定是否在 MDI 选项卡上显示图标。

```
BOOL m_bTabIcons;
```

### <a name="remarks"></a>备注

如果为 TRUE，图标将显示在每个 MDI 选项卡。否则，不在选项卡上显示图标。 默认值是 FALSE。

##  <a name="m_ntabbordersize"></a>  CMDITabInfo::m_nTabBorderSize

指定以像素为单位，每个选项卡窗口的边框大小。

```
int m_nTabBorderSize;
```

### <a name="remarks"></a>备注

[CMFCVisualManager::GetMDITabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize)返回默认值。

##  <a name="m_style"></a>  CMDITabInfo::m_style

指定选项卡标签的样式。

```
CMFCTabCtrl::Style m_style
```

### <a name="remarks"></a>备注

指定一个选项卡标签的以下样式：

|||
|-|-|
|STYLE_3D|三维样式。  |
|STYLE_3D_ONENOTE|Microsoft OneNote 样式。  |
|STYLE_3D_VS2005|Microsoft Visual Studio 2005 样式。  |
|STYLE_3D_SCROLLED|使用矩形选项卡标签的三维样式。  |
|STYLE_FLAT_SHARED_HORZ_SCROLL|与共享水平滚动条的平面样式。  |
|STYLE_3D_ROUNDED_SCROLL|使用倒圆角的选项卡标签的三维样式。  |

##  <a name="m_tablocation"></a>  CMDITabInfo::m_tabLocation

指定的选项卡标签是否位于顶部或底部的页。

```
CMFCTabCtrl::Location m_tabLocation;
```

### <a name="remarks"></a>备注

适用于以下位置标志的选项卡一个：

- LOCATION_BOTTOM： 选项卡标签位于页面底部。

- 选项卡标签将位于页面顶部 LOCATION_TOP:

##  <a name="serialize"></a>  CMDITabInfo::Serialize

读取或写入此对象从存档或存档。

```
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>参数

*ar*<br/>
[in]一个[CArchive 类](../../mfc/reference/carchive-class.md)要序列化对象。

## <a name="see-also"></a>请参阅

[CMDIFrameWndEx 类](../../mfc/reference/cmdiframewndex-class.md)<br/>
[MDI 选项卡式组](../../mfc/mdi-tabbed-groups.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
