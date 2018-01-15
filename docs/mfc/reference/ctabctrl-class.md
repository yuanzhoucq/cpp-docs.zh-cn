---
title: "CTabCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTabCtrl
- AFXCMN/CTabCtrl
- AFXCMN/CTabCtrl::CTabCtrl
- AFXCMN/CTabCtrl::AdjustRect
- AFXCMN/CTabCtrl::Create
- AFXCMN/CTabCtrl::CreateEx
- AFXCMN/CTabCtrl::DeleteAllItems
- AFXCMN/CTabCtrl::DeleteItem
- AFXCMN/CTabCtrl::DeselectAll
- AFXCMN/CTabCtrl::DrawItem
- AFXCMN/CTabCtrl::GetCurFocus
- AFXCMN/CTabCtrl::GetCurSel
- AFXCMN/CTabCtrl::GetExtendedStyle
- AFXCMN/CTabCtrl::GetImageList
- AFXCMN/CTabCtrl::GetItem
- AFXCMN/CTabCtrl::GetItemCount
- AFXCMN/CTabCtrl::GetItemRect
- AFXCMN/CTabCtrl::GetItemState
- AFXCMN/CTabCtrl::GetRowCount
- AFXCMN/CTabCtrl::GetToolTips
- AFXCMN/CTabCtrl::HighlightItem
- AFXCMN/CTabCtrl::HitTest
- AFXCMN/CTabCtrl::InsertItem
- AFXCMN/CTabCtrl::RemoveImage
- AFXCMN/CTabCtrl::SetCurFocus
- AFXCMN/CTabCtrl::SetCurSel
- AFXCMN/CTabCtrl::SetExtendedStyle
- AFXCMN/CTabCtrl::SetImageList
- AFXCMN/CTabCtrl::SetItem
- AFXCMN/CTabCtrl::SetItemExtra
- AFXCMN/CTabCtrl::SetItemSize
- AFXCMN/CTabCtrl::SetItemState
- AFXCMN/CTabCtrl::SetMinTabWidth
- AFXCMN/CTabCtrl::SetPadding
- AFXCMN/CTabCtrl::SetToolTips
dev_langs: C++
helpviewer_keywords:
- CTabCtrl [MFC], CTabCtrl
- CTabCtrl [MFC], AdjustRect
- CTabCtrl [MFC], Create
- CTabCtrl [MFC], CreateEx
- CTabCtrl [MFC], DeleteAllItems
- CTabCtrl [MFC], DeleteItem
- CTabCtrl [MFC], DeselectAll
- CTabCtrl [MFC], DrawItem
- CTabCtrl [MFC], GetCurFocus
- CTabCtrl [MFC], GetCurSel
- CTabCtrl [MFC], GetExtendedStyle
- CTabCtrl [MFC], GetImageList
- CTabCtrl [MFC], GetItem
- CTabCtrl [MFC], GetItemCount
- CTabCtrl [MFC], GetItemRect
- CTabCtrl [MFC], GetItemState
- CTabCtrl [MFC], GetRowCount
- CTabCtrl [MFC], GetToolTips
- CTabCtrl [MFC], HighlightItem
- CTabCtrl [MFC], HitTest
- CTabCtrl [MFC], InsertItem
- CTabCtrl [MFC], RemoveImage
- CTabCtrl [MFC], SetCurFocus
- CTabCtrl [MFC], SetCurSel
- CTabCtrl [MFC], SetExtendedStyle
- CTabCtrl [MFC], SetImageList
- CTabCtrl [MFC], SetItem
- CTabCtrl [MFC], SetItemExtra
- CTabCtrl [MFC], SetItemSize
- CTabCtrl [MFC], SetItemState
- CTabCtrl [MFC], SetMinTabWidth
- CTabCtrl [MFC], SetPadding
- CTabCtrl [MFC], SetToolTips
ms.assetid: 42e4aff6-46ae-4b2c-beaa-d1dce8d82138
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ed981a2f7345a59f3df479bcd82b9326fd84de12
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ctabctrl-class"></a>CTabCtrl 类
提供 Windows 公共选项卡控件的功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CTabCtrl : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CTabCtrl::CTabCtrl](#ctabctrl)|构造 `CTabCtrl` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CTabCtrl::AdjustRect](#adjustrect)|计算给定窗口矩形的选项卡控件的显示区域或计算将对应于给定的显示区域的窗口矩形。|  
|[CTabCtrl::Create](#create)|创建选项卡控件并将其附加到的实例`CTabCtrl`对象。|  
|[CTabCtrl::CreateEx](#createex)|创建与指定的 Windows 扩展样式的选项卡控件并将其附加到的实例`CTabCtrl`对象。|  
|[CTabCtrl::DeleteAllItems](#deleteallitems)|从选项卡控件中移除所有项。|  
|[CTabCtrl::DeleteItem](#deleteitem)|从选项卡控件中移除的项。|  
|[CTabCtrl::DeselectAll](#deselectall)|重置在选项卡控件中，清除任何已按下的项。|  
|[CTabCtrl::DrawItem](#drawitem)|绘制选项卡控件的指定的项。|  
|[CTabCtrl::GetCurFocus](#getcurfocus)|检索当前具有焦点的选项卡控件的选项卡。|  
|[CTabCtrl::GetCurSel](#getcursel)|确定选项卡控件中当前选定的选项卡。|  
|[CTabCtrl::GetExtendedStyle](#getextendedstyle)|检索当前正在使用的选项卡控件的扩展的样式。|  
|[CTabCtrl::GetImageList](#getimagelist)|检索与选项卡控件关联的图像列表。|  
|[CTabCtrl::GetItem](#getitem)|检索有关在选项卡控件的选项卡的信息。|  
|[CTabCtrl::GetItemCount](#getitemcount)|检索选项卡控件中的选项卡的数目。|  
|[CTabCtrl::GetItemRect](#getitemrect)|检索在选项卡控件的选项卡的绑定矩形。|  
|[CTabCtrl::GetItemState](#getitemstate)|检索指定选项卡控件项的状态。|  
|[CTabCtrl::GetRowCount](#getrowcount)|检索当前的选项卡控件中选项卡的行数。|  
|[CTabCtrl::GetToolTips](#gettooltips)|检索与选项卡控件关联的工具提示控件的句柄。|  
|[CTabCtrl::HighlightItem](#highlightitem)|设置选项卡项的突出显示状态。|  
|[CTabCtrl::HitTest](#hittest)|确定哪些选项卡上，如果有的话，位于指定的屏幕位置。|  
|[Ctabctrl:: Insertitem](#insertitem)|在选项卡控件中插入新选项卡。|  
|[CTabCtrl::RemoveImage](#removeimage)|从选项卡控件的图像列表中删除映像。|  
|[CTabCtrl::SetCurFocus](#setcurfocus)|将焦点设置到选项卡控件中的指定选项卡。|  
|[CTabCtrl::SetCurSel](#setcursel)|选项卡控件中选择一个选项卡。|  
|[CTabCtrl::SetExtendedStyle](#setextendedstyle)|设置选项卡控件的扩展的样式。|  
|[CTabCtrl::SetImageList](#setimagelist)|将图像列表分配到选项卡控件。|  
|[CTabCtrl::SetItem](#setitem)|设置某些或所有选项卡的特性。|  
|[CTabCtrl::SetItemExtra](#setitemextra)|设置每个选项卡上为应用程序定义选项卡控件中的数据保留的字节数。|  
|[CTabCtrl::SetItemSize](#setitemsize)|设置的宽度和高度的项。|  
|[CTabCtrl::SetItemState](#setitemstate)|设置指示选项卡控件项的状态。|  
|[CTabCtrl::SetMinTabWidth](#setmintabwidth)|设置选项卡控件中项的最小宽度。|  
|[CTabCtrl::SetPadding](#setpadding)|设置 （填充） 每个选项卡的图标和选项卡控件中的标签周围的空间量。|  
|[CTabCtrl::SetToolTips](#settooltips)|将工具提示控件分配给选项卡控件。|  
  
## <a name="remarks"></a>备注  
 "选项卡控件"是类似于笔记本中的分隔条或文件柜中的标签。 通过使用选项卡控件，应用程序可以为窗口或对话框的相同区域定义多个页。 每一页包含一组信息或一组应用程序将显示当用户选择相应的选项卡上的控件。一种特殊类型的选项卡控件将显示如下所示按钮的标签。 单击按钮时，应立即执行命令而不是显示了一个页面。  
  
 此控件 (因此`CTabCtrl`类) 仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 下运行的程序和更高版本。  
  
 有关详细信息使用`CTabCtrl`，请参阅[控件](../../mfc/controls-mfc.md)和[使用 CTabCtrl](../../mfc/using-ctabctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CTabCtrl`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxcmn.h  
  
##  <a name="adjustrect"></a>CTabCtrl::AdjustRect  
 计算给定窗口矩形的选项卡控件的显示区域或计算将对应于给定的显示区域的窗口矩形。  
  
```  
void AdjustRect(BOOL bLarger,   LPRECT lpRect);
```  
  
### <a name="parameters"></a>参数  
 `bLarger`  
 指示要执行何种操作。 如果此参数为**TRUE**，`lpRect`指定显示矩形和接收相应的窗口矩形。 如果此参数为**FALSE**，`lpRect`指定窗口矩形和接收相应的显示矩形。  
  
 `lpRect`  
 指向[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它指定给定的矩形，并接收的计算的矩形。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTabCtrl#1](../../mfc/reference/codesnippet/cpp/ctabctrl-class_1.cpp)]  
  
##  <a name="create"></a>CTabCtrl::Create  
 创建选项卡控件并将其附加到的实例`CTabCtrl`对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 指定选项卡控件的样式。 应用的任意组合[选项卡控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760549)、 Windows SDK 中所述。 请参阅**备注**有关还可以应用于控件的窗口样式的列表。  
  
 `rect`  
 指定选项卡控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构。  
  
 `pParentWnd`  
 通常指定选项卡控件的父窗口`CDialog`。 它不能**NULL**。  
  
 `nID`  
 指定选项卡控件的 id。  
  
### <a name="return-value"></a>返回值  
 **TRUE**对象的初始化是否成功; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 构造`CTabCtrl`两个步骤中的对象。 首先，调用的构造函数，然后调用**创建**，它创建选项卡控件并将其附加到`CTabCtrl`对象。  
  
 除了选项卡控件样式，可以将下面的窗口样式应用到选项卡控件：  
  
- **WS_CHILD**创建一个表示选项卡控件的子窗口。 不能与使用`WS_POPUP`样式。  
  
- **WS_VISIBLE**创建初始可见选项卡控件。  
  
- **WS_DISABLED**创建最初处于禁用状态的窗口。  
  
- **WS_GROUP**指定一组控件在其中用户可以从一个控件移到下一步使用箭头键的第一个控件。 使用定义的所有控件**WS_GROUP**样式后的第一个控件属于同一个组。 使用下一个控件**WS_GROUP**样式结束的样式组和开始下一个组 （即，下一步的开始处的一个组结尾）。  
  
- **WS_TABSTOP**的控件，通过该用户可以通过使用 TAB 键移动任意数量之一指定。 TAB 键将用户移至指定的下一步控件**WS_TABSTOP**样式。  
  
 若要创建具有扩展的窗口样式的选项卡控件，调用[CTabCtrl::CreateEx](#createex)而不是**创建**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTabCtrl#2](../../mfc/reference/codesnippet/cpp/ctabctrl-class_2.cpp)]  
  
##  <a name="createex"></a>CTabCtrl::CreateEx  
 创建控件 （子窗口），并将其与关联`CTabCtrl`对象。  
  
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
 指定要创建的控件的扩展的样式。 扩展窗口样式的列表，请参阅`dwExStyle`参数[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) Windows SDK 中。  
  
 `dwStyle`  
 指定选项卡控件的样式。 应用的任意组合[选项卡控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760549)、 Windows SDK 中所述。 请参阅**备注**中[创建](#create)有关还可以应用于控件的窗口样式的列表。  
  
 `rect`  
 对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构描述的大小和窗口在客户端坐标中创建的位置`pParentWnd`。  
  
 `pParentWnd`  
 指向控件的父级的窗口的指针。  
  
 `nID`  
 控件的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功则为非 0; 否则为 0。  
  
### <a name="remarks"></a>备注  
 使用`CreateEx`而不是[创建](#create)将扩展的窗口样式，指定的 Windows 扩展的样式加**WS_EX_**。  
  
 `CreateEx`创建具有指定的扩展 Windows 样式控件`dwExStyle`。 设置扩展样式特定于控件使用[SetExtendedStyle](#setextendedstyle)。 例如，使用`CreateEx`设置为此类样式**WS_EX_CONTEXTHELP**，但使用`SetExtendedStyle`设置为此类样式**TCS_EX_FLATSEPARATORS**。 有关详细信息，请参阅中所述的样式[选项卡控件扩展样式](http://msdn.microsoft.com/library/windows/desktop/bb760546)Windows SDK 中。  
  
##  <a name="ctabctrl"></a>CTabCtrl::CTabCtrl  
 构造 `CTabCtrl` 对象。  
  
```  
CTabCtrl();
```  
  
##  <a name="deleteallitems"></a>CTabCtrl::DeleteAllItems  
 从选项卡控件中移除所有项。  
  
```  
BOOL DeleteAllItems();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
##  <a name="deleteitem"></a>CTabCtrl::DeleteItem  
 从选项卡控件中移除指定的项。  
  
```  
BOOL DeleteItem(int nItem);
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 要删除的项的从零开始值。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTabCtrl#3](../../mfc/reference/codesnippet/cpp/ctabctrl-class_3.cpp)]  
  
##  <a name="deselectall"></a>CTabCtrl::DeselectAll  
 重置在选项卡控件中，清除任何已按下的项。  
  
```  
void DeselectAll(BOOL fExcludeFocus);
```  
  
### <a name="parameters"></a>参数  
 *fExcludeFocus*  
 指定的项取消选择作用域的标志。 如果此参数设置为**FALSE**，选项卡上的所有按钮将被重都置。 如果设置为**TRUE**，则将重置当前选定的一个除外的所有选项卡项。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息中，行为[TCM_DESELECTALL](http://msdn.microsoft.com/library/windows/desktop/bb760579)，如 Windows SDK 中所述。  
  
##  <a name="drawitem"></a>CTabCtrl::DrawItem  
 由框架在某个所有者描述选项卡控件发生变化的可视方面时调用。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpDrawItemStruct`  
 指向的指针[DRAWITEMSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb775802)结构描述要绘制的项。  
  
### <a name="remarks"></a>备注  
 **ItemAction**的成员`DRAWITEMSTRUCT`结构定义要执行的绘制操作。  
  
 默认情况下，此成员函数没有任何影响。 重写该成员函数以实现所有者描述的绘图`CTabCtrl`对象。  
  
 应用程序应还原选择的显示上下文中提供的所有图形设备接口 (GDI) 对象`lpDrawItemStruct`之前此成员函数将终止。  
  
##  <a name="getcurfocus"></a>CTabCtrl::GetCurFocus  
 检索当前具有焦点的选项卡的索引。  
  
```  
int GetCurFocus() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前具有焦点的选项卡的从零开始索引。  
  
##  <a name="getcursel"></a>CTabCtrl::GetCurSel  
 检索选项卡控件中当前选定的选项卡。  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功已选定选项卡或 1 如果不选择任何选项卡的从零开始索引。  
  
##  <a name="getextendedstyle"></a>CTabCtrl::GetExtendedStyle  
 检索当前正在使用的选项卡控件的扩展的样式。  
  
```  
DWORD GetExtendedStyle();
```  
  
### <a name="return-value"></a>返回值  
 表示当前正在使用的选项卡控件的扩展的样式。 此值是的组合[选项卡控件扩展样式](http://msdn.microsoft.com/library/windows/desktop/bb760546)，如 Windows SDK 中所述。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[TCM_GETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb760585)，如 Windows SDK 中所述。  
  
##  <a name="getimagelist"></a>CTabCtrl::GetImageList  
 检索与选项卡控件关联的图像列表。  
  
```  
CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，指向选项卡的图像列表的控件;否则为**NULL**。  
  
##  <a name="getitem"></a>CTabCtrl::GetItem  
 检索有关在选项卡控件的选项卡的信息。  
  
```  
BOOL GetItem(int nItem,   TCITEM* pTabCtrlItem) const;  
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 选项卡的从零开始索引。  
  
 `pTabCtrlItem`  
 指向[TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554)结构，用于指定要检索的信息。 此外用于接收选项卡的信息。此结构用于`InsertItem`， `GetItem`，和`SetItem`成员函数。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**如果成功，则**FALSE**否则为。  
  
### <a name="remarks"></a>备注  
 发送消息，**掩码**成员指定要返回的属性。 如果**掩码**成员指定`TCIF_TEXT`值， **pszText**成员必须包含接收项文本的缓冲区的地址和**cchTextMax**成员必须指定缓冲区的大小。  
  
 **掩码**  
 值，该值指定该`TCITEM`结构成员，以检索或设置。 此成员可以是零，也可以是以下值的组合：  
  
- `TCIF_TEXT`**PszText**成员无效。  
  
- `TCIF_IMAGE``iImage`成员无效。  
  
- `TCIF_PARAM`**LParam**成员无效。  
  
- `TCIF_RTLREADING`文本**pszText**希伯来语或阿拉伯语系统上使用从右到左阅读顺序显示。  
  
- `TCIF_STATE`**DwState**成员无效。  
  
 **pszText**  
 指向以 null 结尾的字符串，如果结构包含选项卡的信息包含在选项卡文本指针。如果结构接收信息，此成员将指定的接收在选项卡文本的缓冲区的地址。  
  
 **cchTextMax**  
 指向的缓冲区大小**pszText**。 如果结构未接收信息，则忽略此成员。  
  
 `iImage`  
 如果没有为选项卡的图像中选项卡控件的图像列表，或-1 的索引。  
  
 **lParam**  
 与选项卡关联的应用程序定义的数据。如果有多个四个字节的每个选项卡上的应用程序定义数据，应用程序必须定义一个结构，并使用它而不是`TCITEM`结构。 应用程序定义结构的第一个成员必须是[TCITEMHEADER](http://msdn.microsoft.com/library/windows/desktop/bb760556)结构。 **TCITEMHEADER**结构等同于`TCITEM`结构，但没有**lParam**成员。 结构的大小和的大小之间的差异**TCITEMHEADER**结构应等于每个选项卡上的额外字节数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTabCtrl#4](../../mfc/reference/codesnippet/cpp/ctabctrl-class_4.cpp)]  
  
##  <a name="getitemcount"></a>CTabCtrl::GetItemCount  
 检索选项卡控件中的选项卡的数目。  
  
```  
int GetItemCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 选项卡控件中项的数目。  
  
### <a name="example"></a>示例  
  请参阅示例[CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)。  
  
##  <a name="getitemrect"></a>CTabCtrl::GetItemRect  
 检索指定的选项卡中选项卡控件的边框。  
  
```  
BOOL GetItemRect(int nItem,   LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 选项卡项的从零开始索引。  
  
 `lpRect`  
 指向[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)接收选项卡的边框的结构。这些坐标使用视区的当前映射模式。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
  请参阅示例[CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)。  
  
##  <a name="getitemstate"></a>CTabCtrl::GetItemState  
 检索由标识的选项卡控件项的状态`nItem`。  
  
```  
DWORD GetItemState(
    int nItem,  
    DWORD dwMask) const;  
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 为其检索状态信息项的从零开始的索引号。  
  
 `dwMask`  
 指定用于返回的项的状态标志的掩码。 有关值的列表，请参阅的掩码成员[TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554)结构，如 Windows SDK 中所述。  
  
### <a name="return-value"></a>返回值  
 对引用`DWORD`接收的状态信息的值。 可以是以下值之一：  
  
|“值”|描述|  
|-----------|-----------------|  
|**TCIS_BUTTONPRESSED**|选择选项卡控件项。|  
|**TCIS_HIGHLIGHTED**|选项卡控件项会突出显示，并使用当前的突出显示颜色绘制选项卡和文本。 在使用突出显示颜色时，这将是 true 的内插，不是抖色的颜色。|  
  
### <a name="remarks"></a>备注  
 通过指定项的状态**dwState**的成员`TCITEM`结构。  
  
##  <a name="getrowcount"></a>CTabCtrl::GetRowCount  
 检索当前的选项卡控件中的行数。  
  
```  
int GetRowCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 选项卡控件中选项卡的行数。  
  
### <a name="remarks"></a>备注  
 只有选项卡控件具有**TCS_MULTILINE**样式可以有多个行的选项卡。  
  
##  <a name="gettooltips"></a>CTabCtrl::GetToolTips  
 检索与选项卡控件关联的工具提示控件的句柄。  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则的工具提示控件句柄否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 选项卡控件创建工具提示控件，如果它具有**TCS_TOOLTIPS**样式。 你还可以将工具提示控件通过使用分配给选项卡控件`SetToolTips`成员函数。  
  
##  <a name="highlightitem"></a>CTabCtrl::HighlightItem  
 设置选项卡项的突出显示状态。  
  
```  
BOOL HighlightItem(int idItem,   BOOL fHighlight = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `idItem`  
 选项卡控件项的从零开始索引。  
  
 `fHighlight`  
 值，该值指定要设置的突出显示状态。 如果此值为**TRUE**，选项卡将突出显示; 如果**FALSE**，选项卡上设置为其默认状态。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息[TCM_HIGHLIGHTITEM](http://msdn.microsoft.com/library/windows/desktop/bb760602)，如 Windows SDK 中所述。  
  
##  <a name="hittest"></a>CTabCtrl::HitTest  
 确定哪些选项卡上，如果有的话，位于指定的屏幕位置。  
  
```  
int HitTest(TCHITTESTINFO* pHitTestInfo) const;  
```  
  
### <a name="parameters"></a>参数  
 `pHitTestInfo`  
 指向[TCHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb760553)结构，在 Windows SDK 中，指定要测试的屏幕位置所述。  
  
### <a name="return-value"></a>返回值  
 如果没有选项卡位于指定位置，则返回选项卡或-1 的从零开始的索引。  
  
##  <a name="insertitem"></a>Ctabctrl:: Insertitem  
 在现有的选项卡控件中插入新选项卡。  
  
```  
LONG InsertItem(
    int nItem,
    TCITEM* pTabCtrlItem);

 
LONG InsertItem(
    int nItem,
    LPCTSTR lpszItem);

 
LONG InsertItem(
    int nItem,
    LPCTSTR lpszItem,
    int nImage);

 
LONG InsertItem(
    UINT nMask,
    int nItem,
    LPCTSTR lpszItem,
    int nImage,
    LPARAM lParam);

 
LONG InsertItem(
    UINT nMask,  
    int nItem,  
    LPCTSTR lpszItem,  
    int nImage,  
    LPARAM lParam,  
    DWORD dwState,  
    DWORD dwStateMask);
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 新选项卡的从零开始索引。  
  
 `pTabCtrlItem`  
 指向[TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554)结构，它指定的选项卡的属性。  
  
 `lpszItem`  
 包含选项卡的文本的以 null 结尾的字符串的地址。  
  
 `nImage`  
 要插入从图像列表的图像的从零开始的索引。  
  
 `nMask`  
 指定哪些`TCITEM`结构要设置的属性。 可以是零个或以下值的组合：  
  
- `TCIF_TEXT`**PszText**成员无效。  
  
- `TCIF_IMAGE``iImage`成员无效。  
  
- `TCIF_PARAM`**LParam**成员无效。  
  
- `TCIF_RTLREADING`文本**pszText**希伯来语或阿拉伯语系统上使用从右到左阅读顺序显示。  
  
- `TCIF_STATE`**DwState**成员无效。  
  
 `lParam`  
 与选项卡关联的应用程序定义的数据。  
  
 `dwState`  
 指定项的状态的值。 有关详细信息，请参阅[TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) Windows SDK 中。  
  
 *dwStateMask*  
 指定要设置的状态。 有关详细信息，请参阅[TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) Windows SDK 中。  
  
### <a name="return-value"></a>返回值  
 如果成功，则新的选项卡的从零开始的索引否则为-1。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CTabCtrl#5](../../mfc/reference/codesnippet/cpp/ctabctrl-class_5.cpp)]  
  
##  <a name="removeimage"></a>CTabCtrl::RemoveImage  
 从选项卡控件的图像列表中移除指定的映像。  
  
```  
void RemoveImage(int nImage);
```  
  
### <a name="parameters"></a>参数  
 `nImage`  
 要删除的映像的从零开始索引。  
  
### <a name="remarks"></a>备注  
 选项卡控件将更新每个选项卡的映像索引，以便保持与同一个映像关联的每个选项卡。  
  
##  <a name="setcurfocus"></a>CTabCtrl::SetCurFocus  
 将焦点设置到选项卡控件中的指定选项卡。  
  
```  
void SetCurFocus(int nItem);
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 指定的索引的选项卡上获取焦点。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[TCM_SETCURFOCUS](http://msdn.microsoft.com/library/windows/desktop/bb760610)，如 Windows SDK 中所述。  
  
##  <a name="setcursel"></a>CTabCtrl::SetCurSel  
 选项卡控件中选择一个选项卡。  
  
```  
int SetCurSel(int nItem);
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 要选择的项的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 从零开始的索引的以前选择的选项卡，如果成功，否则为-1。  
  
### <a name="remarks"></a>备注  
 选项卡控件不会发送**TCN_SELCHANGING**或**TCN_SELCHANGE**通知消息时使用此函数在选择选项卡。 发送这些通知，使用**WM_NOTIFY**，当用户单击或使用键盘来更改选项卡。  
  
##  <a name="setextendedstyle"></a>CTabCtrl::SetExtendedStyle  
 设置选项卡控件的扩展的样式。  
  
```  
DWORD SetExtendedStyle(DWORD dwNewStyle,   DWORD dwExMask = 0);
```  
  
### <a name="parameters"></a>参数  
 `dwNewStyle`  
 值，该值指定选项卡上的组合来控制扩展的样式。  
  
 `dwExMask`  
 A`DWORD`值，该值指示在哪种样式`dwNewStyle`要会受到影响。 中的扩展的样式`dwExMask`将会更改。 原样，则将保留所有其他样式。 如果此参数为零，则所有的中的样式`dwNewStyle`将受到影响。  
  
### <a name="return-value"></a>返回值  
 A`DWORD`包含以前的值[选项卡控件扩展样式](http://msdn.microsoft.com/library/windows/desktop/bb760546)，如 Windows SDK 中所述。  
  
### <a name="return-value"></a>返回值  
 此成员函数实现的 Win32 消息行为[TCM_SETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb760627)，如 Windows SDK 中所述。  
  
##  <a name="setimagelist"></a>CTabCtrl::SetImageList  
 将图像列表分配到选项卡控件。  
  
```  
CImageList* SetImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>参数  
 `pImageList`  
 指向要分配给选项卡控件的图像列表的指针。  
  
### <a name="return-value"></a>返回值  
 将指针返回到以前的图像列表或**NULL**如果没有任何以前的图像列表。  
  
##  <a name="setitem"></a>CTabCtrl::SetItem  
 设置某些或所有选项卡的特性。  
  
```  
BOOL SetItem(int nItem,   TCITEM* pTabCtrlItem);
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 项的从零开始索引。  
  
 `pTabCtrlItem`  
 指向[TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554)结构，其中包含新的项特性。 **掩码**成员指定要设置的属性。 如果**掩码**成员指定`TCIF_TEXT`值， **pszText**成员是以 null 结尾的字符串的地址和**cchTextMax**成员将被忽略。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
  请参阅示例[GetItem](#getitem)。  
  
##  <a name="setitemextra"></a>CTabCtrl::SetItemExtra  
 设置每个选项卡上为应用程序定义选项卡控件中的数据保留的字节数。  
  
```  
BOOL SetItemExtra(int nBytes);
```  
  
### <a name="parameters"></a>参数  
 `nBytes`  
 若要设置的额外字节数。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[TCM_SETITEMEXTRA](http://msdn.microsoft.com/library/windows/desktop/bb760633)，如 Windows SDK 中所述。  
  
##  <a name="setitemsize"></a>CTabCtrl::SetItemSize  
 设置选项卡控件项的宽度和高度。  
  
```  
CSize SetItemSize(CSize size);
```  
  
### <a name="parameters"></a>参数  
 `size`  
 选项卡控件项的新宽度和高度（以像素为单位）。  
  
### <a name="return-value"></a>返回值  
 返回选项卡控件项的旧宽度和高度。  
  
##  <a name="setitemstate"></a>CTabCtrl::SetItemState  
 设置由标识的选项卡控件项状态`nItem`。  
  
```  
BOOL SetItemState(
    int nItem,
    DWORD dwMask,
    DWORD dwState);
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 为其设置状态信息项的从零开始索引号。  
  
 `dwMask`  
 指定用于设置其项的状态标志的掩码。 有关值的列表，请参阅的掩码成员[TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554)结构，如 Windows SDK 中所述。  
  
 `dwState`  
 对引用`DWORD`值，该值包含状态信息。 可以是以下值之一：  
  
|“值”|描述|  
|-----------|-----------------|  
|**TCIS_BUTTONPRESSED**|选择选项卡控件项。|  
|**TCIS_HIGHLIGHTED**|选项卡控件项会突出显示，并使用当前的突出显示颜色绘制选项卡和文本。 在使用突出显示颜色时，这将是 true 的内插，不是抖色的颜色。|  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
##  <a name="setmintabwidth"></a>CTabCtrl::SetMinTabWidth  
 设置选项卡控件中项的最小宽度。  
  
```  
int SetMinTabWidth(int cx);
```  
  
### <a name="parameters"></a>参数  
 `cx`  
 要为设置的选项卡控件项的最小宽度。 如果此参数设置为-1，控件将使用默认选项卡宽度。  
  
### <a name="return-value"></a>返回值  
 以前的最小的选项卡宽度。  
  
### <a name="return-value"></a>返回值  
 此成员函数实现的 Win32 消息行为[TCM_SETMINTABWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb760637)，如 Windows SDK 中所述。  
  
##  <a name="setpadding"></a>CTabCtrl::SetPadding  
 设置 （填充） 每个选项卡的图标和选项卡控件中的标签周围的空间量。  
  
```  
void SetPadding(CSize size);
```  
  
### <a name="parameters"></a>参数  
 `size`  
 设置 （填充） 每个选项卡的图标和选项卡控件中的标签周围的空间量。  
  
##  <a name="settooltips"></a>CTabCtrl::SetToolTips  
 将工具提示控件分配给选项卡控件。  
  
```  
void SetToolTips(CToolTipCtrl* pWndTip);
```  
  
### <a name="parameters"></a>参数  
 `pWndTip`  
 工具提示控件的句柄。  
  
### <a name="remarks"></a>备注  
 你可以通过调用与选项卡控件关联的工具提示控件`GetToolTips`。  
  
### <a name="example"></a>示例  
  请参阅示例[CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)。  
  
## <a name="see-also"></a>请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CHeaderCtrl 类](../../mfc/reference/cheaderctrl-class.md)   
 [CListCtrl 类](../../mfc/reference/clistctrl-class.md)
