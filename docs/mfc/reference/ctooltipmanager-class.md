---
title: "CTooltipManager 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager::CreateToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::DeleteToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipParams
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipText
- AFXTOOLTIPMANAGER/CTooltipManager::UpdateTooltips
dev_langs:
- C++
helpviewer_keywords:
- CTooltipManager class
ms.assetid: c71779d7-8b6e-47ef-8500-d4552731fe86
caps.latest.revision: 22
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 3bbf191aacdd318f2afb0bd1a126c3eff290fad6
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="ctooltipmanager-class"></a>CTooltipManager 类
维护有关工具提示的运行时信息。 `CTooltipManager` 类在每个应用程序中实例化一次。  
  
## <a name="syntax"></a>语法  
  
```  
class CTooltipManager : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CTooltipManager::CreateToolTip](#createtooltip)|为指定的 Windows 控件类型创建工具提示控件。|  
|[CTooltipManager::DeleteToolTip](#deletetooltip)|删除工具提示控件。|  
|[CTooltipManager::SetTooltipParams](#settooltipparams)|自定义指定 Windows 控件类型工具提示的可视外观。|  
|[CTooltipManager::SetTooltipText](#settooltiptext)|设置工具提示控件的文本和说明。|  
|[CTooltipManager::UpdateTooltips](#updatetooltips)||  
  
## <a name="remarks"></a>备注  
 使用[CMFCToolTipCtrl 类](../../mfc/reference/cmfctooltipctrl-class.md)， `CMFCToolTipInfo`，和`CTooltipManager`在一起以在您的应用程序中实现自定义工具提示。 有关如何使用这些工具提示类的示例，请参阅[CMFCToolTipCtrl 类](../../mfc/reference/cmfctooltipctrl-class.md)主题。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxtooltipmanager.h  
  
##  <a name="createtooltip"></a>CTooltipManager::CreateToolTip  
 创建工具提示控件。  
  
```  
static BOOL CreateToolTip(
    CToolTipCtrl*& pToolTip,  
    CWnd* pWndParent,  
    UINT nType);
```  
  
### <a name="parameters"></a>参数  
 [out] `pToolTip`  
 工具提示指针的引用。 它设置为该函数将返回指向新创建的工具提示。  
  
 [in] `pWndParent`  
 工具提示的父级。  
  
 [in] `nType`  
 工具提示的类型。  
  
### <a name="return-value"></a>返回值  
 已成功创建了非零值时的工具提示。  
  
### <a name="remarks"></a>备注  
 必须调用[CTooltipManager::DeleteToolTip](#deletetooltip)删除传递回来的工具提示控件`pToolTip`。  
  
 [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)设置它会创建每个工具提示的可视显示参数根据该工具提示键入`nType`指定。 若要更改一个或多个工具提示类型的参数，调用[CTooltipManager::SetTooltipParams](#settooltipparams)。  
  
 下表列出了有效的工具提示类型︰  
  
|工具提示类型|控制类别|示例类型|  
|------------------|----------------------|-------------------|  
|AFX_TOOLTIP_TYPE_BUTTON|一个按钮。|CMFCButton|  
|AFX_TOOLTIP_TYPE_CAPTIONBAR|标题栏。|CMFCCaptionBar|  
|AFX_TOOLTIP_TYPE_DEFAULT|任何不符合另一种类别的控件。|无。|  
|AFX_TOOLTIP_TYPE_DOCKBAR|一个可停靠窗格。|CDockablePane|  
|AFX_TOOLTIP_TYPE_EDIT|文本框。|无。|  
|AFX_TOOLTIP_TYPE_MINIFRAME|袖珍框架。|CPaneFrameWnd|  
|AFX_TOOLTIP_TYPE_PLANNER|计划程序。|无。|  
|AFX_TOOLTIP_TYPE_RIBBON|功能区栏。|CMFCRibbonBar CMFCRibbonPanelMenuBar|  
|AFX_TOOLTIP_TYPE_TAB|一个选项卡上的控件。|CMFCTabCtrl|  
|AFX_TOOLTIP_TYPE_TOOLBAR|一个工具栏。|CMFCToolBar CMFCPopupMenuBar|  
|AFX_TOOLTIP_TYPE_TOOLBOX|工具箱。|无。|  
  
##  <a name="deletetooltip"></a>CTooltipManager::DeleteToolTip  
 删除工具提示控件。  
  
```  
static void DeleteToolTip(CToolTipCtrl*& pToolTip);
```  
  
### <a name="parameters"></a>参数  
 [in, out] `pToolTip`  
 为工具提示将其销毁指针的引用。  
  
### <a name="remarks"></a>备注  
 调用此方法为每个[CToolTipCtrl 类](../../mfc/reference/ctooltipctrl-class.md)创建的[CTooltipManager::CreateToolTip](#createtooltip)。 父控件应调用此方法从其`OnDestroy`处理程序。 这被必需正确移除从 framework 的工具提示。 此方法可设置`pToolTip`到`NULL`它返回之前。  
  
##  <a name="settooltipparams"></a>CTooltipManager::SetTooltipParams  
 自定义在指定的 Windows 控件类型的工具提示控件的外观。  
  
```  
void SetTooltipParams(
    UINT nTypes,  
    CRuntimeClass* pRTC=RUNTIME_CLASS(CMFCToolTipCtrl),  
    CMFCToolTipInfo* pParams=NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `nTypes`  
 指定控件类型。  
  
 [in] `pRTC`  
 运行时类的自定义工具提示。  
  
 [in] `pParams`  
 工具提示的参数。  
  
### <a name="remarks"></a>备注  
 此方法可设置的运行时类和初始参数， [CToolTipManager](../../mfc/reference/ctooltipmanager-class.md)创建工具提示时使用。 当控件调用[CTooltipManager::CreateToolTip](#createtooltip)和工具提示中将类型传递，它是一种类型由`nTypes`，工具提示管理器创建是由指定的运行时类的实例的工具提示控件`pRTC`，并将所指定的参数传递`pParams`到新的工具提示。  
  
 在调用此方法，所有现有的工具提示所有者收到 AFX_WM_UPDATETOOLTIPS 消息并且它们必须通过使用重新创建相应的工具提示[CTooltipManager::CreateToolTip](#createtooltip)。  
  
 `nTypes`可以是任意有效的工具提示的类型[CTooltipManager::CreateToolTip](#createtooltip)用途，也可以是 AFX_TOOLTIP_TYPE_ALL。 如果您传入 AFX_TOOLTIP_TYPE_ALL，所有工具提示类型会受到影响。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`SetTooltipParams`方法`CTooltipManager`类。 此代码段属于[绘制客户端示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_DrawClient #&11;](../../mfc/reference/codesnippet/cpp/ctooltipmanager-class_1.cpp)]  
  
##  <a name="settooltiptext"></a>CTooltipManager::SetTooltipText  
 设置文本和工具提示的说明。  
  
```  
static void SetTooltipText(
    TOOLINFO* pTI,  
    CToolTipCtrl* pToolTip,  
    UINT nType,  
    const CString strText,  
    LPCTSTR lpszDescr=NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `pTI`  
 指向 TOOLINFO 对象的指针。  
  
 [in, out] `pToolTip`  
 指向要为其设置文本和说明的工具提示控件的指针。  
  
 [in] `nType`  
 指定该工具提示与之关联的控件的类型。  
  
 [in] `strText`  
 要将设置为工具提示文本的文本。  
  
 [in] `lpszDescr`  
 指向的工具提示说明的指针。 可以是`NULL`。  
  
### <a name="remarks"></a>备注  
 值`nType`必须是相同的值`nType`参数[CTooltipManager::CreateToolTip](#createtooltip)当您创建工具提示。  
  
##  <a name="updatetooltips"></a>CTooltipManager::UpdateTooltips  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void UpdateTooltips();
```  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolTipCtrl 类](../../mfc/reference/cmfctooltipctrl-class.md)   
 [CMFCToolTipInfo 类](../../mfc/reference/cmfctooltipinfo-class.md)

