---
title: CMFCDropDownToolBar 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::AllowShowOnPaneMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadBitmap
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnLButtonUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnMouseMove
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnSendCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnUpdateCmdUI
dev_langs:
- C++
helpviewer_keywords:
- CMFCDropDownToolBar [MFC], AllowShowOnPaneMenu
- CMFCDropDownToolBar [MFC], LoadBitmap
- CMFCDropDownToolBar [MFC], LoadToolBar
- CMFCDropDownToolBar [MFC], OnLButtonUp
- CMFCDropDownToolBar [MFC], OnMouseMove
- CMFCDropDownToolBar [MFC], OnSendCommand
- CMFCDropDownToolBar [MFC], OnUpdateCmdUI
ms.assetid: 78818ec5-83ce-42fa-a0d4-2d9d5ecc8770
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4f56a02f469babe22c8e5cbb9ebb4d6b806499f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369803"
---
# <a name="cmfcdropdowntoolbar-class"></a>CMFCDropDownToolBar 类
当用户按住顶层工具栏按钮时显示的工具栏。  
  
   [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
## <a name="syntax"></a>语法  
  
```  
class CMFCDropDownToolBar : public CMFCToolBar  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCDropDownToolBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|（重写 `CPane::AllowShowOnPaneMenu`。）|  
|[CMFCDropDownToolBar::LoadBitmap](#loadbitmap)|(重写[CMFCToolBar::LoadBitmap](../../mfc/reference/cmfctoolbar-class.md#loadbitmap)。)|  
|[CMFCDropDownToolBar::LoadToolBar](#loadtoolbar)|(重写[CMFCToolBar::LoadToolBar](../../mfc/reference/cmfctoolbar-class.md#loadtoolbar)。)|  
|[CMFCDropDownToolBar::OnLButtonUp](#onlbuttonup)||  
|[CMFCDropDownToolBar::OnMouseMove](#onmousemove)||  
|[CMFCDropDownToolBar::OnSendCommand](#onsendcommand)|（重写 `CMFCToolBar::OnSendCommand`。）|  
|[CMFCDropDownToolBar::OnUpdateCmdUI](#onupdatecmdui)|(重写[CMFCToolBar::OnUpdateCmdUI](http://msdn.microsoft.com/en-us/571a38ab-2a56-4968-9796-273516126f80)。)|  
  
### <a name="remarks"></a>备注  
 A`CMFCDropDownToolBar`对象将弹出菜单的行为与相结合的可视外观的工具栏。 当用户按下并保存一个下拉工具栏按钮 (请参阅[CMFCDropDownToolbarButton 类](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md))，将出现一个下拉工具栏，然后用户可以通过滚动到它并释放鼠标从下拉列表工具栏选择一个按钮按钮。 用户在下拉工具栏中选择一个按钮后，该按钮显示为顶层工具栏上的当前按钮。  
  
 无法自定义下拉工具栏，或将其停靠，并且它不具有拖曳状态。  
  
 下图显示`CMFCDropDownToolBar`对象：  
  
 ![Cmfcdropdowntoolbar 示例](../../mfc/reference/media/cmfcdropdown.png "cmfcdropdown")  
  
 你创建`CMFCDropDownToolBar`对象创建普通的工具栏上的相同方式 (请参阅[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md))。  
  
 要插入到在父级工具栏的下拉工具栏：  
  
 1. 在父级工具栏资源中保留该按钮的虚拟资源 ID。  
  
 2. 创建`CMFCDropDownToolBarButton`对象，其中包含下拉工具栏 (有关详细信息，请参阅[CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md#cmfcdropdowntoolbarbutton))。  
  
 3. 将与 dummy 按钮`CMFCDropDownToolBarButton`通过使用对象[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)。  
  
 工具栏按钮有关的详细信息，请参阅[演练： 将工具栏上的控件](../../mfc/walkthrough-putting-controls-on-toolbars.md)。 下拉工具栏的示例，请参阅示例项目 VisualStudioDemo。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`Create`中的方法`CMFCDropDownToolBar`类。 此代码片段属于[Visual Studio 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#29](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_1.h)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#30](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxdropdowntoolbar.h  
  
##  <a name="allowshowonpanemenu"></a>  CMFCDropDownToolBar::AllowShowOnPaneMenu  

  
```  
virtual BOOL AllowShowOnPaneMenu() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="loadbitmap"></a>  CMFCDropDownToolBar::LoadBitmap  
 从应用程序资源加载工具栏图像。  
  
```  
virtual BOOL LoadBitmap(
    UINT uiResID,  
    UINT uiColdResID=0,  
    UINT uiMenuResID=0,  
    BOOL bLocked=FALSE,  
    UINT uiDisabledResID=0,  
    UINT uiMenuDisabledResID=0);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiResID`  
 用于引用热工具栏图像的位图的资源 ID。  
  
 [in] `uiColdResID`  
 用于引用冷工具栏图像的位图的资源 ID。  
  
 [in] `uiMenuResID`  
 用于引用常规菜单图像的位图的资源 ID。  
  
 [in] `bLocked`  
 `TRUE` 要锁定工具栏;否则为`FALSE`。  
  
 [in] `uiDisabledResID`  
 用于引用禁用工具栏图像的位图的资源 ID。  
  
 [in] `uiMenuDisabledResID`  
 用于引用禁用菜单图像的位图的资源 ID。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则为非零；否则为零。  
  
### <a name="remarks"></a>备注  
 [CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex)方法调用此方法以加载与工具栏关联的图像。 重写此方法以执行图像资源的自定义加载。  
  
 调用 `LoadBitmapEx` 方法以在创建工具栏后加载其他图像。  
  
##  <a name="loadtoolbar"></a>  CMFCDropDownToolBar::LoadToolBar  

  
```  
virtual BOOL LoadToolBar(
    UINT uiResID,  
    UINT uiColdResID = 0,  
    UINT uiMenuResID = 0,
    BOOL = FALSE,  
    UINT uiDisabledResID = 0,  
    UINT uiMenuDisabledResID = 0,  
    UINT uiHotResID = 0);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiResID`  
 [in] `uiColdResID`  
 [in] `uiMenuResID`  
 [in] `BOOL`  
 [in] `uiDisabledResID`  
 [in] `uiMenuDisabledResID`  
 [in] `uiHotResID`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="onlbuttonup"></a>  CMFCDropDownToolBar::OnLButtonUp  

  
```  
afx_msg void OnLButtonUp(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>参数  
 [in] `nFlags`  
 [in] `point`  
  
### <a name="remarks"></a>备注  
  
##  <a name="onmousemove"></a>  CMFCDropDownToolBar::OnMouseMove  

  
```  
afx_msg void OnMouseMove(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>参数  
 [in] `nFlags`  
 [in] `point`  
  
### <a name="remarks"></a>备注  
  
##  <a name="onsendcommand"></a>  CMFCDropDownToolBar::OnSendCommand  

  
```  
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>参数  
 [in] `pButton`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="onupdatecmdui"></a>  CMFCDropDownToolBar::OnUpdateCmdUI  

  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>参数  
 [in] `pTarget`  
 [in] `bDisableIfNoHndler`  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBar::Create](../../mfc/reference/cmfctoolbar-class.md#create)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [CMFCDropDownToolbarButton 类](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)   
 [演练：将控件置于工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)



