---
title: CTabView 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTabView
- AFXTABVIEW/CTabView
- AFXTABVIEW/CTabView::AddView
- AFXTABVIEW/CTabView::FindTab
- AFXTABVIEW/CTabView::GetActiveView
- AFXTABVIEW/CTabView::GetTabControl
- AFXTABVIEW/CTabView::RemoveView
- AFXTABVIEW/CTabView::SetActiveView
- AFXTABVIEW/CTabView::IsScrollBar
- AFXTABVIEW/CTabView::OnActivateView
dev_langs:
- C++
helpviewer_keywords:
- CTabView [MFC], AddView
- CTabView [MFC], FindTab
- CTabView [MFC], GetActiveView
- CTabView [MFC], GetTabControl
- CTabView [MFC], RemoveView
- CTabView [MFC], SetActiveView
- CTabView [MFC], IsScrollBar
- CTabView [MFC], OnActivateView
ms.assetid: 8e6ecd9d-d28d-432b-8ec8-0446f0204d52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08c0cff2f6586ab5e385808fb806ed435b00bfc9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="ctabview-class"></a>CTabView 类
`CTabView`的类简化了使用选项卡控件类 ( [CMFCTabCtrl](../../mfc/reference/ctabview-class.md)) 中使用 MFC 文档/视图体系结构的应用程序。  
  
## <a name="syntax"></a>语法  
  
```  
class CTabbedView : public CView  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CTabView::AddView](#addview)|将新视图添加到选项卡控件。|  
|[CTabView::FindTab](#findtab)|返回选项卡控件中指定的视图的索引。|  
|[CTabView::GetActiveView](#getactiveview)|将指针返回到当前处于活动状态视图|  
|[CTabView::GetTabControl](#gettabcontrol)|返回与视图相关联的选项卡控件的引用。|  
|[CTabView::RemoveView](#removeview)|从选项卡控件中删除视图。|  
|[CTabView::SetActiveView](#setactiveview)|使视图处于活动状态。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CTabView::IsScrollBar](#isscrollbar)|创建选项卡视图，以确定此选项卡视图是否具有共享水平滚动条时，由框架调用。|  
|[CTabView::OnActivateView](#onactivateview)|选项卡视图进行活动或非活动时，由框架调用。|  
  
## <a name="remarks"></a>备注  
 此类可以轻松将选项卡式的视图放入文档/视图应用程序。 `CTabView` 是`CView`-派生类，该类包含一个嵌入`CMFCTabCtrl`对象。 `CTabView` 处理支持所需的所有消息`CMFCTabCtrl`对象。 只需从派生类`CTabView`，并将其插入你的应用程序，然后添加`CView`-通过使用派生类`AddView`方法。 选项卡控件将显示为选项卡的这些视图。  
  
 例如，你可能拥有的文档，可以表示不同的方式： 作为电子表格、 图表、 可编辑窗体中，依次类推。 你可以创建根据需要绘制数据的单个视图，它们插入你`CTabView`-派生对象并将它们而无需任何其他编码选项卡式。  
  
 [TabbedView 示例： MFC 选项卡式视图应用程序](../../visual-cpp-samples.md)阐释了的用法`CTabView`。  
  
## <a name="example"></a>示例  
 下面的示例演示如何`CTabView`TabbedView 示例中使用。  
  
 [!code-cpp[NVC_MFC_TabbedView#1](../../mfc/reference/codesnippet/cpp/ctabview-class_1.h)]  
  
## <a name="requirements"></a>要求  
 **标头：** afxTabView.h  
  
##  <a name="addview"></a>  CTabView::AddView  
 将视图添加到选项卡控件。  
  
```  
int AddView(
    CRuntimeClass* pViewClass,  
    const CString& strViewLabel,  
    int iIndex=-1,  
    CCreateContext* pContext=NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `pViewClass`  
 指向插入视图的运行时类的指针。  
  
 [in] `strViewLabel`  
 指定选项卡的文本。  
  
 [in] `iIndex`  
 指定在其中插入视图的从零开始的位置。 如果位置为-1 结尾处插入新选项卡。  
  
 [in] `pContext`  
 一个指向`CCreateContext`的视图。  
  
### <a name="return-value"></a>返回值  
 视图索引，如果此方法成功。 否则为-1。  
  
### <a name="remarks"></a>备注  
 调用此函数可将视图添加到选项卡控件嵌入在框架中。  
  
##  <a name="findtab"></a>  CTabView::FindTab  
 返回选项卡控件中指定的视图的索引。  
  
```  
int FindTab(HWND hWndView) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `hWndView`  
 视图的句柄。  
  
### <a name="return-value"></a>返回值  
 如果它找到，则该视图的索引否则为-1。  
  
### <a name="remarks"></a>备注  
 调用此函数可检索具有指定的句柄的视图的索引。  
  
##  <a name="getactiveview"></a>  CTabView::GetActiveView  
 将指针返回到当前处于活动状态的视图。  
  
```  
CView* GetActiveView() const;  
```  
  
### <a name="return-value"></a>返回值  
 活动视图中，指向的有效指针或`NULL`如果没有任何活动的视图。  
  
### <a name="remarks"></a>备注  
  
##  <a name="gettabcontrol"></a>  CTabView::GetTabControl  
 返回与视图相关联的选项卡控件的引用。  
  
```  
DECLARE_DYNCREATE CMFCTabCtrl& GetTabControl();
```  
  
### <a name="return-value"></a>返回值  
 对与视图关联的选项卡控件的引用。  
  
##  <a name="isscrollbar"></a>  CTabView::IsScrollBar  
 创建选项卡视图，以确定此选项卡视图是否具有共享水平滚动条时，由框架调用。  
  
```  
virtual BOOL IsScrollBar() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果应与共享的滚动条一起创建选项卡视图。 否则为 `FALSE`。  
  
### <a name="remarks"></a>备注  
 框架在调用此方法时`CTabView`正在创建对象。  
  
 重写`IsScrollBar`中的方法`CTabView`-派生类，并返回`TRUE`如果你想要创建具有共享水平滚动条的视图。  
  
##  <a name="onactivateview"></a>  CTabView::OnActivateView  
 选项卡视图进行活动或非活动时，由框架调用。  
  
```  
virtual void OnActivateView(CView* view);
```  
  
### <a name="parameters"></a>参数  
 [in] `view`  
 指向该视图的指针。  
  
### <a name="remarks"></a>备注  
 默认实现不执行任何操作。 重写此方法在`CTabView`-派生类来处理此通知。  
  
##  <a name="removeview"></a>  CTabView::RemoveView  
 从选项卡控件中删除视图。  
  
```  
BOOL RemoveView(int iTabNum);
```  
  
### <a name="parameters"></a>参数  
 [in] `iTabNum`  
 要删除的视图索引。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，已删除的视图的索引。 否则为-1。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setactiveview"></a>  CTabView::SetActiveView  
 使视图处于活动状态。  
  
```  
BOOL SetActiveView(int iTabNum);
```  
  
### <a name="parameters"></a>参数  
 [in] `iTabNum`  
 选项卡视图的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果指定的视图已激活，`FALSE`如果视图的索引无效。  
  
### <a name="remarks"></a>备注  
 有关详细信息请参阅[CMFCTabCtrl::SetActiveTab](../../mfc/reference/cmfctabctrl-class.md#setactivetab)。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCTabCtrl](../../mfc/reference/ctabview-class.md)   
 [CView 类](../../mfc/reference/cview-class.md)
