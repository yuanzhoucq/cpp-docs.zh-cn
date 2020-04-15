---
title: CMFCDragFrameImpl 类
ms.date: 10/18/2018
f1_keywords:
- CMFCDragFrameImpl
helpviewer_keywords:
- CMFCDragFrameImpl class [MFC]
ms.assetid: 500cd824-8188-43c2-8754-b7bb46b5648a
ms.openlocfilehash: a2f6f558d6b4452ca06429c7e3017b7c575c6676
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367562"
---
# <a name="cmfcdragframeimpl-class"></a>CMFCDragFrameImpl 类

类`CMFCDragFrameImpl`绘制在标准停靠模式下拖动窗格时出现的拖动矩形。
有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

## <a name="syntax"></a>语法

```
class CMFCDragFrameImpl
```

## <a name="remarks"></a>备注

此类的对象嵌入在每个[CPane 类](../../mfc/reference/cpane-class.md)对象中。 因此，当用户拖动该方法时，`CanFloat`使用 方法的每个窗格都会显示拖动矩形。

您可以使用[AFX_GLOBAL_DATA：m_nDragFrameThicknessFloat](afx-global-data-structure.md#m_ndragframethicknessfloat)和[AFX_GLOBAL_DATA：m_nDragFrameThicknessDock](afx-global-data-structure.md#m_ndragframethicknessdock)来控制拖动矩形的厚度。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CMFCDragFrameImpl](../../mfc/reference/cmfcdragframeimpl-class.md)

## <a name="requirements"></a>要求

**标题：** afxdragframeimpl.h

## <a name="cmfcdragframeimplenddrawdragframe"></a><a name="enddrawdragframe"></a>CMFCDragFrameimpl：：结束绘制拖动框架

```
void EndDrawDragFrame(BOOL bClearInternalRects = TRUE);
```

### <a name="parameters"></a>参数

[在]*b清除内部重新*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcdragframeimplinit"></a><a name="init"></a>CMFCDragframeimpl：：Init

```
void Init(CWnd* pDraggedWnd);
```

### <a name="parameters"></a>参数

[在]*普拉普恩德*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcdragframeimplmovedragframe"></a><a name="movedragframe"></a>CMFCDragFrameimpl：：移动拖动框架

```
void MoveDragFrame(BOOL bForceMove = FALSE);
```

### <a name="parameters"></a>参数

[在]*bForceMove*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcdragframeimplplacetabpredocking"></a><a name="placetabpredocking"></a>CMFCDragFrameimpl：:PlaceTab预对接

```
void PlaceTabPreDocking(
    CBaseTabbedPane* pTabbedBar,
    BOOL bFirstTime);

void PlaceTabPreDocking(CWnd* pCBarToPlaceOn);
```

### <a name="parameters"></a>参数

[在]*pTabbedBar*<br/>

[在]*b 第一次*<br/>

[在]*pCBARtoPlaceon*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcdragframeimplremovetabpredocking"></a><a name="removetabpredocking"></a>CMFCDragFrameimpl：：删除TabpreDocking

```
void RemoveTabPreDocking(CDockablePane* pOldTargetBar = NULL);
```

### <a name="parameters"></a>参数

[在]*pOldTargetBar*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcdragframeimplresetstate"></a><a name="resetstate"></a>CMFCDragFrameimpl：：重置状态

```
void ResetState();
```

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CPane Class](../../mfc/reference/cpane-class.md)
