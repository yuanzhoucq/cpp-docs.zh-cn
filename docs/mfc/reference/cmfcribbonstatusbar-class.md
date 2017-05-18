---
title: "CMFCRibbonStatusBar 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- CMFCRibbonStatusBar class
ms.assetid: 921eb57f-3b40-49fa-a38c-3f2fb6dc2893
caps.latest.revision: 37
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 8fc2ec14c3f6320f45128bf36824ce7f9b8de9c5
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonstatusbar-class"></a>CMFCRibbonStatusBar 类
`CMFCRibbonStatusBar`类实现的状态栏控件可以显示功能区元素。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCRibbonStatusBar : public CMFCRibbonBar  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCRibbonStatusBar::AddDynamicElement](#adddynamicelement)|将动态元素添加到功能区状态栏。|  
|[CMFCRibbonStatusBar::AddElement](#addelement)|将新的功能区元素添加到功能区状态栏。|  
|[CMFCRibbonStatusBar::AddExtendedElement](#addextendedelement)|将功能区元素添加到功能区状态栏扩展区域中。|  
|[CMFCRibbonStatusBar::AddSeparator](#addseparator)|向功能区状态栏的分隔符。|  
|[CMFCRibbonStatusBar::Create](#create)|创建功能区状态栏。|  
|[CMFCRibbonStatusBar::CreateEx](#createex)|创建功能区状态栏扩展样式。|  
|[CMFCRibbonStatusBar::FindByID](#findbyid)||  
|[CMFCRibbonStatusBar::FindElement](#findelement)|返回一个指向具有指定的命令 ID 的元素|  
|[CMFCRibbonStatusBar::GetCount](#getcount)|返回位于功能区状态栏的主区域中的元素数目。|  
|[CMFCRibbonStatusBar::GetElement](#getelement)|返回指向位于指定索引处的元素的指针。|  
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
|[CMFCRibbonStatusBar::OnDrawInformation](#ondrawinformation)|显示功能区的状态栏当启用此信息模式上显示的信息字符串。|  
  
## <a name="remarks"></a>备注  
 通过使用功能区状态栏的内置的上下文菜单，用户可以更改功能区状态栏上的功能区元素的可见性。 您可以动态添加或移除元素。  
  
 功能区状态栏有两个区域︰ 主区域和扩展的区域。 扩展的区域显示在功能区状态栏的右侧，并显示在另一种颜色，比主区域。  
  
 通常情况下，状态栏的主区域显示状态通知并扩展的区域显示视图控件。 尽可能长时间时在用户调整大小功能区状态栏扩展的区域仍然可见。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法`CMFCRibbonStatusBar`类。 该示例演示如何将新的功能区元素添加到功能区状态栏，将功能区元素添加到功能区状态栏扩展区域中添加一个分隔符，并启用功能区状态栏的常规模式。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&15;](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_1.cpp)]  
[!code-cpp[NVC_MFC_RibbonApp #&16;](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)  
  
 [CMFCRibbonStatusBar](../../mfc/reference/cmfcribbonstatusbar-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxribbonstatusbar.h  
  
##  <a name="adddynamicelement"></a>CMFCRibbonStatusBar::AddDynamicElement  
 将动态元素添加到功能区状态栏。  
  
```  
void AddDynamicElement(CMFCRibbonBaseElement* pElement);
```  
  
### <a name="parameters"></a>参数  
 [in] `pElement`  
 一个指向动态元素。  
  
### <a name="remarks"></a>备注  
 与正则元素不同的动态元素不是可自定义和状态栏的自定义菜单上不显示它们。  
  
##  <a name="addelement"></a>CMFCRibbonStatusBar::AddElement  
 将新的功能区元素添加到功能区状态栏。  
  
```  
void AddElement(
    CMFCRibbonBaseElement* pElement,  
    LPCTSTR lpszLabel,  
    BOOL bIsVisible=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pElement`  
 指向添加的元素的指针。  
  
 [in] `lpszLabel`  
 元素文本标签。  
  
 [in] `bIsVisible`  
 `TRUE`如果您想要将元素添加为可见，`FALSE`如果您想要添加的元素为隐藏。  
  
##  <a name="addextendedelement"></a>CMFCRibbonStatusBar::AddExtendedElement  
 将功能区元素添加到功能区状态栏扩展区域中。  
  
```  
void AddExtendedElement(
    CMFCRibbonBaseElement* pElement,  
    LPCTSTR lpszLabel,  
    BOOL bIsVisible=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pElement`  
 指向添加的元素的指针。  
  
 [in] `lpszLabel`  
 元素文本标签。  
  
 [in] `bIsVisible`  
 `TRUE`如果您想要将元素添加为可见，`FALSE`如果您想要添加的元素为隐藏。  
  
### <a name="remarks"></a>备注  
 扩展区域位于状态栏控件的右侧。  
  
##  <a name="addseparator"></a>CMFCRibbonStatusBar::AddSeparator  
 向功能区状态栏的分隔符。  
  
```  
void AddSeparator();
```  
  
### <a name="remarks"></a>备注  
 框架在方法之后添加分隔符[CMFCRibbonStatusBar::AddElement](#addelement)。 将插入的最后一个元素。  
  
##  <a name="create"></a>CMFCRibbonStatusBar::Create  
 创建功能区状态栏。  
  
```  
BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,  
    UINT nID=AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>参数  
 [in] `pParentWnd`  
 指向父窗口的指针。  
  
 [in] `dwStyle`  
 逻辑或组合的控件样式。  
  
 [in] `nID`  
 状态栏控件 ID。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，创建状态栏`FALSE`否则为。  
  
##  <a name="createex"></a>CMFCRibbonStatusBar::CreateEx  
 创建功能区状态栏扩展样式。  
  
```  
BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle=0,  
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,  
    UINT nID=AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>参数  
 `pParentWnd`  
 指向父窗口的指针。  
  
 `dwCtrlStyle`  
 创建状态栏对象的其他样式逻辑或组合。  
  
 `dwStyle`  
 状态栏控件样式。  
  
 `nID`  
 状态栏控件 ID。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，创建状态栏`FALSE`否则为。  
  
##  <a name="findbyid"></a>CMFCRibbonStatusBar::FindByID  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCRibbonBaseElement* FindByID(UINT uiCmdID, BOOL = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmdID`  
 [in] `BOOL`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="findelement"></a>CMFCRibbonStatusBar::FindElement  
 返回一个指向具有指定的命令 ID 的元素  
  
```  
CMFCRibbonBaseElement* FindElement(UINT uiID);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiID`  
 元素的 ID。  
  
### <a name="return-value"></a>返回值  
 指向具有指定的命令 ID 的元素的指针 `NULL`如果没有此类元素。  
  
##  <a name="getcount"></a>CMFCRibbonStatusBar::GetCount  
 返回位于功能区状态栏的主区域中的元素数目。  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 位于功能区状态栏的主区域中的元素数目。  
  
##  <a name="getelement"></a>CMFCRibbonStatusBar::GetElement  
 返回指向位于指定索引处的元素的指针。  
  
```  
CMFCRibbonBaseElement* GetElement(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 指定该元素位于状态栏控件的主区域中的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 指向位于指定索引处的元素的指针。 `NULL`如果索引为负或超过状态栏中的元素数。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getexcount"></a>CMFCRibbonStatusBar::GetExCount  
 返回位于功能区状态栏扩展区域中的元素数目。  
  
```  
int GetExCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 位于功能区状态栏扩展区域中的元素数目。  
  
##  <a name="getexelement"></a>CMFCRibbonStatusBar::GetExElement  
 返回指向元素的指针，该元素位于功能区状态栏扩展区域中的指定索引处。 扩展区域位于状态栏控件的右侧。  
  
```  
CMFCRibbonBaseElement* GetExElement(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 指定元素的索引（从零开始），该元素位于状态栏控件的扩展区域中。  
  
### <a name="return-value"></a>返回值  
 一个指向元素的指针，该元素位于功能区状态栏扩展区域中的指定索引处。 如果 `NULL` 为负或超过功能区状态栏的扩展区域中的元素数，则为 `nIndex`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getextendedarea"></a>CMFCRibbonStatusBar::GetExtendedArea  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL GetExtendedArea(CRect& rect) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `rect`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getspace"></a>CMFCRibbonStatusBar::GetSpace  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetSpace() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="isbottomframe"></a>CMFCRibbonStatusBar::IsBottomFrame  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsBottomFrame() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="isextendedelement"></a>CMFCRibbonStatusBar::IsExtendedElement  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsExtendedElement(CMFCRibbonBaseElement* pElement) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `pElement`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="isinformationmode"></a>CMFCRibbonStatusBar::IsInformationMode  
 确定是否为功能区状态栏启用信息模式。  
  
```  
BOOL IsInformationMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果状态栏可采用的信息模式;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 在信息模式下，状态栏隐藏所有正则窗格，并显示一个消息字符串。  
  
##  <a name="ondrawinformation"></a>CMFCRibbonStatusBar::OnDrawInformation  
 显示功能区的状态栏当启用此信息模式上显示的字符串。  
  
```  
virtual void OnDrawInformation(
    CDC* pDC,  
    CString& strInfo,  
    CRect rectInfo);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `strInfo`  
 信息字符串。  
  
 [in] `rectInfo`  
 绑定矩形。  
  
### <a name="remarks"></a>备注  
 如果你想要自定义状态栏上的信息字符串的外观，重写此方法在派生类中。 使用[CMFCRibbonStatusBar::SetInformation](#setinformation)方法以便将状态栏置于信息模式。 在此模式下，状态栏隐藏所有窗格，并显示由指定的信息字符串`strInfo`。  
  
##  <a name="recalclayout"></a>CMFCRibbonStatusBar::RecalcLayout  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="removeall"></a>CMFCRibbonStatusBar::RemoveAll  
 从功能区状态栏中移除所有元素。  
  
```  
void RemoveAll();
```  
  
##  <a name="removeelement"></a>CMFCRibbonStatusBar::RemoveElement  
 移除具有指定的命令 ID 从功能区状态栏的元素。  
  
```  
BOOL RemoveElement(UINT uiID);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiID`  
 要从状态栏中删除该元素的 ID。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果具有指定的元素`uiID`删除。 否则为 `FALSE`。  
  
##  <a name="setinformation"></a>CMFCRibbonStatusBar::SetInformation  
 启用或禁用功能区状态栏的信息模式。  
  
```  
void SetInformation(LPCTSTR lpszInfo);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszInfo`  
 信息字符串。  
  
### <a name="remarks"></a>备注  
 使用此方法将状态栏中的信息模式。 在此模式下，状态栏隐藏所有窗格，并显示由指定的信息字符串`lpszInfo`。  
  
 LpszInfo 时`NULL`，状态栏将恢复到常规模式。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBar 类](../../mfc/reference/cmfcribbonbar-class.md)   
 [CMFCRibbonBaseElement 类](../../mfc/reference/cmfcribbonbaseelement-class.md)   
 [CMFCRibbonBar 类](../../mfc/reference/cmfcribbonbar-class.md)

