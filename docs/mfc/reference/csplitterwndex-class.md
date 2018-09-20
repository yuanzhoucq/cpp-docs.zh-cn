---
title: CSplitterWndEx 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx::OnDrawSplitter
dev_langs:
- C++
helpviewer_keywords:
- CSplitterWndEx [MFC], OnDrawSplitter
ms.assetid: 33e5eef3-05e1-4a07-a968-bf9207ce8598
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7df892a3d3f038655f37b78fa88babb09d50df2d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373452"
---
# <a name="csplitterwndex-class"></a>CSplitterWndEx 类



表示自定义拆分窗口。

## <a name="syntax"></a>语法

```
class CSplitterWndEx : public CSplitterWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|`CSplitterWndEx::CSplitterWndEx`|默认构造函数。|
|`CSplitterWndEx::~CSplitterWndEx`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CSplitterWndEx::OnDrawSplitter](#ondrawsplitter)|由框架调用以绘制拆分器窗口。 (重写[CSplitterWnd::OnDrawSplitter](csplitterwnd-class.md#ondrawsplitter)。)|

## <a name="remarks"></a>备注

重写`OnDrawSplitter`方法以自定义拆分窗口的图形组件的外观。

`CSplitterWndEx`类使用连同[OnDrawSplitterBorder](cmfcvisualmanager-class.md#ondrawsplitterborder)， [OnDrawSplitterBox](cmfcvisualmanager-class.md#ondrawsplitterbox)，并且[OnFillSplitterBackground](cmfcvisualmanager-class.md#onfillsplitterbackground)方法，它是由视觉管理器实现。 若要使视觉管理器中，若要绘制应用程序中的拆分器窗口，声明替换为`CSplitterWnd`类的`CSplitterWndEx`类。 对于框架窗口应用程序，在 mainfrm.h 中位于 CMainFrame 类中声明拆分器窗口类。 有关示例，请参阅`OutlookDemo`示例在示例目录中。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

[CSplitterWnd](csplitterwnd-class.md)

## <a name="requirements"></a>要求

**标头：** afxsplitterwndex.h

##  <a name="ondrawsplitter"></a>  CSplitterWndEx::OnDrawSplitter

由框架调用以绘制拆分器窗口。

```
virtual void OnDrawSplitter(
   CDC* pDC,
   ESplitType nType,
   const CRect& rect
);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]指向设备上下文指针。 如果此参数为 NULL，该框架重绘活动窗口。

*n 类型*<br/>
[in]其中一个`CSplitterWnd::ESplitType`枚举值，该值指定要绘制的拆分器窗口元素。 有效值为 `splitBox`、`splitBar`、`splitIntersection` 和 `splitBorder`。

*rect*<br/>
[in]指定的维数和位置绘制指定的拆分器窗口元素边框。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../hierarchy-chart.md)<br/>
[类](mfc-classes.md)<br/>
[CSplitterWnd 类](csplitterwnd-class.md)<br/>
[CMFCVisualManager 类](cmfcvisualmanager-class.md)