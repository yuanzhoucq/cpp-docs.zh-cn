---
title: CMFC 剪束分离器类
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::AddToListBox
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CopyFrom
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::GetRegularSize
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsTabStop
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDraw
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDrawOnList
helpviewer_keywords:
- CMFCRibbonSeparator [MFC], CMFCRibbonSeparator
- CMFCRibbonSeparator [MFC], AddToListBox
- CMFCRibbonSeparator [MFC], CopyFrom
- CMFCRibbonSeparator [MFC], GetRegularSize
- CMFCRibbonSeparator [MFC], IsSeparator
- CMFCRibbonSeparator [MFC], IsTabStop
- CMFCRibbonSeparator [MFC], OnDraw
- CMFCRibbonSeparator [MFC], OnDrawOnList
ms.assetid: bedb1a53-cb07-4c3c-be12-698c5409e7cf
ms.openlocfilehash: 41a958c78719f6aedf1cc02f8e3ff5a2dbbf0e1b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368850"
---
# <a name="cmfcribbonseparator-class"></a>CMFC 剪束分离器类

实现功能区分隔符。

## <a name="syntax"></a>语法

```
class CMFCRibbonSeparator : public CMFCRibbonBaseElement
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|||
|-|-|
|名称|说明|
|[CMFC 剪子分离器：CMFC 剪彩器](#cmfcribbonseparator)|构造 `CMFCRibbonSeparator` 对象。|

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|说明|
|[CMFC 剪彩器：：添加列表框](#addtolistbox)|在 **"自定义"** 对话框中向 **"命令"** 列表添加分隔符。 （覆盖[CMFC 功能基础元素：：添加列表框](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox).）|
|`CMFCRibbonSeparator::CreateObject`|由框架用于创建此类类型的动态实例。|
|`CMFCRibbonSeparator::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|

### <a name="protected-methods"></a>受保护的方法

|||
|-|-|
|名称|说明|
|[CMFC 剪彩分离器：：从](#copyfrom)|一种复制方法，用于从另一个对象设置分隔符的成员变量。|
|[CMFC 剪彩分离器：获取常规尺寸](#getregularsize)|返回分隔符的大小。|
|[CMFC 剪子分离器：分离器](#isseparator)|指示这是否是分隔符。|
|[CMFC 剪彩分离器：：IsTabStop](#istabstop)|指示这是否是制表符。|
|[CMFC 剪彩分离器：：OnDraw](#ondraw)|系统调用以在功能区或快速访问工具栏上绘制分隔符。|
|[CMFC 剪彩器：在绘制列表](#ondrawonlist)|系统调用以在**命令**列表中绘制分隔符。|

## <a name="remarks"></a>备注

功能区分隔符是一条垂直或水平线，用于逻辑地分隔功能区元素。 可以在功能区控件、主应用程序菜单、功能区状态栏和快速访问工具栏上绘制分隔符。

要在应用程序中使用分隔符，请构造新对象并将其添加到主应用程序菜单中，如下所示：

```
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```

致电[CMFC 功能面板：：添加分离器](../../mfc/reference/cmfcribbonpanel-class.md#addseparator)以向功能区面板添加分隔符。 分隔符由`AddSeparator`方法在内部分配和添加。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFC 剪子分离器](../../mfc/reference/cmfcribbonseparator-class.md)

## <a name="requirements"></a>要求

**标头：** afxbaseribbonelement.h

## <a name="cmfcribbonseparatoraddtolistbox"></a><a name="addtolistbox"></a>CMFC 剪彩器：：添加列表框

在 **"自定义"** 对话框中向 **"命令"** 列表添加分隔符。

```
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,
    BOOL bDeep);
```

### <a name="parameters"></a>参数

*pWndListBox*<br/>
[在]指向添加分隔符**的命令**列表的指针。

*bDeep*<br/>
[在]忽视。

### <a name="return-value"></a>返回值

*pWndListBox*指定的列表框中的字符串的从零到的索引。

## <a name="cmfcribbonseparatorcmfcribbonseparator"></a><a name="cmfcribbonseparator"></a>CMFC 剪子分离器：CMFC 剪彩器

构造 `CMFCRibbonSeparator` 对象。

```
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```

### <a name="parameters"></a>参数

*比绍里兹*<br/>
[在]如果为 TRUE，则分隔符是水平的;如果为 TRUE，则分离器为水平分离器。如果 FALSE，则分隔符是垂直的。

### <a name="remarks"></a>备注

水平分隔符用于应用程序菜单。 垂直分隔符用于工具栏。

### <a name="example"></a>示例

下面的示例演示如何构造`CMFCRibbonSeparator`类的对象。

[!code-cpp[NVC_MFC_RibbonApp#19](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]

## <a name="cmfcribbonseparatorcopyfrom"></a><a name="copyfrom"></a>CMFC 剪彩分离器：：从

一种复制方法，用于从另一个对象设置分隔符的成员变量。

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>参数

*Src*<br/>
[在]要从中复制的源功能区元素。

## <a name="cmfcribbonseparatorgetregularsize"></a><a name="getregularsize"></a>CMFC 剪彩分离器：获取常规尺寸

返回分隔符的大小。

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备内容的指针。

### <a name="return-value"></a>返回值

给定设备上下文中分隔符的大小。

## <a name="cmfcribbonseparatorisseparator"></a><a name="isseparator"></a>CMFC 剪子分离器：分离器

指示这是否是分隔符。

```
virtual BOOL IsSeparator() const;
```

### <a name="return-value"></a>返回值

对于此类来说，始终为 TRUE。

## <a name="cmfcribbonseparatoristabstop"></a><a name="istabstop"></a>CMFC 剪彩分离器：：IsTabStop

指示这是否是制表符。

```
virtual BOOL IsTabStop() const;
```

### <a name="return-value"></a>返回值

始终为此类提供 FALSE。

### <a name="remarks"></a>备注

功能区分隔符不是制表位。

## <a name="cmfcribbonseparatorondraw"></a><a name="ondraw"></a>CMFC 剪彩分离器：：OnDraw

系统调用以在功能区或快速访问工具栏上绘制分隔符。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

## <a name="cmfcribbonseparatorondrawonlist"></a><a name="ondrawonlist"></a>CMFC 剪彩器：在绘制列表

系统调用以在**命令**列表中绘制分隔符。

```
virtual void OnDrawOnList(
    CDC* pDC,
    CString strText,
    int nTextOffset,
    CRect rect,
    BOOL bIsSelected,
    BOOL bHighlighted);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*pDC*|[在]指向设备上下文的指针。|
|*斯特文本*|[在]列表中显示的文本。|
|*n文本偏移*|[在]在边界矩形的文本和左侧之间间距。|
|*矩形*|[在]指定边界矩形。|
|*bIs选择*|[在]忽视。|
|*b 突出显示*|[在]忽视。|

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
