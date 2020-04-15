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
ms.openlocfilehash: 33d4bc0c72718d028031ac11bc67da6aec5e4907
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374423"
---
# <a name="cmfcimageeditorpalettebar-class"></a>CMFCImageEditorPaletteBar 类

为图像编辑器对话框提供调色板栏功能。

## <a name="syntax"></a>语法

```
class CMFCImageEditorPaletteBar : public CMFCToolBar
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|说明|
|[CMFC图像编辑器调色板栏：：获取罗高](#getrowheight)|返回工具栏按钮的高度。 （覆盖[CMFC 工具栏：获取罗高](../../mfc/reference/cmfctoolbar-class.md#getrowheight).）|
|[CMFC图像编辑器调色板栏：是按钮超尺寸可用](#isbuttonextrasizeavailable)|确定工具栏是否可以显示具有扩展边框的按钮。 （覆盖[CMFC 工具栏：是按钮外大尺寸](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable).）|

### <a name="remarks"></a>备注

此类不适于在您的代码中直接使用。

框架使用此类在图像编辑器对话框中显示调色板栏。 有关图像编辑器对话框的详细信息，请参阅[CMFCImage 编辑器对话类](../../mfc/reference/cmfcimageeditordialog-class.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBa](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFC图像编辑器栏](../../mfc/reference/cmfcimageeditorpalettebar-class.md)

## <a name="requirements"></a>要求

**标题：** afx 图像编辑器.h

## <a name="cmfcimageeditorpalettebargetrowheight"></a><a name="getrowheight"></a>CMFC图像编辑器调色板栏：：获取罗高

返回工具栏按钮的高度。

```
virtual int GetRowHeight() const;
```

### <a name="return-value"></a>返回值

工具栏上每个按钮的高度。

## <a name="cmfcimageeditorpalettebarisbuttonextrasizeavailable"></a><a name="isbuttonextrasizeavailable"></a>CMFC图像编辑器调色板栏：是按钮超尺寸可用

确定工具栏是否可以显示具有扩展边框的按钮。

```
virtual BOOL IsButtonExtraSizeAvailable() const;
```

### <a name="return-value"></a>返回值

此方法返回 FALSE。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImageEditorDialog 类](../../mfc/reference/cmfcimageeditordialog-class.md)
