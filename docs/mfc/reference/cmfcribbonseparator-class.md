---
title: CMFCRibbonSeparator 类
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
ms.openlocfilehash: 05ac8b26cb6b6e7d8e622ecbaac1d4a81bfd35e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565927"
---
# <a name="cmfcribbonseparator-class"></a>CMFCRibbonSeparator 类

实现功能区分隔符。

## <a name="syntax"></a>语法

```
class CMFCRibbonSeparator : public CMFCRibbonBaseElement
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|||
|-|-|
|名称|描述|
|[CMFCRibbonSeparator::CMFCRibbonSeparator](#cmfcribbonseparator)|构造 `CMFCRibbonSeparator` 对象。|

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|描述|
|[CMFCRibbonSeparator::AddToListBox](#addtolistbox)|将添加到分隔符**命令**列表中**自定义**对话框。 (重写[CMFCRibbonBaseElement::AddToListBox](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox)。)|
|`CMFCRibbonSeparator::CreateObject`|由框架用于创建此类类型的动态实例。|
|`CMFCRibbonSeparator::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型相关联的对象。|

### <a name="protected-methods"></a>受保护的方法

|||
|-|-|
|名称|描述|
|[CMFCRibbonSeparator::CopyFrom](#copyfrom)|从另一个对象设置分隔符的成员变量复制方法。|
|[CMFCRibbonSeparator::GetRegularSize](#getregularsize)|返回分隔符的大小。|
|[CMFCRibbonSeparator::IsSeparator](#isseparator)|指示这是否是一个分隔符。|
|[CMFCRibbonSeparator::IsTabStop](#istabstop)|指示这是否是一个制表位。|
|[CMFCRibbonSeparator::OnDraw](#ondraw)|由系统在功能区或快速访问工具栏上绘制分隔符调用。|
|[CMFCRibbonSeparator::OnDrawOnList](#ondrawonlist)|调用的系统上绘制分隔符**命令**列表。|

## <a name="remarks"></a>备注

功能区分隔符为垂直或水平线条，逻辑上将功能区元素。 可以在功能区控件、 主应用程序菜单、 功能区状态栏和快速访问工具栏上绘制分隔符。

若要在应用程序中使用分隔符，构造新对象并将其添加到主应用程序菜单，如下所示：

```
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```
调用[CMFCRibbonPanel::AddSeparator](../../mfc/reference/cmfcribbonpanel-class.md#addseparator)将分隔符添加到功能区面板。 分配和添加在内部分隔符`AddSeparator`方法。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonSeparator](../../mfc/reference/cmfcribbonseparator-class.md)

## <a name="requirements"></a>要求

**标头：** afxbaseribbonelement.h

##  <a name="addtolistbox"></a>  CMFCRibbonSeparator::AddToListBox

将添加到分隔符**命令**列表中**自定义**对话框。

```
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,
    BOOL bDeep);
```

### <a name="parameters"></a>参数

*pWndListBox*<br/>
[in]一个指向**命令**添加分隔符的位置的列表。

*bDeep*<br/>
[in]忽略。

### <a name="return-value"></a>返回值

为指定列表框中字符串的从零开始索引*pWndListBox*。

##  <a name="cmfcribbonseparator"></a>  CMFCRibbonSeparator::CMFCRibbonSeparator

构造 `CMFCRibbonSeparator` 对象。

```
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```

### <a name="parameters"></a>参数

*bIsHoriz*<br/>
[in]如果为 TRUE，该分隔符是水平;如果为 FALSE，分隔符为垂直。

### <a name="remarks"></a>备注

在应用程序菜单中使用水平分隔符。 在工具栏中使用垂直分隔符。

### <a name="example"></a>示例

下面的示例演示如何构造的对象`CMFCRibbonSeparator`类。

[!code-cpp[NVC_MFC_RibbonApp#19](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]

##  <a name="copyfrom"></a>  CMFCRibbonSeparator::CopyFrom

从另一个对象设置分隔符的成员变量复制方法。

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>参数

*src*<br/>
[in]要从复制的源功能区元素。

##  <a name="getregularsize"></a>  CMFCRibbonSeparator::GetRegularSize

返回分隔符的大小。

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]设备内容指向的指针。

### <a name="return-value"></a>返回值

给定的设备上下文上的分隔符的大小。

##  <a name="isseparator"></a>  CMFCRibbonSeparator::IsSeparator

指示这是否是一个分隔符。

```
virtual BOOL IsSeparator() const;
```

### <a name="return-value"></a>返回值

对于此类始终返回 TRUE。

##  <a name="istabstop"></a>  CMFCRibbonSeparator::IsTabStop

指示这是否是一个制表位。

```
virtual BOOL IsTabStop() const;
```

### <a name="return-value"></a>返回值

此类始终为 FALSE。

### <a name="remarks"></a>备注

功能区分隔符不是一个制表位。

##  <a name="ondraw"></a>  CMFCRibbonSeparator::OnDraw

由系统在功能区或快速访问工具栏上绘制分隔符调用。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]指向设备上下文的指针。

##  <a name="ondrawonlist"></a>  CMFCRibbonSeparator::OnDrawOnList

调用的系统上绘制分隔符**命令**列表。

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
|参数|描述|
|*pDC*|[in]指向设备上下文的指针。|
|*strText*|[in]在列表上显示的文本。|
|*nTextOffset*|[in]文本和左侧和右侧的边界矩形之间的间距。|
|*rect*|[in]指定的边框。|
|*bIsSelected*|[in]忽略。|
|*bHighlighted*|[in]忽略。|

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
