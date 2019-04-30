---
title: CMFCImageEditorPaletteBar 类
ms.date: 11/04/2016
f1_keywords:
- CMFCImageEditorPaletteBar
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar::GetRowHeight
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable
helpviewer_keywords:
- CMFCImageEditorPaletteBar [MFC], GetRowHeight
- CMFCImageEditorPaletteBar [MFC], IsButtonExtraSizeAvailable
ms.assetid: 3fb7ba8e-f254-4d56-b913-9941b4ed8138
ms.openlocfilehash: 6812f3f425186484ef892d7f5c626c0dfce0f863
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378097"
---
# <a name="cmfcimageeditorpalettebar-class"></a>CMFCImageEditorPaletteBar 类

提供图像编辑器对话框中的调色板栏的功能。

## <a name="syntax"></a>语法

```
class CMFCImageEditorPaletteBar : public CMFCToolBar
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|描述|
|[CMFCImageEditorPaletteBar::GetRowHeight](#getrowheight)|返回的工具栏按钮的高度。 (重写[CMFCToolBar::GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight)。)|
|[CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable](#isbuttonextrasizeavailable)|确定工具栏是否可以显示已扩展边框的按钮。 (重写[CMFCToolBar::IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable)。)|

### <a name="remarks"></a>备注

此类不适于在代码中直接使用。

该框架使用此类在图像编辑器对话框中显示调色板条。 有关图像编辑器对话框的详细信息，请参阅[CMFCImageEditorDialog 类](../../mfc/reference/cmfcimageeditordialog-class.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBa](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCImageEditorPaletteBar](../../mfc/reference/cmfcimageeditorpalettebar-class.md)

## <a name="requirements"></a>要求

**标头：** afximageeditordialog.h

##  <a name="getrowheight"></a>  CMFCImageEditorPaletteBar::GetRowHeight

返回的工具栏按钮的高度。

```
virtual int GetRowHeight() const;
```

### <a name="return-value"></a>返回值

在工具栏上的每个按钮的高度。

##  <a name="isbuttonextrasizeavailable"></a>  CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable

确定工具栏是否可以显示已扩展边框的按钮。

```
virtual BOOL IsButtonExtraSizeAvailable() const;
```

### <a name="return-value"></a>返回值

此方法返回 FALSE。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImageEditorDialog 类](../../mfc/reference/cmfcimageeditordialog-class.md)
