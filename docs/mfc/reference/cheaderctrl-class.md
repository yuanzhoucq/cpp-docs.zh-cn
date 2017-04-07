---
title: "CHeaderCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHeaderCtrl
- AFXCMN/CHeaderCtrl
- AFXCMN/CHeaderCtrl::CHeaderCtrl
- AFXCMN/CHeaderCtrl::ClearAllFilters
- AFXCMN/CHeaderCtrl::ClearFilter
- AFXCMN/CHeaderCtrl::Create
- AFXCMN/CHeaderCtrl::CreateDragImage
- AFXCMN/CHeaderCtrl::CreateEx
- AFXCMN/CHeaderCtrl::DeleteItem
- AFXCMN/CHeaderCtrl::DrawItem
- AFXCMN/CHeaderCtrl::EditFilter
- AFXCMN/CHeaderCtrl::GetBitmapMargin
- AFXCMN/CHeaderCtrl::GetFocusedItem
- AFXCMN/CHeaderCtrl::GetImageList
- AFXCMN/CHeaderCtrl::GetItem
- AFXCMN/CHeaderCtrl::GetItemCount
- AFXCMN/CHeaderCtrl::GetItemDropDownRect
- AFXCMN/CHeaderCtrl::GetItemRect
- AFXCMN/CHeaderCtrl::GetOrderArray
- AFXCMN/CHeaderCtrl::GetOverflowRect
- AFXCMN/CHeaderCtrl::HitTest
- AFXCMN/CHeaderCtrl::InsertItem
- AFXCMN/CHeaderCtrl::Layout
- AFXCMN/CHeaderCtrl::OrderToIndex
- AFXCMN/CHeaderCtrl::SetBitmapMargin
- AFXCMN/CHeaderCtrl::SetFilterChangeTimeout
- AFXCMN/CHeaderCtrl::SetFocusedItem
- AFXCMN/CHeaderCtrl::SetHotDivider
- AFXCMN/CHeaderCtrl::SetImageList
- AFXCMN/CHeaderCtrl::SetItem
- AFXCMN/CHeaderCtrl::SetOrderArray
dev_langs:
- C++
helpviewer_keywords:
- CHeaderCtrl class
- Windows common controls [C++], CHeaderCtrl
- header controls, CHeaderCtrl class
ms.assetid: b847ac90-5fae-4a87-88e0-ca45f77b8b3b
caps.latest.revision: 24
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: faa23ea6f28c2643c9bee090ea150e37d0add97c
ms.lasthandoff: 04/01/2017

---
# <a name="cheaderctrl-class"></a>CHeaderCtrl 类
提供 Windows 公共标头控件的功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CHeaderCtrl : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CHeaderCtrl::CHeaderCtrl](#cheaderctrl)|构造 `CHeaderCtrl` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CHeaderCtrl::ClearAllFilters](#clearallfilters)|清除所有筛选器的标头控件。|  
|[CHeaderCtrl::ClearFilter](#clearfilter)|清除标头控件的筛选器。|  
|[CHeaderCtrl::Create](#create)|创建一个标头控件并将其附加到`CHeaderCtrl`对象。|  
|[Cheaderctrl:: Createdragimage](#createdragimage)|创建标头控件内的项的图像的透明版本。|  
|[CHeaderCtrl::CreateEx](#createex)|创建指定的 Windows 扩展样式的标头控件，并将其附加到`CListCtrl`对象。|  
|[CHeaderCtrl::DeleteItem](#deleteitem)|标头控件中删除的项。|  
|[CHeaderCtrl::DrawItem](#drawitem)|绘制标题控件中的指定的项。|  
|[CHeaderCtrl::EditFilter](#editfilter)|开始编辑标头控件的指定的筛选器。|  
|[CHeaderCtrl::GetBitmapMargin](#getbitmapmargin)|检索的边距标题控件中的位图的宽度。|  
|[CHeaderCtrl::GetFocusedItem](#getfocuseditem)|获取当前具有焦点的标题控件中的项的标识符。|  
|[CHeaderCtrl::GetImageList](#getimagelist)|检索图像列表用于标题控件中绘制标头项的句柄。|  
|[Cheaderctrl:: Getitem](#getitem)|检索有关标题控件中的项的信息。|  
|[CHeaderCtrl::GetItemCount](#getitemcount)|检索在标头控件中项的计数。|  
|[CHeaderCtrl::GetItemDropDownRect](#getitemdropdownrect)|标题控件中获取指定的下拉按钮的边界矩形信息。|  
|[CHeaderCtrl::GetItemRect](#getitemrect)|检索给定标头控件中项的边框。|  
|[Cheaderctrl:: Getorderarray](#getorderarray)|检索标头控件中的项的从左到右顺序。|  
|[CHeaderCtrl::GetOverflowRect](#getoverflowrect)|获取当前的标头控件的溢出按钮的边框。|  
|[CHeaderCtrl::HitTest](#hittest)|确定哪些标头项，如果有的话，位于指定点处。|  
|[Cheaderctrl:: Insertitem](#insertitem)|标头控件中插入一个新项。|  
|[CHeaderCtrl::Layout](#layout)|检索的大小和位置标头控件的给定矩形范围内。|  
|[Cheaderctrl:: Ordertoindex](#ordertoindex)|检索基于在标头控件中的顺序的项目的索引值。|  
|[CHeaderCtrl::SetBitmapMargin](#setbitmapmargin)|标题控件中设置的边距的位图的宽度。|  
|[CHeaderCtrl::SetFilterChangeTimeout](#setfilterchangetimeout)|中的筛选器属性发生更改的时间与发布之间的超时间隔设置`HDN_FILTERCHANGE`通知。|  
|[CHeaderCtrl::SetFocusedItem](#setfocuseditem)|将焦点设置到当前的标头控件中指定的标头项。|  
|[CHeaderCtrl::SetHotDivider](#sethotdivider)|标头项以指示手动之间的分隔线将拖动的更改和标头项的 drop。|  
|[CHeaderCtrl::SetImageList](#setimagelist)|将图像列表分配到标题控件中。|  
|[Cheaderctrl:: Setitem](#setitem)|标题控件中设置指定的项的属性。|  
|[Cheaderctrl:: Setorderarray](#setorderarray)|标题控件中设置的项的从左到右的顺序。|  
  
## <a name="remarks"></a>备注  
 标头控件是一个窗口通常位于上面的一组文本或数字的列。 它包含每个列的标题以及划分为部分。 用户可拖动分隔各个部分，以设置每个列的宽度的分隔条。 标头控件的说明，请参阅[标头控件](http://msdn.microsoft.com/library/windows/desktop/bb775238)。  
  
 此控件 (因此`CHeaderCtrl`类) 仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 下运行的程序和更高版本。  
  
 添加 Windows 95/Internet Explorer 4.0 版公共控件的功能包括︰  
  
-   标头项自定义排序。  
  
-   标头项拖放，为标头项重新排序。 使用`HDS_DRAGDROP`样式创建时`CHeaderCtrl`对象。  
  
-   标头列文本不断可查看期间列的大小。 使用`HDS_FULLDRAG`样式创建时`CHeaderCtrl`对象。  
  
-   标头的热跟踪，这将指针悬停时突出显示的标头项。 使用`HDS_HOTTRACK`样式创建时`CHeaderCtrl`对象。  
  
-   图像列表支持。 标头项目可以包含存储在映像`CImageList`对象或文本。  
  
 有关使用`CHeaderCtrl`，请参阅[控件](../../mfc/controls-mfc.md)和[使用 CHeaderCtrl](../../mfc/using-cheaderctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHeaderCtrl`  
  
## <a name="requirements"></a>要求  
 **标头：** afxcmn.h  
  
##  <a name="cheaderctrl"></a>CHeaderCtrl::CHeaderCtrl  
 构造 `CHeaderCtrl` 对象。  
  
```  
CHeaderCtrl();
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_1.cpp)]  
  
##  <a name="clearallfilters"></a>CHeaderCtrl::ClearAllFilters  
 清除所有筛选器的标头控件。  
  
```  
BOOL ClearAllFilters();
```  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法实现的行为的 Win32 消息[HDM_CLEARFILTER](http://msdn.microsoft.com/library/windows/desktop/bb775306)列值为-1 中, 所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]  
  
##  <a name="clearfilter"></a>CHeaderCtrl::ClearFilter  
 清除标头控件的筛选器。  
  
```  
BOOL ClearFilter(int nColumn);
```  
  
### <a name="parameters"></a>参数  
 `nColumn`  
 列值，该值指示要清除哪个滤镜。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法实现的行为的 Win32 消息[HDM_CLEARFILTER](http://msdn.microsoft.com/library/windows/desktop/bb775306)中所述， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_3.cpp)]  
  
##  <a name="create"></a>CHeaderCtrl::Create  
 创建一个标头控件并将其附加到`CHeaderCtrl`对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 指定标头控件的样式。 标头控件样式的说明，请参阅[标头控件样式](http://msdn.microsoft.com/library/windows/desktop/bb775241)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `rect`  
 指定标头控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构。  
  
 `pParentWnd`  
 指定标头控件的父窗口中，通常`CDialog`。 它不能**NULL**。  
  
 `nID`  
 指定标头控件的 id。  
  
### <a name="return-value"></a>返回值  
 如果初始化成功; 则为非 0否则为零。  
  
### <a name="remarks"></a>备注  
 构造`CHeaderCtrl`两个步骤中的对象。 首先，调用的构造函数，然后调用**创建**，它创建标头控件并将其附加到`CHeaderCtrl`对象。  
  
 除了标头控件样式，你可以使用以下常见的控件样式确定如何标头控件定位并调整自身大小 (请参阅[公共控件样式](http://msdn.microsoft.com/library/windows/desktop/bb775498)有关详细信息):  
  
- `CCS_BOTTOM`使控件来为自身定位在的父窗口工作区底部和设置窗口的宽度的宽度与父项相同。  
  
- `CCS_NODIVIDER`防止两个像素突出显示绘制控件的顶部。  
  
- `CCS_NOMOVEY`将导致控件调整大小并在响应中水平，但不是垂直移动本身`WM_SIZE`消息。 如果`CCS_NORESIZE`样式时，此样式不适用。 标头控件默认具有此样式。  
  
- `CCS_NOPARENTALIGN`防止自动移动到顶部或底部父窗口的控件。 相反，则控件将其位置尽管有所变化的父窗口中保持为父窗口的大小。 如果`CCS_TOP`或`CCS_BOTTOM`还使用样式，高度将会调整为默认值，但的位置和宽度保持不变。  
  
- `CCS_NORESIZE`在设置其初始大小或新的大小时使用的默认宽度和高度将阻止该控件。 相反，该控件使用的宽度和高度的创建或调整请求中指定。  
  
- `CCS_TOP`使控件来为自身定位在父窗口工作区的顶部和设置窗口的宽度的宽度与父项相同。  
  
 你还可以应用以下的窗口样式到标题控件 (请参阅[窗口样式](../../mfc/reference/window-styles.md)有关详细信息):  
  
- **WS_CHILD**创建子窗口。 不能与使用`WS_POPUP`样式。  
  
- **WS_VISIBLE**创建初始可见的窗口。  
  
- **WS_DISABLED**创建最初处于禁用状态的窗口。  
  
- **WS_GROUP**指定一组控件在其中用户可以从一个控件移到下一步使用箭头键的第一个控件。 使用定义的所有控件**WS_GROUP**样式后的第一个控件属于同一个组。 使用下一个控件**WS_GROUP**样式结束的样式组和开始下一个组 （即，下一步的开始处的一个组结尾）。  
  
- **WS_TABSTOP**的控件，通过该用户可以通过使用 TAB 键移动任意数量之一指定。 TAB 键将用户移至指定的下一步控件**WS_TABSTOP**样式。  
  
 如果你想要将扩展的窗口样式与控件一起使用，调用[CreateEx](#createex)而不是**创建**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]  
  
##  <a name="createex"></a>CHeaderCtrl::CreateEx  
 创建控件 （子窗口），并将其与关联`CHeaderCtrl`对象。  
  
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
 标头控件的样式。 标头控件样式的说明，请参阅[标头控件样式](http://msdn.microsoft.com/library/windows/desktop/bb775241)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 请参阅[创建](#create)有关其他样式的列表。  
  
 `rect`  
 对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构描述的大小和窗口在客户端坐标中创建的位置`pParentWnd`。  
  
 `pParentWnd`  
 指向控件的父级的窗口的指针。  
  
 `nID`  
 控件的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 使用`CreateEx`而不是**创建**将扩展的窗口样式，指定的 Windows 扩展的样式加**WS_EX_**。  
  
##  <a name="createdragimage"></a>Cheaderctrl:: Createdragimage  
 创建标头控件内的项的图像的透明版本。  
  
```  
CImageList* CreateDragImage(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 标头控件中项的从零开始索引。 分配给此项目的映像是透明的映像的基础。  
  
### <a name="return-value"></a>返回值  
 指向的指针[CImageList](../../mfc/reference/cimagelist-class.md)对象成功; 否则为如果**NULL**。 返回的列表包含只有一个映像。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[HDM_CREATEDRAGIMAGE](http://msdn.microsoft.com/library/windows/desktop/bb775308)中所述， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 提供它是为了支持标头项拖放。  
  
 `CImageList`对象向其返回的指针点是临时对象，并在下一步的空闲时间处理过程中删除。  
  
##  <a name="deleteitem"></a>CHeaderCtrl::DeleteItem  
 标头控件中删除的项。  
  
```  
BOOL DeleteItem(int nPos);
```  
  
### <a name="parameters"></a>参数  
 `nPos`  
 指定要删除的项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 5](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_5.cpp)]  
  
##  <a name="drawitem"></a>CHeaderCtrl::DrawItem  
 由框架在所有者绘制标头控件的变化的可视方面时调用。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpDrawItemStruct`  
 指向的指针[DRAWITEMSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb775802)结构描述要绘制的项。  
  
### <a name="remarks"></a>备注  
 **ItemAction**的成员`DRAWITEMSTRUCT`结构定义要执行的绘制操作。  
  
 默认情况下，此成员函数没有任何影响。 重写该成员函数以实现所有者描述的绘图`CHeaderCtrl`对象。  
  
 应用程序应还原选择的显示上下文中提供的所有图形设备接口 (GDI) 对象`lpDrawItemStruct`之前此成员函数将终止。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_6.cpp)]  
  
##  <a name="editfilter"></a>CHeaderCtrl::EditFilter  
 开始编辑标头控件的指定的筛选器。  
  
```  
BOOL EditFilter(
    int nColumn,  
    BOOL bDiscardChanges);
```  
  
### <a name="parameters"></a>参数  
 `nColumn`  
 要编辑的列。  
  
 `bDiscardChanges`  
 一个值，指定如何处理用户的编辑更改，如果用户正在编辑筛选器时[HDM_EDITFILTER](http://msdn.microsoft.com/library/windows/desktop/bb775312)发送消息。  
  
 指定`true`丢弃用户，所做的更改或`false`接受用户所做的更改。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法实现的行为的 Win32 消息[HDM_EDITFILTER](http://msdn.microsoft.com/library/windows/desktop/bb775312)中所述， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]  
  
##  <a name="getbitmapmargin"></a>CHeaderCtrl::GetBitmapMargin  
 检索的边距标题控件中的位图的宽度。  
  
```  
int GetBitmapMargin() const;  
```  
  
### <a name="return-value"></a>返回值  
 以像素为单位的位图边距的宽度。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[HDM_GETBITMAPMARGIN](http://msdn.microsoft.com/library/windows/desktop/bb775314)中所述， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 8](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_8.cpp)]  
  
##  <a name="getfocuseditem"></a>CHeaderCtrl::GetFocusedItem  
 获取在当前的标头控件具有焦点的项的索引。  
  
```  
int GetFocusedItem() const;  
```  
  
### <a name="return-value"></a>返回值  
 具有焦点的标题项的从零开始的索引。  
  
### <a name="remarks"></a>备注  
 此方法可发送[HDM_GETFOCUSEDITEM](http://msdn.microsoft.com/library/windows/desktop/bb775330)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_headerCtrl`，即用于访问当前的标头控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s&#4; 6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例演示`SetFocusedItem`和`GetFocusedItem`方法。 前面的代码部分，我们使用五个列创建标题控件。 但是，您可以拖动列分隔符，以便列不可见。 以下示例设置，然后确认已为焦点项的最后一个列标题。  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s&#4; 4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]  
  
##  <a name="getimagelist"></a>CHeaderCtrl::GetImageList  
 检索图像列表用于标题控件中绘制标头项的句柄。  
  
```  
CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向的指针[CImageList](../../mfc/reference/cimagelist-class.md)对象。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[HDM_GETIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb775332)中所述， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 `CImageList`对象向其返回的指针点是临时对象，并在下一步的空闲时间处理过程中删除。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 9](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_11.cpp)]  
  
##  <a name="getitem"></a>Cheaderctrl:: Getitem  
 检索有关的标头控件项信息。  
  
```  
BOOL GetItem(
    int nPos,  
    HDITEM* pHeaderItem) const;  
```  
  
### <a name="parameters"></a>参数  
 `nPos`  
 指定要检索的项的从零开始索引。  
  
 `pHeaderItem`  
 指向[HDITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247)接收新项的结构。 此结构用于`InsertItem`和`SetItem`成员函数。 在中设置任何标志**掩码**元素确保中的相应元素的值返回时正确填写。 如果**掩码**元素设置为零中的其他结构元素的值是无意义。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 10](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_12.cpp)]  
  
##  <a name="getitemcount"></a>CHeaderCtrl::GetItemCount  
 检索在标头控件中项的计数。  
  
```  
int GetItemCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则标头控件项目数否则为-1。  
  
### <a name="example"></a>示例  
  请参阅示例[CHeaderCtrl::DeleteItem](#deleteitem)。  
  
##  <a name="getitemdropdownrect"></a>CHeaderCtrl::GetItemDropDownRect  
 获取当前的标头控件中的标头项下拉按钮的边框。  
  
```  
BOOL GetItemDropDownRect(
    int iItem,   
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `iItem`|其样式的标头项的从零开始索引`HDF_SPLITBUTTON`。 有关详细信息，请参阅`fmt`的成员[HDITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247)结构。|  
|[out] `lpRect`|指向[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)接收边界的矩形信息的结构。|  
  
### <a name="return-value"></a>返回值  
 `true`如果成功，则此函数否则为`false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[HDM_GETITEMDROPDOWNRECT](http://msdn.microsoft.com/library/windows/desktop/bb775339)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_headerCtrl`，即用于访问当前的标头控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s&#4; 6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例演示`GetItemDropDownRect`方法。 前面的代码部分，我们使用五个列创建标题控件。 下面的代码示例的位置周围绘制三维矩形标头下拉按钮为保留的第一列。  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s&#4; 2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]  
  
##  <a name="getitemrect"></a>CHeaderCtrl::GetItemRect  
 检索给定标头控件中项的边框。  
  
```  
BOOL GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 标头控件项的从零开始索引。  
  
 `lpRect`  
 指向的地址的指针[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)接收边界的矩形信息的结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法实现的行为的 Win32 消息[HDM_GETITEMRECT](http://msdn.microsoft.com/library/windows/desktop/bb775341)中所述， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getorderarray"></a>Cheaderctrl:: Getorderarray  
 检索标头控件中的项的从左到右顺序。  
  
```  
BOOL GetOrderArray(
    LPINT piArray,  
    int iCount);
```  
  
### <a name="parameters"></a>参数  
 `piArray`  
 指向在标头控件中，按它们的出现从左到右的顺序接收项的索引值的缓冲区的地址的指针。  
  
 `iCount`  
 标头控件项的数目。 必须为非负数。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[HDM_GETORDERARRAY](http://msdn.microsoft.com/library/windows/desktop/bb775343)中所述， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 它可用于支持标头项排序。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]  
  
##  <a name="getoverflowrect"></a>CHeaderCtrl::GetOverflowRect  
 获取当前的标头控件的溢出按钮的边框。  
  
```  
BOOL GetOverflowRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[out] `lpRect`|指向[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)接收边界的矩形信息的结构。|  
  
### <a name="return-value"></a>返回值  
 `true`如果成功，则此函数否则为`false`。  
  
### <a name="remarks"></a>备注  
 如果标头控件包含比可同时显示多个项，该控件可以显示滚动溢出按钮的不可见的项。 标头控件必须具有`HDS_OVERFLOW`和`HDF_SPLITBUTTON`样式以显示溢出按钮。 边界的矩形包含溢出按钮，以及存在仅当显示溢出按钮。 有关详细信息，请参阅[标头控件样式](http://msdn.microsoft.com/library/windows/desktop/bb775241)。  
  
 此方法可发送[HDM_GETOVERFLOWRECT](http://msdn.microsoft.com/library/windows/desktop/bb775345)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_headerCtrl`，即用于访问当前的标头控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s&#4; 6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例演示`GetOverflowRect`方法。 前面的代码部分，我们使用五个列创建标题控件。 但是，您可以拖动列分隔符，以便列不可见。 如果看不到某些列，标头控件绘制溢出按钮。 下面的代码示例的溢出按钮的位置绘制带 3D 矩形。  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s&#4; 3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]  
  
##  <a name="hittest"></a>CHeaderCtrl::HitTest  
 确定哪些标头项，如果有的话，位于指定点处。  
  
```  
int HitTest(LPHDHITTESTINFO* phdhti);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in, out] `phdhti`|指向[HDHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb775245)结构，它指定要测试的点并接收测试的结果。|  
  
### <a name="return-value"></a>返回值  
 标头项，如果有的话，位于指定位置; 的从零开始索引否则为-1。  
  
### <a name="remarks"></a>备注  
 此方法可发送[HDM_HITTEST](http://msdn.microsoft.com/library/windows/desktop/bb775349)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_headerCtrl`，即用于访问当前的标头控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s&#4; 6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例演示`HitTest`方法。 此代码示例的前面部分，我们使用五个列创建标题控件。 但是，您可以拖动列分隔符，以便列不可见。 此示例将报告列的索引，如果可见和-1，如果列不可见。  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s&#4; 1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_16.cpp)]  
  
##  <a name="insertitem"></a>Cheaderctrl:: Insertitem  
 将新项插入到指定索引处的标头控件。  
  
```  
int InsertItem(
    int nPos,  
    HDITEM* phdi);
```  
  
### <a name="parameters"></a>参数  
 `nPos`  
 要插入的项的索引（索引从零开始）。 如果值为零，标头控件的开头插入项。 如果值大于最大值，在标头控件的末尾插入项。  
  
 *phdi*  
 指向[HDITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247)结构，它包含有关要插入的项的信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则新的项的索引否则为-1。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]  
  
##  <a name="layout"></a>CHeaderCtrl::Layout  
 检索的大小和位置标头控件的给定矩形范围内。  
  
```  
BOOL Layout(HDLAYOUT* pHeaderLayout);
```  
  
### <a name="parameters"></a>参数  
 *pHeaderLayout*  
 指向[HDLAYOUT](http://msdn.microsoft.com/library/windows/desktop/bb775249)结构，其中包含用于设置的大小和位置标头控件的信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数用于确定相应的维度的新的标头控件，是以占据给定的矩形。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]  
  
##  <a name="ordertoindex"></a>Cheaderctrl:: Ordertoindex  
 检索基于在标头控件中的顺序的项目的索引值。  
  
```  
int OrderToIndex(int nOrder) const;  
```  
  
### <a name="parameters"></a>参数  
 *nOrder*  
 出现在标头控件中，从左到右的项的从零开始顺序。  
  
### <a name="return-value"></a>返回值  
 基于在标头控件中的顺序的项的索引。 索引将从左到右、 从 0 开始计数。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 宏[HDM_ORDERTOINDEX](http://msdn.microsoft.com/library/windows/desktop/bb775355)中所述， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 它可用于支持标头项排序。  
  
##  <a name="setbitmapmargin"></a>CHeaderCtrl::SetBitmapMargin  
 标题控件中设置的边距的位图的宽度。  
  
```  
int SetBitmapMargin(int nWidth);
```  
  
### <a name="parameters"></a>参数  
 `nWidth`  
 指定以像素为单位，距环绕现有标头控件中的位图的宽度。  
  
### <a name="return-value"></a>返回值  
 以像素为单位的位图边距的宽度。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[HDM_SETBITMAPMARGIN](http://msdn.microsoft.com/library/windows/desktop/bb775357)中所述， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]  
  
##  <a name="setfilterchangetimeout"></a>CHeaderCtrl::SetFilterChangeTimeout  
 中的筛选器属性发生更改的时间与发布之间的超时间隔设置[HDN_FILTERCHANGE](http://msdn.microsoft.com/library/windows/desktop/bb775277)通知。  
  
```  
int SetFilterChangeTimeout(DWORD dwTimeOut);
```  
  
### <a name="parameters"></a>参数  
 *dwTimeOut*  
 超时值，以毫秒为单位。  
  
### <a name="return-value"></a>返回值  
 正在修改的筛选器控件索引。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[HDM_SETFILTERCHANGETIMEOUT](http://msdn.microsoft.com/library/windows/desktop/bb775359)中所述， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]  
  
##  <a name="setfocuseditem"></a>CHeaderCtrl::SetFocusedItem  
 将焦点设置到当前的标头控件中指定的标头项。  
  
```  
BOOL SetFocusedItem(int iItem);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `iItem`|标头项的从零开始索引。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[HDM_SETFOCUSEDITEM](http://msdn.microsoft.com/library/windows/desktop/bb775361)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_headerCtrl`，即用于访问当前的标头控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s&#4; 6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例演示`SetFocusedItem`和`GetFocusedItem`方法。 前面的代码部分，我们使用五个列创建标题控件。 但是，您可以拖动列分隔符，以便列不可见。 以下示例设置，然后确认已为焦点项的最后一个列标题。  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s&#4; 4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]  
  
##  <a name="sethotdivider"></a>CHeaderCtrl::SetHotDivider  
 标头项以指示手动之间的分隔线将拖动的更改和标头项的 drop。  
  
```  
int SetHotDivider(CPoint pt);  
int SetHotDivider(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 `pt`  
 指针的位置。 标头控件突出显示相应的分隔符基于指针的位置。  
  
 `nIndex`  
 突出显示分隔符的索引。  
  
### <a name="return-value"></a>返回值  
 突出显示分隔符的索引。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[HDM_SETHOTDIVIDER](http://msdn.microsoft.com/library/windows/desktop/bb775363)中所述， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 提供它是为了支持标头项拖放。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CHeaderCtrl # 16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]  
  
##  <a name="setimagelist"></a>CHeaderCtrl::SetImageList  
 将图像列表分配到标题控件中。  
  
```  
CImageList* SetImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>参数  
 `pImageList`  
 指向的指针`CImageList`对象，其中包含要分配给标头控件的图像列表。  
  
### <a name="return-value"></a>返回值  
 指向的指针[CImageList](../../mfc/reference/cimagelist-class.md)以前分配给标头控件的对象。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[HDM_SETIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb775365)中所述， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 `CImageList`对象向其返回的指针点是临时对象，并在下一步的空闲时间处理过程中删除。  
  
### <a name="example"></a>示例  
  请参阅示例[CHeaderCtrl::GetImageList](#getimagelist)。  
  
##  <a name="setitem"></a>Cheaderctrl:: Setitem  
 标题控件中设置指定的项的属性。  
  
```  
BOOL SetItem(
    int nPos,  
    HDITEM* pHeaderItem);
```  
  
### <a name="parameters"></a>参数  
 `nPos`  
 要操作的项的从零开始的索引。  
  
 `pHeaderItem`  
 指向[HDITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247)结构，其中包含新的项目的信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
  请参阅示例[cheaderctrl:: Getitem](#getitem)。  
  
##  <a name="setorderarray"></a>Cheaderctrl:: Setorderarray  
 标题控件中设置的项的从左到右的顺序。  
  
```  
BOOL SetOrderArray(
    int iCount,  
    LPINT piArray);
```  
  
### <a name="parameters"></a>参数  
 `iCount`  
 标头控件项的数目。  
  
 `piArray`  
 指向在标头控件中，按它们的出现从左到右的顺序接收项的索引值的缓冲区的地址的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 宏[HDM_SETORDERARRAY](http://msdn.microsoft.com/library/windows/desktop/bb775369)中所述， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 它可用于支持标头项排序。  
  
### <a name="example"></a>示例  
  请参阅示例[cheaderctrl:: Getorderarray](#getorderarray)。  
  
## <a name="see-also"></a>另请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CTabCtrl 类](../../mfc/reference/ctabctrl-class.md)   
 [CListCtrl 类](../../mfc/reference/clistctrl-class.md)   
 [CImageList 类](../../mfc/reference/cimagelist-class.md)

