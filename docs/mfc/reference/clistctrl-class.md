---
title: "CListCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CListCtrl
dev_langs:
- C++
helpviewer_keywords:
- CListCtrl class
- LVS_REPORT
- LVS_LIST
- LVS_ICON
- list view controls
- list view controls, CListCtrl class
- Windows common controls [C++], CListCtrl
- LVS_SMALLICON
ms.assetid: fe08a1ca-4b05-4ff7-a12a-ee4c765a2197
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: fb82dd194d59bff9e0a3fe8f047686a8bcc4d927
ms.lasthandoff: 02/24/2017

---
# <a name="clistctrl-class"></a>CListCtrl 类
封装显示一组项的“列表视图控件”功能，每一项均包含一个图标（来自图像列表）和标签。  
  
## <a name="syntax"></a>语法  
  
```  
class CListCtrl : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CListCtrl::CListCtrl](#clistctrl)|构造 `CListCtrl` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CListCtrl::ApproximateViewRect](#approximateviewrect)|确定的宽度和高度需要它来显示列表视图控件的项。|  
|[CListCtrl::Arrange](#arrange)|对齐网格上的项。|  
|[CListCtrl::CancelEditLabel](#canceleditlabel)|取消编辑操作的项文本。|  
|[CListCtrl::Create](#create)|创建列表控件，并将其附加到`CListCtrl`对象。|  
|[CListCtrl::CreateDragImage](#createdragimage)|创建一个拖动图像列表的指定项。|  
|[CListCtrl::CreateEx](#createex)|与指定的 Windows 扩展样式创建列表控件，并将其附加到`CListCtrl`对象。|  
|[CListCtrl::DeleteAllItems](#deleteallitems)|从控件中删除所有项。|  
|[CListCtrl::DeleteColumn](#deletecolumn)|从列表视图控件中删除某一列。|  
|[CListCtrl::DeleteItem](#deleteitem)|从控件中删除的项。|  
|[CListCtrl::DrawItem](#drawitem)|当所有者描述控件更改的可视方位时调用。|  
|[CListCtrl::EditLabel](#editlabel)|开始在就地编辑的项的文本。|  
|[CListCtrl::EnableGroupView](#enablegroupview)|启用或禁用是否在列表视图控件中的项目显示为一组。|  
|[CListCtrl::EnsureVisible](#ensurevisible)|确保项目可见。|  
|[CListCtrl::FindItem](#finditem)|搜索具有指定特征的列表视图项。|  
|[CListCtrl::GetBkColor](#getbkcolor)|检索列表视图控件的背景色。|  
|[CListCtrl::GetBkImage](#getbkimage)|检索当前的背景图像的列表视图控件。|  
|[Clistctrl:: Getcallbackmask](#getcallbackmask)|检索列表视图控件的回调掩码。|  
|[CListCtrl::GetCheck](#getcheck)|检索与项目关联的状态图像的当前显示状态。|  
|[CListCtrl::GetColumn](#getcolumn)|检索控件的列的属性。|  
|[CListCtrl::GetColumnOrderArray](#getcolumnorderarray)|检索列表视图控件的列顺序 （从左到右）。|  
|[CListCtrl::GetColumnWidth](#getcolumnwidth)|检索报表视图或列表视图中的列的宽度。|  
|[CListCtrl::GetCountPerPage](#getcountperpage)|计算列表视图控件中垂直可以容纳的项的数目。|  
|[CListCtrl::GetEditControl](#geteditcontrol)|检索用于编辑某项的文本编辑控件的句柄。|  
|[CListCtrl::GetEmptyText](#getemptytext)|检索要显示当前的 list view 控件是否为空的字符串。|  
|[CListCtrl::GetExtendedStyle](#getextendedstyle)|检索列表视图控件的当前扩展的样式。|  
|[CListCtrl::GetFirstSelectedItemPosition](#getfirstselecteditemposition)|检索在列表视图控件中的第一个选定的列表视图项位置。|  
|[CListCtrl::GetFocusedGroup](#getfocusedgroup)|检索当前的列表视图控件中具有键盘焦点的组。|  
|[CListCtrl::GetGroupCount](#getgroupcount)|检索当前的列表视图控件中的组数。|  
|[CListCtrl::GetGroupInfo](#getgroupinfo)|为指定的一组列表视图控件中获取的信息。|  
|[CListCtrl::GetGroupInfoByIndex](#getgroupinfobyindex)|检索有关指定的组中当前的 list view 控件的信息。|  
|[CListCtrl::GetGroupMetrics](#getgroupmetrics)|检索一个组的度量值。|  
|[CListCtrl::GetGroupRect](#getgrouprect)|检索指定的组中当前的 list view 控件的边框。|  
|[CListCtrl::GetGroupState](#getgroupstate)|检索当前的列表视图控件中的指定组的状态。|  
|[CListCtrl::GetHeaderCtrl](#getheaderctrl)|检索列表视图控件的标头控件。|  
|[CListCtrl::GetHotCursor](#gethotcursor)|检索用于列表视图控件启用热跟踪时使用的游标。|  
|[CListCtrl::GetHotItem](#gethotitem)|检索当前光标下的列表视图项。|  
|[CListCtrl::GetHoverTime](#gethovertime)|检索列表视图控件的当前悬停时间。|  
|[CListCtrl::GetImageList](#getimagelist)|检索图像列表用于绘图的列表视图项的句柄。|  
|[CListCtrl::GetInsertMark](#getinsertmark)|检索当前的位置插入标记。|  
|[CListCtrl::GetInsertMarkColor](#getinsertmarkcolor)|检索当前颜色的插入标记。|  
|[CListCtrl::GetInsertMarkRect](#getinsertmarkrect)|将检索限定插入点的矩形。|  
|[Clistctrl:: Getitem](#getitem)|检索列表视图项的属性。|  
|[CListCtrl::GetItemCount](#getitemcount)|检索在列表视图控件中的项的数目。|  
|[CListCtrl::GetItemData](#getitemdata)|检索与项目关联的应用程序特定的值。|  
|[CListCtrl::GetItemIndexRect](#getitemindexrect)|为所有或部分当前列表视图控件中的子项中检索的绑定矩形。|  
|[CListCtrl::GetItemPosition](#getitemposition)|检索列表视图项的位置。|  
|[CListCtrl::GetItemRect](#getitemrect)|检索项的边框。|  
|[CListCtrl::GetItemSpacing](#getitemspacing)|计算当前的列表视图控件中的项之间的间距。|  
|[CListCtrl::GetItemState](#getitemstate)|检索列表视图项的状态。|  
|[CListCtrl::GetItemText](#getitemtext)|检索在列表视图项或子项的文本。|  
|[CListCtrl::GetNextItem](#getnextitem)|搜索与指定的属性和与给定项的指定关系的列表视图项。|  
|[CListCtrl::GetNextItemIndex](#getnextitemindex)|检索具有指定的一组属性的当前列表视图控件中的项的索引。|  
|[CListCtrl::GetNextSelectedItem](#getnextselecteditem)|检索一个列表视图项的位置，以及用于循环的下一步选择的列表视图项的位置的索引。|  
|[CListCtrl::GetNumberOfWorkAreas](#getnumberofworkareas)|检索列表视图控件的工作区域的当前数目。|  
|[CListCtrl::GetOrigin](#getorigin)|检索列表视图控件的当前视图原点。|  
|[CListCtrl::GetOutlineColor](#getoutlinecolor)|检索列表视图控件的边框的颜色。|  
|[CListCtrl::GetSelectedColumn](#getselectedcolumn)|检索列表控件中当前选定列的索引。|  
|[CListCtrl::GetSelectedCount](#getselectedcount)|检索列表视图控件中选定项的数目。|  
|[CListCtrl::GetSelectionMark](#getselectionmark)|检索列表视图控件的选择标记。|  
|[CListCtrl::GetStringWidth](#getstringwidth)|确定显示给定字符串的所有所需的最小列宽度。|  
|[CListCtrl::GetSubItemRect](#getsubitemrect)|检索列表视图控件中的项的边框。|  
|[CListCtrl::GetTextBkColor](#gettextbkcolor)|检索列表视图控件的文本的背景颜色。|  
|[CListCtrl::GetTextColor](#gettextcolor)|检索列表视图控件的文本颜色。|  
|[CListCtrl::GetTileInfo](#gettileinfo)|检索有关列表视图控件中的图块的信息。|  
|[CListCtrl::GetTileViewInfo](#gettileviewinfo)|检索有关列表视图控件平铺视图中的信息。|  
|[CListCtrl::GetToolTips](#gettooltips)|检索列表视图控件用于显示工具提示的工具提示控件。|  
|[CListCtrl::GetTopIndex](#gettopindex)|检索的最顶层的可见项的索引。|  
|[CListCtrl::GetView](#getview)|获取列表视图控件的视图。|  
|[CListCtrl::GetViewRect](#getviewrect)|检索列表视图控件中的所有项的边框。|  
|[CListCtrl::GetWorkAreas](#getworkareas)|检索列表视图控件的当前工作区。|  
|[CListCtrl::HasGroup](#hasgroup)|确定列表视图控件是否具有指定的组。|  
|[CListCtrl::HitTest](#hittest)|确定哪个列表视图项位于指定位置。|  
|[CListCtrl::InsertColumn](#insertcolumn)|在列表视图控件中插入新列。|  
|[CListCtrl::InsertGroup](#insertgroup)|将一组插入到列表视图控件。|  
|[CListCtrl::InsertGroupSorted](#insertgroupsorted)|将指定的组插入到组的排序列表。|  
|[CListCtrl::InsertItem](#insertitem)|在列表视图控件中插入新项。|  
|[CListCtrl::InsertMarkHitTest](#insertmarkhittest)|检索与指定的点最接近的插入点。|  
|[CListCtrl::IsGroupViewEnabled](#isgroupviewenabled)|确定是否为列表视图控件启用的组视图。|  
|[CListCtrl::IsItemVisible](#isitemvisible)|指示当前的列表视图控件中的指定的项是否可见。|  
|[CListCtrl::MapIDToIndex](#mapidtoindex)|将当前的列表视图控件中的项的唯一 ID 映射到索引。|  
|[CListCtrl::MapIndexToID](#mapindextoid)|将当前的列表视图控件中的项的索引映射到唯一的 id。|  
|[CListCtrl::MoveGroup](#movegroup)|将指定的组移动。|  
|[CListCtrl::MoveItemToGroup](#moveitemtogroup)|将移动指定的组指定零开始的列表视图控件索引。|  
|[CListCtrl::RedrawItems](#redrawitems)|强制重新绘制的项的范围的列表视图控件。|  
|[CListCtrl::RemoveAllGroups](#removeallgroups)|从列表视图控件中移除所有组。|  
|[CListCtrl::RemoveGroup](#removegroup)|从列表视图控件中删除指定的组。|  
|[CListCtrl::Scroll](#scroll)|将列表视图控件的内容滚动。|  
|[CListCtrl::SetBkColor](#setbkcolor)|设置在列表视图控件的背景色。|  
|[CListCtrl::SetBkImage](#setbkimage)|设置列表视图控件的当前的背景图像。|  
|[Clistctrl:: Setcallbackmask](#setcallbackmask)|设置的列表视图控件的回调掩码。|  
|[CListCtrl::SetCheck](#setcheck)|设置当前显示与项相关联的状态图像的状态。|  
|[CListCtrl::SetColumn](#setcolumn)|设置列表视图列的属性。|  
|[CListCtrl::SetColumnOrderArray](#setcolumnorderarray)|设置的列表视图控件的列顺序 （从左到右）。|  
|[CListCtrl::SetColumnWidth](#setcolumnwidth)|更改报表视图或列表视图中的列的宽度。|  
|[CListCtrl::SetExtendedStyle](#setextendedstyle)|设置的列表视图控件的当前扩展的样式。|  
|[CListCtrl::SetGroupInfo](#setgroupinfo)|设置为指定的组列表视图控件的信息。|  
|[CListCtrl::SetGroupMetrics](#setgroupmetrics)|设置的列表视图控件的组度量值。|  
|[CListCtrl::SetHotCursor](#sethotcursor)|设置为列表视图控件启用热跟踪时使用的光标。|  
|[CListCtrl::SetHotItem](#sethotitem)|设置的列表视图控件的当前热项。|  
|[CListCtrl::SetHoverTime](#sethovertime)|设置的列表视图控件的当前悬停时间。|  
|[CListCtrl::SetIconSpacing](#seticonspacing)|设置在列表视图控件中的图标之间的间距。|  
|[CListCtrl::SetImageList](#setimagelist)|将图像列表分配给列表视图控件。|  
|[CListCtrl::SetInfoTip](#setinfotip)|设置工具提示文本。|  
|[CListCtrl::SetInsertMark](#setinsertmark)|将插入点设置为已定义的位置。|  
|[CListCtrl::SetInsertMarkColor](#setinsertmarkcolor)|设置插入点的颜色。|  
|[Clistctrl:: Setitem](#setitem)|设置的部分或全部列表视图项的属性。|  
|[CListCtrl::SetItemCount](#setitemcount)|准备添加大量项的列表视图控件。|  
|[CListCtrl::SetItemCountEx](#setitemcountex)|设置虚拟列表视图控件的项计数。|  
|[CListCtrl::SetItemData](#setitemdata)|设置项的应用程序特定的值。|  
|[CListCtrl::SetItemIndexState](#setitemindexstate)|设置当前的列表视图控件中的项的状态。|  
|[CListCtrl::SetItemPosition](#setitemposition)|将项移到列表视图控件中的指定位置。|  
|[CListCtrl::SetItemState](#setitemstate)|更改列表视图控件中的项的状态。|  
|[CListCtrl::SetItemText](#setitemtext)|更改列表视图项或子项的文本。|  
|[CListCtrl::SetOutlineColor](#setoutlinecolor)|设置列表视图控件的边框的颜色。|  
|[CListCtrl::SetSelectedColumn](#setselectedcolumn)|将列表视图控件的所选的列的设置。|  
|[CListCtrl::SetSelectionMark](#setselectionmark)|设置的列表视图控件的选择标记。|  
|[CListCtrl::SetTextBkColor](#settextbkcolor)|在列表视图控件中设置文本的背景色。|  
|[CListCtrl::SetTextColor](#settextcolor)|设置的列表视图控件的文本颜色。|  
|[CListCtrl::SetTileInfo](#settileinfo)|设置列表视图控件的磁贴的信息。|  
|[CListCtrl::SetTileViewInfo](#settileviewinfo)|平铺视图中设置的列表视图控件使用的信息。|  
|[CListCtrl::SetToolTips](#settooltips)|设置将使用列表视图控件来显示工具提示的工具提示控件。|  
|[CListCtrl::SetView](#setview)|将列表视图控件的视图设置。|  
|[CListCtrl::SetWorkAreas](#setworkareas)|设置图标可以显示在列表视图控件中的位置的区域。|  
|[CListCtrl::SortGroups](#sortgroups)|排序的组列表视图控件与用户定义函数。|  
|[CListCtrl::SortItems](#sortitems)|使用应用程序定义比较函数的列表视图项进行排序。|  
|[CListCtrl::SortItemsEx](#sortitemsex)|使用应用程序定义比较函数的列表视图项进行排序。|  
|[CListCtrl::SubItemHitTest](#subitemhittest)|确定哪些列表视图项目时，如果有的话位于给定位置。|  
|[CListCtrl::Update](#update)|强制控件重绘窗体的指定的项。|  
  
## <a name="remarks"></a>备注  
 除了一个图标和标签，每一项可以有在右侧的图标和标签列中显示的信息。 此控件 (并因此`CListCtrl`类) 仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 下运行的程序和更高版本。  
  
 下面是简要概述`CListCtrl`类。 有关详细的概念性讨论，请参阅[使用 CListCtrl](../../mfc/using-clistctrl.md)和[控件](../../mfc/controls-mfc.md)。  
  
## <a name="views"></a>视图  
 列表视图控件可以显示其内容在四种不同的方式，称为"视图"。  
  
-   图标视图  
  
     每个项都显示为带有它下面放一个标签的全尺寸图标 （32 x 32 像素为单位）。 用户可以将项拖动到列表视图窗口中的任何位置。  
  
-   小图标视图  
  
     每个项显示为小图标 （16 x 16 像素为单位） 具有标签到它的右侧。 用户可以将项拖动到列表视图窗口中的任何位置。  
  
-   列表视图  
  
     每个项都显示为带有标签与它的右侧的小图标。 项列中排列，并且无法拖到列表视图窗口中的任何位置。  
  
-   报表视图  
  
     每个项将显示在各占一行，在右侧列中排列的其他信息。 最左侧的列包含的小图标和标签，并且后续列都包含由应用程序指定的子项。 内嵌的标题控件 (类[CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)) 实现这些列。 标头控件和报表视图中的列的详细信息，请参阅[使用 CListCtrl︰ 控件 （报表视图） 中添加列](../../mfc/adding-columns-to-the-control-report-view.md)。  
  
 另请参见：  
  
-   知识库文章 Q250614︰ 如何︰ 在报表视图 CListCtrl 的项目排序  
  
-   知识库文章 Q200054: PRB: OnTimer() 是不调用反复为列表控件  
  
 控件的当前列表视图的样式确定当前的视图。 有关这些样式和它们的用法的详细信息，请参阅[使用 CListCtrl︰ 更改列表控件样式](../../mfc/changing-list-control-styles.md)。  
  
## <a name="extended-styles"></a>扩展的样式  
 除了标准列表样式类`CListCtrl`支持大量的扩展样式，提供丰富的功能。 此功能的一些示例包括︰  
  
-   将鼠标指针悬停所选内容  
  
     如果启用，则允许自动选择了某个项，当光标在项上停留一段时间。  
  
-   虚拟列表视图  
  
     如果启用，允许该控件以支持多达`DWORD`项。 这是通过将管理的应用程序中的项数据的开销。 除了所选择的项目和焦点的信息，必须由应用程序管理项的所有信息。 有关详细信息，请参阅[使用 CListCtrl︰ 虚拟列表控件](../../mfc/virtual-list-controls.md)。  
  
-   – 和两个 – 一键式激活  
  
     如果启用，允许 （自动突出显示的项文本） 的热跟踪和突出显示的项的一个或两个 – 单击激活。  
  
-   拖放列排序  
  
     如果启用，则允许对列表视图控件中的列的拖放进行重新排序。 仅在报表视图中可用。  
  
 有关使用这些新扩展样式，请参阅[使用 CListCtrl︰ 更改列表控件样式](../../mfc/changing-list-control-styles.md)。  
  
## <a name="items-and-subitems"></a>项和子项  
 在列表视图控件中的每个项由一个图标 （来自图像列表）、 标签、 当前状态和一个应用程序定义的值 （称为"项数据"） 组成。 一个或多个子项也可以与相关联的每一项。 "子项"是一个字符串，在报表视图中，可以显示在右侧的项的图标和标签列中。 列表视图控件中的所有项必须都具有相同数量的子项。  
  
 类**CListCtrl**用于插入、 删除、 查找、 和修改这些项目提供多个函数。 有关详细信息，请参阅[clistctrl:: Getitem](#getitem)， [CListCtrl::InsertItem](#insertitem)，和[CListCtrl::FindItem](#finditem)，[将项添加到该控件](../adding-items-to-the-control.md)，和[滚动、 排列、 排序和列表控件中查找](../scrolling-arranging-sorting-and-finding-in-list-controls.md)。  
  
 默认情况下，列表视图控件负责存储项的图标和文本属性。 但是，这些项类型，除了类`CListCtrl`支持"回调项"。 "回调项"是列表视图项为其应用程序，而不是控件 — 存储文本和 / 或图标。 回调掩码用于指定哪些项目属性 （文本和/或图标） 提供的应用程序。 如果应用程序使用回调项，它必须能够提供按需文本和/或图标的属性。 当应用程序已经保留其中一些信息时，回调项非常有用。 有关详细信息，请参阅[使用 CListCtrl︰ 回调项和回调掩码](../callback-items-and-the-callback-mask.md)。  
  
## <a name="image-lists"></a>图像列表  
 图标、 标头项图像和应用程序 – 为列表视图项包含多个图像列表中定义的状态 (由类实现[CImageList](cimagelist-class.md))，从而增加并将分配给列表视图控件。 每个列表视图控件可具有最多四个不同类型的图像列表︰  
  
-   大图标  
  
     图标视图中使用的全尺寸图标。  
  
-   小图标  
  
     用在小图标、 列表和报告视图图标视图中使用的图标的较小版本。  
  
-   应用程序定义的状态  
  
     包含用于表示一个应用程序定义的状态的项的图标旁边显示的状态图像。  
  
-   标头项  
  
     在报表视图用于显示在每个标头控件项的小图像。  
  
 默认情况下，列表视图控件销毁时销毁; 分配给它的图像列表但是，开发人员可以通过每个图像列表时销毁不再使用，具体由该应用程序确定自定义此行为。 有关详细信息，请参阅[使用 CListCtrl︰ 列表项和图像列表](../list-items-and-image-lists.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](cobject-class.md)  
  
 [CCmdTarget](ccmdtarget-class.md)  
  
 [CWnd](cwnd-class.md)  
  
 `CListCtrl`  
  
## <a name="requirements"></a>要求  
 **标头：** afxcmn.h  
  
##  <a name="a-nameapproximateviewrecta--clistctrlapproximateviewrect"></a><a name="approximateviewrect"></a>CListCtrl::ApproximateViewRect  
 确定的宽度和高度需要它来显示列表视图控件的项。  
  
```  
CSize ApproximateViewRect(
    CSize sz = CSize(-1,  
 -1),  
    int iCount = -1) const;  
```  
  
### <a name="parameters"></a>参数  
 `sz`  
 该控件，以像素为单位的建议的尺寸。 如果未指定维度，框架将使用该控件的当前宽度或高度值。  
  
 `iCount`  
 若要在控件中显示的项目数。 如果此参数为-1，框架将使用的总项数当前在控件中。  
  
### <a name="return-value"></a>返回值  
 一个`CSize`包含的大致宽度和高度显示的项，以像素为单位所需的对象。  
  
### <a name="remarks"></a>备注  
 此成员函数实现 Win32 宏的行为[ListView_ApproximateViewRect](http://msdn.microsoft.com/library/windows/desktop/bb761231)，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namearrangea--clistctrlarrange"></a><a name="arrange"></a>CListCtrl::Arrange  
 重新定位图标视图中的项目，以便它们在网格上对齐。  
  
```  
BOOL Arrange(UINT nCode);
```  
  
### <a name="parameters"></a>参数  
 `nCode`  
 指定的项的对齐方式样式。 它可以是下列值之一︰  
  
- `LVA_ALIGNLEFT`将窗口的项目沿左边缘对齐。  
  
- `LVA_ALIGNTOP`将窗口的项目沿上边缘对齐。  
  
- `LVA_DEFAULT`将根据列表视图当前对齐样式 （默认值） 的项目。  
  
- `LVA_SNAPTOGRID`将所有图标都对齐到最接近的网格位置。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 `nCode`参数指定对齐样式。  
  
### <a name="example"></a>示例    
```cpp  
    // Align all of the list view control items along the top
    // of the window (the list view control must be in icon or
    // small icon mode).
    m_myListCtrl.Arrange(LVA_ALIGNTOP);
```

  
##  <a name="a-namecanceleditlabela--clistctrlcanceleditlabel"></a><a name="canceleditlabel"></a>CListCtrl::CancelEditLabel  
 取消编辑操作的项文本。  
  
```  
void CancelEditLabel();
```  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_CANCELEDITLABEL](http://msdn.microsoft.com/library/windows/desktop/bb774886)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-nameclistctrla--clistctrlclistctrl"></a><a name="clistctrl"></a>CListCtrl::CListCtrl  
 构造 `CListCtrl` 对象。  
  
```  
CListCtrl();
```  
  
##  <a name="a-namecreatea--clistctrlcreate"></a><a name="create"></a>CListCtrl::Create  
 创建列表控件，并将其附加到`CListCtrl`对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 指定列表控件的样式。 适用于控件的列表控件样式的任意组合。 请参阅[列表视图的窗口样式](http://msdn.microsoft.com/library/windows/desktop/bb774739)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]有关这些样式的完整列表。 设置扩展样式特定于控件使用[SetExtendedStyle](#setextendedstyle)。  
  
 `rect`  
 指定列表控件的大小和位置。 它可为`CRect`对象或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构。  
  
 `pParentWnd`  
 指定列表控件的父窗口，通常`CDialog`。 它不能**NULL**。  
  
 `nID`  
 指定列表控件的 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 您构造`CListCtrl`分两个步骤。 首先，调用构造函数，然后调用**创建**，它创建列表视图控件，并将其附加到`CListCtrl`对象。  
  
 若要将扩展的窗口样式应用于列表控件对象，调用[CreateEx](#createex)而不是**创建**。  
  
### <a name="example"></a>示例  

```cpp  
    m_myListCtrl.Create(
        WS_CHILD|WS_VISIBLE|WS_BORDER|LVS_REPORT|LVS_EDITLABELS,
        CRect(10,10,400,200), pParentWnd, IDD_MYLISTCTRL);   
```

  
##  <a name="a-namecreateexa--clistctrlcreateex"></a><a name="createex"></a>CListCtrl::CreateEx  
 创建控件 （子窗口），并将其与相关联`CListCtrl`对象。  
  
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
 指定要创建的控件的扩展的样式。 扩展窗口样式的列表，请参阅`dwExStyle`参数[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
 `dwStyle`  
 指定列表控件的样式。 适用于控件的列表控件样式的任意组合。 有关这些样式的完整列表，请参阅[列表视图的窗口样式](http://msdn.microsoft.com/library/windows/desktop/bb774739)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
 `rect`  
 对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构的结构描述的大小和窗口，在中创建的工作区坐标位置`pParentWnd`。  
  
 `pParentWnd`  
 指向控件的父级的窗口的指针。  
  
 `nID`  
 控件的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 使用`CreateEx`而不是[创建](#create)应用扩展的窗口样式、 指定的 Windows 扩展的样式前言**WS_EX_**。  
  
 `CreateEx`创建具有指定的扩展窗口样式控件`dwExStyle`。 若要设置特定于控件的扩展的样式，调用[SetExtendedStyle](#setextendedstyle)。 例如，使用`CreateEx`设置作为此类样式**WS_EX_CONTEXTHELP**，但使用`SetExtendedStyle`设置作为此类样式**LVS_EX_FULLROWSELECT**。 有关详细信息，请参阅主题中介绍的样式[扩展列表视图样式](http://msdn.microsoft.com/library/windows/desktop/bb774732)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namecreatedragimagea--clistctrlcreatedragimage"></a><a name="createdragimage"></a>CListCtrl::CreateDragImage  
 创建指定的项的一个拖动图像列表`nItem`。  
  
```  
CImageList* CreateDragImage(
    int nItem,  
    LPPOINT lpPoint);
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 要创建其拖动图像列表的项的索引。  
  
 `lpPoint`  
 地址的指针[点](http://msdn.microsoft.com/library/windows/desktop/dd162805)结构，它接收的图像的左上角的初始位置在视图中协调。  
  
### <a name="return-value"></a>返回值  
 拖动图像列表中，如果成功，则指向的指针否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 `CImageList`对象是永久性的并且必须将其完成后删除。 例如：  
  

```cpp  
        CImageList* pImageList = m_myListCtrl.CreateDragImage(nItem, &point);

        // do something

        delete pImageList;
```

  
##  <a name="a-namedeleteallitemsa--clistctrldeleteallitems"></a><a name="deleteallitems"></a>CListCtrl::DeleteAllItems  
 从列表视图控件中删除所有项。  
  
```  
BOOL DeleteAllItems();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="example"></a>示例  

```cpp  
    // Delete all of the items from the list view control.
    m_myListCtrl.DeleteAllItems();
    ASSERT(m_myListCtrl.GetItemCount() == 0);
```

  
##  <a name="a-namedeletecolumna--clistctrldeletecolumn"></a><a name="deletecolumn"></a>CListCtrl::DeleteColumn  
 从列表视图控件中删除某一列。  
  
```  
BOOL DeleteColumn(int nCol);
```  
  
### <a name="parameters"></a>参数  
 `nCol`  
 要删除的列的索引。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="example"></a>示例  

```cpp  
        int nColumnCount = m_myListCtrl.GetHeaderCtrl()->GetItemCount();

        // Delete all of the columns.
        for (int i=0; i < nColumnCount; i++)
        {
            m_myListCtrl.DeleteColumn(0);
        }
```

  
##  <a name="a-namedeleteitema--clistctrldeleteitem"></a><a name="deleteitem"></a>CListCtrl::DeleteItem  
 从列表视图控件中删除的项。  
  
```  
BOOL DeleteItem(int nItem);
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 指定要删除的项的索引。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="example"></a>示例  
```cpp  
        int nCount = m_myListCtrl.GetItemCount();

        // Delete all of the items from the list view control.
        for (int i=0; i < nCount; i++)
        {
            m_myListCtrl.DeleteItem(0);
        }
```

  
##  <a name="a-namedrawitema--clistctrldrawitem"></a><a name="drawitem"></a>CListCtrl::DrawItem  
 由框架在所有者绘制列表视图控件更改的可视方位时调用。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpDrawItemStruct`  
 指向长指针`DRAWITEMSTRUCT`结构，其中包含有关所需的绘图类型的信息。  
  
### <a name="remarks"></a>备注  
 **ItemAction**的成员[DRAWITEMSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb775802)结构定义要执行的绘制操作。  
  
 默认情况下，此成员函数没有任何影响。 重写该成员函数以实现所有者描述的绘图`CListCtrl`对象。  
  
 应用程序应还原选择用于显示上下文中提供的所有图形设备接口 (GDI) 对象`lpDrawItemStruct`之前此成员函数将终止。  
  
##  <a name="a-nameeditlabela--clistctrleditlabel"></a><a name="editlabel"></a>CListCtrl::EditLabel  
 开始在就地编辑的项的文本。  
  
```  
CEdit* EditLabel(int nItem);
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 要编辑的列表视图项的索引。  
  
### <a name="return-value"></a>返回值  
 如果成功，一个指向`CEdit`对象，它是用于编辑的项文本; 否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 列表视图控件具有`LVS_EDITLABELS`窗口样式，用户可编辑位置中的项目标签。 用户开始编辑通过单击具有焦点的项的标签。  
  
 使用此函数以开始进行就地编辑的指定的列表视图项的文本。  
  
### <a name="example"></a>示例  
```cpp  
        // Make sure the focus is set to the list view control.
        m_myListCtrl.SetFocus();

        // Show the edit control on the label of the first
        // item in the list view control.
        CEdit* pmyEdit = m_myListCtrl.EditLabel(1);
        ASSERT(pmyEdit != NULL);
```

  
##  <a name="a-nameenablegroupviewa--clistctrlenablegroupview"></a><a name="enablegroupview"></a>CListCtrl::EnableGroupView  
 启用或禁用是否在列表视图控件中的项目显示为一组。  
  
```  
LRESULT EnableGroupView(BOOL fEnable);
```  
  
### <a name="parameters"></a>参数  
 `fEnable`  
 指示是否启用将 listview 控件与组显示的项。 **TRUE**以便分组，则**FALSE**以将其禁用。  
  
### <a name="return-value"></a>返回值  
 返回下列值之一︰  
  
- **0**能够显示列表视图项根据一组已启用或禁用。  
  
- **1**已成功更改控件的状态。  
  
- **为-1**操作失败。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_ENABLEGROUPVIEW](http://msdn.microsoft.com/library/windows/desktop/bb774900)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-nameensurevisiblea--clistctrlensurevisible"></a><a name="ensurevisible"></a>CListCtrl::EnsureVisible  
 确保列表视图项至少部分可见。  
  
```  
BOOL EnsureVisible(
    int nItem,  
    BOOL bPartialOK);
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 是要显示的列表视图项的索引。  
  
 `bPartialOK`  
 指定是否可以接受部分可见性。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 如有必要，将滚动列表视图控件。 如果`bPartialOK`参数为非零，则不会发生滚动该项是否部分可见。  
  
### <a name="example"></a>示例  
```cpp  
        // Ensure that the last item is visible.
        int nCount = m_myListCtrl.GetItemCount();
        if (nCount > 0)
            m_myListCtrl.EnsureVisible(nCount-1, FALSE);
```

  
##  <a name="a-namefinditema--clistctrlfinditem"></a><a name="finditem"></a>CListCtrl::FindItem  
 搜索具有指定特征的列表视图项。  
  
```  
int FindItem(
    LVFINDINFO* pFindInfo,  
    int nStart = -1) const;  
```  
  
### <a name="parameters"></a>参数  
 `pFindInfo`  
 一个指向[LVFINDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774745)结构，它包含有关要在其中搜索的项的信息。  
  
 `nStart`  
 此项开始搜索，则为-1 以从头开始的索引。 处的项`nStart`如果从搜索中排除`nStart`是否不等于-1。  
  
### <a name="return-value"></a>返回值  
 如果成功的项目或否则为-1 的索引。  
  
### <a name="remarks"></a>备注  
 `pFindInfo`参数指向**LVFINDINFO**结构，其中包含用于搜索列表视图项的信息。  
  
### <a name="example"></a>示例  

```cpp  
        LVFINDINFO info;
        int nIndex;

        info.flags = LVFI_PARTIAL|LVFI_STRING;
        info.psz = _T("item");

        // Delete all of the items that begin with the string.
        while ((nIndex = m_myListCtrl.FindItem(&info)) != -1)
        {
            m_myListCtrl.DeleteItem(nIndex);
        }
```

  
##  <a name="a-namegetbkcolora--clistctrlgetbkcolor"></a><a name="getbkcolor"></a>CListCtrl::GetBkColor  
 检索列表视图控件的背景色。  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 用来指定 RGB 颜色的 32 位值。  
  
### <a name="example"></a>示例  
  请参阅示例[CListCtrl::SetBkColor](#setbkcolor)。  
  
##  <a name="a-namegetbkimagea--clistctrlgetbkimage"></a><a name="getbkimage"></a>CListCtrl::GetBkImage  
 检索当前的背景图像的列表视图控件。  
  
```  
BOOL GetBkImage(LVBKIMAGE* plvbkImage) const;  
```  
  
### <a name="parameters"></a>参数  
 `plvbkImage`  
 一个指向**LVBKIMAGE**结构，它包含当前的背景图像的列表视图。  
  
### <a name="return-value"></a>返回值  
 则返回非零，如果成功，否则为零。  
  
### <a name="remarks"></a>备注  
 此方法实现 Win32 宏的行为[ListView_GetBkImage](http://msdn.microsoft.com/library/windows/desktop/bb761246)，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  

```cpp  
        LVBKIMAGE bki;

        // If no background image is set for the list view control use
        // the Microsoft homepage image as the background image.
        if (m_myListCtrl.GetBkImage(&bki) && (bki.ulFlags == LVBKIF_SOURCE_NONE))
        {
            m_myListCtrl.SetBkImage(
                _T("http://www.microsoft.com/library/images/gifs/homepage/microsoft.gif"),
                TRUE);
        }
```

  
##  <a name="a-namegetcallbackmaska--clistctrlgetcallbackmask"></a><a name="getcallbackmask"></a>Clistctrl:: Getcallbackmask  
 检索列表视图控件的回调掩码。  
  
```  
UINT GetCallbackMask() const;  
```  
  
### <a name="return-value"></a>返回值  
 列表视图控件的回调掩码。  
  
### <a name="remarks"></a>备注  
 "回调项"是列表视图项为其应用程序，而不是控件 — 存储文本和 / 或图标。 虽然列表视图控件可以为您存储这些属性，可能想要使用回调项，如果应用程序已经维护其中一些信息。 回调掩码指定哪些项状态位维护应用程序，并应用于整个控件，而不是特定项。 回调掩码默认为零，这意味着控件将跟踪所有项状态。 如果应用程序使用回调项，或者指定一个非零的回调掩码，它必须能够提供按需列表视图项特性。  
  
### <a name="example"></a>示例  
  请参阅示例[clistctrl:: Setcallbackmask](#setcallbackmask)。  
  
##  <a name="a-namegetchecka--clistctrlgetcheck"></a><a name="getcheck"></a>CListCtrl::GetCheck  
 检索与项相关联的状态图像的当前显示状态。  
  
```  
BOOL GetCheck(int nItem) const;  
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 列表控件项的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 非零，如果选择了项目，否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数实现 Win32 宏的行为[ListView_GetCheckState](http://msdn.microsoft.com/library/windows/desktop/bb761250)，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CListCtrl::SetCheck](#setcheck)。  
  
##  <a name="a-namegetcolumna--clistctrlgetcolumn"></a><a name="getcolumn"></a>CListCtrl::GetColumn  
 检索列表视图控件的列的属性。  
  
```  
BOOL GetColumn(
    int nCol,  
    LVCOLUMN* pColumn) const;  
```  
  
### <a name="parameters"></a>参数  
 `nCol`  
 要检索其属性的列的索引。  
  
 `pColumn`  
 地址的指针[LVCOLUMN](http://msdn.microsoft.com/library/windows/desktop/bb774743)结构，它指定要检索的信息并接收有关列的信息。 **掩码**成员指定要检索的列属性。 如果**掩码**成员指定`LVCF_TEXT`值， **pszText**成员必须包含接收项文本的缓冲区的地址和**cchTextMax**成员必须指定缓冲区的大小。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 **LVCOLUMN**结构包含在报表视图中的列的相关信息。  
  
### <a name="example"></a>示例  

```cpp  
        LVCOLUMN col;

        col.mask = LVCF_WIDTH;

        // Double the column width of the first column.
        if (m_myListCtrl.GetColumn(0, &col))
        {
            col.cx *= 2;
            m_myListCtrl.SetColumn(0, &col);
        }
```

  
##  <a name="a-namegetcolumnorderarraya--clistctrlgetcolumnorderarray"></a><a name="getcolumnorderarray"></a>CListCtrl::GetColumnOrderArray  
 检索列表视图控件的列顺序 （从左到右）。  
  
```  
BOOL GetColumnOrderArray(
    LPINT piArray,  
    int iCount = -1);
```  
  
### <a name="parameters"></a>参数  
 `piArray`  
 指向将包含在列表视图控件中列的索引值的缓冲区的指针。 缓冲区必须足够大以包含在列表视图控件中的列的总数。  
  
 `iCount`  
 在列表视图控件中的列数。 如果此参数为-1，由框架自动检索的列数。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 此成员函数实现 Win32 宏的行为[ListView_GetColumnOrderArray](http://msdn.microsoft.com/library/windows/desktop/bb761254)，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  

```cpp  
        // Reverse the order of the columns in the list view control
        // (i.e. make the first column the last, the last column
        // the first, and so on...).
        CHeaderCtrl* pHeaderCtrl = m_myListCtrl.GetHeaderCtrl();

        if (pHeaderCtrl != NULL)
        {
            int  nColumnCount = pHeaderCtrl->GetItemCount();
            LPINT pnOrder = (LPINT) malloc(nColumnCount*sizeof(int));
            ASSERT(pnOrder != NULL);
m_myListCtrl.GetColumnOrderArray(pnOrder, nColumnCount);

            int i, j, nTemp;
            for (i = 0, j = nColumnCount-1; i < j; i++, j--)
            {
                nTemp = pnOrder[i];
                pnOrder[i] = pnOrder[j];
                pnOrder[j] = nTemp;
            }

            m_myListCtrl.SetColumnOrderArray(nColumnCount, pnOrder);
            free(pnOrder);
        }
```

  
##  <a name="a-namegetcolumnwidtha--clistctrlgetcolumnwidth"></a><a name="getcolumnwidth"></a>CListCtrl::GetColumnWidth  
 检索报表视图或列表视图中的列的宽度。  
  
```  
int GetColumnWidth(int nCol) const;  
```  
  
### <a name="parameters"></a>参数  
 `nCol`  
 指定要检索其宽度所在列的索引。  
  
### <a name="return-value"></a>返回值  
 以像素为单位指定的列的宽度`nCol`。  
  
### <a name="example"></a>示例  

```cpp  
        // Increase the column width of the second column by 20.
        int nWidth = m_myListCtrl.GetColumnWidth(1);
        m_myListCtrl.SetColumnWidth(1, 20 + nWidth);
```

  
##  <a name="a-namegetcountperpagea--clistctrlgetcountperpage"></a><a name="getcountperpage"></a>CListCtrl::GetCountPerPage  
 计算的装载量垂直列表视图控件的可视区域中时在列表视图或报表视图中的项的数目。  
  
```  
int GetCountPerPage() const;  
```  
  
### <a name="return-value"></a>返回值  
 可以适合垂直列表视图控件的可视区域中时在列表视图或报表视图中的项的数目。  
  
### <a name="example"></a>示例  
  请参阅示例[CListCtrl::GetTopIndex](#gettopindex)。  
  
##  <a name="a-namegeteditcontrola--clistctrlgeteditcontrol"></a><a name="geteditcontrol"></a>CListCtrl::GetEditControl  
 检索用于编辑的列表视图项的文本编辑控件的句柄。  
  
```  
CEdit* GetEditControl() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，一个指向[CEdit](cedit-class.md)对象，它是用于编辑的项文本; 否则为**NULL**。  
  
### <a name="example"></a>示例  

```cpp  
        // The string replacing the text in the edit control.
        LPCTSTR lpszmyString = _T("custom label!");

        // If possible, replace the text in the label edit control.
        CEdit* pEdit = m_myListCtrl.GetEditControl();

        if (pEdit != NULL)
        {
            pEdit->SetWindowText(lpszmyString);
        }
```

  
##  <a name="a-namegetemptytexta--clistctrlgetemptytext"></a><a name="getemptytext"></a>CListCtrl::GetEmptyText  
 检索要显示当前的 list view 控件是否为空的字符串。  
  
```  
CString GetEmptyText() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个[CString](../../atl-mfc-shared/reference/cstringt-class.md) ，其中包含要显示该控件是否为空的文本。  
  
### <a name="remarks"></a>备注  
 此方法可发送[LVM_GETEMPTYTEXT](http://msdn.microsoft.com/library/windows/desktop/bb774921)消息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegetextendedstylea--clistctrlgetextendedstyle"></a><a name="getextendedstyle"></a>CListCtrl::GetExtendedStyle  
 检索列表视图控件的当前扩展的样式。  
  
```  
DWORD GetExtendedStyle();
```  
  
### <a name="return-value"></a>返回值  
 当前正在使用该列表的扩展样式的组合视图控件。 这些扩展样式的描述性列表，请参阅[扩展列表视图样式](http://msdn.microsoft.com/library/windows/desktop/bb774732)中的主题[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 此成员函数实现 Win32 宏的行为[ListView_GetExtendedListViewStyle](http://msdn.microsoft.com/library/windows/desktop/bb761264)，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CListCtrl::SetExtendedStyle](#setextendedstyle)。  
  
##  <a name="a-namegetfirstselecteditempositiona--clistctrlgetfirstselecteditemposition"></a><a name="getfirstselecteditemposition"></a>CListCtrl::GetFirstSelectedItemPosition  
 获取在列表视图控件中的第一个选择项位置。  
  
```  
POSITION GetFirstSelectedItemPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个**位置**可以用于迭代或检索对象指针; 值**NULL**如果未不选择任何项。  
  
### <a name="example"></a>示例  
 下面的代码示例演示此函数的用法。  
  

```cpp  
        POSITION pos = m_myListCtrl.GetFirstSelectedItemPosition();
        if (pos == NULL)
        {
            TRACE(_T("No items were selected!\n"));
        }
        else
        {
            while (pos)
            {
                int nItem = m_myListCtrl.GetNextSelectedItem(pos);
                TRACE(_T("Item %d was selected!\n"), nItem);
                // you could do your own processing on nItem here
            }
        }
```

  
##  <a name="a-namegetfocusedgroupa--clistctrlgetfocusedgroup"></a><a name="getfocusedgroup"></a>CListCtrl::GetFocusedGroup  
 检索当前的列表视图控件中具有键盘焦点的组。  
  
```  
int GetFocusedGroup() const;  
```  
  
### <a name="return-value"></a>返回值  
 其状态的组的索引`LVGS_FOCUSED`，如果有这样一个组; 否则为-1。  
  
### <a name="remarks"></a>备注  
 此方法可发送[LVM_GETFOCUSEDGROUP](http://msdn.microsoft.com/library/windows/desktop/bb774925)消息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。 有关详细信息，请参阅`LVGS_FOCUSED`值`state`的成员[LVGROUP](http://msdn.microsoft.com/library/windows/desktop/bb774769)结构。  
  
##  <a name="a-namegetgroupcounta--clistctrlgetgroupcount"></a><a name="getgroupcount"></a>CListCtrl::GetGroupCount  
 检索当前的列表视图控件中的组数。  
  
```  
int GetGroupCount()const;  
```  
  
### <a name="return-value"></a>返回值  
 在列表视图控件中的组的数目。  
  
### <a name="remarks"></a>备注  
 此方法可发送[LVM_GETGROUPCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb774931)消息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]-->。  
  
##  <a name="a-namegetgroupinfoa--clistctrlgetgroupinfo"></a><a name="getgroupinfo"></a>CListCtrl::GetGroupInfo  
 为指定的一组列表视图控件中获取的信息。  
  
```  
int GetGroupInfo(
    int iGroupId,  
    PLVGROUP pgrp) const;  
```  
  
### <a name="parameters"></a>参数  
 `iGroupId`  
 要检索其信息的组的标识符。  
  
 `pgrp`  
 一个指向[LVGROUP](http://msdn.microsoft.com/library/windows/desktop/bb774769)包含指定的组相关信息。  
  
### <a name="return-value"></a>返回值  
 否则，返回组如果成功，则为-1 的 ID。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_GETGROUPINFO](http://msdn.microsoft.com/library/windows/desktop/bb774932)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegetgroupinfobyindexa--clistctrlgetgroupinfobyindex"></a><a name="getgroupinfobyindex"></a>CListCtrl::GetGroupInfoByIndex  
 检索有关指定的组中当前的 list view 控件的信息。  
  
```  
BOOL GetGroupInfoByIndex(
    int iIndex,   
    PLVGROUP pGroup) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `iIndex`|组的从零开始索引。|  
|[out] `pGroup`|指向[LVGROUP](http://msdn.microsoft.com/library/windows/desktop/bb774769)接收由指定的组的相关信息的结构`iIndex`参数。<br /><br /> 调用方负责初始化的成员[LVGROUP](http://msdn.microsoft.com/library/windows/desktop/bb774769)结构。 设置`cbSize`成员为该结构的大小，并且所用的标志`mask`成员来指定要检索的信息。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[LVM_GETGROUPINFOBYINDEX](http://msdn.microsoft.com/library/windows/desktop/bb774933)消息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]-->。  
  
### <a name="example"></a>示例  
 下面的代码示例定义一个变量， `m_listCtrl`，也就是说，用来访问当前的 list view 控件。 此变量将在下一个示例中使用。  

```cpp  
public:
    // Variable used to access the list control.
    CListCtrl m_listCtrl; 
```

  
### <a name="example"></a>示例  
 下面的代码示例演示`GetGroupInfoByIndex`方法。 在此代码的前面一节中我们创建了一个列表视图控件的示例显示在报表视图中的标题为"ClientID"和"等级"的两个列。 如果存在这样一个组，下面的代码示例检索有关其索引为 0，组的信息。    
```cpp  
    // GetGroupInfoByIndex
    const int GROUP_HEADER_BUFFER_SIZE = 40;

// Initialize the structure 
    LVGROUP gInfo = {0};
    gInfo.cbSize = sizeof(LVGROUP);
    wchar_t wstrHeadGet[GROUP_HEADER_BUFFER_SIZE] = {0};
    gInfo.cchHeader = GROUP_HEADER_BUFFER_SIZE;
    gInfo.pszHeader = wstrHeadGet;
    gInfo.mask = (LVGF_ALIGN | LVGF_STATE | LVGF_HEADER | LVGF_GROUPID);
    gInfo.state = LVGS_NORMAL;
    gInfo.uAlign  = LVGA_HEADER_LEFT;

    BOOL bRet = m_listCtrl.GetGroupInfoByIndex( 0, &gInfo );
    if (bRet == TRUE) {
        CString strHeader = CString( gInfo.pszHeader );
        CString str;
        str.Format(_T("Header: '%s'"), strHeader);
        AfxMessageBox(str, MB_ICONINFORMATION);
    }
    else
    {
        AfxMessageBox(_T("No group information was retrieved."));
    }
```

  
##  <a name="a-namegetgroupmetricsa--clistctrlgetgroupmetrics"></a><a name="getgroupmetrics"></a>CListCtrl::GetGroupMetrics  
 检索一个组的度量值。  
  
```  
void GetGroupMetrics(PLVGROUPMETRICS pGroupMetrics) const;  
```  
  
### <a name="parameters"></a>参数  
 `pGroupMetrics`  
 一个指向[LVGROUPMETRICS](http://msdn.microsoft.com/library/windows/desktop/bb774752)包含组度量值信息。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_GETGROUPMETRICS](http://msdn.microsoft.com/library/windows/desktop/bb774934)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegetgrouprecta--clistctrlgetgrouprect"></a><a name="getgrouprect"></a>CListCtrl::GetGroupRect  
 检索指定的组中当前的 list view 控件的边框。  
  
```  
BOOL GetGroupRect(
    int iGroupId,   
    LPRECT lpRect,   
    int iCoords = LVGGR_GROUP) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `iGroupId`|指定一组。|  
|[in, out] `lpRect`|指向[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构。 如果此方法成功，该结构接收由指定的组的矩形坐标`iGroupId`。|  
|[in] `iCoords`|指定要检索的矩形坐标。 使用下列值之一︰<br /><br /> - `LVGGR_GROUP`-整个展开的组 （默认值） 坐标。<br />- `LVGGR_HEADER`坐标只有标头 （折叠组）。<br />- `LVGGR_SUBSETLINK`坐标只对子集链路 （标记子集）。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 调用方负责分配[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)指向结构`pRect`参数。  
  
 此方法可发送[LVM_GETGROUPRECT](http://msdn.microsoft.com/library/windows/desktop/bb774935)消息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义一个变量， `m_listCtrl`，也就是说，用来访问当前的 list view 控件。 此变量将在下一个示例中使用。    
```cpp  
public:
    // Variable used to access the list control.
    CListCtrl m_listCtrl; 
```

  
### <a name="example"></a>示例  
 下面的代码示例演示`GetGroupRect`方法。 在此代码示例早期部分中，我们创建了一个显示在报表视图中的标题为"ClientID"和"等级"的两个列的列表视图控件。 如果存在这样一个组，下面的代码示例绘制 3D 矩形框住其索引为 0 的组。    
  
```cpp  
    // GetGroupRect

    // Get the graphics rectangle that surrounds group 0.
    CRect rect;
    BOOL bRet = m_listCtrl.GetGroupRect( 0, &rect, LVGGR_GROUP); 
    // Draw a blue rectangle around group 0.
    if (bRet == TRUE) {
        m_listCtrl.GetDC()->Draw3dRect( &rect, RGB(0, 0, 255), RGB(0, 0, 255));
    }
    else {
        AfxMessageBox(_T("No group information was retrieved."), MB_ICONINFORMATION);
    }
```

  
##  <a name="a-namegetgroupstatea--clistctrlgetgroupstate"></a><a name="getgroupstate"></a>CListCtrl::GetGroupState  
 检索当前的列表视图控件中的指定组的状态。  
  
```  
UINT GetGroupState(
    int iGroupId,   
    DWORD dwMask) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `iGroupId`|组的从零开始索引。|  
|[in] `dwMask`|指定要检索指定组的状态值的掩码。 有关详细信息，请参阅`mask`的成员[LVGROUP](http://msdn.microsoft.com/library/windows/desktop/bb774769)结构。|  
  
### <a name="return-value"></a>返回值  
 为指定的组，则为 0，如果找不到组请求的状态。  
  
### <a name="remarks"></a>备注  
 返回值的按位与运算的结果位于`dwMask`参数和值的`state`的成员[LVGROUP](http://msdn.microsoft.com/library/windows/desktop/bb774769)结构，它表示当前的 list view 控件。  
  
 此方法可发送[LVM_GETGROUPSTATE](http://msdn.microsoft.com/library/windows/desktop/bb774936)消息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。 有关详细信息，请参阅[ListView_GetGroupState](http://msdn.microsoft.com/library/windows/desktop/bb761288)宏。  
  
##  <a name="a-namegetheaderctrla--clistctrlgetheaderctrl"></a><a name="getheaderctrl"></a>CListCtrl::GetHeaderCtrl  
 检索列表视图控件的标头控件。  
  
```  
CHeaderCtrl* GetHeaderCtrl();
```  
  
### <a name="return-value"></a>返回值  
 指向使用列表视图控件的标头控件的指针。  
  
### <a name="remarks"></a>备注  
 此成员函数实现 Win32 宏的行为[ListView_GetHeader](http://msdn.microsoft.com/library/windows/desktop/bb761290)，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CListCtrl::GetColumnOrderArray](#getcolumnorderarray)。  
  
##  <a name="a-namegethotcursora--clistctrlgethotcursor"></a><a name="gethotcursor"></a>CListCtrl::GetHotCursor  
 检索用于列表视图控件启用热跟踪时使用的游标。  
  
```  
HCURSOR GetHotCursor();
```  
  
### <a name="return-value"></a>返回值  
 正在使用列表视图控件的当前热光标资源句柄。  
  
### <a name="remarks"></a>备注  
 此成员函数实现 Win32 宏的行为[ListView_GetHotCursor](http://msdn.microsoft.com/library/windows/desktop/bb761292)，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。 将光标移到任何列表视图项时，将显示热的游标，仅启用了悬停选择时, 可见。 通过设置启用悬停选择**LVS_EX_TRACKSELECT**扩展样式。  
  
### <a name="example"></a>示例    
  
```cpp  
        // Set the hot cursor to be the system app starting cursor.
        HCURSOR hCursor = ::LoadCursor(NULL, IDC_APPSTARTING);
        m_myListCtrl.SetHotCursor(hCursor);
        ASSERT(m_myListCtrl.GetHotCursor() == hCursor);
```

  
##  <a name="a-namegethotitema--clistctrlgethotitem"></a><a name="gethotitem"></a>CListCtrl::GetHotItem  
 检索当前光标下的列表视图项。  
  
```  
int GetHotItem();
```  
  
### <a name="return-value"></a>返回值  
 列表视图控件的当前热项的索引。  
  
### <a name="remarks"></a>备注  
 此成员函数实现 Win32 宏的行为[ListView_GetHotItem](http://msdn.microsoft.com/library/windows/desktop/bb761294)，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。 热项都定义为已启用当前选定的项时热跟踪 （和将鼠标指针悬停选择）。  
  
 如果启用热跟踪，当用户悬停在列表视图项上时，无需使用鼠标按钮自动突出显示项目标签。  
  
### <a name="example"></a>示例    
  
```cpp  
    // Set the hot item to the first item only if no other item is 
    // highlighted.
    if (m_myListCtrl.GetHotItem() == -1)
        m_myListCtrl.SetHotItem(0);
```

  
##  <a name="a-namegethovertimea--clistctrlgethovertime"></a><a name="gethovertime"></a>CListCtrl::GetHoverTime  
 检索列表视图控件的当前悬停时间。  
  
```  
DWORD GetHoverTime() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回延迟，以毫秒为单位，鼠标光标必须将鼠标指针悬停在某个项之前选中该选项。 如果返回值为-1，悬停时间后，则默认悬停时间。  
  
### <a name="remarks"></a>备注  
 此成员函数实现 Win32 宏的行为[ListView_GetHoverTime](http://msdn.microsoft.com/library/windows/desktop/bb761296)，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例    
  
```cpp  
        // If the hover time is the default set to 1 sec.
        DWORD dwTime = m_myListCtrl.GetHoverTime();
        if (dwTime == -1)
            m_myListCtrl.SetHoverTime(1000);
```

  
##  <a name="a-namegetimagelista--clistctrlgetimagelist"></a><a name="getimagelist"></a>CListCtrl::GetImageList  
 检索图像列表用于绘图的列表视图项的句柄。  
  
```  
CImageList* GetImageList(int nImageList) const;  
```  
  
### <a name="parameters"></a>参数  
 `nImageList`  
 值，该值指定要检索的图像列表。 它可以是下列值之一︰  
  
- `LVSIL_NORMAL`带有大图标的图像列表。  
  
- `LVSIL_SMALL`带有小图标的图像列表。  
  
- `LVSIL_STATE`包含状态图像的图像列表。  
  
### <a name="return-value"></a>返回值  
 指向用于绘制列表视图项的图像列表的指针。  
  
### <a name="example"></a>示例    
  
```cpp  
        ASSERT(m_myListCtrl.GetImageList(LVSIL_NORMAL) == NULL);
m_myListCtrl.SetImageList(&m_lcImageList, LVSIL_NORMAL);
        ASSERT(m_myListCtrl.GetImageList(LVSIL_NORMAL) == &m_lcImageList);
```

  
##  <a name="a-namegetinsertmarka--clistctrlgetinsertmark"></a><a name="getinsertmark"></a>CListCtrl::GetInsertMark  
 检索当前的位置插入标记。  
  
```  
BOOL GetInsertMark(LPLVINSERTMARK lvim) const;  
```  
  
### <a name="parameters"></a>参数  
 `lvim`  
 一个指向[LVINSERTMARK](http://msdn.microsoft.com/library/windows/desktop/bb774758)结构，其中包含插入标记的信息。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**如果成功，或**FALSE**否则为。 **FALSE**如果返回的大小以`cbSize`的成员**LVINSERTMARK**结构不相等的结构的实际大小。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_GETINSERTMARK](http://msdn.microsoft.com/library/windows/desktop/bb774945)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegetinsertmarkcolora--clistctrlgetinsertmarkcolor"></a><a name="getinsertmarkcolor"></a>CListCtrl::GetInsertMarkColor  
 检索当前颜色的插入标记。  
  
```  
COLORREF GetInsertMarkColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)结构，其中包含插入点的颜色。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_GETINSERTMARKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774947)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegetinsertmarkrecta--clistctrlgetinsertmarkrect"></a><a name="getinsertmarkrect"></a>CListCtrl::GetInsertMarkRect  
 将检索限定插入点的矩形。  
  
```  
int GetInsertMarkRect(LPRECT pRect) const;  
```  
  
### <a name="parameters"></a>参数  
 `pRect`  
 指向`RECT`结构，其中包含限定插入点的矩形的坐标。  
  
### <a name="return-value"></a>返回值  
 返回下列值之一︰  
  
- **0**未找到插入点。  
  
- **1**找到插入点。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_GETINSERTMARKRECT](http://msdn.microsoft.com/library/windows/desktop/bb774949)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegetitema--clistctrlgetitem"></a><a name="getitem"></a>Clistctrl:: Getitem  
 检索部分或全部的列表视图项属性。  
  
```  
BOOL GetItem(LVITEM* pItem) const;  
```  
  
### <a name="parameters"></a>参数  
 `pItem`  
 指向[LVITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760)结构，它接收项的属性。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 **LVITEM**结构指定或接收的列表视图项的属性。  
  
##  <a name="a-namegetitemcounta--clistctrlgetitemcount"></a><a name="getitemcount"></a>CListCtrl::GetItemCount  
 检索在列表视图控件中的项的数目。  
  
```  
int GetItemCount() const; 
```  
  
### <a name="return-value"></a>返回值  
 在列表视图控件中的项的数目。  
  
### <a name="example"></a>示例  
  请参阅示例[CListCtrl::DeleteItem](#deleteitem)。  
  
##  <a name="a-namegetitemdataa--clistctrlgetitemdata"></a><a name="getitemdata"></a>CListCtrl::GetItemData  
 检索与指定的项相关联的 32 位应用程序特定的值`nItem`。  
  
```  
DWORD_PTR GetItemData(int nItem) const; 
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 要检索其数据的列表项的索引。  
  
### <a name="return-value"></a>返回值  
 与指定的项关联的 32 位应用程序特定值。  
  
### <a name="remarks"></a>备注  
 此值是**lParam**的成员[LVITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760)结构，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]  
  
### <a name="example"></a>示例  

```cpp  
    // If any item's data is equal to zero then reset it to -1.
    for (int i=0; i < m_myListCtrl.GetItemCount(); i++)
    {
        if (m_myListCtrl.GetItemData(i) == 0)
        {
            m_myListCtrl.SetItemData(i, (DWORD) -1);
        }
    }
```

  
##  <a name="a-namegetitemindexrecta--clistctrlgetitemindexrect"></a><a name="getitemindexrect"></a>CListCtrl::GetItemIndexRect  
 为所有或部分当前列表视图控件中的子项中检索的绑定矩形。  
  
```  
BOOL GetItemIndexRect(
    PLVITEMINDEX pItemIndex,   
    int iColumn,   
    int rectType,   
    LPRECT pRect) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `pItemIndex`|指向[LVITEMINDEX](http://msdn.microsoft.com/library/windows/desktop/bb774762)子项的父项的结构。<br /><br /> 调用方负责分配和设置的成员[LVITEMINDEX](http://msdn.microsoft.com/library/windows/desktop/bb774762)结构。 此参数不能为`NULL`。|  
|[in] `iColumn`|在控件中的列的从零开始索引。|  
|[in] `rectType`|为其检索边框的列表视图子项的部分。 指定下列值之一：<br /><br /> `LVIR_BOUNDS`-返回整个子项，包括图标和标签的边框。<br /><br /> `LVIR_ICON`-返回图标或小图标的子项的边框。<br /><br /> `LVIR_LABEL`-返回子项文本的边框。|  
|[out] `pRect`|指向[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它接收的子项信息的绑定矩形。<br /><br /> 调用方负责分配[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构。 此参数不能为`NULL`。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[LVM_GETITEMINDEXRECT](http://msdn.microsoft.com/library/windows/desktop/bb761046)消息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。 有关详细信息，请参阅[ListView_GetItemIndexRect 宏](http://msdn.microsoft.com/library/windows/desktop/bb774959)。  
  
### <a name="example"></a>示例  
 下面的代码示例定义一个变量， `m_listCtrl`，也就是说，用来访问当前的 list view 控件。 此变量将在下一个示例中使用。    
  
```cpp  
public:
    // Variable used to access the list control.
    CListCtrl m_listCtrl; 
```

  
### <a name="example"></a>示例  
 下面的代码示例演示`GetGroupRect`方法。 在输入此代码之前我们创建了一个列表视图控件的示例显示在报表视图中的标题为"ClientID"和"等级"的两个列。 下面的代码示例在两列均绘制第二个子项周围的 3D 矩形。    
  
```cpp  
    // GetItemIndexRect
    // Get the rectangle that bounds the second item in the first group.
    LVITEMINDEX lvItemIndex;
    lvItemIndex.iGroup = 0;
    lvItemIndex.iItem = 1;
    CRect rect;
    BOOL bRet = m_listCtrl.GetItemIndexRect(
        &lvItemIndex, 0, LVIR_BOUNDS, &rect);

    // Draw a red rectangle around the item.
    m_listCtrl.GetDC()->Draw3dRect( &rect, RGB(255, 0, 0), RGB(255, 0, 0) );
```

  
##  <a name="a-namegetitempositiona--clistctrlgetitemposition"></a><a name="getitemposition"></a>CListCtrl::GetItemPosition  
 检索列表视图项的位置。  
  
```  
BOOL GetItemPosition(
    int nItem,  
    LPPOINT lpPoint) const;  
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 要检索其位置的项的索引。  
  
 `lpPoint`  
 地址的指针[点](http://msdn.microsoft.com/library/windows/desktop/dd162805)结构，它接收项的左上角的位置在视图中协调。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="example"></a>示例    
  
```cpp  
        POINT pt;

        // Move all items in the list control 100 pixels to the right.
        UINT i, nCount = m_myListCtrl.GetItemCount();

        for (i=0; i < nCount; i++)
        {
            m_myListCtrl.GetItemPosition(i, &pt);
            pt.x += 100;
            m_myListCtrl.SetItemPosition(i, pt);
        }   
```

  
##  <a name="a-namegetitemrecta--clistctrlgetitemrect"></a><a name="getitemrect"></a>CListCtrl::GetItemRect  
 检索为所有或部分当前视图中的项的边框。  
  
```  
BOOL GetItemRect(
    int nItem,  
    LPRECT lpRect,  
    UINT nCode) const;  
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 要检索其位置的项的索引。  
  
 `lpRect`  
 地址的指针[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它接收的边框。  
  
 `nCode`  
 要检索的绑定矩形的列表视图项的一部分。 它可以是下列值之一︰  
  
- `LVIR_BOUNDS`返回整个项，包括图标和标签的边框。  
  
- `LVIR_ICON`返回的图标或小图标的边框。  
  
- `LVIR_LABEL`返回项文本的边框。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="example"></a>示例    
  
```cpp  
// OnClick is the handler for the NM_CLICK notification
void CListCtrlDlg::OnClick(NMHDR* pNMHDR, LRESULT* pResult)
{
    UNREFERENCED_PARAMETER(pResult);
LPNMITEMACTIVATE pia = (LPNMITEMACTIVATE)pNMHDR;

    // Get the current mouse location and convert it to client
    // coordinates.
    CPoint pos( ::GetMessagePos() ); 
    ScreenToClient(&pos);

    // Get indexes of the first and last visible items in 
    // the listview control.
    int index = m_myListCtrl.GetTopIndex();
    int last_visible_index = index + m_myListCtrl.GetCountPerPage();
    if (last_visible_index > m_myListCtrl.GetItemCount())
        last_visible_index = m_myListCtrl.GetItemCount();

    // Loop until number visible items has been reached.
    while (index <= last_visible_index)
    {
        // Get the bounding rectangle of an item. If the mouse
        // location is within the bounding rectangle of the item,
        // you know you have found the item that was being clicked.
        CRect r;
        m_myListCtrl.GetItemRect(index, &r, LVIR_BOUNDS);
        if (r.PtInRect(pia->ptAction))
        {
            UINT flag = LVIS_SELECTED | LVIS_FOCUSED;
            m_myListCtrl.SetItemState(index, flag, flag);
            break;
        }

        // Get the next item in listview control.
        index++;
    }
}
```

  
##  <a name="a-namegetitemspacinga--clistctrlgetitemspacing"></a><a name="getitemspacing"></a>CListCtrl::GetItemSpacing  
 计算当前的列表视图控件中的项之间的间距。  
  
```  
BOOL GetItemSpacing(
    BOOL fSmall,   
    int* pnHorzSpacing,   
    int* pnVertSpacing) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `fSmall`|要检索的项的间距的视图。 指定`true`为小图标视图中，或`false`图标视图。|  
|[out] `pnHorzSpacing`|包含项之间的水平间距。|  
|[out] `pnVertSpacing`|包含项之间的垂直间距。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[LVM_GETITEMSPACING](http://msdn.microsoft.com/library/windows/desktop/bb761051)消息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegetitemstatea--clistctrlgetitemstate"></a><a name="getitemstate"></a>CListCtrl::GetItemState  
 检索列表视图项的状态。  
  
```  
UINT GetItemState(
    int nItem,  
    UINT nMask) const;  
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 要检索其状态的项的索引。  
  
 `nMask`  
 指定用于返回的项的状态标志的掩码。  
  
### <a name="return-value"></a>返回值  
 指定列表的状态标志查看项。  
  
### <a name="remarks"></a>备注  
 通过指定项的状态**状态**的成员[LVITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760)结构，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。 当您指定或更改项的状态**stateMask**成员指定你想要更改的状态位。  
  
### <a name="example"></a>示例  
  请参阅示例[CListCtrl::GetTopIndex](#gettopindex)。  
  
##  <a name="a-namegetitemtexta--clistctrlgetitemtext"></a><a name="getitemtext"></a>CListCtrl::GetItemText  
 检索在列表视图项或子项的文本。  
  
```  
int GetItemText(
    int nItem,  
    int nSubItem,  
    LPTSTR lpszText,  
    int nLen) const; 
 
CString GetItemText(
    int nItem,  
    int nSubItem) const;  
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 要检索其文本的项的索引。  
  
 `nSubItem`  
 指定的文本是要检索的子项。  
  
 `lpszText`  
 要接收项文本的字符串指针。  
  
 `nLen`  
 指向缓冲区的长度`lpszText`。  
  
### <a name="return-value"></a>返回值  
 返回的版本`int`返回检索的字符串的长度。  
  
 返回的版本`CString`返回项的文本。  
  
### <a name="remarks"></a>备注  
 如果`nSubItem`为零，则此函数可检索项标签中; 如果`nSubItem`为非零值，则它将检索该子项的文本。 有关子项参数的详细信息，请参阅有关的讨论[LVITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760)结构中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegetnextitema--clistctrlgetnextitem"></a><a name="getnextitem"></a>CListCtrl::GetNextItem  
 搜索列表查看具有指定的属性并且具有与给定项的指定的关系的项。  
  
```  
int GetNextItem(
    int nItem,  
    int nFlags) const;  
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 项的索引开始进行搜索或为-1 以查找与指定的标志相匹配的第一项。 从搜索中排除指定的项本身。  
  
 `nFlags`  
 几何之间关系的请求项添加到指定的项和所请求的项的状态。 几何关系可以是下列值之一︰  
  
- `LVNI_ABOVE`为上面指定的项的项的搜索。  
  
- `LVNI_ALL`搜索按索引 （默认值） 的后续项。  
  
- `LVNI_BELOW`低于指定的项的项的搜索。  
  
- `LVNI_TOLEFT`搜索指定项的左侧项。  
  
- `LVNI_TORIGHT`搜索指定项的右侧项。  
  
 该状态可以是零，或者它可以是一个或多个值︰  
  
- `LVNI_DROPHILITED`项具有`LVIS_DROPHILITED`状态标志设置。  
  
- `LVNI_FOCUSED`项具有`LVIS_FOCUSED`状态标志设置。  
  
- `LVNI_SELECTED`项具有`LVIS_SELECTED`状态标志设置。  
  
 如果某个项不包含所有指定的状态标志设置，继续搜索下一个项目。  
  
### <a name="return-value"></a>返回值  
 如果成功，下一项或否则为-1 的索引。  
  
##  <a name="a-namegetnextitemindexa--clistctrlgetnextitemindex"></a><a name="getnextitemindex"></a>CListCtrl::GetNextItemIndex  
 检索具有指定的一组属性的当前列表视图控件中的项的索引。  
  
```  
BOOL GetNextItemIndex(
    PLVITEMINDEX pItemIndex,   
    int nFlags) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in, out] `pItemIndex`|指向[LVITEMINDEX](http://msdn.microsoft.com/library/windows/desktop/bb774762)结构，它描述的项开始执行搜索，则为-1 以查找匹配中的标记的第一项`nFlags`参数。<br /><br /> 如果此方法成功，`LVITEMINDEX`结构描述的搜索操作找到的项。|  
|[in] `nFlags`|指定要执行搜索的方式的标志的按位组合 (OR)。<br /><br /> 搜索可以依赖于索引、 状态或目标项的外观，或者由指定的目标项的相对于项的物理位置`pItemIndex`参数。 有关详细信息，请参阅`flags`中的参数[LVM_GETNEXTITEMINDEX](http://msdn.microsoft.com/library/windows/desktop/bb761059)消息。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 调用方负责分配和设置的成员`LVITEMINDEX`指向结构`pItemIndex`参数。  
  
 此方法可发送[LVM_GETNEXTITEMINDEX](http://msdn.microsoft.com/library/windows/desktop/bb761059)邮件中，Windows SDK 中所述。  
  
##  <a name="a-namegetnextselecteditema--clistctrlgetnextselecteditem"></a><a name="getnextselecteditem"></a>CListCtrl::GetNextSelectedItem  
 获取由标识的列表项的索引`pos`，然后设置*pos*到**位置**值。  
  
```  
int GetNextSelectedItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 对引用**位置**的以前调用返回值`GetNextSelectedItem`或`GetFirstSelectedItemPosition`。 通过此调用至下一个位置更新的值。  
  
### <a name="return-value"></a>返回值  
 由标识的列表项的索引`pos`。  
  
### <a name="remarks"></a>备注  
 您可以使用`GetNextSelectedItem`在向前迭代循环中，如果您建立的初始位置，通过调用`GetFirstSelectedItemPosition`。  
  
 您必须确保您**位置**值是否有效。 如果该值无效，Microsoft 基础类库的调试版本断言。  
  
### <a name="example"></a>示例  
 下面的代码示例演示此函数的用法。    
  
```cpp  
        POSITION pos = m_myListCtrl.GetFirstSelectedItemPosition();
        if (pos == NULL)
        {
            TRACE(_T("No items were selected!\n"));
        }
        else
        {
            while (pos)
            {
                int nItem = m_myListCtrl.GetNextSelectedItem(pos);
                TRACE(_T("Item %d was selected!\n"), nItem);
                // you could do your own processing on nItem here
            }
        }
```

  
##  <a name="a-namegetnumberofworkareasa--clistctrlgetnumberofworkareas"></a><a name="getnumberofworkareas"></a>CListCtrl::GetNumberOfWorkAreas  
 检索列表视图控件的工作区域的当前数目。  
  
```  
UINT GetNumberOfWorkAreas() const;  
```  
  
### <a name="return-value"></a>返回值  
 不使用这一次。  
  
### <a name="remarks"></a>备注  
 此成员函数实现 Win32 宏的行为[ListView_GetNumberOfWorkAreas](http://msdn.microsoft.com/library/windows/desktop/bb774988)，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例    
  
```cpp  
        UINT i, uCount = m_myListCtrl.GetNumberOfWorkAreas();
        LPRECT lpRects = (LPRECT) malloc(uCount*sizeof(RECT));

        if (lpRects != NULL)
        {
            // Dump all of the work area dimensions.
            m_myListCtrl.GetWorkAreas(uCount, lpRects);

            for (i=0; i < uCount; i++)
            {
                TRACE(_T("Work area %d; left = %d, top = %d, right = %d, ")
                    _T("bottom = %d\r\n"),
                    i, lpRects[i].left, lpRects[i].top, lpRects[i].right, 
                    lpRects[i].bottom);
            }

            free(lpRects);
        }
        else
        {
            TRACE(_T("Couldn't allocate enough memory!"));   
        }

```

  
##  <a name="a-namegetoutlinecolora--clistctrlgetoutlinecolor"></a><a name="getoutlinecolor"></a>CListCtrl::GetOutlineColor  
 检索列表视图控件的边框的颜色。  
  
```  
COLORREF GetOutlineColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)结构，它包含的轮廓颜色。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_GETOUTLINECOLOR](http://msdn.microsoft.com/library/windows/desktop/bb761065)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegetorigina--clistctrlgetorigin"></a><a name="getorigin"></a>CListCtrl::GetOrigin  
 检索列表视图控件的当前视图原点。  
  
```  
BOOL GetOrigin(LPPOINT lpPoint) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpPoint`  
 地址的指针[点](http://msdn.microsoft.com/library/windows/desktop/dd162805)结构，它接收视图原点。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。 但是，如果控件位于报表视图中，则返回值始终为零。  
  
##  <a name="a-namegetselectedcolumna--clistctrlgetselectedcolumn"></a><a name="getselectedcolumn"></a>CListCtrl::GetSelectedColumn  
 检索列表控件中当前选定的列的索引。  
  
```  
UINT GetSelectedColumn() const;  
```  
  
### <a name="return-value"></a>返回值  
 所选列的索引。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_GETSELECTEDCOLUMN](http://msdn.microsoft.com/library/windows/desktop/bb761067)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegetselectedcounta--clistctrlgetselectedcount"></a><a name="getselectedcount"></a>CListCtrl::GetSelectedCount  
 检索列表视图控件中选定项的数目。  
  
```  
UINT GetSelectedCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 在列表视图控件中选定项的数目。  
  
### <a name="example"></a>示例    
  
```cpp  
        UINT i, uSelectedCount = m_myListCtrl.GetSelectedCount();
        int  nItem = -1;

        // Update all of the selected items.
        if (uSelectedCount > 0)
        {
            for (i=0; i < uSelectedCount; i++)
            {
                nItem = m_myListCtrl.GetNextItem(nItem, LVNI_SELECTED);
                ASSERT(nItem != -1);
                m_myListCtrl.Update(nItem); 
            }
        }
```

  
##  <a name="a-namegetselectionmarka--clistctrlgetselectionmark"></a><a name="getselectionmark"></a>CListCtrl::GetSelectionMark  
 检索列表视图控件的选择标记。  
  
```  
int GetSelectionMark();
```  
  
### <a name="return-value"></a>返回值  
 从零开始的选择标记中或如果没有选择标记为-1。  
  
### <a name="remarks"></a>备注  
 此成员函数实现 Win32 宏的行为[ListView_GetSelectionMark](http://msdn.microsoft.com/library/windows/desktop/bb774998)，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  

```cpp  
    // Set the selection mark to the first item only if no other item is 
    // selected.
    if (m_myListCtrl.GetSelectionMark() == -1)
        m_myListCtrl.SetSelectionMark(0);
```

  
##  <a name="a-namegetstringwidtha--clistctrlgetstringwidth"></a><a name="getstringwidth"></a>CListCtrl::GetStringWidth  
 确定显示给定字符串的所有所需的最小列宽度。  
  
```  
int GetStringWidth(LPCTSTR lpsz) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpsz`  
 以 null 结尾的字符串，其宽度是确定的地址。  
  
### <a name="return-value"></a>返回值  
 宽度 （像素） 指向字符串`lpsz`。  
  
### <a name="remarks"></a>备注  
 返回的宽度会考虑控件的当前字体和列边距，而非一个小图标的宽度。  
  
### <a name="example"></a>示例  

```cpp  
        CString strColumn;
        int nWidth;

        // Insert six columns in the list view control. Make the width of
        // the column be the width of the column header plus 50%.
        for (int i = 0; i < 6; i++)
        {
            strColumn.Format(_T("column %d"), i);
            nWidth = 3*m_myListCtrl.GetStringWidth(strColumn)/2;
            m_myListCtrl.InsertColumn(i, strColumn, LVCFMT_LEFT, nWidth);
        }
```

  
##  <a name="a-namegetsubitemrecta--clistctrlgetsubitemrect"></a><a name="getsubitemrect"></a>CListCtrl::GetSubItemRect  
 检索列表视图控件中的项的边框。  
  
```  
BOOL GetSubItemRect(
    int iItem,  
    int iSubItem,  
    int nArea,  
    CRect& ref);
```  
  
### <a name="parameters"></a>参数  
 *iItem*  
 子项的父项的索引。  
  
 *iSubItem*  
 子项&1; 开始的索引。  
  
 *nArea*  
 确定的边框 （列表视图子项） 的部分要从中检索。 通过将按位 OR 运算符应用于一个或多个下列值指定的绑定矩形的部分 （图标、 标签或两者）︰  
  
- `LVIR_BOUNDS`返回整个项，包括图标和标签的边框。  
  
- `LVIR_ICON`返回的图标或小图标的边框。  
  
- `LVIR_LABEL`返回整个项，包括图标和标签的边框。 这等同于`LVIR_BOUNDS`。  
  
 `ref`  
 引用[CRect](../../atl-mfc-shared/reference/crect-class.md)包含子项的坐标的对象的边框。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 此成员函数实现 Win32 宏的行为[ListView_GetSubItemRect](http://msdn.microsoft.com/library/windows/desktop/bb775004)，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegettextbkcolora--clistctrlgettextbkcolor"></a><a name="gettextbkcolor"></a>CListCtrl::GetTextBkColor  
 检索列表视图控件的文本的背景颜色。  
  
```  
COLORREF GetTextBkColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 用来指定 RGB 颜色的 32 位值。  
  
### <a name="example"></a>示例  
  请参阅示例[CListCtrl::SetTextBkColor](#settextbkcolor)。  
  
##  <a name="a-namegettextcolora--clistctrlgettextcolor"></a><a name="gettextcolor"></a>CListCtrl::GetTextColor  
 检索列表视图控件的文本颜色。  
  
```  
COLORREF GetTextColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 用来指定 RGB 颜色的 32 位值。  
  
### <a name="example"></a>示例  
  请参阅示例[CListCtrl::SetTextColor](#settextcolor)。  
  
##  <a name="a-namegettileinfoa--clistctrlgettileinfo"></a><a name="gettileinfo"></a>CListCtrl::GetTileInfo  
 检索有关列表视图控件中的图块的信息。  
  
```  
BOOL GetTileInfo(PLVTILEINFO pti) const;  
```  
  
### <a name="parameters"></a>参数  
 *pti*  
 一个指向[LVTILEINFO](http://msdn.microsoft.com/library/windows/desktop/bb774766)接收磁贴信息的结构。  
  
### <a name="return-value"></a>返回值  
 不使用返回的值。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_GETTILEINFO](http://msdn.microsoft.com/library/windows/desktop/bb761081)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegettileviewinfoa--clistctrlgettileviewinfo"></a><a name="gettileviewinfo"></a>CListCtrl::GetTileViewInfo  
 检索有关列表视图控件平铺视图中的信息。  
  
```  
BOOL GetTileViewInfo(PLVTILEVIEWINFO ptvi) const;  
```  
  
### <a name="parameters"></a>参数  
 `ptvi`  
 一个指向[LVTILEVIEWINFO](http://msdn.microsoft.com/library/windows/desktop/bb774768)结构，它接收检索到的信息。  
  
### <a name="return-value"></a>返回值  
 不使用返回的值。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_GETTILEVIEWINFO](http://msdn.microsoft.com/library/windows/desktop/bb761083)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegettooltipsa--clistctrlgettooltips"></a><a name="gettooltips"></a>CListCtrl::GetToolTips  
 检索列表视图控件用于显示工具提示的工具提示控件。  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向[CToolTipCtrl](ctooltipctrl-class.md)要使用列表控件对象。 如果[创建](#create)成员函数使用的样式**LVS_NOTOOLTIPS**，使用任何工具提示，并**NULL**返回。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[LVM_GETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb761085)，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。 MFC 实现`GetToolTips`返回`CToolTipCtrl`对象，它使用通过列表控件，而不是工具提示控件的句柄。  
  
### <a name="example"></a>示例  

```cpp  
        CToolTipCtrl* pTip = m_myListCtrl.GetToolTips();
        if (NULL != pTip)
        {
            pTip->UpdateTipText(_T("I'm a list view!"), &m_myListCtrl,
                IDD_MYLISTCTRL);
        }
```

  
##  <a name="a-namegettopindexa--clistctrlgettopindex"></a><a name="gettopindex"></a>CListCtrl::GetTopIndex  
 在列表视图或报表视图中检索的最顶层的可见项的索引。  
  
```  
int GetTopIndex() const;  
```  
  
### <a name="return-value"></a>返回值  
 最顶层的可见项的索引。  
  
### <a name="example"></a>示例  

 
```cpp  
        // Make sure the focus is set to the list view control.
        m_myListCtrl.SetFocus();

        // Select all of the items that are completely visible.
        int n = m_myListCtrl.GetTopIndex();
        int nLast = n + m_myListCtrl.GetCountPerPage();

        for (; n < nLast; n++)
        {
            m_myListCtrl.SetItemState(n, LVIS_SELECTED, LVIS_SELECTED);
            ASSERT(m_myListCtrl.GetItemState(n, LVIS_SELECTED) == LVIS_SELECTED); 
        }
```

  
##  <a name="a-namegetviewa--clistctrlgetview"></a><a name="getview"></a>CListCtrl::GetView  
 获取列表视图控件的视图。  
  
```  
DWORD GetView() const;  
```  
  
### <a name="return-value"></a>返回值  
 列表视图控件的当前视图。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_GETVIEW](http://msdn.microsoft.com/library/windows/desktop/bb761091)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegetviewrecta--clistctrlgetviewrect"></a><a name="getviewrect"></a>CListCtrl::GetViewRect  
 检索列表视图控件中的所有项的边框。  
  
```  
BOOL GetViewRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 地址的指针[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 列表视图中必须是在图标视图或小图标视图中。  
  
##  <a name="a-namegetworkareasa--clistctrlgetworkareas"></a><a name="getworkareas"></a>CListCtrl::GetWorkAreas  
 检索列表视图控件的当前工作区。  
  
```  
void GetWorkAreas(
    int nWorkAreas,  
    LPRECT prc) const;  
```  
  
### <a name="parameters"></a>参数  
 `nWorkAreas`  
 数`RECT`结构中包含*中国*数组。  
  
 `prc`  
 指向数组的指针`RECT`结构 (或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象) 中接收列表视图控件的工作区域。 在这些结构中的值是在工作区坐标。  
  
### <a name="remarks"></a>备注  
 此成员函数实现 Win32 宏的行为[ListView_GetWorkAreas](http://msdn.microsoft.com/library/windows/desktop/bb775024)，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CListCtrl::GetNumberOfWorkAreas](#getnumberofworkareas)。  
  
##  <a name="a-namehasgroupa--clistctrlhasgroup"></a><a name="hasgroup"></a>CListCtrl::HasGroup  
 确定列表视图控件是否具有指定的组。  
  
```  
BOOL HasGroup(int iGroupId) const;  
```  
  
### <a name="parameters"></a>参数  
 `iGroupId`  
 正在请求的组的标识符。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**成功时， **FALSE**失败。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_HASGROUP](http://msdn.microsoft.com/library/windows/desktop/bb761097)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namehittesta--clistctrlhittest"></a><a name="hittest"></a>CListCtrl::HitTest  
 确定哪些列表视图项目时，如果有的话的指定位置。  
  
```  
int HitTest(LVHITTESTINFO* pHitTestInfo) const;  
  
int HitTest(
    CPoint pt,  
    UINT* pFlags = NULL) const;  
```  
  
### <a name="parameters"></a>参数  
 `pHitTestInfo`  
 地址的指针**LVHITTESTINFO**结构，其中包含要进行命中测试和程序的位置接收的命中测试的结果有关的信息。  
  
 `pt`  
 要测试的点。  
  
 `pFlags`  
 为接收有关测试结果的整数的指针。 请查看解释**标志**的成员[LVHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb774754)结构中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 指定的位置处的项的索引`pHitTestInfo`(如果有） 或否则为-1。  
  
### <a name="remarks"></a>备注  
 您可以使用`LVHT_ABOVE`， `LVHT_BELOW`， `LVHT_TOLEFT`，和`LVHT_TORIGHT`的结构值**标志**成员以确定是否要向下滚动列表视图控件的内容。 两个这些标志可以结合使用，例如，如果的位置的上方和左边的工作区。  
  
 你可以测试**LVHT_ONITEM**该结构的值**标志**成员以确定给定的位置是否在列表视图项。 此值按位或运算位于`LVHT_ONITEMICON`， `LVHT_ONITEMLABEL`，和`LVHT_ONITEMSTATEICON`的结构值**标志**成员。  
  
### <a name="example"></a>示例  

```cpp  
void CListCtrlDlg::OnRClick(NMHDR* pNMHDR, LRESULT* pResult)
{
    LPNMITEMACTIVATE pia = (LPNMITEMACTIVATE)pNMHDR;
    CPoint point(pia->ptAction);

    // Select the item the user clicked on.
    UINT uFlags;
    int nItem = m_myListCtrl.HitTest(point, &uFlags);

    if (uFlags & LVHT_ONITEMLABEL)
    {
        m_myListCtrl.SetItem(nItem, 0, LVIF_STATE, NULL, 0, LVIS_SELECTED, 
            LVIS_SELECTED, 0);
    }

    *pResult = 0;
}
```

  
##  <a name="a-nameinsertcolumna--clistctrlinsertcolumn"></a><a name="insertcolumn"></a>CListCtrl::InsertColumn  
 在列表视图控件中插入新列。  
  
```  
int InsertColumn(
    int nCol,  
    const LVCOLUMN* pColumn);

 
int InsertColumn(
    int nCol,  
    LPCTSTR lpszColumnHeading,  
    int nFormat = LVCFMT_LEFT,  
    int nWidth = -1,  
    int nSubItem = -1);
```  
  
### <a name="parameters"></a>参数  
 `nCol`  
 新的列的索引。  
  
 `pColumn`  
 地址的指针**LVCOLUMN**结构，其中包含新列的属性。  
  
 *lpszColumnHeading*  
 一个包含列标题的字符串的地址。  
  
 `nFormat`  
 整数，指定列的对齐方式。 它可以是下列值之一︰ **LVCFMT_LEFT**， **LVCFMT_RIGHT**，或**LVCFMT_CENTER**。  
  
 `nWidth`  
 列的宽度，以像素为单位。 如果此参数为-1，未设置列的宽度。  
  
 `nSubItem`  
 与该列关联的子项的索引。 如果此参数为-1，没有子项是与列相关联。  
  
### <a name="return-value"></a>返回值  
 如果成功，新的列或否则为-1 的索引。  
  
### <a name="remarks"></a>备注  
 在列表视图控件中最左侧的列必须是左对齐。  
  
 [LVCOLUMN](http://msdn.microsoft.com/library/windows/desktop/bb774743)结构包含在报表视图中的列的属性。 它还用于接收有关列的信息。 中介绍了此结构[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-nameinsertgroupa--clistctrlinsertgroup"></a><a name="insertgroup"></a>CListCtrl::InsertGroup  
 将一组插入到列表视图控件。  
  
```  
LRESULT InsertGroup(
    int index,  
    PLVGROUP pgrp);
```  
  
### <a name="parameters"></a>参数  
 *索引*  
 在组很要插入的项的索引。  
  
 `pgrp`  
 一个指向[LVGROUP](http://msdn.microsoft.com/library/windows/desktop/bb774769)结构，它包含要添加的组。  
  
### <a name="return-value"></a>返回值  
 如果操作失败，则返回的项的组已添加到，则为-1 的索引。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_INSERTGROUP](http://msdn.microsoft.com/library/windows/desktop/bb761103)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-nameinsertgroupsorteda--clistctrlinsertgroupsorted"></a><a name="insertgroupsorted"></a>CListCtrl::InsertGroupSorted  
 将指定的组插入到组的排序列表。  
  
```  
LRESULT InsertGroupSorted(PLVINSERTGROUPSORTED pStructInsert);
```  
  
### <a name="parameters"></a>参数  
 *pStructInsert*  
 一个指向[LVINSERTGROUPSORTED](http://msdn.microsoft.com/library/windows/desktop/bb774756)结构，其中包含要插入的组。  
  
### <a name="return-value"></a>返回值  
 不使用返回的值。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_INSERTGROUPSORTED](http://msdn.microsoft.com/library/windows/desktop/bb761105)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-nameinsertitema--clistctrlinsertitem"></a><a name="insertitem"></a>CListCtrl::InsertItem  
 将项插入到列表视图控件。  
  
```  
int InsertItem(const LVITEM* pItem);

 
int InsertItem(
    int nItem,  
    LPCTSTR lpszItem);

 
int InsertItem(
    int nItem,  
    LPCTSTR lpszItem,  
    int nImage);

 
int InsertItem(
    UINT nMask,  
    int nItem,  
    LPCTSTR lpszItem,  
    UINT nState,  
    UINT nStateMask,  
    int nImage,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>参数  
 `pItem`  
 指向[LVITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760)结构，它指定项的属性，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
 `nItem`  
 要插入项的索引。  
  
 `lpszItem`  
 包含项的标签的字符串的地址或`LPSTR_TEXTCALLBACK`如果该项是回调项。 回调项的信息，请参阅[clistctrl:: Getcallbackmask](#getcallbackmask)。  
  
 `nImage`  
 项的图像的索引或`I_IMAGECALLBACK`如果该项是回调项。 回调项的信息，请参阅[clistctrl:: Getcallbackmask](#getcallbackmask)。  
  
 `nMask`  
 `nMask`参数指定哪一项作为参数传递的属性是否有效。 它可以是一个或多个掩码值中所述[LVITEM 结构](http://msdn.microsoft.com/library/windows/desktop/bb774760)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。 可以使用按位 OR 运算符组合的有效值。  
  
 `nState`  
 指示项的状态、 状态图像和覆盖图像。 请参阅[!INCLUDE[winSDK](./includes/winsdk_md.md)]主题[LVITEM 结构](http://msdn.microsoft.com/library/windows/desktop/bb774760)有关详细信息和[列表视图项状态](http://msdn.microsoft.com/library/windows/desktop/bb774733)有关的有效标志列表。  
  
 `nStateMask`  
 指示将检索或修改状态成员的哪些位。 请参阅[LVITEM 结构](http://msdn.microsoft.com/library/windows/desktop/bb774760)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]有关详细信息。  
  
 `lParam`  
 与项目关联一个 32 位应用程序特定值。 如果指定此参数，则必须设置`nMask`属性`LVIF_PARAM`。  
  
### <a name="return-value"></a>返回值  
 如果成功，新的项或否则为-1 的索引。  
  
### <a name="remarks"></a>备注  
 调用此方法可能会导致**LVM_INSERTITEM**消息发送到您的控件窗口。 该控件相关联的消息处理程序可能无法设置项文本在某些情况下的 (例如，如使用的窗口样式**LVS_OWNERDRAW**)。 有关这些条件的详细信息，请参阅[LVM_INSERTITEM](http://msdn.microsoft.com/library/windows/desktop/bb761107)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  

```cpp  
        CString strText;
        int nColumnCount = m_myListCtrl.GetHeaderCtrl()->GetItemCount();

        // Insert 10 items in the list view control.
        for (int i = 0; i < 10; i++)
        {
            strText.Format(TEXT("item %d"), i);

            // Insert the item, select every other item.
            m_myListCtrl.InsertItem(LVIF_TEXT | LVIF_STATE, i, strText, 
                (i % 2) == 0 ? LVIS_SELECTED : 0, LVIS_SELECTED, 0, 0);

            // Initialize the text of the subitems.
            for (int j = 1; j < nColumnCount; j++)
            {
                strText.Format(TEXT("sub-item %d %d"), i, j);
                m_myListCtrl.SetItemText(i, j, strText);
            }
        }
```

  
##  <a name="a-nameinsertmarkhittesta--clistctrlinsertmarkhittest"></a><a name="insertmarkhittest"></a>CListCtrl::InsertMarkHitTest  
 检索与指定的点最接近的插入点。  
  
```  
int InsertMarkHitTest(
    LPPOINT pPoint,  
    LPLVINSERTMARK lvim) const;  
```  
  
### <a name="parameters"></a>参数  
 `pPoint`  
 一个指向[点](http://msdn.microsoft.com/library/windows/desktop/dd162805)结构，其中包含命中的测试坐标中，列表控件的工作区相对。  
  
 `lvim`  
 一个指向[LVINSERTMARK](http://msdn.microsoft.com/library/windows/desktop/bb774758)结构，它指定由点参数定义的坐标最接近的插入点。  
  
### <a name="return-value"></a>返回值  
 插入点最接近指定点。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_INSERTMARKHITTEST](http://msdn.microsoft.com/library/windows/desktop/bb761131)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-nameisgroupviewenableda--clistctrlisgroupviewenabled"></a><a name="isgroupviewenabled"></a>CListCtrl::IsGroupViewEnabled  
 确定是否为列表视图控件启用的组视图。  
  
```  
BOOL IsGroupViewEnabled() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**如果启用了组视图，或**FALSE**否则为。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_ISGROUPVIEWENABLED](http://msdn.microsoft.com/library/windows/desktop/bb761133)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-nameisitemvisiblea--clistctrlisitemvisible"></a><a name="isitemvisible"></a>CListCtrl::IsItemVisible  
 指示当前的列表视图控件中的指定的项是否可见。  
  
```  
BOOL IsItemVisible(int index) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `index`|当前列表视图控件中的项的从零开始索引。|  
  
### <a name="return-value"></a>返回值  
 `true`如果指定的项是可见的; 否则为`false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[LVM_ISITEMVISIBLE](http://msdn.microsoft.com/library/windows/desktop/bb761135)消息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namemapidtoindexa--clistctrlmapidtoindex"></a><a name="mapidtoindex"></a>CListCtrl::MapIDToIndex  
 将当前的列表视图控件中的项的唯一 ID 映射到索引。  
  
```  
UINT MapIDToIndex(UINT id) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `id`|项的唯一 ID。|  
  
### <a name="return-value"></a>返回值  
 当前索引，以获取指定的 id。  
  
### <a name="remarks"></a>备注  
 列表视图控件内部跟踪由索引的项。 因为索引可能会更改控件的生存期内，这可能造成问题。 List view 控件可以标记 id 的项创建项时创建，你可以使用此 ID 以在列表视图控件的生存期内保证唯一性。  
  
 请注意，在多线程环境中索引保证仅在承载该列表视图控件，不在后台线程上的线程上。  
  
 此方法可发送[LVM_MAPIDTOINDEX](http://msdn.microsoft.com/library/windows/desktop/bb761137)消息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namemapindextoida--clistctrlmapindextoid"></a><a name="mapindextoid"></a>CListCtrl::MapIndexToID  
 将当前的列表视图控件中的项的索引映射到唯一的 id。  
  
```  
UINT MapIndexToID(UINT index) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `index`|项的从零开始的索引。|  
  
### <a name="return-value"></a>返回值  
 指定的项的的唯一 ID。  
  
### <a name="remarks"></a>备注  
 列表视图控件内部跟踪由索引的项。 因为索引可能会更改控件的生存期内，这可能造成问题。 当创建项时，list view 控件可以标记具有 ID 的项。 此 ID 可用于列表视图控件的生存期内访问特定项。  
  
 请注意，在多线程环境中索引保证仅在承载该列表视图控件，不在后台线程上的线程上。  
  
 此方法可发送[LVM_MAPINDEXTOID](http://msdn.microsoft.com/library/windows/desktop/bb761139)消息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义一个变量， `m_listCtrl`，也就是说，用来访问当前的 list view 控件。 此变量将在下一个示例中使用。    
  
```cpp  
public:
    // Variable used to access the list control.
    CListCtrl m_listCtrl; 
```

  
### <a name="example"></a>示例  
 下面的代码示例演示`MapIndexToID`方法。 在此代码示例早期部分中，我们创建了一个显示在报表视图中的标题为"ClientID"和"等级"的两个列的列表视图控件。 下面的示例将每个列表视图项的索引映射到一个标识的编号，然后检索每个标识号的索引。 最后，示例报告是否检索到原始的索引。    
  
```cpp  
    // MapIndexToID
    int iCount = m_listCtrl.GetItemCount();
    UINT nId = 0;
    UINT nIndex = 0;
    for (int iIndexOriginal = 0; iIndexOriginal < iCount; iIndexOriginal++)
    {
        // Map index to ID.
        nId = m_listCtrl.MapIndexToID((UINT)iIndexOriginal);

        // Map ID to index.
        nIndex = m_listCtrl.MapIDToIndex(nId);

        if (nIndex != (UINT)(iIndexOriginal))
        {
            CString str;
            str.Format(_T("Mapped index (%d) is not equal to original index (%d)"),
                nIndex, (UINT)(iIndexOriginal));
            AfxMessageBox(str);
            return;
        }
    }
    AfxMessageBox(_T("The mapped indexes and original indexes are equal."), 
        MB_ICONINFORMATION);
```

  
##  <a name="a-namemovegroupa--clistctrlmovegroup"></a><a name="movegroup"></a>CListCtrl::MoveGroup  
 将移动指定的组指定零开始的列表视图控件索引。  
  
```  
LRESULT MoveGroup(
    int iGroupId,  
    int toIndex);
```  
  
### <a name="parameters"></a>参数  
 `iGroupId`  
 要移动的组的标识符。  
  
 `toIndex`  
 从零开始的索引，组都是要移动。  
  
### <a name="return-value"></a>返回值  
 不使用返回的值。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_MOVEGROUP](http://msdn.microsoft.com/library/windows/desktop/bb761141)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namemoveitemtogroupa--clistctrlmoveitemtogroup"></a><a name="moveitemtogroup"></a>CListCtrl::MoveItemToGroup  
 将指定的项移动到指定的组。  
  
```  
void MoveItemToGroup(
    int idItemFrom,  
    int idGroupTo);
```  
  
### <a name="parameters"></a>参数  
 [in] `idItemFrom`  
 要移动的项的索引。  
  
 [in] `idGroupTo`  
 该项目将移到组的标识符。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  当前未实现此方法。  
  
 此方法模拟的功能[LVM_MOVEITEMTOGROUP](http://msdn.microsoft.com/library/windows/desktop/bb761143)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-nameredrawitemsa--clistctrlredrawitems"></a><a name="redrawitems"></a>CListCtrl::RedrawItems  
 强制重新绘制的项的范围的列表视图控件。  
  
```  
BOOL RedrawItems(
    int nFirst,  
    int nLast);
```  
  
### <a name="parameters"></a>参数  
 `nFirst`  
 要进行重新绘制的第一项的索引。  
  
 `nLast`  
 要进行重新绘制的最后一项的索引。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 指定的项不实际重新绘制列表视图窗口接收之前`WM_PAINT`消息。 若要立即重绘，调用 Windows [UpdateWindow](http://msdn.microsoft.com/library/windows/desktop/dd145167)函数之后，使用此函数。  
  
##  <a name="a-nameremoveallgroupsa--clistctrlremoveallgroups"></a><a name="removeallgroups"></a>CListCtrl::RemoveAllGroups  
 从列表视图控件中移除所有组。  
  
```  
void RemoveAllGroups();
```  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_REMOVEALLGROUPS](http://msdn.microsoft.com/library/windows/desktop/bb761147)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-nameremovegroupa--clistctrlremovegroup"></a><a name="removegroup"></a>CListCtrl::RemoveGroup  
 从列表视图控件中删除指定的组。  
  
```  
LRESULT RemoveGroup(int iGroupId);
```  
  
### <a name="parameters"></a>参数  
 `iGroupId`  
 要删除的组的标识符。  
  
### <a name="return-value"></a>返回值  
 否则，返回组如果成功，则为-1 的索引。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_REMOVEGROUP](http://msdn.microsoft.com/library/windows/desktop/bb761149)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namescrolla--clistctrlscroll"></a><a name="scroll"></a>CListCtrl::Scroll  
 将列表视图控件的内容滚动。  
  
```  
BOOL Scroll(CSize size);
```  
  
### <a name="parameters"></a>参数  
 `size`  
 一个`CSize`对象，它指定水平和垂直滚动，以像素为单位的数量。 **Y**的成员`size`除以高度 （像素） 列表视图控件的行，以及所产生的行数的滚动控件。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
##  <a name="a-namesetbkcolora--clistctrlsetbkcolor"></a><a name="setbkcolor"></a>CListCtrl::SetBkColor  
 设置在列表视图控件的背景色。  
  
```  
BOOL SetBkColor(COLORREF cr);
```  
  
### <a name="parameters"></a>参数  
 `cr`  
 背景色，若要设置，或`CLR_NONE`没有背景色的值。 使用背景颜色的列表视图控件重绘自身明显快于而无需背景色。 有关信息，请参阅[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="example"></a>示例  

 
```cpp  
        // Use the 3D button face color for the background.
        COLORREF crBkColor = ::GetSysColor(COLOR_3DFACE);
        m_myListCtrl.SetBkColor(crBkColor);
        ASSERT(m_myListCtrl.GetBkColor() == crBkColor);
```

  
##  <a name="a-namesetbkimagea--clistctrlsetbkimage"></a><a name="setbkimage"></a>CListCtrl::SetBkImage  
 设置的列表视图控件的背景图像。  
  
```  
BOOL SetBkImage(LVBKIMAGE* plvbkImage);
 
BOOL SetBkImage(
    HBITMAP hbm,  
    BOOL fTile = TRUE,  
    int xOffsetPercent = 0,  
    int yOffsetPercent = 0);
 
BOOL SetBkImage(
    LPTSTR pszUrl,  
    BOOL fTile = TRUE,  
    int xOffsetPercent = 0,  
    int yOffsetPercent = 0);
```  
  
### <a name="parameters"></a>参数  
 `plvbkImage`  
 地址的指针**LVBKIMAGE**包含新的背景图像信息的结构。  
  
 `hbm`  
 位图的句柄。  
  
 `pszUrl`  
 一个**NULL**-结尾的字符串，其中包含的背景图像的 URL。  
  
 *fTile*  
 如果该图像平铺的列表视图控件，则背景中，非零值否则为 0。  
  
 *xOffsetPercent*  
 偏移量，以像素为单位的图像的左边缘，从列表视图控件的原点。  
  
 *yOffsetPercent*  
 偏移量，单位是像素的图像的上边缘，从列表视图控件的原点。  
  
### <a name="return-value"></a>返回值  
 则返回非零，如果成功，否则为零。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  因为`CListCtrl::SetBkImage`利用 OLE 和 COM 功能，必须在使用之前初始化 OLE 库`SetBkImage`。 最好在初始化应用程序时初始化 COM 库和取消初始化库，应用程序终止时。 这将自动完成在 MFC 中进行的应用程序使用的 ActiveX 技术、 OLE 自动化、 OLE 链接/嵌入或 ODBC/DAO 操作。  
  
### <a name="example"></a>示例  
  请参阅示例[CListCtrl::GetBkImage](#getbkimage)。  
  
##  <a name="a-namesetcallbackmaska--clistctrlsetcallbackmask"></a><a name="setcallbackmask"></a>Clistctrl:: Setcallbackmask  
 设置的列表视图控件的回调掩码。  
  
```  
BOOL SetCallbackMask(UINT nMask);
```  
  
### <a name="parameters"></a>参数  
 `nMask`  
 回调掩码的新值。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="example"></a>示例  

 
```cpp  
    // Set the callback mask so that only the selected and focused states
    // are stored for each item.
    m_myListCtrl.SetCallbackMask(LVIS_SELECTED|LVIS_FOCUSED);
    ASSERT(m_myListCtrl.GetCallbackMask() == 
        (LVIS_SELECTED|LVIS_FOCUSED));
```


##  <a name="a-namesetchecka--clistctrlsetcheck"></a><a name="setcheck"></a>CListCtrl::SetCheck  
 确定列表控件项的状态图像是否可见。  
  
```  
BOOL SetCheck(
    int nItem,  
    BOOL fCheck = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 列表控件项的从零开始的索引。  
  
 `fCheck`  
 指定是否应导致项的状态图像可见。 默认情况下， *fCheck*是**TRUE**和状态图像是否可见。 如果`fCheck`是**FALSE**，它是不可见。  
  
### <a name="return-value"></a>返回值  
 非零，如果选中该项，否则为 0。  
  
### <a name="example"></a>示例  

 
```cpp  
        int nCount = m_myListCtrl.GetItemCount();
        BOOL fCheck = FALSE;

        // Set the check state of every other item to TRUE and 
        // all others to FALSE.
        for (int i = 0; i < nCount; i++)
        {
            m_myListCtrl.SetCheck(i, fCheck);
            ASSERT((m_myListCtrl.GetCheck(i) && fCheck) || 
                (!m_myListCtrl.GetCheck(i) && !fCheck));
            fCheck = !fCheck;
        }
```

  
##  <a name="a-namesetcolumna--clistctrlsetcolumn"></a><a name="setcolumn"></a>CListCtrl::SetColumn  
 设置列表视图列的属性。  
  
```  
BOOL SetColumn(
    int nCol,  
    const LVCOLUMN* pColumn);
```  
  
### <a name="parameters"></a>参数  
 `nCol`  
 要设置其属性的列的索引。  
  
 `pColumn`  
 地址的指针[LVCOLUMN](http://msdn.microsoft.com/library/windows/desktop/bb774743)结构，其中包含新的列属性，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。 该结构的**掩码**成员指定哪一列属性设置。 如果**掩码**成员指定`LVCF_TEXT`值，该结构的**pszText**成员是以 null 结尾的字符串和结构的地址**cchTextMax**成员将被忽略。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="example"></a>示例  
  请参阅示例[CListCtrl::GetColumn](#getcolumn)。  
  
##  <a name="a-namesetcolumnorderarraya--clistctrlsetcolumnorderarray"></a><a name="setcolumnorderarray"></a>CListCtrl::SetColumnOrderArray  
 设置的列表视图控件的列顺序 （从左到右）。  
  
```  
BOOL SetColumnOrderArray(
    int iCount,  
    LPINT piArray);
```  
  
### <a name="parameters"></a>参数  
 `piArray`  
 指向包含在列表视图控件 （从左到右） 中的列的索引值的缓冲区的指针。 缓冲区必须足够大以包含在列表视图控件中的列的总数。  
  
 `iCount`  
 在列表视图控件中的列数。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 此成员函数实现 Win32 宏的行为[ListView_SetColumnOrderArray](http://msdn.microsoft.com/library/windows/desktop/bb775072)，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CListCtrl::GetColumnOrderArray](#getcolumnorderarray)。  
  
##  <a name="a-namesetcolumnwidtha--clistctrlsetcolumnwidth"></a><a name="setcolumnwidth"></a>CListCtrl::SetColumnWidth  
 更改报表视图或列表视图中的列的宽度。  
  
```  
BOOL SetColumnWidth(
    int nCol,  
    int cx);
```  
  
### <a name="parameters"></a>参数  
 `nCol`  
 为设置宽度的列的索引。 在列表视图中，此参数必须为 0。  
  
 `cx`  
 新的列的宽度。 可以是**LVSCW_AUTOSIZE**或**LVSCW_AUTOSIZE_USEHEADER**，如中所述[LVM_SETCOLUMNWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb761163)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
##  <a name="a-namesetextendedstylea--clistctrlsetextendedstyle"></a><a name="setextendedstyle"></a>CListCtrl::SetExtendedStyle  
 设置的列表视图控件的当前扩展的样式。  
  
```  
DWORD SetExtendedStyle(DWORD dwNewStyle);
```  
  
### <a name="parameters"></a>参数  
 `dwNewStyle`  
 要使用列表视图控件的扩展样式组合。 有关这些样式的描述性列表，请参阅[扩展列表视图样式](http://msdn.microsoft.com/library/windows/desktop/bb774732)中的主题[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 上一个组合扩展使用列表视图控件的样式。  
  
### <a name="remarks"></a>备注  
 此成员函数实现 Win32 宏的行为[ListView_SetExtendedListViewStyle](http://msdn.microsoft.com/library/windows/desktop/bb775076)，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  

 
```cpp  
    // Allow the header controls item to be movable by the user.
    m_myListCtrl.SetExtendedStyle
        (m_myListCtrl.GetExtendedStyle()|LVS_EX_HEADERDRAGDROP);
```

  
##  <a name="a-namesetgroupinfoa--clistctrlsetgroupinfo"></a><a name="setgroupinfo"></a>CListCtrl::SetGroupInfo  
 设置描述当前的 list view 控件的指定的组的信息。  
  
```  
int SetGroupInfo(
    int iGroupId,  
    PLVGROUP pgrp);
```  
  
### <a name="parameters"></a>参数  
 `iGroupId`  
 设置其信息的组的标识符。  
  
 `pgrp`  
 指向[LVGROUP](http://msdn.microsoft.com/library/windows/desktop/bb774769)结构，其中包含要设置的信息。 调用方负责分配此结构并设置其成员。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则组的 ID否则为-1。  
  
### <a name="remarks"></a>备注  
 此方法可发送[LVM_SETGROUPINFO](http://msdn.microsoft.com/library/windows/desktop/bb761167)消息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namesetgroupmetricsa--clistctrlsetgroupmetrics"></a><a name="setgroupmetrics"></a>CListCtrl::SetGroupMetrics  
 设置的列表视图控件的组度量值。  
  
```  
void SetGroupMetrics(PLVGROUPMETRICS pGroupMetrics);
```  
  
### <a name="parameters"></a>参数  
 `pGroupMetrics`  
 一个指向[LVGROUPMETRICS](http://msdn.microsoft.com/library/windows/desktop/bb774752)结构，它包含要设置的组度量值信息。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_SETGROUPMETRICS](http://msdn.microsoft.com/library/windows/desktop/bb761168)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namesethotcursora--clistctrlsethotcursor"></a><a name="sethotcursor"></a>CListCtrl::SetHotCursor  
 设置为列表视图控件启用热跟踪时使用的光标。  
  
```  
HCURSOR SetHotCursor(HCURSOR hc);
```  
  
### <a name="parameters"></a>参数  
 *hc*  
 光标资源，用于表示热光标的句柄。  
  
### <a name="return-value"></a>返回值  
 正在使用列表视图控件的上一个热光标资源句柄。  
  
### <a name="remarks"></a>备注  
 此成员函数实现 Win32 宏的行为[ListView_SetHotCursor](http://msdn.microsoft.com/library/windows/desktop/bb775082)，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
 此时将显示热的游标，仅启用了悬停选择时, 可见，如光标越过任何列表视图项。 通过设置启用悬停选择**LVS_EX_TRACKSELECT**扩展样式。  
  
### <a name="example"></a>示例  
  请参阅示例[CListCtrl::GetHotCursor](#gethotcursor)。  
  
##  <a name="a-namesethotitema--clistctrlsethotitem"></a><a name="sethotitem"></a>CListCtrl::SetHotItem  
 设置的列表视图控件的当前热项。  
  
```  
int SetHotItem(int iIndex);
```  
  
### <a name="parameters"></a>参数  
 `iIndex`  
 要设置为热项的项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 以前热项的从零开始索引。  
  
### <a name="remarks"></a>备注  
 此成员函数实现 Win32 宏的行为[ListView_SetHotItem](http://msdn.microsoft.com/library/windows/desktop/bb775083)，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CListCtrl::GetHotItem](#gethotitem)。  
  
##  <a name="a-namesethovertimea--clistctrlsethovertime"></a><a name="sethovertime"></a>CListCtrl::SetHoverTime  
 设置的列表视图控件的当前悬停时间。  
  
```  
DWORD SetHoverTime(DWORD dwHoverTime = (DWORD)-1);
```  
  
### <a name="parameters"></a>参数  
 *dwHoverTime*  
 新的延迟，以毫秒为单位，鼠标光标必须将鼠标指针悬停在某个项之前选中该选项。 如果传递的默认值，则时间设置为默认悬停时间。  
  
### <a name="return-value"></a>返回值  
 以前悬停时间，以毫秒为单位。  
  
### <a name="remarks"></a>备注  
 此成员函数实现 Win32 宏的行为[ListView_SetHoverTime](http://msdn.microsoft.com/library/windows/desktop/bb775084)，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CListCtrl::GetHoverTime](#gethovertime)。  
  
##  <a name="a-nameseticonspacinga--clistctrlseticonspacing"></a><a name="seticonspacing"></a>CListCtrl::SetIconSpacing  
 设置在列表视图控件中的图标之间的间距。  
  
```  
CSize SetIconSpacing(
    int cx,  
    int cy);  
  
CSize SetIconSpacing(CSize size);
```  
  
### <a name="parameters"></a>参数  
 `cx`  
 X 轴上的图标之间的距离 （以像素为单位）。  
  
 `cy`  
 Y 轴上的图标之间的距离 （以像素为单位）。  
  
 `size`  
 一个`CSize`对象，它指定 x 轴上的图标和 y 轴之间的距离 （以像素为单位）。  
  
### <a name="return-value"></a>返回值  
 一个[CSize](../../atl-mfc-shared/reference/csize-class.md)对象，它包含以前的值的图标大小。  
  
### <a name="remarks"></a>备注  
 此成员函数实现 Win32 宏的行为[ListView_SetIconSpacing](http://msdn.microsoft.com/library/windows/desktop/bb775085)，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  

 
```cpp  
    // Leave lots of space between icons.
    m_myListCtrl.SetIconSpacing(CSize(100, 100));
```

  
##  <a name="a-namesetimagelista--clistctrlsetimagelist"></a><a name="setimagelist"></a>CListCtrl::SetImageList  
 将图像列表分配给列表视图控件。  
  
```  
CImageList* SetImageList(
    CImageList* pImageList,  
    int nImageListType);
```  
  
### <a name="parameters"></a>参数  
 `pImageList`  
 指向要分配的图像列表的指针。  
  
 `nImageListType`  
 图像列表的类型。 它可以是下列值之一︰  
  
- `LVSIL_NORMAL`带有大图标的图像列表。  
  
- `LVSIL_SMALL`带有小图标的图像列表。  
  
- `LVSIL_STATE`包含状态图像的图像列表。  
  
### <a name="return-value"></a>返回值  
 指向上一个图像列表的指针。  
  
### <a name="example"></a>示例  
  请参阅示例[CListCtrl::GetImageList](#getimagelist)。  
  
##  <a name="a-namesetinfotipa--clistctrlsetinfotip"></a><a name="setinfotip"></a>CListCtrl::SetInfoTip  
 设置工具提示文本。  
  
```  
BOOL SetInfoTip(PLVSETINFOTIP plvInfoTip);
```  
  
### <a name="parameters"></a>参数  
 *plvInfoTip*  
 一个指向[LVFSETINFOTIP](http://msdn.microsoft.com/library/windows/desktop/bb774764)结构，它包含要设置的信息。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**成功时， **FALSE**失败。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_SETINFOTIP](http://msdn.microsoft.com/library/windows/desktop/bb761180)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namesetinsertmarka--clistctrlsetinsertmark"></a><a name="setinsertmark"></a>CListCtrl::SetInsertMark  
 将插入点设置为已定义的位置。  
  
```  
BOOL SetInsertMark(LPLVINSERTMARK lvim);
```  
  
### <a name="parameters"></a>参数  
 `lvim`  
 一个指向[LVINSERTMARK](http://msdn.microsoft.com/library/windows/desktop/bb774758)结构，它指定在何处设置插入点。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**如果成功，或**FALSE**否则为。 **FALSE**如果返回的大小以`cbSize`的成员**LVINSERTMARK**结构不相等的结构的实际大小或插入点时不适用于当前视图中。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_SETINSERTMARK](http://msdn.microsoft.com/library/windows/desktop/bb761182)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namesetinsertmarkcolora--clistctrlsetinsertmarkcolor"></a><a name="setinsertmarkcolor"></a>CListCtrl::SetInsertMarkColor  
 设置插入点的颜色。  
  
```  
COLORREF SetInsertMarkColor(COLORREF color);
```  
  
### <a name="parameters"></a>参数  
 `color`  
 一个[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)结构，它指定要设置插入点的颜色。  
  
### <a name="return-value"></a>返回值  
 返回**COLORREF**结构，它包含以前的颜色。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_SETINSERTMARKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb761184)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namesetitema--clistctrlsetitem"></a><a name="setitem"></a>Clistctrl:: Setitem  
 设置的部分或全部列表视图项的属性。  
  
```  
BOOL SetItem(const LVITEM* pItem);

 
BOOL SetItem(
    int nItem,  
    int nSubItem,  
    UINT nMask,  
    LPCTSTR lpszItem,  
    int nImage,  
    UINT nState,  
    UINT nStateMask,  
    LPARAM lParam);

 
BOOL SetItem(
    int nItem,  
    int nSubItem,  
    UINT nMask,  
    LPCTSTR lpszItem,  
    int nImage,  
    UINT nState,  
    UINT nStateMask,  
    LPARAM lParam,  
    int nIndent);
```  
  
### <a name="parameters"></a>参数  
 `pItem`  
 地址的指针[LVITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760)结构，其中包含新的项属性，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。 该结构的**iItem**和**iSubItem**成员标识的项或子项，以及该结构的**掩码**成员指定要设置的属性。 有关详细信息**掩码**成员，请参阅**备注**。  
  
 `nItem`  
 要设置其属性的项的索引。  
  
 `nSubItem`  
 要设置其属性的子项的索引。  
  
 `nMask`  
 指定哪些属性将设置 （请参见备注）。  
  
 `lpszItem`  
 指定项的标签以 null 结尾的字符串的地址。  
  
 `nImage`  
 图像列表中的项的图像的索引。  
  
 `nState`  
 指定的状态更改 （请参见备注） 的值。  
  
 `nStateMask`  
 指定要更改 （请参见备注） 的状态。  
  
 `lParam`  
 要与项关联一个 32 位应用程序特定值。  
  
 `nIndent`  
 宽度，以像素为单位的缩进。 如果`nIndent`小于超过系统定义的最小宽度，新的宽度设置为系统定义的最小值  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 **IItem**和**iSubItem**成员**LVITEM**结构和`nItem`和`nSubItem`参数标识的项和子项要设置其属性。  
  
 **掩码**的成员**LVITEM**结构和`nMask`参数指定哪一项属性是要设置︰  
  
- `LVIF_TEXT`**PszText**成员或`lpszItem`参数是以 null 结尾的字符串的地址; **cchTextMax**成员将被忽略。  
  
- `LVIF_STATE`**StateMask**成员或`nStateMask`参数指定哪一项表明若要更改与**状态**成员或`nState`参数则包含这些状态的值。  
  
### <a name="example"></a>示例  
  请参阅示例[CListCtrl::HitTest](#hittest)。  
  
##  <a name="a-namesetitemcounta--clistctrlsetitemcount"></a><a name="setitemcount"></a>CListCtrl::SetItemCount  
 准备添加大量项的列表视图控件。  
  
```  
void SetItemCount(int nItems);
```  
  
### <a name="parameters"></a>参数  
 `nItems`  
 最终，该控件将包含的项目数。  
  
### <a name="remarks"></a>备注  
 若要设置虚拟列表视图控件的项计数，请参阅[CListCtrl::SetItemCountEx](#setitemcountex)。  
  
### <a name="remarks"></a>备注  
 此成员函数实现 Win32 宏的行为[ListView_SetItemCount](http://msdn.microsoft.com/library/windows/desktop/bb775093)，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  

 
```cpp  
        CString str;

        // Add 1024 items to the list view control.
        m_myListCtrl.SetItemCount(1024);

        for (int i = 0; i < 1024; i++)
        {
            str.Format(TEXT("item %d"), i);
            m_myListCtrl.InsertItem(i, str);
        }
```

  
##  <a name="a-namesetitemcountexa--clistctrlsetitemcountex"></a><a name="setitemcountex"></a>CListCtrl::SetItemCountEx  
 设置虚拟列表视图控件的项计数。  
  
```  
BOOL SetItemCountEx(
    int iCount,  
    DWORD dwFlags = LVSICF_NOINVALIDATEALL);
```  
  
### <a name="parameters"></a>参数  
 `iCount`  
 最终，该控件将包含的项目数。  
  
 `dwFlags`  
 指定项的计数重置后的列表视图控件的行为。 此值可以是以下组合︰  
  
- **LVSICF_NOINVALIDATEALL**列表视图控件不会重新绘制，除非受影响的项目当前位于视图。 这是默认值。  
  
- **LVSICF_NOSCROLL**项进行计数的更改时，列表视图控件不会更改滚动位置。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 此成员函数实现 Win32 宏的行为[ListView_SetItemCountEx](http://msdn.microsoft.com/library/windows/desktop/bb775095)，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]，仅应调用的虚拟列表视图。  
  
### <a name="example"></a>示例  

 
```cpp  
        CString str;

        // Add 1024 items to the list view control.

        // Force my virtual list view control to allocate 
        // enough memory for my 1024 items.
        m_myVirtualListCtrl.SetItemCountEx(1024, LVSICF_NOSCROLL|
            LVSICF_NOINVALIDATEALL);

        for (int i = 0; i < 1024; i++)
        {
            str.Format(TEXT("item %d"), i);
            m_myVirtualListCtrl.InsertItem(i, str);
        }
```

  
##  <a name="a-namesetitemdataa--clistctrlsetitemdata"></a><a name="setitemdata"></a>CListCtrl::SetItemData  
 设置与指定的项相关联的 32 位应用程序特定的值`nItem`。  
  
```  
BOOL SetItemData(int nItem, DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 要设置其数据的列表项的索引。  
  
 `dwData`  
 要与项关联一个 32 位值。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此值是**lParam**的成员[LVITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760)结构，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  

 
```cpp  
    // Set the data of each item to be equal to its index.
    for (int i = 0; i < m_myListCtrl.GetItemCount(); i++)
    {
        m_myListCtrl.SetItemData(i, i);
    }
```

  
##  <a name="a-namesetitemindexstatea--clistctrlsetitemindexstate"></a><a name="setitemindexstate"></a>CListCtrl::SetItemIndexState  
 设置当前的列表视图控件中的项的状态。  
  
```  
BOOL SetItemIndexState(
    PLVITEMINDEX pItemIndex,   
    DWORD dwState,   
    DWORD dwMask) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `pItemIndex`|指向[LVITEMINDEX](http://msdn.microsoft.com/library/windows/desktop/bb774762)描述的项的结构。 调用方负责分配此结构并设置其成员。|  
|[in] `dwState`|要设置的项的状态即的按位组合[列表视图项状态](http://msdn.microsoft.com/library/windows/desktop/bb774733)。 指定为重置为零或一个用于设置，状态。|  
|[in] `dwMask`|通过指定的状态的有效位掩码`dwState`参数。 指定的按位组合 (OR)[列表视图项状态](http://msdn.microsoft.com/library/windows/desktop/bb774733)。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 有关详细信息`dwState`参数，请参阅[列表视图项状态](http://msdn.microsoft.com/library/windows/desktop/bb774733)。  
  
 有关详细信息`dwMask`参数，请参阅`stateMask`的成员[LVITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760)结构。  
  
 此方法可发送[LVM_SETITEMINDEXSTATE](http://msdn.microsoft.com/library/windows/desktop/bb761190)消息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namesetitempositiona--clistctrlsetitemposition"></a><a name="setitemposition"></a>CListCtrl::SetItemPosition  
 将项移到列表视图控件中的指定位置。  
  
```  
BOOL SetItemPosition(
    int nItem,  
    POINT pt);
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 要设置其位置的项的索引。  
  
 `pt`  
 一个[点](http://msdn.microsoft.com/library/windows/desktop/dd162805)结构，它指定视图中的新位置坐标，该项目的窗口左上角。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 该控件必须是图标或小图标视图中。  
  
 如果在列表视图控件具有`LVS_AUTOARRANGE`样式，列表视图中排列后设置项的位置。  
  
### <a name="example"></a>示例  
  请参阅示例[CListCtrl::GetItemPosition](#getitemposition)。  
  
##  <a name="a-namesetitemstatea--clistctrlsetitemstate"></a><a name="setitemstate"></a>CListCtrl::SetItemState  
 更改列表视图控件中的项的状态。  
  
```  
BOOL SetItemState(
    int nItem,  
    LVITEM* pItem);

 
BOOL SetItemState(
    int nItem,  
    UINT nState,  
    UINT nMask);
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 要设置其状态的项的索引。  
  
 `pItem`  
 地址的指针[LVITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760)结构，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。 该结构的**stateMask**成员指定的状态更改，与该结构的位**状态**成员将包含这些位的新值。 其他成员将被忽略。  
  
 `nState`  
 状态位的新值。 有关可能的值的列表，请参阅[CListCtrl::GetNextItem](#getnextitem)和[LVITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760)状态成员。  
  
 `nMask`  
 指定要更改的状态位掩码。 此值对应于的 stateMask 成员[LVITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760)结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 项的"状态"是一个值，指定项的可用性，该值指示用户的操作，或者是否则反映项目的状态。 列表视图控件更改某些状态位，如当用户选择一个项。 应用程序可能会更改其他状态位来禁用或隐藏该项，或指定覆盖图像或状态图像。  
  
### <a name="example"></a>示例  
  请参阅示例[CListCtrl::GetTopIndex](#gettopindex)。  
  
##  <a name="a-namesetitemtexta--clistctrlsetitemtext"></a><a name="setitemtext"></a>CListCtrl::SetItemText  
 更改列表视图项或子项的文本。  
  
```  
BOOL SetItemText(
    int nItem,  
    int nSubItem,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 要设置其文本的项的索引。  
  
 `nSubItem`  
 若要设置的项目标签子项，则为零的索引。  
  
 `lpszText`  
 包含新的项文本的字符串指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 此方法不应使用与包含 LVS_OWNERDATA 窗口样式的控件 （事实上，这将导致断言在调试版本中）。 有关此列表控件样式的详细信息，请参阅[列表视图控件概述](http://msdn.microsoft.com/library/windows/desktop/bb774735)。  
  
### <a name="example"></a>示例  
  请参阅示例[CListCtrl::InsertItem](#insertitem)。  
  
##  <a name="a-namesetoutlinecolora--clistctrlsetoutlinecolor"></a><a name="setoutlinecolor"></a>CListCtrl::SetOutlineColor  
 如果设置的列表视图控件的边框颜色[LVS_EX_BORDERSELECT](http://msdn.microsoft.com/library/windows/desktop/bb774739)设置扩展的窗口样式。  
  
```  
COLORREF SetOutlineColor(COLORREF color);
```  
  
### <a name="parameters"></a>参数  
 `color`  
 新[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)结构，它包含的轮廓颜色。  
  
### <a name="return-value"></a>返回值  
 上一个**COLORREF**结构，它包含的轮廓颜色  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_SETOUTLINECOLOR](http://msdn.microsoft.com/library/windows/desktop/bb761200)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namesetselectedcolumna--clistctrlsetselectedcolumn"></a><a name="setselectedcolumn"></a>CListCtrl::SetSelectedColumn  
 将列表视图控件的所选的列的设置。  
  
```  
LRESULT SetSelectedColumn(int iCol);
```  
  
### <a name="parameters"></a>参数  
 *iCol*  
 要选择的列的索引。  
  
### <a name="return-value"></a>返回值  
 不使用返回的值。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_SETSELECTEDCOLUMN](http://msdn.microsoft.com/library/windows/desktop/bb761202)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namesetselectionmarka--clistctrlsetselectionmark"></a><a name="setselectionmark"></a>CListCtrl::SetSelectionMark  
 设置的列表视图控件的选择标记。  
  
```  
int SetSelectionMark(int iIndex);
```  
  
### <a name="parameters"></a>参数  
 `iIndex`  
 多个所选内容中的第一项的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 上一选择标记，否则为-1 时没有选择标记。  
  
### <a name="remarks"></a>备注  
 此成员函数实现 Win32 宏的行为[ListView_SetSelectionMark](http://msdn.microsoft.com/library/windows/desktop/bb775112)，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CListCtrl::GetSelectionMark](#getselectionmark)。  
  
##  <a name="a-namesettextbkcolora--clistctrlsettextbkcolor"></a><a name="settextbkcolor"></a>CListCtrl::SetTextBkColor  
 在列表视图控件中设置文本的背景色。  
  
```  
BOOL SetTextBkColor(COLORREF cr);
```  
  
### <a name="parameters"></a>参数  
 `cr`  
 一个**COLORREF**指定新文本背景色。 有关信息，请参阅[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="example"></a>示例  

 
```cpp  
        // Use the 3D button face color for the background.
        COLORREF crBkColor = ::GetSysColor(COLOR_3DFACE);
        m_myListCtrl.SetTextBkColor(crBkColor);
        ASSERT(m_myListCtrl.GetTextBkColor() == crBkColor);
```

  
##  <a name="a-namesettextcolora--clistctrlsettextcolor"></a><a name="settextcolor"></a>CListCtrl::SetTextColor  
 设置的列表视图控件的文本颜色。  
  
```  
BOOL SetTextColor(COLORREF cr);
```  
  
### <a name="parameters"></a>参数  
 `cr`  
 一个**COLORREF**指定新的文本颜色。 有关信息，请参阅[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="example"></a>示例  

 
```cpp  
    // Use the window text color for
    // the item text of the list view control.
    COLORREF crTextColor = ::GetSysColor(COLOR_WINDOWTEXT);
    m_myListCtrl.SetTextColor(crTextColor);
    ASSERT(m_myListCtrl.GetTextColor() == crTextColor);
```

  
##  <a name="a-namesettileinfoa--clistctrlsettileinfo"></a><a name="settileinfo"></a>CListCtrl::SetTileInfo  
 设置列表视图控件的磁贴的信息。  
  
```  
BOOL SetTileInfo(PLVTILEINFO pti);
```  
  
### <a name="parameters"></a>参数  
 *pti*  
 一个指向[LVTILEINFO](http://msdn.microsoft.com/library/windows/desktop/bb774766)结构，它包含要设置的信息。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**成功时， **FALSE**失败。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_SETTILEINFO](http://msdn.microsoft.com/library/windows/desktop/bb761210)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namesettileviewinfoa--clistctrlsettileviewinfo"></a><a name="settileviewinfo"></a>CListCtrl::SetTileViewInfo  
 平铺视图中设置的列表视图控件使用的信息。  
  
```  
BOOL SetTileViewInfo(PLVTILEVIEWINFO ptvi);
```  
  
### <a name="parameters"></a>参数  
 `ptvi`  
 一个指向[LVTILEVIEWINFO](http://msdn.microsoft.com/library/windows/desktop/bb774768)结构，它包含要设置的信息。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**成功时， **FALSE**失败。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_SETTILEVIEWINFO](http://msdn.microsoft.com/library/windows/desktop/bb761212)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namesettooltipsa--clistctrlsettooltips"></a><a name="settooltips"></a>CListCtrl::SetToolTips  
 设置将使用列表视图控件来显示工具提示的工具提示控件。  
  
```  
CToolTipCtrl* SetToolTips(CToolTipCtrl* pWndTip);
```  
  
### <a name="parameters"></a>参数  
 `pWndTip`  
 一个指向`CToolTipCtrl`列表控件将使用的对象。  
  
### <a name="return-value"></a>返回值  
 一个指向[CToolTipCtrl](ctooltipctrl-class.md)对象，它包含控件，以前使用的工具提示或`NULL`如果以前不使用任何工具提示。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[LVM_SETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb761216)，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
 若要不使用工具提示，指出`LVS_NOTOOLTIPS`时您创建样式`CListCtrl`对象。  
  
##  <a name="a-namesetviewa--clistctrlsetview"></a><a name="setview"></a>CListCtrl::SetView  
 将列表视图控件的视图设置。  
  
```  
DWORD SetView(int iView);
```  
  
### <a name="parameters"></a>参数  
 *iView*  
 要选择的视图。  
  
### <a name="return-value"></a>返回值  
 否则，返回 1，如果成功，则为-1。 例如，如果视图是无效，则返回-1。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_SETVIEW](http://msdn.microsoft.com/library/windows/desktop/bb761220)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namesetworkareasa--clistctrlsetworkareas"></a><a name="setworkareas"></a>CListCtrl::SetWorkAreas  
 设置图标可以显示在列表视图控件中的位置的区域。  
  
```  
void SetWorkAreas(
    int nWorkAreas,  
    LPRECT lpRect);
```  
  
### <a name="parameters"></a>参数  
 `nWorkAreas`  
 数`RECT`结构 (或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象) 指向数组中`lpRect`。  
  
 `lpRect`  
 数组的地址`RECT`结构 (或`CRect`对象)，用于指定列表视图控件的新的工作区域。 必须在客户端坐标中指定这些区域。 如果此参数为**NULL**，在工作区将被设置为该控件的工作区。  
  
### <a name="remarks"></a>备注  
 此成员函数实现 Win32 宏的行为[ListView_SetWorkAreas](http://msdn.microsoft.com/library/windows/desktop/bb775128)，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  

 
```cpp  
    // Remove all working areas.
    m_myListCtrl.SetWorkAreas(0, NULL);
```

  
##  <a name="a-namesortgroupsa--clistctrlsortgroups"></a><a name="sortgroups"></a>CListCtrl::SortGroups  
 使用应用程序定义比较函数按 ID 列表视图控件中的组进行排序。  
  
```  
BOOL SortGroups(
    PFNLVGROUPCOMPARE _pfnGroupCompare,  
    LPVOID _plv);
```  
  
### <a name="parameters"></a>参数  
 `_pfnGroupCompare`  
 指向组的比较函数的指针。  
  
 `_plv`  
 Void 指针的指针。  
  
### <a name="return-value"></a>返回值  
 成功时返回 `true`，失败时返回 `false`。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LVM_SORTGROUPS](http://msdn.microsoft.com/library/windows/desktop/bb761225)消息，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namesortitemsa--clistctrlsortitems"></a><a name="sortitems"></a>CListCtrl::SortItems  
 通过使用应用程序定义比较函数列表视图项进行排序。  
  
```  
BOOL SortItems(
    PFNLVCOMPARE pfnCompare,  
    DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>参数  
 [in] `pfnCompare`  
 应用程序定义比较函数的地址。  
  
 排序操作调用的比较函数每次需要确定两个列表项的相对顺序。 比较函数必须是独立的函数不是任何类的成员或类的静态成员。  
  
 [in] `dwData`  
 传递给比较函数的应用程序定义的值。  
  
### <a name="return-value"></a>返回值  
 `true`如果成功，则该方法否则为`false`。  
  
### <a name="remarks"></a>备注  
 此方法可更改每个项以反映新的序列的索引。  
  
 比较函数， `pfnCompare`，具有以下形式︰  
  
```  
int CALLBACK CompareFunc(LPARAM lParam1,
    LPARAM lParam2,
    LPARAM lParamSort);
```  
如果第一项应位于第二个之前，比较函数必须返回一个负值，如果第一项应遵循第二个或为零正值将这两项相等。  
  
 `lParam1`参数是与进行比较的第一项相关联的 32 位值和`lParam2`参数是与第二个项相关联的值。 以下是中指定的列的值`lParam`的项目的成员[LVITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760)结构时插入到列表。 `lParamSort`参数等同于`dwData`值。  
  
 此方法可发送[LVM_SORTITEMS](http://msdn.microsoft.com/library/windows/desktop/bb761227)消息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 以下是一个简单的比较函数，将导致项正在按其`lParam`值。  
  
```cpp  
// Sort items by associated lParam
int CALLBACK CListCtrlDlg::MyCompareProc(LPARAM lParam1, LPARAM lParam2, 
    LPARAM lParamSort)
{
    UNREFERENCED_PARAMETER(lParamSort);
return (int)(lParam1 - lParam2);
}
```
  
```cpp  
// Sort the items by passing in the comparison function.
void CListCtrlDlg::Sort()
{
    m_myListCtrl.SortItems(&CListCtrlDlg::MyCompareProc, 0);
}
```
  
##  <a name="a-namesortitemsexa--clistctrlsortitemsex"></a><a name="sortitemsex"></a>CListCtrl::SortItemsEx  
 当前的列表视图控件的项进行排序通过使用应用程序定义比较函数。  
  
```  
BOOL SortItemsEx(
    PFNLVCOMPARE pfnCompare,   
    DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `pfnCompare`|应用程序定义比较函数的地址。<br /><br /> 排序操作调用的比较函数每次需要确定两个列表项的相对顺序。 比较函数必须是独立的函数不是任何类的成员或类的静态成员。|  
|[in] `dwData`|应用程序定义的值传递给比较函数。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法可更改每个项以反映新的序列的索引。  
  
 比较函数， `pfnCompare`，具有以下形式︰  
  
```  
int CALLBACK CompareFunc(LPARAM lParam1,
    LPARAM lParam2,
    LPARAM lParamSort);
```  
此消息就像[LVM_SORTITEMS](http://msdn.microsoft.com/library/windows/desktop/bb761227)，除了的信息类型传递给比较函数。 在[LVM_SORTITEMS](http://msdn.microsoft.com/library/windows/desktop/bb761227)，`lParam1`和`lParam2`是要比较的项的值。 在[LVM_SORTITEMSEX](http://msdn.microsoft.com/library/windows/desktop/bb761228)，`lParam1`是要比较的第一个项的当前索引和`lParam2`是第二个项的当前索引。 您可以发送[LVM_GETITEMTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761055)消息以检索有关某项的详细信息。  
  
 如果第一项应位于第二个之前，比较函数必须返回一个负值，如果第一项应遵循第二个或为零正值将这两项相等。  
  
> [!NOTE]
>  在排序过程中，列表视图内容不稳定。 如果回调函数向 list view 控件发送任何消息以外[LVM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb774953)，则结果不可预知。  
  
 此方法可发送[LVM_SORTITEMSEX](http://msdn.microsoft.com/library/windows/desktop/bb761228)消息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义一个变量， `m_listCtrl`，也就是说，用来访问当前的 list view 控件。 此变量将在下一个示例中使用。  
  
```cpp  
public:
    // Variable used to access the list control.
    CListCtrl m_listCtrl; 
```

  
### <a name="example"></a>示例  
 下面的代码示例演示`SortItemEx`方法。 在此代码示例早期部分中，我们创建了一个显示在报表视图中的标题为"ClientID"和"等级"的两个列的列表视图控件。 下面的代码示例对表排序通过使用"评分"列中的值。  
  

```cpp  
// The ListCompareFunc() method is a global function used by SortItemEx().
int CALLBACK ListCompareFunc(
                             LPARAM lParam1, 
                             LPARAM lParam2, 
                             LPARAM lParamSort)
{
    CListCtrl* pListCtrl = (CListCtrl*) lParamSort;
    CString    strItem1 = pListCtrl->GetItemText(static_cast<int>(lParam1), 1);
    CString    strItem2 = pListCtrl->GetItemText(static_cast<int>(lParam2), 1)
    int x1 = _tstoi(strItem1.GetBuffer());
    int x2 = _tstoi(strItem2.GetBuffer());
    int result = 0;
    if ((x1 - x2) < 0)
        result = -1;
    else if ((x1 - x2) == 0)
        result = 0;
    else
        result = 1;

    return result;
}

void CCListCtrl_s2Dlg::OnBnClickedButton1()
{
    // SortItemsEx
    m_listCtrl.SortItemsEx( ListCompareFunc, (LPARAM)&m_listCtrl );
}
```

  
##  <a name="a-namesubitemhittesta--clistctrlsubitemhittest"></a><a name="subitemhittest"></a>CListCtrl::SubItemHitTest  
 确定哪些列表视图项目时，如果有的话位于给定位置。  
  
```  
int SubItemHitTest(LPLVHITTESTINFO pInfo);
```  
  
### <a name="parameters"></a>参数  
 `pInfo`  
 一个指向[LVHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb774754)结构。  
  
### <a name="return-value"></a>返回值  
 该项目，或子项、 正在测试 （如果有），或否则为-1 基于&1; 的索引。  
  
### <a name="remarks"></a>备注  
 此成员函数实现 Win32 宏的行为[ListView_SubItemHitTest](http://msdn.microsoft.com/library/windows/desktop/bb775135)，如中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  

```cpp  
void CListCtrlDlg::OnDblClk(NMHDR* pNMHDR, LRESULT* pResult)
{
    UNREFERENCED_PARAMETER(pResult);
LPNMITEMACTIVATE pia = (LPNMITEMACTIVATE)pNMHDR;
    LVHITTESTINFO lvhti;

    // Clear the subitem text the user clicked on.
    lvhti.pt = pia->ptAction;
    m_myListCtrl.SubItemHitTest(&lvhti);

    if (lvhti.flags & LVHT_ONITEMLABEL)
    {
        m_myListCtrl.SetItemText(lvhti.iItem, lvhti.iSubItem, NULL);
    }
}
```

  
##  <a name="a-nameupdatea--clistctrlupdate"></a><a name="update"></a>CListCtrl::Update  
 强制重新绘制由指定的项列表视图控件`nItem`。  
  
```  
BOOL Update(int nItem);
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 要更新项的索引。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 此函数还将排列在列表视图控件时才`LVS_AUTOARRANGE`样式。  
  
### <a name="example"></a>示例  
  请参阅示例[CListCtrl::GetSelectedCount](#getselectedcount)。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 ROWLIST](../../visual-cpp-samples.md)   
 [CWnd 类](cwnd-class.md)   
 [层次结构图](../hierarchy-chart.md)   
 [CImageList 类](cimagelist-class.md)


