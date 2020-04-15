---
title: CMFC 功能状态栏类
ms.date: 11/04/2016
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
ms.openlocfilehash: f76c2014cd3f6ed6e479fb66436224e675c69569
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368817"
---
# <a name="cmfcribbonstatusbar-class"></a>CMFC 功能状态栏类

类`CMFCRibbonStatusBar`实现一个可以显示功能区元素的状态栏控件。

## <a name="syntax"></a>语法

```
class CMFCRibbonStatusBar : public CMFCRibbonBar
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC 功能状态栏：：添加动态元素](#adddynamicelement)|向功能区状态栏添加动态元素。|
|[CMFC 功能状态栏：添加元素](#addelement)|向功能区状态栏添加新功能区元素。|
|[CMFC 功能状态栏：：添加扩展元素](#addextendedelement)|将功能区元素添加到功能区状态栏的扩展区域。|
|[CMFC 功能状态栏：添加分离器](#addseparator)|向功能区状态栏添加分隔符。|
|[CMFC 功能状态栏：创建](#create)|创建功能区状态栏。|
|[CMFC 功能状态栏：创建Ex](#createex)|创建具有扩展样式的功能区状态栏。|
|[CMFC 功能状态栏：查找ByID](#findbyid)||
|[CMFC 功能状态栏：查找元素](#findelement)|返回指向具有指定命令 ID 的元素的指针。|
|[CMFC 功能状态栏：获取计数](#getcount)|返回位于功能区状态栏主区域的元素数。|
|[CMFC 功能状态栏：获取元素](#getelement)|返回指向位于指定索引的元素的指针。|
|[CMFC 功能状态栏：获取ExCount](#getexcount)|返回位于功能区状态栏扩展区域的元素数。|
|[CMFC 功能状态栏：获取Exelement](#getexelement)|返回指向元素的指针，该元素位于功能区状态栏扩展区域中的指定索引处。|
|[CMFC 功能状态栏：获取扩展区域](#getextendedarea)||
|[CMFC 功能状态栏：获取空间](#getspace)||
|[CMFC 功能状态栏：：是底部框架](#isbottomframe)||
|[CMFC 功能状态栏：：扩展元素](#isextendedelement)||
|[CMFC 功能状态栏：信息模式](#isinformationmode)|确定功能区状态栏是否启用了信息模式。|
|[CMFC 功能状态栏：Recalclayout](#recalclayout)|（覆盖[CMFC 功能栏：recalclayout](../../mfc/reference/cmfcribbonbar-class.md#recalclayout).）|
|[CMFC 功能状态栏：：删除所有](#removeall)|从功能区状态栏中删除所有元素。|
|[CMFC 功能状态栏：删除元素](#removeelement)|从功能区状态栏中删除具有指定命令 ID 的元素。|
|[CMFC 功能状态栏：设置信息](#setinformation)|启用或禁用功能区状态栏的信息模式。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CMFC 功能状态栏：：绘制信息](#ondrawinformation)|显示启用信息模式时功能区状态栏上显示的信息字符串。|

## <a name="remarks"></a>备注

用户可以使用功能区状态栏的内置上下文菜单来更改功能区状态栏上的功能区元素的可见性。 您可以动态添加或删除元素。

功能区状态栏有两个区域：主区域和扩展区域。 扩展区域显示在功能区状态栏的右侧，以与主区域不同的颜色显示。

通常，状态栏的主要区域显示状态通知，扩展区域显示视图控件。 当用户调整功能区状态栏的大小时，扩展区域尽可能长时间可见。

## <a name="example"></a>示例

下面的示例演示了如何使用 `CMFCRibbonStatusBar` 类中的各种方法。 该示例演示如何向功能区状态栏添加新功能区元素、向功能区状态栏的扩展区域添加功能区元素、添加分隔符以及启用功能区状态栏的常规模式。

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

**标题：** afxribbonstatusbar.h

## <a name="cmfcribbonstatusbaradddynamicelement"></a><a name="adddynamicelement"></a>CMFC 功能状态栏：：添加动态元素

向功能区状态栏添加动态元素。

```
void AddDynamicElement(CMFCRibbonBaseElement* pElement);
```

### <a name="parameters"></a>参数

*p元素*<br/>
[在]指向动态元素的指针。

### <a name="remarks"></a>备注

与常规元素不同，动态元素不可自定义，状态栏的自定义菜单不显示它们。

## <a name="cmfcribbonstatusbaraddelement"></a><a name="addelement"></a>CMFC 功能状态栏：添加元素

向功能区状态栏添加新功能区元素。

```
void AddElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>参数

*p元素*<br/>
[在]指向添加元素的指针。

*lpszLabel*<br/>
[在]元素的文本标签。

*b可见*<br/>
[在]如果要将元素添加为可见元素，则为 FALSE，如果要将元素添加为隐藏元素，则为 FALSE。

## <a name="cmfcribbonstatusbaraddextendedelement"></a><a name="addextendedelement"></a>CMFC 功能状态栏：：添加扩展元素

将功能区元素添加到功能区状态栏的扩展区域。

```
void AddExtendedElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>参数

*p元素*<br/>
[在]指向添加元素的指针。

*lpszLabel*<br/>
[在]元素的文本标签。

*b可见*<br/>
[在]如果要将元素添加为可见元素，则为 FALSE，如果要将元素添加为隐藏元素，则为 FALSE。

### <a name="remarks"></a>备注

扩展区域位于状态栏控件的右侧。

## <a name="cmfcribbonstatusbaraddseparator"></a><a name="addseparator"></a>CMFC 功能状态栏：添加分离器

向功能区状态栏添加分隔符。

```
void AddSeparator();
```

### <a name="remarks"></a>备注

框架在方法[CMFCRibbonStatus 状态栏后添加分隔符：addElement](#addelement)。 插入最后一个元素。

## <a name="cmfcribbonstatusbarcreate"></a><a name="create"></a>CMFC 功能状态栏：创建

创建功能区状态栏。

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>参数

*pparentwnd*<br/>
[在]指向父窗口的指针。

*dwStyle*<br/>
[在]控件样式的逻辑 OR 组合。

*nID*<br/>
[在]状态栏的控制 ID。

### <a name="return-value"></a>返回值

如果成功创建状态栏，则为 TRUE，否则为 FALSE。

## <a name="cmfcribbonstatusbarcreateex"></a><a name="createex"></a>CMFC 功能状态栏：创建Ex

创建具有扩展样式的功能区状态栏。

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle=0,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>参数

*pparentwnd*<br/>
指向父窗口的指针。

*dwCtrl风格*<br/>
用于创建状态栏对象的其他样式的逻辑 OR 组合。

*dwStyle*<br/>
状态栏的控制样式。

*nID*<br/>
状态栏的控制 ID。

### <a name="return-value"></a>返回值

如果成功创建状态栏，则为 TRUE，否则为 FALSE。

## <a name="cmfcribbonstatusbarfindbyid"></a><a name="findbyid"></a>CMFC 功能状态栏：查找ByID

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

```
CMFCRibbonBaseElement* FindByID(UINT uiCmdID, BOOL = TRUE);
```

### <a name="parameters"></a>参数

[在]*乌伊CmdID*<br/>
[在]*波尔*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcribbonstatusbarfindelement"></a><a name="findelement"></a>CMFC 功能状态栏：查找元素

返回指向具有指定命令 ID 的元素的指针。

```
CMFCRibbonBaseElement* FindElement(UINT uiID);
```

### <a name="parameters"></a>参数

*uiID*<br/>
[在]元素的 ID。

### <a name="return-value"></a>返回值

指向具有指定命令 ID 的元素的指针。 如果没有此类元素，则为 NULL。

## <a name="cmfcribbonstatusbargetcount"></a><a name="getcount"></a>CMFC 功能状态栏：获取计数

返回位于功能区状态栏主区域的元素数。

```
int GetCount() const;
```

### <a name="return-value"></a>返回值

位于功能区状态栏主区域的元素数。

## <a name="cmfcribbonstatusbargetelement"></a><a name="getelement"></a>CMFC 功能状态栏：获取元素

返回指向位于指定索引的元素的指针。

```
CMFCRibbonBaseElement* GetElement(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
[在]指定位于状态栏控件主区域的元素的零基索引。

### <a name="return-value"></a>返回值

指向位于指定索引的元素的指针。 如果索引为负或超过状态栏中的元素数，则为 NULL。

### <a name="remarks"></a>备注

## <a name="cmfcribbonstatusbargetexcount"></a><a name="getexcount"></a>CMFC 功能状态栏：获取ExCount

返回位于功能区状态栏扩展区域的元素数。

```
int GetExCount() const;
```

### <a name="return-value"></a>返回值

位于功能区状态栏扩展区域的元素数。

## <a name="cmfcribbonstatusbargetexelement"></a><a name="getexelement"></a>CMFC 功能状态栏：获取Exelement

返回指向元素的指针，该元素位于功能区状态栏扩展区域中的指定索引处。 扩展区域位于状态栏控件的右侧。

```
CMFCRibbonBaseElement* GetExElement(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
[在]指定位于状态栏控件扩展区域的元素的零基索引。

### <a name="return-value"></a>返回值

一个指向元素的指针，该元素位于功能区状态栏扩展区域中的指定索引处。 如果*nIndex*为负或超过功能区状态栏扩展区域中的元素数，则 NULL。

### <a name="remarks"></a>备注

## <a name="cmfcribbonstatusbargetextendedarea"></a><a name="getextendedarea"></a>CMFC 功能状态栏：获取扩展区域

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>参数

[在]*rect*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcribbonstatusbargetspace"></a><a name="getspace"></a>CMFC 功能状态栏：获取空间

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

```
int GetSpace() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcribbonstatusbarisbottomframe"></a><a name="isbottomframe"></a>CMFC 功能状态栏：：是底部框架

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

```
BOOL IsBottomFrame() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcribbonstatusbarisextendedelement"></a><a name="isextendedelement"></a>CMFC 功能状态栏：：扩展元素

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

```
BOOL IsExtendedElement(CMFCRibbonBaseElement* pElement) const;
```

### <a name="parameters"></a>参数

[在]*p元素*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcribbonstatusbarisinformationmode"></a><a name="isinformationmode"></a>CMFC 功能状态栏：信息模式

确定功能区状态栏是否启用了信息模式。

```
BOOL IsInformationMode() const;
```

### <a name="return-value"></a>返回值

如果状态栏可以在信息模式下工作，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

在信息模式下，状态栏隐藏所有常规窗格并显示消息字符串。

## <a name="cmfcribbonstatusbarondrawinformation"></a><a name="ondrawinformation"></a>CMFC 功能状态栏：：绘制信息

显示启用信息模式时功能区状态栏上显示的字符串。

```
virtual void OnDrawInformation(
    CDC* pDC,
    CString& strInfo,
    CRect rectInfo);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

*斯特信息*<br/>
[在]信息字符串。

*rectInfo*<br/>
[在]边界矩形。

### <a name="remarks"></a>备注

如果要自定义状态栏上信息字符串的外观，请在派生类中重写此方法。 使用[CMFC 功能状态栏：：设置信息](#setinformation)方法将状态栏置于信息模式。 在此模式下，状态栏隐藏所有窗格并显示*strInfo*指定的信息字符串。

## <a name="cmfcribbonstatusbarrecalclayout"></a><a name="recalclayout"></a>CMFC 功能状态栏：Recalclayout

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>备注

## <a name="cmfcribbonstatusbarremoveall"></a><a name="removeall"></a>CMFC 功能状态栏：：删除所有

从功能区状态栏中删除所有元素。

```
void RemoveAll();
```

## <a name="cmfcribbonstatusbarremoveelement"></a><a name="removeelement"></a>CMFC 功能状态栏：删除元素

从功能区状态栏中删除具有指定命令 ID 的元素。

```
BOOL RemoveElement(UINT uiID);
```

### <a name="parameters"></a>参数

*uiID*<br/>
[在]要从状态栏中删除的元素的 ID。

### <a name="return-value"></a>返回值

如果删除了具有指定*uiID*的元素，则为 TRUE。 否则。

## <a name="cmfcribbonstatusbarsetinformation"></a><a name="setinformation"></a>CMFC 功能状态栏：设置信息

启用或禁用功能区状态栏的信息模式。

```
void SetInformation(LPCTSTR lpszInfo);
```

### <a name="parameters"></a>参数

*lpszInfo*<br/>
[在]信息字符串。

### <a name="remarks"></a>备注

使用此方法将状态栏置于信息模式。 在此模式下，状态栏隐藏所有窗格并显示*lpszInfo*指定的信息字符串。

当 lpszInfo 为 NULL 时，状态栏将恢复为常规模式。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFC剪条类](../../mfc/reference/cmfcribbonbar-class.md)<br/>
[CMFCRibbonBaseElement 类](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[CMFC剪条类](../../mfc/reference/cmfcribbonbar-class.md)
