---
title: CMFCRibbonStatusBar 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonStatusBar
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddDynamicElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddExtendedElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddSeparator
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::Create
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::CreateEx
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::FindByID
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::FindElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetCount
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExCount
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExtendedArea
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetSpace
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsBottomFrame
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsExtendedElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsInformationMode
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RecalcLayout
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RemoveAll
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RemoveElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::SetInformation
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::OnDrawInformation
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonStatusBar [MFC], AddDynamicElement
- CMFCRibbonStatusBar [MFC], AddElement
- CMFCRibbonStatusBar [MFC], AddExtendedElement
- CMFCRibbonStatusBar [MFC], AddSeparator
- CMFCRibbonStatusBar [MFC], Create
- CMFCRibbonStatusBar [MFC], CreateEx
- CMFCRibbonStatusBar [MFC], FindByID
- CMFCRibbonStatusBar [MFC], FindElement
- CMFCRibbonStatusBar [MFC], GetCount
- CMFCRibbonStatusBar [MFC], GetElement
- CMFCRibbonStatusBar [MFC], GetExCount
- CMFCRibbonStatusBar [MFC], GetExElement
- CMFCRibbonStatusBar [MFC], GetExtendedArea
- CMFCRibbonStatusBar [MFC], GetSpace
- CMFCRibbonStatusBar [MFC], IsBottomFrame
- CMFCRibbonStatusBar [MFC], IsExtendedElement
- CMFCRibbonStatusBar [MFC], IsInformationMode
- CMFCRibbonStatusBar [MFC], RecalcLayout
- CMFCRibbonStatusBar [MFC], RemoveAll
- CMFCRibbonStatusBar [MFC], RemoveElement
- CMFCRibbonStatusBar [MFC], SetInformation
- CMFCRibbonStatusBar [MFC], OnDrawInformation
ms.assetid: 921eb57f-3b40-49fa-a38c-3f2fb6dc2893
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4303dc9f5f72e4a9500a1d5a6a7c210e7f7bc62f
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063791"
---
# <a name="cmfcribbonstatusbar-class"></a>CMFCRibbonStatusBar 类

`CMFCRibbonStatusBar`类实现状态栏控件可以显示功能区元素。

## <a name="syntax"></a>语法

```
class CMFCRibbonStatusBar : public CMFCRibbonBar
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCRibbonStatusBar::AddDynamicElement](#adddynamicelement)|向功能区状态栏的动态元素。|
|[CMFCRibbonStatusBar::AddElement](#addelement)|将新的功能区元素添加到功能区状态栏。|
|[CMFCRibbonStatusBar::AddExtendedElement](#addextendedelement)|将功能区元素添加到功能区状态栏扩展区域。|
|[CMFCRibbonStatusBar::AddSeparator](#addseparator)|向功能区状态栏的分隔符。|
|[CMFCRibbonStatusBar::Create](#create)|创建功能区状态栏。|
|[CMFCRibbonStatusBar::CreateEx](#createex)|创建功能区状态栏扩展样式。|
|[CMFCRibbonStatusBar::FindByID](#findbyid)||
|[CMFCRibbonStatusBar::FindElement](#findelement)|返回一个指向的元素的具有指定的命令 id。|
|[CMFCRibbonStatusBar::GetCount](#getcount)|返回位于功能区状态栏的主区域中的元素数目。|
|[CMFCRibbonStatusBar::GetElement](#getelement)|返回一个指向位于指定索引处的元素。|
|[CMFCRibbonStatusBar::GetExCount](#getexcount)|返回位于功能区状态栏扩展区域中的元素数目。|
|[CMFCRibbonStatusBar::GetExElement](#getexelement)|返回指向元素的指针，该元素位于功能区状态栏扩展区域中的指定索引处。|
|[CMFCRibbonStatusBar::GetExtendedArea](#getextendedarea)||
|[CMFCRibbonStatusBar::GetSpace](#getspace)||
|[CMFCRibbonStatusBar::IsBottomFrame](#isbottomframe)||
|[CMFCRibbonStatusBar::IsExtendedElement](#isextendedelement)||
|[CMFCRibbonStatusBar::IsInformationMode](#isinformationmode)|确定是否为功能区状态栏启用信息模式。|
|[CMFCRibbonStatusBar::RecalcLayout](#recalclayout)|(重写[CMFCRibbonBar::RecalcLayout](../../mfc/reference/cmfcribbonbar-class.md#recalclayout)。)|
|[CMFCRibbonStatusBar::RemoveAll](#removeall)|从功能区状态栏中移除所有元素。|
|[CMFCRibbonStatusBar::RemoveElement](#removeelement)|移除具有指定的命令 ID 从功能区状态栏的元素。|
|[CMFCRibbonStatusBar::SetInformation](#setinformation)|启用或禁用功能区状态栏的信息模式。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CMFCRibbonStatusBar::OnDrawInformation](#ondrawinformation)|显示在功能区状态栏的信息模式启用时显示的信息字符串。|

## <a name="remarks"></a>备注

通过使用功能区状态栏的内置的上下文菜单，用户可以更改功能区状态栏上的功能区元素的可见性。 您可以动态添加或移除元素。

功能区状态栏有两个区域： 主要区域和扩展的区域。 扩展的区域显示功能区状态栏右侧，并显示在不同的颜色，比主要区域。

通常情况下，状态栏的主区域显示状态通知并扩展的区域显示视图的控件。 尽可能长时间在用户调整功能区状态栏扩展的区域保持可见。

## <a name="example"></a>示例

下面的示例演示了如何使用 `CMFCRibbonStatusBar` 类中的各种方法。 该示例演示如何将新的功能区元素添加到功能区状态栏，将功能区元素添加到功能区状态栏扩展区域添加分隔符，并启用功能区状态栏的常规模式。

[!code-cpp[NVC_MFC_RibbonApp#15](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_1.cpp)]
[!code-cpp[NVC_MFC_RibbonApp#16](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)

[CMFCRibbonStatusBar](../../mfc/reference/cmfcribbonstatusbar-class.md)

## <a name="requirements"></a>要求

**标头：** afxribbonstatusbar.h

##  <a name="adddynamicelement"></a>  CMFCRibbonStatusBar::AddDynamicElement

向功能区状态栏的动态元素。

```
void AddDynamicElement(CMFCRibbonBaseElement* pElement);
```

### <a name="parameters"></a>参数

*pElement*<br/>
[in]一个指向动态元素。

### <a name="remarks"></a>备注

与正则元素不同的动态元素不是可自定义和状态栏的自定义菜单不显示它们。

##  <a name="addelement"></a>  CMFCRibbonStatusBar::AddElement

将新的功能区元素添加到功能区状态栏。

```
void AddElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>参数

*pElement*<br/>
[in]指向添加的元素的指针。

*lpszLabel*<br/>
[in]元素的文本标签。

*bIsVisible*<br/>
[in]如果你想要将元素添加为可见，则返回 FALSE 如果你想要将元素添加为隐藏，则为 TRUE。

##  <a name="addextendedelement"></a>  CMFCRibbonStatusBar::AddExtendedElement

将功能区元素添加到功能区状态栏扩展区域。

```
void AddExtendedElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>参数

*pElement*<br/>
[in]指向添加的元素的指针。

*lpszLabel*<br/>
[in]元素的文本标签。

*bIsVisible*<br/>
[in]如果你想要将元素添加为可见，则返回 FALSE 如果你想要将元素添加为隐藏，则为 TRUE。

### <a name="remarks"></a>备注

扩展区域位于状态栏控件的右侧。

##  <a name="addseparator"></a>  CMFCRibbonStatusBar::AddSeparator

向功能区状态栏的分隔符。

```
void AddSeparator();
```

### <a name="remarks"></a>备注

Framework 方法的后面添加一个分隔符[CMFCRibbonStatusBar::AddElement](#addelement)。 将插入的最后一个元素。

##  <a name="create"></a>  CMFCRibbonStatusBar::Create

创建功能区状态栏。

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>参数

*pParentWnd*<br/>
[in]指向父窗口的指针。

*dwStyle*<br/>
[in]逻辑或组合的控件样式。

*nID*<br/>
[in]状态栏控件 ID。

### <a name="return-value"></a>返回值

如果状态栏成功创建，FALSE 否则，则为 TRUE。

##  <a name="createex"></a>  CMFCRibbonStatusBar::CreateEx

创建功能区状态栏扩展样式。

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle=0,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>参数

*pParentWnd*<br/>
指向父窗口的指针。

*dwCtrlStyle*<br/>
逻辑或组合的创建状态栏对象的其他样式。

*dwStyle*<br/>
状态栏控件样式。

*nID*<br/>
状态栏控件 ID。

### <a name="return-value"></a>返回值

如果状态栏成功创建，FALSE 否则，则为 TRUE。

##  <a name="findbyid"></a>  CMFCRibbonStatusBar::FindByID

有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。

```
CMFCRibbonBaseElement* FindByID(UINT uiCmdID, BOOL = TRUE);
```

### <a name="parameters"></a>参数

[in]*uiCmdID*<br/>
[in]*BOOL*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="findelement"></a>  CMFCRibbonStatusBar::FindElement

返回一个指向的元素的具有指定的命令 id。

```
CMFCRibbonBaseElement* FindElement(UINT uiID);
```

### <a name="parameters"></a>参数

*uiID*<br/>
[in]元素的 ID。

### <a name="return-value"></a>返回值

指向的元素具有指定的命令 id。 如果没有此类元素不为 NULL。

##  <a name="getcount"></a>  CMFCRibbonStatusBar::GetCount

返回位于功能区状态栏的主区域中的元素数目。

```
int GetCount() const;
```

### <a name="return-value"></a>返回值

位于功能区状态栏的主区域中的元素数。

##  <a name="getelement"></a>  CMFCRibbonStatusBar::GetElement

返回一个指向位于指定索引处的元素。

```
CMFCRibbonBaseElement* GetElement(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
[in]指定位于状态栏控件的主区域中的元素的从零开始索引。

### <a name="return-value"></a>返回值

指向位于指定索引处的元素的指针。 如果索引为负或超过状态栏中的元素数为 NULL。

### <a name="remarks"></a>备注

##  <a name="getexcount"></a>  CMFCRibbonStatusBar::GetExCount

返回位于功能区状态栏扩展区域中的元素数目。

```
int GetExCount() const;
```

### <a name="return-value"></a>返回值

位于功能区状态栏扩展区域中的元素数。

##  <a name="getexelement"></a>  CMFCRibbonStatusBar::GetExElement

返回指向元素的指针，该元素位于功能区状态栏扩展区域中的指定索引处。 扩展区域位于状态栏控件的右侧。

```
CMFCRibbonBaseElement* GetExElement(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
[in]指定位于状态栏控件的扩展区域中的元素的从零开始索引。

### <a name="return-value"></a>返回值

一个指向元素的指针，该元素位于功能区状态栏扩展区域中的指定索引处。 则为 NULL *nIndex*为负或超过功能区状态栏扩展区域中的元素数。

### <a name="remarks"></a>备注

##  <a name="getextendedarea"></a>  CMFCRibbonStatusBar::GetExtendedArea

有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>参数

[in]*rect*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getspace"></a>  CMFCRibbonStatusBar::GetSpace

有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。

```
int GetSpace() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="isbottomframe"></a>  CMFCRibbonStatusBar::IsBottomFrame

有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。

```
BOOL IsBottomFrame() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="isextendedelement"></a>  CMFCRibbonStatusBar::IsExtendedElement

有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。

```
BOOL IsExtendedElement(CMFCRibbonBaseElement* pElement) const;
```

### <a name="parameters"></a>参数

[in]*pElement*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="isinformationmode"></a>  CMFCRibbonStatusBar::IsInformationMode

确定是否为功能区状态栏启用信息模式。

```
BOOL IsInformationMode() const;
```

### <a name="return-value"></a>返回值

如果状态栏中的信息模式; 可以起作用，则返回 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

在信息模式下，状态栏隐藏所有正则窗格并显示一个消息字符串。

##  <a name="ondrawinformation"></a>  CMFCRibbonStatusBar::OnDrawInformation

显示在功能区状态栏的信息模式启用时显示的字符串。

```
virtual void OnDrawInformation(
    CDC* pDC,
    CString& strInfo,
    CRect rectInfo);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]指向设备上下文的指针。

*strInfo*<br/>
[in]信息字符串。

*rectInfo*<br/>
[in]边界矩形。

### <a name="remarks"></a>备注

如果你想要自定义状态栏上的信息字符串的外观，重写此方法在派生类中。 使用[CMFCRibbonStatusBar::SetInformation](#setinformation)方法来将状态栏中的信息模式。 在此模式下，状态栏隐藏所有窗格并显示指定的信息字符串*strInfo*。

##  <a name="recalclayout"></a>  CMFCRibbonStatusBar::RecalcLayout

有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>备注

##  <a name="removeall"></a>  CMFCRibbonStatusBar::RemoveAll

从功能区状态栏中移除所有元素。

```
void RemoveAll();
```

##  <a name="removeelement"></a>  CMFCRibbonStatusBar::RemoveElement

移除具有指定的命令 ID 从功能区状态栏的元素。

```
BOOL RemoveElement(UINT uiID);
```

### <a name="parameters"></a>参数

*uiID*<br/>
[in]若要从状态栏中删除元素的 ID。

### <a name="return-value"></a>返回值

如果具有指定的元素则为 TRUE *uiID*中删除。 FALSE 否则为。

##  <a name="setinformation"></a>  CMFCRibbonStatusBar::SetInformation

启用或禁用功能区状态栏的信息模式。

```
void SetInformation(LPCTSTR lpszInfo);
```

### <a name="parameters"></a>参数

*lpszInfo*<br/>
[in]信息字符串。

### <a name="remarks"></a>备注

使用此方法将状态栏中的信息模式。 在此模式下，状态栏隐藏所有窗格并显示指定的信息字符串*lpszInfo*。

当 lpszInfo 为 NULL 时，状态栏将恢复到常规模式。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBar 类](../../mfc/reference/cmfcribbonbar-class.md)<br/>
[CMFCRibbonBaseElement 类](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[CMFCRibbonBar 类](../../mfc/reference/cmfcribbonbar-class.md)
