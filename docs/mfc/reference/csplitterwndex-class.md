---
title: CSplitterWndEx 类
ms.date: 11/04/2016
f1_keywords:
- CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx::OnDrawSplitter
helpviewer_keywords:
- CSplitterWndEx [MFC], OnDrawSplitter
ms.assetid: 33e5eef3-05e1-4a07-a968-bf9207ce8598
ms.openlocfilehash: d7952e3082bf68cff7ad9ba218073081ee522320
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363922"
---
# <a name="csplitterwndex-class"></a>CSplitterWndEx 类

表示自定义拆分窗口。

## <a name="syntax"></a>语法

```
class CSplitterWndEx : public CSplitterWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|`CSplitterWndEx::CSplitterWndEx`|默认构造函数。|
|`CSplitterWndEx::~CSplitterWndEx`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CSplitterwndEx：：在牵引器上](#ondrawsplitter)|由框架调用以绘制拆分窗口。 （覆盖[CSplitterwnd：onDrawSplitter](csplitterwnd-class.md#ondrawsplitter).）|

## <a name="remarks"></a>备注

重写方法`OnDrawSplitter`以自定义拆分器窗口的图形组件的外观。

该`CSplitterWndEx`类与[OnDrawSplitter 边界](cmfcvisualmanager-class.md#ondrawsplitterborder)[、OnDrawSplitterBox](cmfcvisualmanager-class.md#ondrawsplitterbox)和[OnFillSplitter 背景](cmfcvisualmanager-class.md#onfillsplitterbackground)方法一起使用，这些方法由可视化管理器实现。 要使可视化管理器在应用程序中绘制拆分器窗口，请将`CSplitterWnd`类的声明替换为`CSplitterWndEx`类。 对于帧窗口应用程序，拆分器窗口类在位于 mainfrm.h 中的 CMainFrame 类中声明。 例如，请参阅示例目录中`OutlookDemo`的示例。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

[CSplitterWnd](csplitterwnd-class.md)

## <a name="requirements"></a>要求

**标题：** afxsplitterwndex.h

## <a name="csplitterwndexondrawsplitter"></a><a name="ondrawsplitter"></a>CSplitterwndEx：：在牵引器上

由框架调用以绘制拆分窗口。

```
virtual void OnDrawSplitter(
   CDC* pDC,
   ESplitType nType,
   const CRect& rect
);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。 如果此参数为 NULL，则框架将重绘活动窗口。

nType**<br/>
[在]`CSplitterWnd::ESplitType`指定要绘制的拆分窗口元素的枚举值之一。 有效的值为 `splitBox`、`splitBar`、`splitIntersection` 和 `splitBorder`。

*矩形*<br/>
[在]指定用于绘制指定拆分窗口元素的尺寸和位置的边界矩形。

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[层次结构图表](../hierarchy-chart.md)<br/>
[类](mfc-classes.md)<br/>
[CSplitterWnd 类](csplitterwnd-class.md)<br/>
[CMFCVisualManager 类](cmfcvisualmanager-class.md)
