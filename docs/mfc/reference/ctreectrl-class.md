---
title: "CTreeCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTreeCtrl
- AFXCMN/CTreeCtrl
- AFXCMN/CTreeCtrl::CTreeCtrl
- AFXCMN/CTreeCtrl::Create
- AFXCMN/CTreeCtrl::CreateDragImage
- AFXCMN/CTreeCtrl::CreateEx
- AFXCMN/CTreeCtrl::DeleteAllItems
- AFXCMN/CTreeCtrl::DeleteItem
- AFXCMN/CTreeCtrl::EditLabel
- AFXCMN/CTreeCtrl::EndEditLabelNow
- AFXCMN/CTreeCtrl::EnsureVisible
- AFXCMN/CTreeCtrl::Expand
- AFXCMN/CTreeCtrl::GetBkColor
- AFXCMN/CTreeCtrl::GetCheck
- AFXCMN/CTreeCtrl::GetChildItem
- AFXCMN/CTreeCtrl::GetCount
- AFXCMN/CTreeCtrl::GetDropHilightItem
- AFXCMN/CTreeCtrl::GetEditControl
- AFXCMN/CTreeCtrl::GetExtendedStyle
- AFXCMN/CTreeCtrl::GetFirstVisibleItem
- AFXCMN/CTreeCtrl::GetImageList
- AFXCMN/CTreeCtrl::GetIndent
- AFXCMN/CTreeCtrl::GetInsertMarkColor
- AFXCMN/CTreeCtrl::GetItem
- AFXCMN/CTreeCtrl::GetItemData
- AFXCMN/CTreeCtrl::GetItemExpandedImageIndex
- AFXCMN/CTreeCtrl::GetItemHeight
- AFXCMN/CTreeCtrl::GetItemImage
- AFXCMN/CTreeCtrl::GetItemPartRect
- AFXCMN/CTreeCtrl::GetItemRect
- AFXCMN/CTreeCtrl::GetItemState
- AFXCMN/CTreeCtrl::GetItemStateEx
- AFXCMN/CTreeCtrl::GetItemText
- AFXCMN/CTreeCtrl::GetLastVisibleItem
- AFXCMN/CTreeCtrl::GetLineColor
- AFXCMN/CTreeCtrl::GetNextItem
- AFXCMN/CTreeCtrl::GetNextSiblingItem
- AFXCMN/CTreeCtrl::GetNextVisibleItem
- AFXCMN/CTreeCtrl::GetParentItem
- AFXCMN/CTreeCtrl::GetPrevSiblingItem
- AFXCMN/CTreeCtrl::GetPrevVisibleItem
- AFXCMN/CTreeCtrl::GetRootItem
- AFXCMN/CTreeCtrl::GetScrollTime
- AFXCMN/CTreeCtrl::GetSelectedCount
- AFXCMN/CTreeCtrl::GetSelectedItem
- AFXCMN/CTreeCtrl::GetTextColor
- AFXCMN/CTreeCtrl::GetToolTips
- AFXCMN/CTreeCtrl::GetVisibleCount
- AFXCMN/CTreeCtrl::HitTest
- AFXCMN/CTreeCtrl::InsertItem
- AFXCMN/CTreeCtrl::ItemHasChildren
- AFXCMN/CTreeCtrl::MapAccIdToItem
- AFXCMN/CTreeCtrl::MapItemToAccID
- AFXCMN/CTreeCtrl::Select
- AFXCMN/CTreeCtrl::SelectDropTarget
- AFXCMN/CTreeCtrl::SelectItem
- AFXCMN/CTreeCtrl::SelectSetFirstVisible
- AFXCMN/CTreeCtrl::SetAutoscrollInfo
- AFXCMN/CTreeCtrl::SetBkColor
- AFXCMN/CTreeCtrl::SetCheck
- AFXCMN/CTreeCtrl::SetExtendedStyle
- AFXCMN/CTreeCtrl::SetImageList
- AFXCMN/CTreeCtrl::SetIndent
- AFXCMN/CTreeCtrl::SetInsertMark
- AFXCMN/CTreeCtrl::SetInsertMarkColor
- AFXCMN/CTreeCtrl::SetItem
- AFXCMN/CTreeCtrl::SetItemData
- AFXCMN/CTreeCtrl::SetItemExpandedImageIndex
- AFXCMN/CTreeCtrl::SetItemHeight
- AFXCMN/CTreeCtrl::SetItemImage
- AFXCMN/CTreeCtrl::SetItemState
- AFXCMN/CTreeCtrl::SetItemStateEx
- AFXCMN/CTreeCtrl::SetItemText
- AFXCMN/CTreeCtrl::SetLineColor
- AFXCMN/CTreeCtrl::SetScrollTime
- AFXCMN/CTreeCtrl::SetTextColor
- AFXCMN/CTreeCtrl::SetToolTips
- AFXCMN/CTreeCtrl::ShowInfoTip
- AFXCMN/CTreeCtrl::SortChildren
- AFXCMN/CTreeCtrl::SortChildrenCB
dev_langs:
- C++
helpviewer_keywords:
- directory lists
- tree view controls
- file lists [C++]
- CTreeCtrl class
ms.assetid: 96e20031-6161-4143-8c12-8d1816c66d90
caps.latest.revision: 23
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 5341367b44540e2d0991fd61e52611826bbdcda1
ms.lasthandoff: 02/24/2017

---
# <a name="ctreectrl-class"></a>CTreeCtrl Class
提供 Windows 公共树视图控件的功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CTreeCtrl : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CTreeCtrl::CTreeCtrl](#ctreectrl)|构造 `CTreeCtrl` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CTreeCtrl::Create](#create)|创建的树视图控件，并将其附加到`CTreeCtrl`对象。|  
|[CTreeCtrl::CreateDragImage](#createdragimage)|创建指定的树视图项一个拖动位图。|  
|[CTreeCtrl::CreateEx](#createex)|创建具有指定的 Windows 扩展样式的树控件并将其附加到`CTreeCtrl`对象。|  
|[CTreeCtrl::DeleteAllItems](#deleteallitems)|删除在树视图控件中的所有项目。|  
|[CTreeCtrl::DeleteItem](#deleteitem)|删除的树视图控件中的新项。|  
|[CTreeCtrl::EditLabel](#editlabel)|编辑指定的树视图项在原位。|  
|[CTreeCtrl::EndEditLabelNow](#endeditlabelnow)|取消当前的树视图控件中的树视图项的标签上的编辑操作。|  
|[CTreeCtrl::EnsureVisible](#ensurevisible)|确保其树视图控件中可见的树视图项。|  
|[CTreeCtrl::Expand](#expand)|文件夹将展开或折叠，指定的树视图项的子项。|  
|[CTreeCtrl::GetBkColor](#getbkcolor)|检索控件的当前背景色。|  
|[CTreeCtrl::GetCheck](#getcheck)|检索树控件项的复选状态。|  
|[CTreeCtrl::GetChildItem](#getchilditem)|检索指定的树视图项的子级。|  
|[CTreeCtrl::GetCount](#getcount)|检索与树视图控件相关联的树项的数目。|  
|[CTreeCtrl::GetDropHilightItem](#getdrophilightitem)|检索拖放操作的目标。|  
|[CTreeCtrl::GetEditControl](#geteditcontrol)|检索用于编辑指定的树视图项的编辑控件的句柄。|  
|[CTreeCtrl::GetExtendedStyle](#getextendedstyle)|检索当前的树视图控件使用的扩展的样式。|  
|[CTreeCtrl::GetFirstVisibleItem](#getfirstvisibleitem)|检索指定的树视图项的第一个可见项。|  
|[CTreeCtrl::GetImageList](#getimagelist)|检索与树视图控件关联的图像列表的句柄。|  
|[CTreeCtrl::GetIndent](#getindent)|从其父级中检索的树视图项的偏移量 （以像素为单位）。|  
|[CTreeCtrl::GetInsertMarkColor](#getinsertmarkcolor)|检索用来绘制树视图中插入标记的颜色。|  
|[CTreeCtrl::GetItem](#getitem)|检索指定的树视图项的属性。|  
|[CTreeCtrl::GetItemData](#getitemdata)|返回与项相关联的 32 位应用程序特定的值。|  
|[CTreeCtrl::GetItemExpandedImageIndex](#getitemexpandedimageindex)|检索当前的树视图控件的指定的项处于展开状态时要显示图像的索引。|  
|[CTreeCtrl::GetItemHeight](#getitemheight)|检索树视图项的当前的高度。|  
|[CTreeCtrl::GetItemImage](#getitemimage)|检索与项目关联的图像。|  
|[CTreeCtrl::GetItemPartRect](#getitempartrect)|检索当前的树视图控件中的指定项的指定部分的边框。|  
|[CTreeCtrl::GetItemRect](#getitemrect)|检索的树视图项的边框。|  
|[CTreeCtrl::GetItemState](#getitemstate)|返回某项的状态。|  
|[CTreeCtrl::GetItemStateEx](#getitemstateex)|检索当前的树视图控件中的指定项的扩展的状态。|  
|[CTreeCtrl::GetItemText](#getitemtext)|返回某项的文本。|  
|[CTreeCtrl::GetLastVisibleItem](#getlastvisibleitem)|检索当前的树视图控件中最后一个展开的项目。|  
|[CTreeCtrl::GetLineColor](#getlinecolor)|检索树视图控件的当前线条颜色。|  
|[CTreeCtrl::GetNextItem](#getnextitem)|检索下一个匹配的指定的关系的树视图项。|  
|[CTreeCtrl::GetNextSiblingItem](#getnextsiblingitem)|检索指定的树视图项的下一个同级。|  
|[CTreeCtrl::GetNextVisibleItem](#getnextvisibleitem)|检索指定的树视图项的下一个可见项。|  
|[CTreeCtrl::GetParentItem](#getparentitem)|检索指定的树视图项的父项。|  
|[CTreeCtrl::GetPrevSiblingItem](#getprevsiblingitem)|检索指定的树视图项的上一个同级。|  
|[CTreeCtrl::GetPrevVisibleItem](#getprevvisibleitem)|检索指定的树视图项的上一个可见项。|  
|[CTreeCtrl::GetRootItem](#getrootitem)|检索指定的树视图项的根。|  
|[CTreeCtrl::GetScrollTime](#getscrolltime)|检索树视图控件的最大滚动时间。|  
|[CTreeCtrl::GetSelectedCount](#getselectedcount)|检索当前的树视图控件中选定项的数目。|  
|[CTreeCtrl::GetSelectedItem](#getselecteditem)|检索当前所选的树视图项。|  
|[CTreeCtrl::GetTextColor](#gettextcolor)|检索控件的当前文本颜色。|  
|[CTreeCtrl::GetToolTips](#gettooltips)|检索子树视图控件所使用的工具提示控件的句柄。|  
|[CTreeCtrl::GetVisibleCount](#getvisiblecount)|检索与树视图控件相关联的可见的树项的数目。|  
|[CTreeCtrl::HitTest](#hittest)|返回与相关的游标的当前位置`CTreeCtrl`对象。|  
|[CTreeCtrl::InsertItem](#insertitem)|在树视图控件中插入新项。|  
|[CTreeCtrl::ItemHasChildren](#itemhaschildren)|返回非零，如果指定的项具有子项。|  
|[CTreeCtrl::MapAccIdToItem](#mapaccidtoitem)|将指定的辅助功能标识符映射到当前的树视图控件中的树视图项的句柄。|  
|[CTreeCtrl::MapItemToAccID](#mapitemtoaccid)|将指定的句柄映射到为可访问性标识符对于当前的树视图控件中的树视图项。|  
|[CTreeCtrl::Select](#select)|选择、 滚动到视图中，或重新绘制指定的树视图项。|  
|[CTreeCtrl::SelectDropTarget](#selectdroptarget)|为目标的拖放操作将重新绘制树项目。|  
|[CTreeCtrl::SelectItem](#selectitem)|选择指定的树视图项。|  
|[CTreeCtrl::SelectSetFirstVisible](#selectsetfirstvisible)|选择指定的树视图项作为第一个可见项。|  
|[CTreeCtrl::SetAutoscrollInfo](#setautoscrollinfo)|设置当前的树视图控件的滚动率。|  
|[CTreeCtrl::SetBkColor](#setbkcolor)|设置控件的背景色。|  
|[CTreeCtrl::SetCheck](#setcheck)|设置树控件项的复选状态。|  
|[CTreeCtrl::SetExtendedStyle](#setextendedstyle)|设置当前的树视图控件的扩展的样式。|  
|[CTreeCtrl::SetImageList](#setimagelist)|设置与树视图控件关联的图像列表的句柄。|  
|[CTreeCtrl::SetIndent](#setindent)|设置从其父树视图项的偏移量 （以像素为单位）。|  
|[CTreeCtrl::SetInsertMark](#setinsertmark)|设置树视图控件中插入标记。|  
|[CTreeCtrl::SetInsertMarkColor](#setinsertmarkcolor)|设置用于绘制树视图中插入标记的颜色。|  
|[CTreeCtrl::SetItem](#setitem)|设置为指定的树视图项的属性。|  
|[CTreeCtrl::SetItemData](#setitemdata)|设置与项目关联的 32 位应用程序特定的值。|  
|[CTreeCtrl::SetItemExpandedImageIndex](#setitemexpandedimageindex)|设置要在当前的树视图控件的指定的项处于展开状态时显示的图像的索引。|  
|[CTreeCtrl::SetItemHeight](#setitemheight)|设置树的高度查看项。|  
|[CTreeCtrl::SetItemImage](#setitemimage)|将图像与项相关联。|  
|[CTreeCtrl::SetItemState](#setitemstate)|设置项的状态。|  
|[CTreeCtrl::SetItemStateEx](#setitemstateex)|对于当前的树视图控件中设置指定项的扩展的状态。|  
|[CTreeCtrl::SetItemText](#setitemtext)|设置项的文本。|  
|[CTreeCtrl::SetLineColor](#setlinecolor)|设置树视图控件的当前线条颜色。|  
|[CTreeCtrl::SetScrollTime](#setscrolltime)|设置树视图控件的最大滚动时间。|  
|[CTreeCtrl::SetTextColor](#settextcolor)|设置控件的文本颜色。|  
|[CTreeCtrl::SetToolTips](#settooltips)|设置树视图控件的子工具提示控件。|  
|[CTreeCtrl::ShowInfoTip](#showinfotip)|显示当前的树视图控件中的指定项目的信息提示。|  
|[CTreeCtrl::SortChildren](#sortchildren)|对给定的父项的子级进行排序。|  
|[CTreeCtrl::SortChildrenCB](#sortchildrencb)|对排序使用的应用程序定义的排序函数给定的父项的子级。|  
  
## <a name="remarks"></a>备注  
 "树视图控件"是一个窗口，在磁盘上显示的项，如文档中的标题中一种索引，或文件和目录的项的层次列表。 每个项包含一个标签和一个可选位图图像，且每个项可以有一个与之关联的子项列表。 通过单击项，用户可以展开和折叠关联的子项列表。  
  
 此控件 (并因此`CTreeCtrl`类) 仅适用于在 Windows 98 和 Windows NT 版本 4 下运行的程序和更高版本。  
  
 有关详细信息使用`CTreeCtrl`，请参阅︰  
  
- [控件](../../mfc/controls-mfc.md)  
  
- [使用 CTreeCtrl](../../mfc/using-ctreectrl.md)  
  
- [树视图控件参考](http://msdn.microsoft.com/library/windows/desktop/bb759988)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
-   知识库文章 Q222905︰ 如何︰ 为 CTreeCtrl 显示上下文菜单  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CTreeCtrl`  
  
## <a name="requirements"></a>要求  
 **标头：** afxcmn.h  
  
##  <a name="create"></a>CTreeCtrl::Create  
 如果您指定的目录树控件在对话框模板，或者您使用[CTreeView](../../mfc/reference/ctreeview-class.md)，树控件在创建对话框或视图时自动创建。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 指定树视图控件的样式。 应用中所述的窗口样式[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)，和的任意组合[树视图控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760013)中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `rect`  
 指定树视图控件的大小和位置。 它可为[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构。  
  
 `pParentWnd`  
 指定树视图控件的父窗口，通常`CDialog`。 它不能**NULL**。  
  
 `nID`  
 指定树视图控件的 id。  
  
### <a name="return-value"></a>返回值  
 如果初始化成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 如果您想要创建的树控件用作子窗口的某些其他窗口，使用**创建**成员函数。 如果您创建树控件使用**创建**，必须将其传递**WS_VISIBLE**，除了其他树视图样式。  
  
 您构造`CTreeCtrl`分两个步骤。 第一次调用构造函数中，然后调用**创建**，它创建树视图控件，并将其附加到`CTreeCtrl`对象。  
  
 若要创建具有扩展的窗口样式的树控件，调用[CreateEx](#createex)而不是**创建**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&1;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_1.cpp)]  
  
##  <a name="createex"></a>CTreeCtrl::CreateEx  
 调用此函数可创建的控件 （子窗口），并将其与关联`CTreeCtrl`对象。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwExStyle`  
 指定要创建的控件的扩展的样式。 扩展窗口样式的列表，请参阅`dwExStyle`参数[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwStyle`  
 指定树视图控件的样式。 应用中所述的窗口样式[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)，和的任意组合[树视图控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760013)中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `rect`  
 对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构的结构描述的大小和窗口，在中创建的工作区坐标位置`pParentWnd`。  
  
 `pParentWnd`  
 指向控件的父级的窗口的指针。  
  
 `nID`  
 控件的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为非否则返回 0。  
  
### <a name="remarks"></a>备注  
 使用`CreateEx`而不是[创建](#create)应用扩展的窗口样式、 指定的 Windows 扩展的样式前言**WS_EX_**。  
  
##  <a name="createdragimage"></a>CTreeCtrl::CreateDragImage  
 调用此函数可在树视图控件中创建给定项目的一个拖动位图、 创建的位图图像列表并将该位图添加到图像列表。  
  
```  
CImageList* CreateDragImage(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 要拖动的树项的句柄。  
  
### <a name="return-value"></a>返回值  
 指针到向其中拖动位图添加，如果成功，则图像列表否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 应用程序使用的图像列表函数时将项拖显示图像。  
  
 `CImageList`对象是永久性的并且必须将其完成后删除。 例如:   
  
 [!code-cpp[NVC_MFC_CTreeCtrl #&2;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_2.cpp)]  
  
##  <a name="ctreectrl"></a>CTreeCtrl::CTreeCtrl  
 构造 `CTreeCtrl` 对象。  
  
```  
CTreeCtrl();
```  
  
##  <a name="deleteallitems"></a>CTreeCtrl::DeleteAllItems  
 调用此函数可从树视图控件中删除所有项。  
  
```  
BOOL DeleteAllItems();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&3;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_3.cpp)]  
  
##  <a name="deleteitem"></a>CTreeCtrl::DeleteItem  
 调用此函数可从树视图控件中删除项目。  
  
```  
BOOL DeleteItem(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 要删除的树项的句柄。 如果*hitem*具有**TVI_ROOT**值，将从树视图控件中删除所有项。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&4;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_4.cpp)]  
  
##  <a name="editlabel"></a>CTreeCtrl::EditLabel  
 调用此函数可开始进行就地编辑的指定的项的文本。  
  
```  
CEdit* EditLabel(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 要编辑的树项的句柄。  
  
### <a name="return-value"></a>返回值  
 如果成功，一个指向`CEdit`对象，它是用于编辑的项文本; 否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 编辑是通过项的文本替换为包含文本的单行编辑控件实现的。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&5;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_5.cpp)]  
  
##  <a name="endeditlabelnow"></a>CTreeCtrl::EndEditLabelNow  
 结束当前的树视图控件中的树视图项的标签上的编辑操作。  
  
```  
BOOL EndEditLabelNow(BOOL fCancelWithoutSave);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `fCancelWithoutSave`|`true`若要放弃对树视图项的更改，然后结束编辑操作，才能或`false`结束操作之前将更改保存到的树视图项。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[TVM_ENDEDITLABELNOW](http://msdn.microsoft.com/library/windows/desktop/bb773564)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="ensurevisible"></a>CTreeCtrl::EnsureVisible  
 调用此函数可确保可见的树视图项。  
  
```  
BOOL EnsureVisible(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 被设置为可见的树项句柄。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**系统如果滚动要确保指定的项是可见的树视图控件中的项。 否则，返回值是**FALSE**。  
  
### <a name="remarks"></a>备注  
 如有必要，该函数，则展开父项目或滚动树视图控件，以使项可见。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&6;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_6.cpp)]  
  
##  <a name="expand"></a>CTreeCtrl::Expand  
 如果有的话与给定的父项相关联，则调用此函数可展开或折叠子项目的列表。  
  
```  
BOOL Expand(
    HTREEITEM hItem,  
    UINT nCode);
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 正在扩展的树项句柄。  
  
 `nCode`  
 一个标志，指示要采取的操作类型。 此标志可以具有下列值之一︰  
  
- `TVE_COLLAPSE`折叠列表。  
  
- `TVE_COLLAPSERESET`折叠列表，并删除子项目。 **TVIS_EXPANDEDONCE**重置状态标志。 此标志必须与使用`TVE_COLLAPSE`标志。  
  
- `TVE_EXPAND`扩展的列表。  
  
- `TVE_TOGGLE`如果当前已展开，或者如果当前处于折叠状态即可展开它，将折叠列表。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
  请参阅示例[CTreeCtrl::EnsureVisible](#ensurevisible)。  
  
##  <a name="getbkcolor"></a>CTreeCtrl::GetBkColor  
 此成员函数实现的行为的 Win32 消息[TVM_GETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773570)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个**COLORREF**值，该值表示控件的当前窗口的背景色。 如果此值为-1，该控件使用的系统窗口颜色。 在这种情况下，可以使用`::GetSysColor(COLOR_WINDOW)`才能使用该控件的当前系统颜色。  
  
### <a name="example"></a>示例  
  请参阅示例[CTreeCtrl::SetTextColor](#settextcolor)。  
  
##  <a name="getcheck"></a>CTreeCtrl::GetCheck  
 调用此成员函数可检索项的复选状态。  
  
```  
BOOL GetCheck(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 **HTREEITEM**有关可用于接收的状态信息。  
  
### <a name="return-value"></a>返回值  
 非零，如果已选中的树控件项目;否则为 0。  
  
### <a name="example"></a>示例  
  请参阅示例[CTreeCtrl::SetCheck](#setcheck)。  
  
##  <a name="getchilditem"></a>CTreeCtrl::GetChildItem  
 调用此函数可检索的树视图项，是由指定的项的子级`hItem`。  
  
```  
HTREEITEM GetChildItem(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 树项的句柄。  
  
### <a name="return-value"></a>返回值  
 子项目，如果成功，则该句柄否则为**NULL**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&7;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_7.cpp)]  
  
##  <a name="getcount"></a>CTreeCtrl::GetCount  
 调用此函数可检索树视图控件中项的计数。  
  
```  
UINT GetCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 在树视图控件中的项的数目。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&8;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_8.cpp)]  
  
##  <a name="getdrophilightitem"></a>CTreeCtrl::GetDropHilightItem  
 调用此函数可检索项是拖放操作的目标。  
  
```  
HTREEITEM GetDropHilightItem() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则删除项的句柄否则为**NULL**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&9;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_9.cpp)]  
  
##  <a name="geteditcontrol"></a>CTreeCtrl::GetEditControl  
 调用此函数可检索用于编辑的树视图项的文本编辑控件的句柄。  
  
```  
CEdit* GetEditControl() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向用来编辑项文本，如果成功，则编辑控件的指针否则为**NULL**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&10;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_10.cpp)]  
  
##  <a name="getextendedstyle"></a>CTreeCtrl::GetExtendedStyle  
 检索当前的树视图控件使用的扩展的样式。  
  
```  
DWORD GetExtendedStyle() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个值，包含当前的树视图控件的按位组合 (OR) 的扩展样式。 有关详细信息，请参阅[树视图控件扩展样式](http://msdn.microsoft.com/library/windows/desktop/bb759981)。  
  
### <a name="remarks"></a>备注  
 此方法可发送[TVM_GETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb773580)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getfirstvisibleitem"></a>CTreeCtrl::GetFirstVisibleItem  
 调用此函数可检索树视图控件的第一个可见项。  
  
```  
HTREEITEM GetFirstVisibleItem() const;  
```  
  
### <a name="return-value"></a>返回值  
 第一个可见项; 该句柄否则为**NULL**。  
  
### <a name="example"></a>示例  
  请参阅示例[CTreeCtrl::SetCheck](#setcheck)。  
  
##  <a name="getimagelist"></a>CTreeCtrl::GetImageList  
 调用此函数可检索的普通的句柄或状态图像列表与树视图控件相关联。  
  
```  
CImageList* GetImageList(UINT nImageList) const;  
```  
  
### <a name="parameters"></a>参数  
 `nImageList`  
 要检索的图像列表的类型。 图像列表可以是下列值之一︰  
  
- `TVSIL_NORMAL`检索的普通映像列表，其中包含为树视图项的所选的和未选中映像。  
  
- `TVSIL_STATE`检索状态图像列表中，包含在用户定义的状态的树视图项的图像。  
  
### <a name="return-value"></a>返回值  
 如果成功，则该控件的图像列表的指针否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 在树视图控件中的每个项只能有一对与其相关联的位图图像。 选择的项，并且其他显示当未选定项时，将显示一幅图像。 例如，某一项可能显示为选中状态时打开的文件夹和关闭的文件夹未选中状态时。  
  
 图像列表的详细信息，请参阅[CImageList](../../mfc/reference/cimagelist-class.md)类。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&11;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_11.cpp)]  
  
##  <a name="getindent"></a>CTreeCtrl::GetIndent  
 调用此函数可检索的量，以像素为单位，该子项目相对于其父项缩进。  
  
```  
UINT GetIndent() const;  
```  
  
### <a name="return-value"></a>返回值  
 以像素为单位度量的缩进量。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&12;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_12.cpp)]  
  
##  <a name="getinsertmarkcolor"></a>CTreeCtrl::GetInsertMarkColor  
 此成员函数实现的行为的 Win32 消息[TVM_GETINSERTMARKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773590)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
COLORREF GetInsertMarkColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个**COLORREF**值，该值包含当前插入标记颜色。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&13;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_13.cpp)]  
  
##  <a name="getitem"></a>CTreeCtrl::GetItem  
 调用此函数可检索指定的树视图项的属性。  
  
```  
BOOL GetItem(TVITEM* pItem) const;  
```  
  
### <a name="parameters"></a>参数  
 `pItem`  
 一个指向[TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456)结构，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
  请参阅示例[CTreeCtrl::DeleteItem](#deleteitem)。  
  
##  <a name="getitemdata"></a>CTreeCtrl::GetItemData  
 调用此函数可检索与指定的项相关联的 32 位应用程序特定的值。  
  
```  
DWORD_PTR GetItemData(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 要检索其数据的项的句柄。  
  
### <a name="return-value"></a>返回值  
 与指定的项关联的 32 位应用程序特定值`hItem`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&14;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_14.cpp)]  
  
##  <a name="getitemexpandedimageindex"></a>CTreeCtrl::GetItemExpandedImageIndex  
 检索当前的树视图控件的指定的项处于展开状态时要显示图像的索引。  
  
```  
int GetItemExpandedImageIndex(HTREEITEM hItem)const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `hItem`|树视图控件项的句柄。|  
  
### <a name="return-value"></a>返回值  
 当指定的项处于展开状态时要显示的图像的索引。  
  
### <a name="remarks"></a>备注  
 此方法可发送[TVM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb773596)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 消息返回[TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459)结构描述的树视图控件项目，然后此方法检索`iExpandedImage`从该结构的成员。  
  
##  <a name="getitemheight"></a>CTreeCtrl::GetItemHeight  
 此成员函数实现的行为的 Win32 消息[TVM_GETITEMHEIGHT](http://msdn.microsoft.com/library/windows/desktop/bb773599)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
SHORT GetItemHeight() const;  
```  
  
### <a name="return-value"></a>返回值  
 该项目，以像素为单位的高度。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&15;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_15.cpp)]  
  
##  <a name="getitemimage"></a>CTreeCtrl::GetItemImage  
 在树视图控件中的每个项只能有一对与其相关联的位图图像。  
  
```  
BOOL GetItemImage(
    HTREEITEM hItem,  
    int& nImage,  
    int& nSelectedImage) const;  
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 要检索其图像的项的句柄。  
  
 `nImage`  
 一个整数，接收的树视图控件图像列表中的项的图像的索引。  
  
 `nSelectedImage`  
 一个整数，接收项的树视图控件图像列表中的所选图像的索引。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 在某一项的标签的左侧显示图像。 选择的项，并且其他显示当未选定项时，将显示一幅图像。 例如，某一项可能显示为选中状态时打开的文件夹和关闭的文件夹未选中状态时。  
  
 调用此函数可检索项的图像和树视图控件图像列表中的其所选的图像的索引。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&16;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_16.cpp)]  
  
##  <a name="getitempartrect"></a>CTreeCtrl::GetItemPartRect  
 检索当前的树视图控件中的指定项的指定部分的边框。  
  
```  
BOOL GetItemPartRect(
    HTREEITEM hItem,   
    int nPart,   
    LPRECT lpRect)const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `hItem`|树视图控件项的句柄。|  
|[in] `nPart`|部件的标识符。 必须设置为`TVGIPR_BUTTON`。|  
|[out] `lpRect`|指向[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构。 如果此方法成功，该结构接收为由指定的部件的矩形坐标`hItem`和`nPart`。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 每个树控件项受图形矩形。 该项目时单击该矩形中的点，则称其为*命中*。 此方法返回最大的矩形，以便单击该矩形中的点时，由标识的项`hItem`命中参数。  
  
 此方法可发送`TVM_GETITEMPARTRECT`消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 有关详细信息，请参阅[TreeView_GetItemPartRect](http://msdn.microsoft.com/library/windows/desktop/bb773847)宏。  
  
### <a name="example"></a>示例  
 下面的代码示例定义一个变量， `m_treeCtrl`，也就是说，用来访问当前的树视图控件。 此代码示例还定义一个无符号的整数和几个 HTREEITEM 变量。 在下一个示例中使用这些变量。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例使用的可访问性标识符和[CTreeCtrl::MapAccIdToItem](#mapaccidtoitem)方法来检索到的根树视图项的句柄。 然后，该示例使用该句柄和[CTreeCtrl::GetItemPartRect](#getitempartrect)方法周围绘制一个三维矩形该项。 前面的某一节的代码示例中，而不会显示，我们创建了包含针对美国国家/地区根节点、 宾夕法尼亚州和华盛顿州的状态的子节点并在这些状态中的城市的树项目树视图。 我们使用[CTreeCtrl::MapItemToAccID](#mapitemtoaccid)方法将根树视图项关联的辅助功能标识符。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&5;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_18.cpp)]  
  
##  <a name="getitemrect"></a>CTreeCtrl::GetItemRect  
 调用此函数可检索的绑定矩形`hItem`并确定它是否可见。  
  
```  
BOOL GetItemRect(
    HTREEITEM hItem,  
    LPRECT lpRect,  
    BOOL bTextOnly) const;  
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 树视图控件项的句柄。  
  
 `lpRect`  
 指向[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它接收的边框。 坐标是相对于树视图控件的左上角。  
  
 *bTextOnly*  
 如果此参数不为零，该边框包括仅项的文本。 否则，它在树视图控件中包括项占用的整个行。  
  
### <a name="return-value"></a>返回值  
 如果该项是可见，请与边界的矩形中包含非零`lpRect`。 否则为 0 且`lpRect`未初始化。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&17;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_19.cpp)]  
  
##  <a name="getitemstate"></a>CTreeCtrl::GetItemState  
 返回由指定的项的状态`hItem`。  
  
```  
UINT GetItemState(
    HTREEITEM hItem,  
    UINT nStateMask) const;  
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 要检索其状态的项的句柄。  
  
 `nStateMask`  
 掩码，指示要检索的一个或多个状态。 有关详细信息的可能值为`nStateMask`，请参阅的讨论**状态**和**stateMask**成员[TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 一个**UINT** ，它持有 nStateMask 指定的值的按位 OR。 在可能的值的信息，请参阅[CTreeCtrl::GetItem](#getitem)。 要查找某个特定状态的值，请执行 state 值和返回值的按位与运算，如下面的示例中所示。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&18;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_20.cpp)]  
  
##  <a name="getitemstateex"></a>CTreeCtrl::GetItemStateEx  
 检索当前的树视图控件中的指定项的扩展的状态。  
  
```  
UINT GetItemStateEx(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `hItem`|树视图控件项的句柄。|  
  
### <a name="return-value"></a>返回值  
 扩展的项的状态。 有关详细信息，请参阅`uStateEx`的成员[TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459)结构。  
  
### <a name="remarks"></a>备注  
 此方法可发送[TVM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb773596)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 消息返回[TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459)结构描述的树视图控件项目，因此该方法用于检索`uStateEx`从该结构的成员。  
  
##  <a name="getitemtext"></a>CTreeCtrl::GetItemText  
 返回由指定的项的文本`hItem`。  
  
```  
CString GetItemText(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 要检索其文本的项的句柄。  
  
### <a name="return-value"></a>返回值  
 一个`CString`对象，其中包含项的文本。  
  
### <a name="example"></a>示例  
  请参阅示例[CTreeCtrl::GetNextItem](#getnextitem)。  
  
##  <a name="getlastvisibleitem"></a>CTreeCtrl::GetLastVisibleItem  
 检索当前的树视图控件中的最后一个未扩展的节点项。  
  
```  
HTREEITEM GetLastVisibleItem() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则此方法的最后一个未扩展的节点项目窗口的句柄否则为`NULL`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[TVM_GETNEXTITEM](http://msdn.microsoft.com/library/windows/desktop/bb773622)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 有关详细信息，请参阅`TVGN_LASTVISIBLE`中标记出来`flag`该消息的参数。  
  
### <a name="example"></a>示例  
 下面的代码示例定义一个变量， `m_treeCtrl`，也就是说，用来访问当前的树视图控件。 此代码示例还定义一个无符号的整数和几个 HTREEITEM 变量。 下面的示例使用一个或多个这些变量。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例检索到最后一个未展开的树视图节点项的句柄，然后绘制 3D 矩形框住该项目。 前面的某一节的代码示例中，而不会显示，我们创建了包含针对美国国家/地区根节点、 宾夕法尼亚州和华盛顿州的状态的子节点并在这些状态中的城市的树项目树视图。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&6;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_21.cpp)]  
  
##  <a name="getlinecolor"></a>CTreeCtrl::GetLineColor  
 此成员函数实现的行为的 win32 消息[TVM_GETLINECOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773619)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
COLORREF GetLineColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前的线条颜色。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&19;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_22.cpp)]  
  
##  <a name="getnextitem"></a>CTreeCtrl::GetNextItem  
 调用此函数可检索的树视图项，具有指定的关系，由指示`nCode`参数，再到`hItem`。  
  
```  
HTREEITEM GetNextItem(
    HTREEITEM hItem,  
    UINT nCode) const;  
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 树项的句柄。  
  
 `nCode`  
 一个标志，指示与关系的类型`hItem`。 此标志可以是下列值之一︰  
  
- `TVGN_CARET`检索当前所选的项。  
  
- `TVGN_CHILD`检索由指定的项的第一个子项目`hItem`参数。  
  
- `TVGN_DROPHILITE`检索拖放操作的目标的项。  
  
- `TVGN_FIRSTVISIBLE`检索第一个可见项。  
  
- `TVGN_LASTVISIBLE`检索在树中最后一个展开的项目。 这并不检索树视图窗口中可见的最后一项。  
  
- `TVGN_NEXT`检索下一个同级项。  
  
- `TVGN_NEXTVISIBLE`检索遵循指定的项的下一个可见项。  
  
- `TVGN_PARENT`检索指定项的父级。  
  
- `TVGN_PREVIOUS`检索前面的同级项。  
  
- `TVGN_PREVIOUSVISIBLE`检索位于指定的项的第一个可见项。  
  
- `TVGN_ROOT`检索指定的项的一部分的根项的第一个子级项。  
  
### <a name="return-value"></a>返回值  
 如果成功，则下一个项的句柄否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 此函数将返回**NULL**要检索的项是否在树的根节点。 例如，如果您使用与此消息`TVGN_PARENT`标志的树视图根节点，第一级子消息将返回**NULL**。  
  
### <a name="example"></a>示例  
 为举例说明如何使用`GetNextItem`在循环中，请参阅[CTreeCtrl::DeleteItem](#deleteitem)。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl #&20;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_23.cpp)]  
  
##  <a name="getnextsiblingitem"></a>CTreeCtrl::GetNextSiblingItem  
 调用此函数可检索的下一个同级`hItem`。  
  
```  
HTREEITEM GetNextSiblingItem(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 树项的句柄。  
  
### <a name="return-value"></a>返回值  
 下一步的同级项; 的句柄否则为**NULL**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&21;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_24.cpp)]  
  
##  <a name="getnextvisibleitem"></a>CTreeCtrl::GetNextVisibleItem  
 调用此函数可检索的下一个可见项`hItem`。  
  
```  
HTREEITEM GetNextVisibleItem(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 树项的句柄。  
  
### <a name="return-value"></a>返回值  
 下一个可见项; 的句柄否则为**NULL**。  
  
### <a name="example"></a>示例  
  请参阅示例[CTreeCtrl::SetCheck](#setcheck)。  
  
##  <a name="getparentitem"></a>CTreeCtrl::GetParentItem  
 调用此函数可检索的父`hItem`。  
  
```  
HTREEITEM GetParentItem(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 树项的句柄。  
  
### <a name="return-value"></a>返回值  
 父项，则该句柄否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 此函数将返回**NULL**如果指定的项的父级是树的根节点。  
  
### <a name="example"></a>示例  
  请参阅示例[CTreeCtrl::EnsureVisible](#ensurevisible)。  
  
##  <a name="getprevsiblingitem"></a>CTreeCtrl::GetPrevSiblingItem  
 调用此函数可检索的上一个同级`hItem`。  
  
```  
HTREEITEM GetPrevSiblingItem(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 树项的句柄。  
  
### <a name="return-value"></a>返回值  
 前面的同级; 该句柄否则为**NULL**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&22;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_25.cpp)]  
  
##  <a name="getprevvisibleitem"></a>CTreeCtrl::GetPrevVisibleItem  
 调用此函数可检索的上一个可见项`hItem`。  
  
```  
HTREEITEM GetPrevVisibleItem(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 树项的句柄。  
  
### <a name="return-value"></a>返回值  
 上一个可见项; 的句柄否则为**NULL**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl 第&23;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_26.cpp)]  
  
##  <a name="getrootitem"></a>CTreeCtrl::GetRootItem  
 调用此函数可检索树视图控件的根项。  
  
```  
HTREEITEM GetRootItem() const;  
```  
  
### <a name="return-value"></a>返回值  
 根项; 的句柄否则为**NULL**。  
  
### <a name="example"></a>示例  
  请参阅示例[CTreeCtrl::EditLabel](#editlabel)。  
  
##  <a name="getscrolltime"></a>CTreeCtrl::GetScrollTime  
 调用该成员函数以检索树视图控件的最大滚动时间。  
  
```  
UINT GetScrollTime() const;  
```  
  
### <a name="return-value"></a>返回值  
 最大滚动时间，以毫秒为单位。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 win32 消息[TVM_GETSCROLLTIME](http://msdn.microsoft.com/library/windows/desktop/bb773625)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getselectedcount"></a>CTreeCtrl::GetSelectedCount  
 检索当前的树视图控件中选定项的数目。  
  
```  
UINT GetSelectedCount();
```  
  
### <a name="return-value"></a>返回值  
 选定项的数目。  
  
### <a name="remarks"></a>备注  
 此方法可发送[TVM_GETSELECTEDCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb773629)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getselecteditem"></a>CTreeCtrl::GetSelectedItem  
 调用此函数可检索当前选定的项的树视图控件。  
  
```  
HTREEITEM GetSelectedItem() const;  
```  
  
### <a name="return-value"></a>返回值  
 所选的项; 的句柄否则为**NULL**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&24;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_27.cpp)]  
  
##  <a name="gettextcolor"></a>CTreeCtrl::GetTextColor  
 此成员函数实现的行为的 Win32 消息[TVM_GETTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773633)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
COLORREF GetTextColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个**COLORREF**值，该值表示当前的文本颜色。 如果此值为-1，该控件用于系统颜色的文本颜色。  
  
### <a name="example"></a>示例  
  请参阅示例[CTreeCtrl::SetTextColor](#settextcolor)。  
  
##  <a name="gettooltips"></a>CTreeCtrl::GetToolTips  
 此成员函数实现的行为的 Win32 消息[TVM_GETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb773729)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)树控件要使用对象。 如果[创建](#create)成员函数使用的样式**TVS_NOTOOLTIPS**，使用任何工具提示，并**NULL**返回。  
  
### <a name="remarks"></a>备注  
 MFC 实现`GetToolTips`返回`CToolTipCtrl`对象，使用树控件中，而不是工具提示控件的句柄。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&25;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_28.cpp)]  
  
##  <a name="getvisiblecount"></a>CTreeCtrl::GetVisibleCount  
 调用此函数可检索的树视图控件中可见的项计数。  
  
```  
UINT GetVisibleCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 在树视图控件; 中的可见项的数量否则为-1。  
  
### <a name="example"></a>示例  
  请参阅示例[CTreeCtrl::SetCheck](#setcheck)。  
  
##  <a name="hittest"></a>CTreeCtrl::HitTest  
 调用此函数可确定相对于工作区的树视图控件的指定点的位置。  
  
```  
HTREEITEM HitTest(
    CPoint pt,  
    UINT* pFlags = NULL) const;  
  
HTREEITEM HitTest(TVHITTESTINFO* pHitTestInfo) const;  
```  
  
### <a name="parameters"></a>参数  
 `pt`  
 工作区坐标点的测试。  
  
 `pFlags`  
 指向一个整数，它接收的命中测试的结果有关的信息。 它可以是一个或多个值下列出**标志**备注部分中的成员。  
  
 `pHitTestInfo`  
 地址的指针[TVHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb773448)结构，其中包含要进行命中测试和程序的位置接收的命中测试的结果有关的信息。  
  
### <a name="return-value"></a>返回值  
 占据指定的点的树视图项的句柄或**NULL**如果没有项占用点。  
  
### <a name="remarks"></a>备注  
 当调用此函数时，`pt`参数指定要测试的点的坐标。 该函数将返回位于指定点处的项的句柄或**NULL**如果没有项占用点。 此外，`pFlags`参数包含一个值，该值指示指定点的位置。 可能的值有：  
  
|||  
|-|-|  
|值|含义|  
|TVHT_ABOVE|客户端区域的上方。|  
|TVHT_BELOW|下面的工作区。|  
|TVHT_NOWHERE|在客户端区域中，但仍低于的最后一项。|  
|TVHT_ONITEM|上的位图或与项目关联的标签。|  
|TVHT_ONITEMBUTTON|在与项目关联的按钮。|  
|TVHT_ONITEMICON|在与项目关联的位图。|  
|TVHT_ONITEMINDENT|在与项目关联的缩进。|  
|TVHT_ONITEMLABEL|在与项目关联的标签 （字符串）。|  
|TVHT_ONITEMRIGHT|在右侧的项的区域。|  
|TVHT_ONITEMSTATEICON|在用户定义的状态中的树视图项的状态图标。|  
|TVHT_TOLEFT|客户端区域的左侧。|  
|TVHT_TORIGHT|客户端区域的右侧。|  
|||  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&26;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_29.cpp)]  
  
##  <a name="insertitem"></a>CTreeCtrl::InsertItem  
 调用此函数可在树视图控件中插入新项。  
  
```  
HTREEITEM InsertItem(LPTVINSERTSTRUCT lpInsertStruct);

 
HTREEITEM InsertItem(
    UINT nMask,  
    LPCTSTR lpszItem,  
    int nImage,  
    int nSelectedImage,  
    UINT nState,  
    UINT nStateMask,  
    LPARAM lParam,  
    HTREEITEM hParent,  
    HTREEITEM hInsertAfter);

 
HTREEITEM InsertItem(
    LPCTSTR lpszItem,  
    HTREEITEM hParent = TVI_ROOT,  
    HTREEITEM hInsertAfter = TVI_LAST);

 
HTREEITEM InsertItem(
    LPCTSTR lpszItem,  
    int nImage,  
    int nSelectedImage,  
    HTREEITEM hParent = TVI_ROOT,  
    HTREEITEM hInsertAfter = TVI_LAST);
```  
  
### <a name="parameters"></a>参数  
 *lpInsertStruct*  
 一个指向`TVINSERTSTRUCT`，它指定要插入的树视图项的属性。  
  
 `nMask`  
 整数，指定要设置的属性。 请参阅`TVITEM`结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `lpszItem`  
 一个包含项的文本字符串的地址。  
  
 `nImage`  
 在树视图控件图像列表中的项的图像的索引。  
  
 `nSelectedImage`  
 在树视图控件图像列表中的项的所选图像的索引。  
  
 `nState`  
 指定的项的状态的值。 请参阅中的树视图控件项状态[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关适当的状态的列表。  
  
 `nStateMask`  
 指定要设置哪些状态。 请参阅`TVITEM`结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `lParam`  
 与项目关联一个 32 位应用程序特定值。  
  
 `hParent`  
 插入的项的父级的句柄。  
  
 *hInsertAfter*  
 在新的项之前要插入的项的句柄。  
  
### <a name="return-value"></a>返回值  
 如果成功，则新的项的句柄否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 该示例演示情况下您可能需要插入的树控件项时使用该函数的每个版本。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&27;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_30.cpp)]  
  
##  <a name="itemhaschildren"></a>CTreeCtrl::ItemHasChildren  
 使用此函数可确定指定的树项目`hItem`具有子项。  
  
```  
BOOL ItemHasChildren(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 树项的句柄。  
  
### <a name="return-value"></a>返回值  
 如果树项指定了非零`hItem`具有个子项; 如果不为 0。  
  
### <a name="remarks"></a>备注  
 如果这样，随后可以使用[CTreeCtrl::GetChildItem](#getchilditem)来检索这些子项。  
  
### <a name="example"></a>示例  
  请参阅示例[CTreeCtrl::GetSelectedItem](#getselecteditem)。  
  
##  <a name="mapaccidtoitem"></a>CTreeCtrl::MapAccIdToItem  
 将指定的辅助功能标识符映射到当前的树视图控件中的树视图项的句柄。  
  
```  
HTREEITEM MapAccIdToItem(UINT uAccId) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `uAccId`|中的树视图项的元素可访问性标识符。|  
  
### <a name="return-value"></a>返回值  
 树视图项的句柄 ( `HTREEITEM`) 对应于`uAccId`参数。 有关详细信息，请参阅`hItem`的成员[TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459)结构。  
  
### <a name="remarks"></a>备注  
 辅助功能是一些帮助残障人士使用的用户的应用程序使用的计算机。 可访问性标识符由使用`IAccessible`接口来唯一地在窗口中指定的元素。 有关辅助功能标识符的详细信息，搜索"有关 Active Accessibility 的支持"主题，网址[Microsoft Developer Network](http://go.microsoft.com/fwlink/linkid=56322)。  
  
 此方法可发送[TVM_MAPACCIDTOHTREEITEM](http://msdn.microsoft.com/library/windows/desktop/bb773734)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义一个变量， `m_treeCtrl`，也就是说，用来访问当前的树视图控件。 此代码示例还定义一个无符号的整数和几个 HTREEITEM 变量。 在下一个示例中使用这些变量。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例使用的可访问性标识符和[CTreeCtrl::MapAccIdToItem](#mapaccidtoitem)方法来检索到的根树视图项的句柄。 该示例使用该句柄和[CTreeCtrl::GetItemPartRect](#getitempartrect)方法周围绘制一个三维矩形该项。 前面的某一节的代码示例中，而不会显示，我们创建了包含针对美国国家/地区根节点、 宾夕法尼亚州和华盛顿州的状态的子节点并在这些状态中的城市的树项目树视图。 我们使用[CTreeCtrl::MapItemToAccID](#mapitemtoaccid)方法将根树视图项关联的辅助功能标识符。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&5;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_18.cpp)]  
  
##  <a name="mapitemtoaccid"></a>CTreeCtrl::MapItemToAccID  
 将当前的树视图控件中的树视图项的指定句柄映射到的辅助功能标识符。  
  
```  
UINT MapItemToAccID(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `hItem`|在控件中的树视图项句柄。 有关详细信息，请参阅`hItem`的成员[TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459)结构。|  
  
### <a name="return-value"></a>返回值  
 对应的辅助功能标识符`hItem`参数。  
  
### <a name="remarks"></a>备注  
 辅助功能是一些帮助残障人士使用的用户的应用程序使用的计算机。 可访问性标识符由使用`IAccessible`接口来唯一地在窗口中指定的元素。 有关辅助功能标识符的详细信息，搜索"有关 Active Accessibility 的支持"主题，网址[Microsoft Developer Network](http://go.microsoft.com/fwlink/linkid=56322)。  
  
 此方法可发送[TVM_MAPHTREEITEMTOACCID](http://msdn.microsoft.com/library/windows/desktop/bb773735)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义一个变量， `m_treeCtrl`，也就是说，用来访问当前的树视图控件。 此代码示例还定义一个无符号的整数和几个 HTREEITEM 变量。 在下一个示例中使用这些变量。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例获取树视图控件项的标识号。 前面的某一节的代码示例中，而不会显示，我们创建了包含针对美国国家/地区根节点、 宾夕法尼亚州和华盛顿州的状态的子节点并在这些状态中的城市的树项目树视图。 此代码示例获取根国家/地区节点的唯一标识号。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&2;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_31.cpp)]  
  
##  <a name="select"></a>CTreeCtrl::Select  
 调用此函数可选择给定的树视图项、 将该项滚入视图中，或在样式中用于指示拖放操作的目标绘该项。  
  
```  
BOOL Select(
    HTREEITEM hItem,  
    UINT nCode);
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 树项的句柄。  
  
 `nCode`  
 要执行的操作类型。 此参数可以是下列值之一︰  
  
- `TVGN_CARET`将所选内容设置为给定的项。  
  
- `TVGN_DROPHILITE`在样式中用于指示拖放操作的目标将重新绘制给定的项。  
  
- `TVGN_FIRSTVISIBLE`垂直滚动的树视图，以使给定的项是第一个可见项。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果`nCode`包含值`TVGN_CARET`，父窗口接收**TVN_SELCHANGING**和**TVN_SELCHANGED**通知消息。 此外，指定的项是否折叠的父项的子级，与父级的子项列表展开以显示指定的项。 在这种情况下，父窗口都将接收**TVN_ITEMEXPANDING**和**TVN_ITEMEXPANDED**通知消息。  
  
### <a name="example"></a>示例  
  请参阅示例[CTreeCtrl::HitTest](#hittest)。  
  
##  <a name="selectdroptarget"></a>CTreeCtrl::SelectDropTarget  
 调用此函数可在样式中用于指示拖放操作的目标绘该项。  
  
```  
BOOL SelectDropTarget(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 树项的句柄。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&9;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_9.cpp)]  
  
##  <a name="selectitem"></a>CTreeCtrl::SelectItem  
 调用此函数可选择给定的树视图项。  
  
```  
BOOL SelectItem(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 树项的句柄。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果`hItem`是**NULL**，则此函数中不选择任何项。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&26;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_29.cpp)]  
  
##  <a name="selectsetfirstvisible"></a>CTreeCtrl::SelectSetFirstVisible  
 调用此函数可垂直滚动的树视图，以便给定的项是第一个可见项。  
  
```  
BOOL SelectSetFirstVisible(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 要将其设置为第一个可见项的树项的句柄。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 该函数将一条消息发送到与窗口`TVM_SELECTITEM`和`TVGN_FIRSTVISIBLE`消息参数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&28;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_32.cpp)]  
  
##  <a name="setautoscrollinfo"></a>CTreeCtrl::SetAutoscrollInfo  
 设置当前的树视图控件的滚动率。  
  
```  
BOOL SetAutoscrollInfo(
    UINT uPixelsPerSec,   
    UINT uUpdateTime);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `uPixelsPerSec`|每秒的时间来滚动的像素数。|  
|[in] `uUpdateTime`|该控件的更新之间的时间间隔。|  
  
### <a name="return-value"></a>返回值  
 始终返回 `true`。  
  
### <a name="remarks"></a>备注  
 自动滚动参数用于滚动到视图中当前不可见的项。 树视图控件都必须具有`TVS_EX_AUTOHSCROLL`扩展样式中, 所述[树视图控件扩展样式](http://msdn.microsoft.com/library/windows/desktop/bb759981)。  
  
 此方法可发送[TVM_SETAUTOSCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb773738)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义一个变量， `m_treeCtrl`，也就是说，用来访问当前的树视图控件。 此代码示例还定义一个无符号的整数和几个 HTREEITEM 变量。 在下一个示例中使用这些变量。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例设置当前的树视图控件的滚动行为。 前面的某一节的代码示例中，而不会显示，我们创建了包含针对美国国家/地区根节点、 宾夕法尼亚州和华盛顿州的状态的子节点并在这些状态中的城市的树项目树视图。 我们有意进行树视图控件窄，因此必须自动滚动以显示具有焦点的树项目。 代码示例设置要自动滚动 30 个像素，每秒每隔 5 秒，直至树项在视图中的树视图控件。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&4;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_33.cpp)]  
  
##  <a name="setbkcolor"></a>CTreeCtrl::SetBkColor  
 此成员函数实现的行为的 Win32 消息[TVM_SETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773741)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
COLORREF SetBkColor(COLORREF clr);
```  
  
### <a name="parameters"></a>参数  
 `clr`  
 一个**COLORREF**值，该值包含新的背景色。 如果此值为-1，该控件将恢复为背景色使用系统颜色。  
  
### <a name="return-value"></a>返回值  
 一个**COLORREF**值，该值表示当前的文本颜色。 如果此值为-1，该控件用于系统颜色的文本颜色。  
  
### <a name="example"></a>示例  
  请参阅示例[CTreeCtrl::SetTextColor](#settextcolor)。  
  
##  <a name="setcheck"></a>CTreeCtrl::SetCheck  
 调用该成员函数以设置树控件项的复选状态。  
  
```  
BOOL SetCheck(
    HTREEITEM hItem,  
    BOOL fCheck = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 **HTREEITEM**要接收检查状态更改。  
  
 `fCheck`  
 指示是否为选中或取消选中的树控件项目。 默认情况下，`SetCheck`设置要检查的项。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 当检查的树控件项目 (`fCheck`设置为**TRUE**)，项与相邻的复选标记出现。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&29;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_34.cpp)]  
  
### <a name="example"></a>示例  
 若要使用复选框，请填充树控件之前设置 TVS_CHECKBOXES。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl #&30;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_35.cpp)]  
  
##  <a name="setextendedstyle"></a>CTreeCtrl::SetExtendedStyle  
 设置当前的树视图控件的扩展的样式。  
  
```  
DWORD SetExtendedStyle(
    DWORD dwExMask,   
    DWORD dwExStyles);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `dwExMask`|指定哪种样式在当前的树视图控件中受此方法的位掩码。 如果此参数为零，则将忽略和的值`dwExStyles`参数分配给树视图控件。<br /><br /> 指定零个或样式中所述的按位组合 (OR)[树视图控件扩展样式](http://msdn.microsoft.com/library/windows/desktop/bb759981)。|  
|[in] `dwExStyles`|指定当前的树视图中的样式控制转移到设置或清除的位掩码。<br /><br /> 若要设置样式组合，指定样式中所述的按位组合 (OR)[树视图控件扩展样式](http://msdn.microsoft.com/library/windows/desktop/bb759981)。 若要清除一组的样式，请指定零。|  
  
### <a name="return-value"></a>返回值  
 一个包含上一个扩展控件样式的值。  
  
### <a name="remarks"></a>备注  
 此方法清除中指定的样式`dwExMask`参数，然后设置中指定的样式`dwExStyles`参数。 只有对应于中的位的扩展的样式`dwExMask`更改。  
  
 此方法可发送[TVM_SETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb773744)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义一个变量， `m_treeCtrl`，也就是说，用来访问当前的树视图控件。 此代码示例还定义一个无符号的整数和几个 HTREEITEM 变量。 在下一个示例中使用这些变量。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例将添加`TVS_EX_AUTOHSCROLL`扩展到当前的树视图控件的样式。 前面的某一节的代码示例中，而不会显示，我们创建了包含针对美国国家/地区根节点、 宾夕法尼亚州和华盛顿州的状态的子节点并在这些状态中的城市的树项目树视图。 我们有意进行树视图控件窄，因此必须自动滚动以显示具有焦点的树项目。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&3;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_36.cpp)]  
  
##  <a name="setimagelist"></a>CTreeCtrl::SetImageList  
 调用此函数可设置正常或状态图像列表为树视图控件和重绘控件使用新的映像。  
  
```  
CImageList* SetImageList(
    CImageList* pImageList,  
    int nImageListType);
```  
  
### <a name="parameters"></a>参数  
 `pImageList`  
 指向要分配的图像列表的指针。 如果`pImageList`是**NULL**，从树视图控件中移除所有映像。  
  
 `nImageListType`  
 若要设置的图像列表的类型。 图像列表可以是下列值之一︰  
  
- `TVSIL_NORMAL`设置的普通映像列表，其中包含为树视图项的所选的和未选中映像。 有关覆盖图像，必须使用该状态。  
  
- `TVSIL_STATE`设置状态图像列表中，包含在用户定义的状态的树视图项的图像。  
  
### <a name="return-value"></a>返回值  
 指针，指向上一个图像列表中，如果有的话;否则为**NULL**。  
  
### <a name="example"></a>示例  
  请参阅示例[CTreeCtrl::GetImageList](#getimagelist)。  
  
##  <a name="setindent"></a>CTreeCtrl::SetIndent  
 调用此函数可设置缩进的树视图控件的宽度和重绘控件以反映新的宽度。  
  
```  
void SetIndent(UINT nIndent);
```  
  
### <a name="parameters"></a>参数  
 `nIndent`  
 宽度，以像素为单位的缩进。 如果`nIndent`小于超过系统定义的最小宽度，新的宽度设置为系统定义的最小值。  
  
### <a name="example"></a>示例  
  请参阅示例[CTreeCtrl::GetIndent](#getindent)。  
  
##  <a name="setinsertmark"></a>CTreeCtrl::SetInsertMark  
 此成员函数实现的行为的 Win32 消息[TVM_SETINSERTMARK](http://msdn.microsoft.com/library/windows/desktop/bb773753)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
BOOL SetInsertMark(
    HTREEITEM hItem,  
    BOOL fAfter = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 **HTREEITEM** ，它指定在哪一项将置于插入标记。 如果此参数为**NULL**，插入标记为删除。  
  
 *fAfter*  
 **BOOL**值，该值指定是否插入标记位于之前或之后指定的项。 如果此参数不为零，则将在项后面放置插入标记。 如果此参数为零，则将该项的前面放置插入标记。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&31;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_37.cpp)]  
  
##  <a name="setinsertmarkcolor"></a>CTreeCtrl::SetInsertMarkColor  
 此成员函数实现的行为的 Win32 消息[TVM_SETINSERTMARKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773755)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
COLORREF SetInsertMarkColor(COLORREF clrNew);
```  
  
### <a name="parameters"></a>参数  
 `clrNew`  
 一个**COLORREF**值，该值包含新的插入标记颜色。  
  
### <a name="return-value"></a>返回值  
 一个**COLORREF**值，该值包含以前的插入标记颜色。  
  
### <a name="example"></a>示例  
  请参阅示例[CTreeCtrl::GetInsertMarkColor](#getinsertmarkcolor)。  
  
##  <a name="setitem"></a>CTreeCtrl::SetItem  
 调用此函数可设置指定的树视图项的属性。  
  
```  
BOOL SetItem(TVITEM* pItem);

 
BOOL SetItem(
    HTREEITEM hItem,  
    UINT nMask,  
    LPCTSTR lpszItem,  
    int nImage,  
    int nSelectedImage,  
    UINT nState,  
    UINT nStateMask,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>参数  
 `pItem`  
 一个指向[TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456)结构，其中包含新的项属性，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `hItem`  
 要设置其属性的项的句柄。 请参阅**hItem**的成员`TVITEM`结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `nMask`  
 整数，指定要设置的属性。 请参阅**掩码**的成员`TVITEM`结构。  
  
 `lpszItem`  
 一个包含项的文本字符串的地址。  
  
 `nImage`  
 在树视图控件图像列表中的项的图像的索引。 请参阅`iImage`的成员`TVITEM`结构。  
  
 `nSelectedImage`  
 在树视图控件图像列表中的项的所选图像的索引。 请参阅**iSelectedImage**的成员`TVITEM`结构。  
  
 `nState`  
 指定的项的状态的值。 请参阅**状态**的成员`TVITEM`结构。  
  
 `nStateMask`  
 指定要设置哪些状态。 请参阅**stateMask**的成员`TVITEM`结构。  
  
 `lParam`  
 与项目关联一个 32 位应用程序特定值。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 在`TVITEM`结构， **hItem**成员标识的项，与**掩码**成员指定要设置的属性。  
  
 如果**掩码**成员或`nMask`参数指定`TVIF_TEXT`值， **pszText**成员或`lpszItem`是以 null 结尾的字符串的地址和**cchTextMax**成员将被忽略。 如果**掩码**(或`nMask`) 指定`TVIF_STATE`值， **stateMask**成员或`nStateMask`参数指定哪一项表明若要更改与**状态**成员或`nState`参数则包含这些状态的值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&32;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_38.cpp)]  
  
##  <a name="setitemdata"></a>CTreeCtrl::SetItemData  
 调用此函数可设置与指定的项相关联的 32 位应用程序特定的值。  
  
```  
BOOL SetItemData(
    HTREEITEM hItem,  
    DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 要检索其数据的项的句柄。  
  
 `dwData`  
 与指定的项关联的 32 位应用程序特定值`hItem`。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl 第&33;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_39.cpp)]  
  
##  <a name="setitemexpandedimageindex"></a>CTreeCtrl::SetItemExpandedImageIndex  
 设置要在当前的树视图控件的指定的项处于展开状态时显示的图像的索引。  
  
```  
BOOL SetItemExpandedImageIndex(
    HTREEITEM hItem,   
    int iExpandedImage);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `hItem`|树视图控件项的句柄。|  
|[in] `iExpandedImage`|当指定的项处于展开状态时要显示的图像的索引。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[TVM_SETITEM](http://msdn.microsoft.com/library/windows/desktop/bb773758)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 此方法分配`iExpandedImage`参数`iExpandedImage`的成员[TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459)结构，然后在消息中结构的使用。  
  
### <a name="example"></a>示例  
 下面的代码示例定义一个变量， `m_treeCtrl`，也就是说，用来访问当前的树视图控件。 此代码示例还定义一个无符号的整数和几个 HTREEITEM 变量。 在下一个示例中使用这些变量。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例是简单的测试，确定是否[CTreeCtrl::GetItemExpandedImageIndex](#getitemexpandedimageindex)方法将返回所设置的值[CTreeCtrl::SetItemExpandedImageIndex](#setitemexpandedimageindex)方法。 前面的某一节的代码示例中，而不会显示，我们创建了包含针对美国国家/地区根节点、 宾夕法尼亚州和华盛顿州的状态的子节点并在这些状态中的城市的树项目树视图。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&8;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_40.cpp)]  
  
##  <a name="setitemheight"></a>CTreeCtrl::SetItemHeight  
 此成员函数实现的行为的 Win32 消息[TVM_SETITEMHEIGHT](http://msdn.microsoft.com/library/windows/desktop/bb773761)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
SHORT SetItemHeight(SHORT cyHeight);
```  
  
### <a name="parameters"></a>参数  
 `cyHeight`  
 在树视图中，以像素为单位指定的每一项新的高度。 如果此参数为早于图像的高度，则会将它设为图像的高度。 如果此参数不为偶数，它将被舍入到最接近偶数值。 如果此参数为-1，该控件将恢复为使用其默认项高度。  
  
### <a name="return-value"></a>返回值  
 上一项，以像素为单位的高度。  
  
### <a name="example"></a>示例  
  请参阅示例[CTreeCtrl::GetItemHeight](#getitemheight)。  
  
##  <a name="setitemimage"></a>CTreeCtrl::SetItemImage  
 将图像与项相关联。  
  
```  
BOOL SetItemImage(
    HTREEITEM hItem,  
    int nImage,  
    int nSelectedImage);
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 要设置其图像的项的句柄。  
  
 `nImage`  
 在树视图控件图像列表中的项的图像的索引。  
  
 `nSelectedImage`  
 在树视图控件图像列表中的项的所选图像的索引。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 在树视图控件中的每个项只能有一对与其相关联的位图图像。 在某一项的标签的左侧显示图像。 选择的项，并且其他显示当未选定项时，将显示一幅图像。 例如，某一项可能显示为选中状态时打开的文件夹和关闭的文件夹未选中状态时。  
  
 调用此函数可设置项的图像和树视图控件图像列表中的其所选的图像的索引。  
  
 有关映像的详细信息，请参阅[CImageList](../../mfc/reference/cimagelist-class.md)。  
  
### <a name="example"></a>示例  
  请参阅示例[CTreeCtrl::GetItemImage](#getitemimage)。  
  
##  <a name="setitemstate"></a>CTreeCtrl::SetItemState  
 设置由指定的项的状态`hItem`。  
  
```  
BOOL SetItemState(
    HTREEITEM hItem,  
    UINT nState,  
    UINT nStateMask);
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 要设置其状态的项的句柄。  
  
 `nState`  
 指定项的新状态。  
  
 `nStateMask`  
 指定要更改哪些状态。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 状态的信息，请参阅[CTreeCtrl::GetItem](#getitem)。  
  
### <a name="example"></a>示例  
  请参阅示例[CTreeCtrl::GetItemState](#getitemstate)。  
  
##  <a name="setitemstateex"></a>CTreeCtrl::SetItemStateEx  
 对于当前的树视图控件中设置指定项的扩展的状态。  
  
```  
BOOL SetItemStateEx(
    HTREEITEM hItem,   
    UINT uStateEx);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `hItem`|树视图控件项的句柄。|  
|[in] `uStateEx`|扩展的项的状态。 有关详细信息，请参阅`uStateEx`的成员[TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459)结构。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[TVM_SETITEM](http://msdn.microsoft.com/library/windows/desktop/bb773758)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 此方法分配`uStateEx`参数`uStateEx`的成员[TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459)结构，然后在消息中结构的使用。  
  
### <a name="example"></a>示例  
 下面的代码示例定义一个变量， `m_treeCtrl`，也就是说，用来访问当前的树视图控件。 此代码示例还定义一个无符号的整数和几个 HTREEITEM 变量。 在下一个示例中使用这些变量。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例将一个树视图项设置为禁用状态。 前面的某一节的代码示例中，而不会显示，我们创建了包含针对美国国家/地区根节点、 宾夕法尼亚州和华盛顿州的状态的子节点并在这些状态中的城市的树项目树视图。 此代码示例将宾夕法尼亚州节点设置为禁用状态。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&7;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_41.cpp)]  
  
##  <a name="setitemtext"></a>CTreeCtrl::SetItemText  
 设置由指定的项的文本`hItem`。  
  
```  
BOOL SetItemText(
    HTREEITEM hItem,  
    LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 要设置其文本的项的句柄。  
  
 `lpszItem`  
 包含项的新文本的字符串的地址  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&34;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_42.cpp)]  
  
##  <a name="setlinecolor"></a>CTreeCtrl::SetLineColor  
 调用此成员函数可设置树视图控件的当前线条颜色。  
  
```  
COLORREF SetLineColor(COLORREF clrNew = CLR_DEFAULT);
```  
  
### <a name="parameters"></a>参数  
 `clrNew`  
 新的线条颜色。  
  
### <a name="return-value"></a>返回值  
 以前的线条颜色。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 win32 消息[TVM_SETLINECOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773764)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&35;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_43.cpp)]  
  
##  <a name="setscrolltime"></a>CTreeCtrl::SetScrollTime  
 调用此成员函数可设置树视图控件的最大滚动时间。  
  
```  
UINT SetScrollTime(UINT uScrollTime);
```  
  
### <a name="parameters"></a>参数  
 *uScrollTime*  
 新的最大滚动时间，以毫秒为单位。 如果此值为小于 100，它将舍入为 100。  
  
### <a name="return-value"></a>返回值  
 上一个最大滚动时间，以毫秒为单位。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 win32 消息[TVM_SETSCROLLTIME](http://msdn.microsoft.com/library/windows/desktop/bb773767)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="settextcolor"></a>CTreeCtrl::SetTextColor  
 此成员函数实现的行为的 Win32 消息[TVM_SETTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773769)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
COLORREF SetTextColor(COLORREF clr);
```  
  
### <a name="parameters"></a>参数  
 `clr`  
 一个**COLORREF**值，该值包含新的文本颜色。 如果此参数为-1，该控件将恢复为使用系统颜色的文本颜色。  
  
### <a name="return-value"></a>返回值  
 一个**COLORREF**值，该值表示前一种文本颜色。 如果此值为-1，该控件文本颜色都使用系统颜色。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&36;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_44.cpp)]  
  
##  <a name="settooltips"></a>CTreeCtrl::SetToolTips  
 此成员函数实现的行为的 Win32 消息[TVM_SETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb773772)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
CToolTipCtrl* SetToolTips(CToolTipCtrl* pWndTip);
```  
  
### <a name="parameters"></a>参数  
 `pWndTip`  
 一个指向[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)树控件将使用的对象。  
  
### <a name="return-value"></a>返回值  
 一个指向[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)对象，它包含控件，以前使用的工具提示或**NULL**如果以前不使用任何工具提示。  
  
### <a name="remarks"></a>备注  
 若要使用工具提示，指示**TVS_NOTOOLTIPS**时您创建样式`CTreeCtrl`对象。  
  
### <a name="example"></a>示例  
  请参阅示例[CTreeCtrl::GetToolTips](#gettooltips)。  
  
##  <a name="showinfotip"></a>CTreeCtrl::ShowInfoTip  
 显示当前的树视图控件中的指定项目的信息提示。  
  
```  
void ShowInfoTip(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `hItem`|在控件中的树视图项句柄。 有关详细信息，请参阅`hItem`的成员[TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459)结构。|  
  
### <a name="remarks"></a>备注  
 有关工具提示和信息提示之间的差异的详细信息，搜索"工具提示和信息提示"主题，网址[Microsoft Developer Network](http://go.microsoft.com/fwlink/linkid=56322)。  
  
 此方法可发送[TVM_SHOWINFOTIP](http://msdn.microsoft.com/library/windows/desktop/bb773779)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="sortchildren"></a>CTreeCtrl::SortChildren  
 调用此函数可按字母顺序排序的树视图控件中的给定的父项的子项。  
  
```  
BOOL SortChildren(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>参数  
 `hItem`  
 其子项是要排序的父项句柄。 如果`hItem`是**NULL**，排序将继续从树的根。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 `SortChildren`将通过树; 进行递归仅直属子级`hItem`进行排序。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&37;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_45.cpp)]  
  
##  <a name="sortchildrencb"></a>CTreeCtrl::SortChildrenCB  
 调用此函数可使用应用程序定义的回调函数以比较项的树视图项进行排序。  
  
```  
BOOL SortChildrenCB(LPTVSORTCB pSort);
```  
  
### <a name="parameters"></a>参数  
 *pSort*  
 指向[TVSORTCB](http://msdn.microsoft.com/library/windows/desktop/bb773462)结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 该结构的比较函数**lpfnCompare**，必须返回值为负的第一项应位于第二个之前，如果一个正数，如果值为第一项应遵循第二个，或为零的两项相等。  
  
 `lParam1`和`lParam2`参数对应于**lParam**的成员[TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456)结构的两个项进行比较。 `lParamSort`参数对应于**lParam**的成员`TV_SORTCB`结构。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&38;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_46.cpp)]  
  
 [!code-cpp[NVC_MFC_CTreeCtrl #&39;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_47.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 CMNCTRL1](../../visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CImageList 类](../../mfc/reference/cimagelist-class.md)

