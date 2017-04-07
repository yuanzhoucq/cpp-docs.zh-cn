---
title: "CComboBox 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComboBox
- AFXWIN/CComboBox
- AFXWIN/CComboBox::CComboBox
- AFXWIN/CComboBox::AddString
- AFXWIN/CComboBox::Clear
- AFXWIN/CComboBox::CompareItem
- AFXWIN/CComboBox::Copy
- AFXWIN/CComboBox::Create
- AFXWIN/CComboBox::Cut
- AFXWIN/CComboBox::DeleteItem
- AFXWIN/CComboBox::DeleteString
- AFXWIN/CComboBox::Dir
- AFXWIN/CComboBox::DrawItem
- AFXWIN/CComboBox::FindString
- AFXWIN/CComboBox::FindStringExact
- AFXWIN/CComboBox::GetComboBoxInfo
- AFXWIN/CComboBox::GetCount
- AFXWIN/CComboBox::GetCueBanner
- AFXWIN/CComboBox::GetCurSel
- AFXWIN/CComboBox::GetDroppedControlRect
- AFXWIN/CComboBox::GetDroppedState
- AFXWIN/CComboBox::GetDroppedWidth
- AFXWIN/CComboBox::GetEditSel
- AFXWIN/CComboBox::GetExtendedUI
- AFXWIN/CComboBox::GetHorizontalExtent
- AFXWIN/CComboBox::GetItemData
- AFXWIN/CComboBox::GetItemDataPtr
- AFXWIN/CComboBox::GetItemHeight
- AFXWIN/CComboBox::GetLBText
- AFXWIN/CComboBox::GetLBTextLen
- AFXWIN/CComboBox::GetLocale
- AFXWIN/CComboBox::GetMinVisible
- AFXWIN/CComboBox::GetTopIndex
- AFXWIN/CComboBox::InitStorage
- AFXWIN/CComboBox::InsertString
- AFXWIN/CComboBox::LimitText
- AFXWIN/CComboBox::MeasureItem
- AFXWIN/CComboBox::Paste
- AFXWIN/CComboBox::ResetContent
- AFXWIN/CComboBox::SelectString
- AFXWIN/CComboBox::SetCueBanner
- AFXWIN/CComboBox::SetCurSel
- AFXWIN/CComboBox::SetDroppedWidth
- AFXWIN/CComboBox::SetEditSel
- AFXWIN/CComboBox::SetExtendedUI
- AFXWIN/CComboBox::SetHorizontalExtent
- AFXWIN/CComboBox::SetItemData
- AFXWIN/CComboBox::SetItemDataPtr
- AFXWIN/CComboBox::SetItemHeight
- AFXWIN/CComboBox::SetLocale
- AFXWIN/CComboBox::SetMinVisibleItems
- AFXWIN/CComboBox::SetTopIndex
- AFXWIN/CComboBox::ShowDropDown
dev_langs:
- C++
helpviewer_keywords:
- combo boxes, CComboBox objects
- CComboBox class
ms.assetid: 4e73b5df-0d2e-4658-9706-38133fb10513
caps.latest.revision: 25
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
ms.openlocfilehash: 5328c245e0d662c4701042b37c16870d6b1e33c7
ms.lasthandoff: 02/24/2017

---
# <a name="ccombobox-class"></a>CComboBox 类
提供 Windows 组合框功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CComboBox : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CComboBox::CComboBox](#ccombobox)|构造 `CComboBox` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Ccombobox::](#addstring)|将字符串添加到组合框，或在列表框的排序位置的列表框中列表的末尾**CBS_SORT**样式。|  
|[CComboBox::Clear](#clear)|（清除） 中删除当前选定内容，如果有的话，编辑控件中。|  
|[CComboBox::CompareItem](#compareitem)|由框架来确定新列表项的已排序的所有者描述组合框中的相对位置调用。|  
|[CComboBox::Copy](#copy)|如果有的话，到剪贴板中复制当前的选择， **CF_TEXT**格式。|  
|[CComboBox::Create](#create)|创建组合框，并将其附加到`CComboBox`对象。|  
|[CComboBox::Cut](#cut)|（剪切） 中删除当前选定内容，如果有，在编辑控件，并将复制到剪贴板中删除的文本**CF_TEXT**格式。|  
|[CComboBox::DeleteItem](#deleteitem)|当从一个所有者描述的组合框删除列表项时，由框架调用。|  
|[CComboBox::DeleteString](#deletestring)|从组合框的列表框中删除一个字符串。|  
|[CComboBox::Dir](#dir)|将文件名称的列表添加到组合框的列表框中。|  
|[CComboBox::DrawItem](#drawitem)|由框架当所有者描述的组合框中更改的可视方位时调用。|  
|[CComboBox::FindString](#findstring)|查找第一个字符串，其中包含一个组合框的列表框中指定的前缀。|  
|[CComboBox::FindStringExact](#findstringexact)|查找第一个列表框中的字符串 （组合框） 与指定的字符串匹配。|  
|[CComboBox::GetComboBoxInfo](#getcomboboxinfo)|检索有关的信息`CComboBox`对象。|  
|[CComboBox::GetCount](#getcount)|检索一个组合框的列表框中的项的数目。|  
|[CComboBox::GetCueBanner](#getcuebanner)|获取组合框控件显示的提示文本。|  
|[CComboBox::GetCurSel](#getcursel)|检索当前选定项的索引，如果任何一个组合框的列表框中。|  
|[CComboBox::GetDroppedControlRect](#getdroppedcontrolrect)|检索一个下拉组合框的可见 （向下拖放到） 列表框中的屏幕坐标。|  
|[CComboBox::GetDroppedState](#getdroppedstate)|确定下拉组合框列表框是否可见的 （向下删除）。|  
|[CComboBox::GetDroppedWidth](#getdroppedwidth)|检索最小允许组合框的下拉列表框中部分的宽度。|  
|[CComboBox::GetEditSel](#geteditsel)|获取编辑控件的组合框中当前所选内容的起始和结束字符位置。|  
|[CComboBox::GetExtendedUI](#getextendedui)|确定一个组合框是否具有默认用户界面或扩展的用户界面。|  
|[CComboBox::GetHorizontalExtent](#gethorizontalextent)|返回以像素为单位可以水平滚动的组合框的列表框中部分的宽度。|  
|[CComboBox::GetItemData](#getitemdata)|检索与指定的组合框项相关联的应用程序提供 32 位值。|  
|[CComboBox::GetItemDataPtr](#getitemdataptr)|检索与指定的组合框项相关联的应用程序提供 32 位指针。|  
|[CComboBox::GetItemHeight](#getitemheight)|检索在组合框中的列表项的高度。|  
|[CComboBox::GetLBText](#getlbtext)|从组合框的列表框中获取一个字符串。|  
|[CComboBox::GetLBTextLen](#getlbtextlen)|获取组合框的列表框中字符串的长度。|  
|[CComboBox::GetLocale](#getlocale)|检索一个组合框的区域设置标识符。|  
|[CComboBox::GetMinVisible](#getminvisible)|获取当前的组合框下拉列表中的可见项的最小数量。|  
|[CComboBox::GetTopIndex](#gettopindex)|在组合框的列表框中部分返回的第一个可见项的索引。|  
|[CComboBox::InitStorage](#initstorage)|预先分配为项目和组合框的列表框中部分中的字符串的内存块的能力。|  
|[CComboBox::InsertString](#insertstring)|将字符串插入组合框的列表框。|  
|[CComboBox::LimitText](#limittext)|限制用户可以输入到组合框中编辑控件的文本的长度。|  
|[CComboBox::MeasureItem](#measureitem)|由框架来确定组合框大小创建一个所有者描述的组合框时调用。|  
|[CComboBox::Paste](#paste)|将数据从剪贴板插入到当前光标位置的编辑控件。 只有当剪贴板包含中的数据插入数据**CF_TEXT**格式。|  
|[CComboBox::ResetContent](#resetcontent)|删除所有项从列表框中，并编辑一个组合框控件。|  
|[CComboBox::SelectString](#selectstring)|搜索字符串的组合框的列表框中，如果找到该字符串，列表框中选择该字符串，并将字符串复制到编辑控件。|  
|[CComboBox::SetCueBanner](#setcuebanner)|设置为组合框控件显示的提示文本。|  
|[CComboBox::SetCurSel](#setcursel)|组合框的列表框中选择一个字符串。|  
|[CComboBox::SetDroppedWidth](#setdroppedwidth)|设置最小允许组合框的下拉列表框中部分的宽度。|  
|[CComboBox::SetEditSel](#seteditsel)|编辑控件的组合框中选择字符。|  
|[CComboBox::SetExtendedUI](#setextendedui)|选择默认用户界面或具有一个组合框的扩展的用户界面**CBS_DROPDOWN**或**CBS_DROPDOWNLIST**样式。|  
|[CComboBox::SetHorizontalExtent](#sethorizontalextent)|以像素为单位可以水平滚动的组合框的列表框中部分设置的宽度。|  
|[CComboBox::SetItemData](#setitemdata)|设置与组合框中指定的项相关联的 32 位值。|  
|[CComboBox::SetItemDataPtr](#setitemdataptr)|设置与组合框中指定的项关联的 32 位指针。|  
|[CComboBox::SetItemHeight](#setitemheight)|设置组合框或组合框的编辑控件 （或静态文本） 部分的高度中列表项的高度。|  
|[CComboBox::SetLocale](#setlocale)|设置组合框的区域设置标识符。|  
|[CComboBox::SetMinVisibleItems](#setminvisibleitems)|设置当前的组合框的下拉列表中的可见项的最小数量。|  
|[CComboBox::SetTopIndex](#settopindex)|指示组合框以在顶部显示具有指定索引的项的列表框中部分。|  
|[CComboBox::ShowDropDown](#showdropdown)|显示或隐藏了一个组合框的列表框中**CBS_DROPDOWN**或**CBS_DROPDOWNLIST**样式。|  
  
## <a name="remarks"></a>备注  
 组合框包含与静态控件或编辑控件组合在一个列表框。 该控件的列表框中部分可能会显示在所有时间或可能仅下拉当用户选择在控件旁边的下拉箭头。  
  
 在列表框中当前选定的项 （如果有） 显示在静态或编辑控件。 此外，如果对组合框下拉列表样式，用户可以在列表中，键入某一项的初始字符和列表框中，如果可见，请将突出显示与该初始字符的下一项。  
  
 下表比较了三个组合框[样式](../../mfc/reference/combo-box-styles.md)。  
  
|样式|当列表框中是可见的|静态或编辑控件|  
|-----------|-------------------------------|-----------------------------|  
|简单|Always|Edit|  
|Drop-down|向下删除时|Edit|  
|下拉列表|向下删除时|Static|  
  
 您可以创建`CComboBox`对象通过对话框模板中或直接在您的代码。 在这两种情况下，第一次调用构造函数`CComboBox`构造`CComboBox`对象; 然后，调用[创建](#create)成员函数来创建控件并将其附加到`CComboBox`对象。  
  
 如果你想要处理 Windows 通知消息发送到其父组合框 (通常派生自该类`CDialog`)，将消息映射条目和消息处理程序成员函数添加到每个消息的父类。  
  
 每个消息映射条目采用以下形式︰  
  
 **ON_**Notification **(**`id`**,**`memberFxn`**)**  
  
 其中`id`指定发送通知的组合框控件的子窗口 ID 和`memberFxn`留下来处理通知的父成员函数的名称。  
  
 父元素的函数原型是，如下所示︰  
  
 **afx_msg** `void` `memberFxn` **( );**  
  
 无法预测会发送某些通知的顺序。 具体而言， **CBN_SELCHANGE**之前或之后，可能会出现通知**CBN_CLOSEUP**通知。  
  
 潜在的消息映射条目如下所示︰  
  
- **ON_CBN_CLOSEUP** (Windows 3.1 及更高版本。)组合框的列表框中已关闭。 此通知消息不会发送具有一个组合框进行[CBS_SIMPLE](../../mfc/reference/combo-box-styles.md)样式。  
  
- **ON_CBN_DBLCLK**用户双击某个字符串的组合框的列表框中。 此通知消息仅发送与组合框**CBS_SIMPLE**样式。 使用组合框[CBS_DROPDOWN](../../mfc/reference/combo-box-styles.md)或[CBS_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md)样式，不能出现一次双击因为一次单击隐藏列表框。  
  
- **ON_CBN_DROPDOWN**即将下拉组合框的列表框 （让用户看到）。 此通知消息可能仅对组合框与**CBS_DROPDOWN**或**CBS_DROPDOWNLIST**样式。  
  
- **ON_CBN_EDITCHANGE**用户已执行可能更改组合框的编辑控件部分中的文本的操作。 与不同**CBN_EDITUPDATE**消息，即可发送此消息在 Windows 更新屏幕。 它不会发送该组合框是否**CBS_DROPDOWNLIST**样式。  
  
- **ON_CBN_EDITUPDATE**组合框的编辑控件部分即将显示更改后的文本。 该控件设置文本格式之后，但之前显示的文本，即可发送此通知消息。 它不会发送该组合框是否**CBS_DROPDOWNLIST**样式。  
  
- **ON_CBN_ERRSPACE**组合框无法分配足够的内存来满足特定的请求。  
  
- **ON_CBN_SELENDCANCEL** (Windows 3.1 及更高版本。)指示应取消用户的选择。 用户单击某项，然后单击另一个窗口或控件，若要隐藏的组合框的列表框。 此通知消息发送之前**CBN_CLOSEUP**通知消息，以指示应忽略用户的选择。 **CBN_SELENDCANCEL**或**CBN_SELENDOK**发送通知消息即使**CBN_CLOSEUP**不发送通知消息 (在带有的组合框的情况下为**CBS_SIMPLE**样式)。  
  
- **ON_CBN_SELENDOK**在用户选择一项，然后按 ENTER 键或单击向下箭头键，若要隐藏的组合框的列表框。 此通知消息发送之前**CBN_CLOSEUP**消息，以指示该用户的所选内容应视为有效。 **CBN_SELENDCANCEL**或**CBN_SELENDOK**发送通知消息即使**CBN_CLOSEUP**不发送通知消息 (在带有的组合框的情况下为**CBS_SIMPLE**样式)。  
  
- **ON_CBN_KILLFOCUS**组合框正在失去输入的焦点。  
  
- **ON_CBN_SELCHANGE**中组合框的列表框中选择的是将要应用用户的列表框中单击或使用箭头键更改所选内容更改。 组合框中编辑控件中的文本在处理此消息时，仅通过检索`GetLBText`或其他类似的函数。 `GetWindowText`不能使用。  
  
- **ON_CBN_SETFOCUS**组合框中接收到输入的焦点。  
  
 如果您创建`CComboBox`（通过对话框资源） 的对话框内的对象`CComboBox`当用户关闭对话框中，将自动销毁对象。  
  
 如果您嵌入`CComboBox`另一个窗口中的对象的对象，不需要将其销毁。 如果您创建`CComboBox`对象在堆栈上，自动被销毁。 如果您创建`CComboBox`使用堆上的对象**新**函数，则必须调用**删除**上要销毁 Windows 组合框时对其进行销毁的对象。  
  
 **请注意**如果你想要处理`WM_KEYDOWN`和`WM_CHAR`消息，必须为子类组合框的编辑和列表框控件中，派生类从`CEdit`和`CListBox`，并将这些消息的处理程序添加到派生的类。 有关详细信息，请参阅[http://support.microsoft.com/default.aspxscid=kb;en-us;Q174667](http://support.microsoft.com/default.aspxscid=kb;en-us;q174667)和[CWnd::SubclassWindow](../../mfc/reference/cwnd-class.md#subclasswindow)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CComboBox`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="addstring"></a>Ccombobox::  
 将一个字符串添加到组合框的列表框中。  
  
```  
int AddString(LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>参数  
 `lpszString`  
 指向要添加的以 null 结尾的字符串。  
  
### <a name="return-value"></a>返回值  
 如果返回值是大于或等于 0，则到列表框中的字符串的从零开始的索引。 返回值是**CB_ERR**如果发生错误; 返回值是**CB_ERRSPACE**如果没有足够空间可用于存储新的字符串。  
  
### <a name="remarks"></a>备注  
 如果不通过创建列表框[CBS_SORT](../../mfc/reference/combo-box-styles.md)样式，则字符串添加到列表的末尾。 否则为该字符串插入到列表中，并对列表进行排序。  
  
> [!NOTE]
>  Windows **ComboBoxEx** 控件不支持此函数。 此控件的详细信息，请参阅[ComboBoxEx 控件](http://msdn.microsoft.com/library/windows/desktop/bb775738)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 若要在列表中的特定位置插入一个字符串，请使用[InsertString](#insertstring)成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&3;](../../mfc/reference/codesnippet/cpp/ccombobox-class_1.cpp)]  
  
##  <a name="ccombobox"></a>CComboBox::CComboBox  
 构造 `CComboBox` 对象。  
  
```  
CComboBox();
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&1;](../../mfc/reference/codesnippet/cpp/ccombobox-class_2.cpp)]  
  
##  <a name="clear"></a>CComboBox::Clear  
 （清除） 中删除当前选定内容，如果有的话，编辑控件的组合框中。  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>备注  
 若要删除当前所选内容并放置到剪贴板上已删除的内容，请使用[剪切](#cut)成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&4;](../../mfc/reference/codesnippet/cpp/ccombobox-class_3.cpp)]  
  
##  <a name="compareitem"></a>CComboBox::CompareItem  
 由框架来确定新项的已排序的所有者描述组合框的列表框中部分中的相对位置调用。  
  
```  
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpCompareItemStruct`  
 指向长指针[COMPAREITEMSTRUCT](../../mfc/reference/compareitemstruct-structure.md)结构。  
  
### <a name="return-value"></a>返回值  
 指示中所述的两个项目的相对位置`COMPAREITEMSTRUCT`结构。 它可以是任何以下值︰  
  
|值|含义|  
|-----------|-------------|  
|– 1|在第 2 项之前进行排序的第 1 项。|  
|0|第 1 项和第 2 项的排序相同。|  
|1|在项 2 之后，第 1 项进行排序。|  
  
 请参阅[CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)有关的说明`COMPAREITEMSTRUCT`。  
  
### <a name="remarks"></a>备注  
 默认情况下，此成员函数没有任何影响。 如果您创建具有一个所有者绘制的组合框**LBS_SORT**样式，您必须重写该成员函数以帮助框架添加到列表框中的新项进行排序。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&5;](../../mfc/reference/codesnippet/cpp/ccombobox-class_4.cpp)]  
  
##  <a name="copy"></a>CComboBox::Copy  
 如果有的话，组合框拖到剪贴板中的编辑控件中复制当前的选择， **CF_TEXT**格式。  
  
```  
void Copy();
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&6;](../../mfc/reference/codesnippet/cpp/ccombobox-class_5.cpp)]  
  
##  <a name="create"></a>CComboBox::Create  
 创建组合框，并将其附加到`CComboBox`对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 指定组合框的样式。 应用的任意组合[组合框样式](../../mfc/reference/combo-box-styles.md)的框。  
  
 `rect`  
 指向的位置和组合框的大小。 可以是[RECT 结构](../../mfc/reference/rect-structure1.md)或`CRect`对象。  
  
 `pParentWnd`  
 指定组合框的父窗口 (通常`CDialog`)。 它不能**NULL**。  
  
 `nID`  
 指定组合框控件 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 您构造`CComboBox`两个步骤中的对象。 首先，调用构造函数，然后调用**创建**，它创建 Windows 组合框，并将其附加到`CComboBox`对象。  
  
 当**创建**执行时，Windows 将发送[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)， [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)， [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)，和[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)消息到组合框。  
  
 默认情况下，通过处理这些消息的消息[OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)， [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)， [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)，和[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成员函数中`CWnd`基类。 若要扩展的默认消息处理，从派生类`CComboBox`、 将消息映射添加到新的类，并重写前面的消息处理程序成员函数。 重写`OnCreate`，例如，若要为新类执行所需的初始化。  
  
 将应用以下[窗口样式](../../mfc/reference/window-styles.md)向组合框控件。 :  
  
- **WS_CHILD**始终  
  
- **WS_VISIBLE**通常  
  
- **WS_DISABLED**很少  
  
- **WS_VSCROLL**若要添加垂直滚动的列表框中组合框  
  
- **WS_HSCROLL**若要添加水平滚动的列表框中组合框  
  
- **WS_GROUP**控件组合  
  
- **WS_TABSTOP**要包括在 tab 键顺序中的组合框  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&2;](../../mfc/reference/codesnippet/cpp/ccombobox-class_6.cpp)]  
  
##  <a name="cut"></a>CComboBox::Cut  
 删除 （剪切） 当前所选内容，如果任何组合框中编辑控制，并将复制到剪贴板中删除的文本**CF_TEXT**格式。  
  
```  
void Cut();
```  
  
### <a name="remarks"></a>备注  
 若要删除当前所选内容而无需将放到剪贴板中删除的文本，请调用[清除](#clear)成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&7;](../../mfc/reference/codesnippet/cpp/ccombobox-class_7.cpp)]  
  
##  <a name="deleteitem"></a>CComboBox::DeleteItem  
 当用户从所有者描述中删除项时由框架调用`CComboBox`对象或销毁组合框。  
  
```  
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpDeleteItemStruct`  
 向 Windows 的长指针[DELETEITEMSTRUCT](../../mfc/reference/deleteitemstruct-structure.md)结构，其中包含有关已删除的项的信息。 请参阅[CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem)有关此结构的说明。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现不执行任何操作。 重写此函数可根据需要重绘组合框。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&8;](../../mfc/reference/codesnippet/cpp/ccombobox-class_8.cpp)]  
  
##  <a name="deletestring"></a>CComboBox::DeleteString  
 删除位置中的项`nIndex`从组合框。  
  
```  
int DeleteString(UINT nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定要删除的字符串的索引。  
  
### <a name="return-value"></a>返回值  
 如果返回值是大于或等于 0，它是在列表中剩余的字符串的计数。 返回值是**CB_ERR**如果`nIndex`列表中指定索引大于项的数目。  
  
### <a name="remarks"></a>备注  
 后面的所有项`nIndex`现在将下移一个位置。 例如，如果组合框包含两个项，则删除的第一项将导致现在将在第一个位置中剩余项。 `nIndex`=&0; 的第一个位置中的项。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&9;](../../mfc/reference/codesnippet/cpp/ccombobox-class_9.cpp)]  
  
##  <a name="dir"></a>CComboBox::Dir  
 将文件名或驱动器的列表添加到组合框的列表框中。  
  
```  
int Dir(
    UINT attr,  
    LPCTSTR lpszWildCard);
```  
  
### <a name="parameters"></a>参数  
 `attr`  
 可以是任意组合的`enum`值中所述[cfile:: Getstatus](../../mfc/reference/cfile-class.md#getstatus)或以下值的任意组合︰  
  
- **DDL_READWRITE**可以读取或写入到文件。  
  
- **DDL_READONLY**可以读取但不是会写入到文件。  
  
- **DDL_HIDDEN**文件处于隐藏状态并且未出现在目录列表。  
  
- **DDL_SYSTEM**文件是系统文件。  
  
- **DDL_DIRECTORY**由指定的名称`lpszWildCard`指定的目录。  
  
- **DDL_ARCHIVE**存档文件。  
  
- **DDL_DRIVES**包括与指定的名称相匹配的所有驱动器`lpszWildCard`。  
  
- **DDL_EXCLUSIVE**独占标志。 如果设置了排他标志，仅指定类型的文件列出。 否则，除了"正常"文件列出指定类型的文件。  
  
 `lpszWildCard`  
 指向以文件规范字符串。 该字符串可以包含通配符 (例如，*。\*)。  
  
### <a name="return-value"></a>返回值  
 如果返回值是大于或等于 0，则最后一个文件名添加到列表中的从零开始的索引。 返回值是**CB_ERR**如果发生错误; 返回值是**CB_ERRSPACE**如果没有足够空间可用于存储新的字符串。  
  
### <a name="remarks"></a>备注  
 Windows **ComboBoxEx** 控件不支持此函数。 此控件的详细信息，请参阅[ComboBoxEx 控件](http://msdn.microsoft.com/library/windows/desktop/bb775738)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&10;](../../mfc/reference/codesnippet/cpp/ccombobox-class_10.cpp)]  
  
##  <a name="drawitem"></a>CComboBox::DrawItem  
 由框架在所有者绘制组合框中更改的可视方位时调用。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpDrawItemStruct`  
 一个指向[DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md)结构，其中包含有关所需的绘图类型的信息。  
  
### <a name="remarks"></a>备注  
 **ItemAction**的成员`DRAWITEMSTRUCT`结构定义要执行的绘制操作。 请参阅[CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)有关此结构的说明。  
  
 默认情况下，此成员函数没有任何影响。 重写该成员函数以实现所有者描述的绘图`CComboBox`对象。 此成员函数将终止之前，该应用程序应还原选择用于显示上下文中提供的所有图形设备接口 (GDI) 对象`lpDrawItemStruct`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&11;](../../mfc/reference/codesnippet/cpp/ccombobox-class_11.cpp)]  
  
##  <a name="findstring"></a>CComboBox::FindString  
 发现，但不会选择第一个字符串，其中包含一个组合框的列表框中指定的前缀。  
  
```  
int FindString(
    int nStartAfter,  
    LPCTSTR lpszString) const;  
```  
  
### <a name="parameters"></a>参数  
 `nStartAfter`  
 包含要搜索的第一项之前的项的从零开始索引。 当搜索到达列表框的底部时，它将继续从列表框的顶部返回由指定的项`nStartAfter`。 如果为 –&1;，从一开始搜索整个列表框。  
  
 `lpszString`  
 指向以 null 结尾的字符串，其中包含要搜索的前缀。 搜索不区分大小写，因此此字符串可以包含任何的大写和小写字母组合。  
  
### <a name="return-value"></a>返回值  
 如果返回值是大于或等于 0，则匹配项的从零开始索引。 它是**CB_ERR**如果搜索未成功。  
  
### <a name="remarks"></a>备注  
 Windows **ComboBoxEx** 控件不支持此函数。 此控件的详细信息，请参阅[ComboBoxEx 控件](http://msdn.microsoft.com/library/windows/desktop/bb775738)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&12;](../../mfc/reference/codesnippet/cpp/ccombobox-class_12.cpp)]  
  
##  <a name="findstringexact"></a>CComboBox::FindStringExact  
 调用`FindStringExact`成员函数来查找第一个列表框中 （在组合框） 与匹配的字符串中指定的字符串`lpszFind`。  
  
```  
int FindStringExact(
    int nIndexStart,  
    LPCTSTR lpszFind) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndexStart`  
 指定要搜索的第一项之前的项的从零开始索引。 当搜索到达列表框的底部时，它将继续从列表框的顶部返回由指定的项`nIndexStart`。 如果`nIndexStart`为 –&1;，从一开始搜索整个列表框。  
  
 `lpszFind`  
 指向以 null 结尾的字符串来搜索。 此字符串可以包含完整的文件名，包括扩展名。 搜索不区分大小写，因此此字符串可以包含任何的大写和小写字母组合。  
  
### <a name="return-value"></a>返回值  
 匹配项的从零开始的索引或**CB_ERR**如果搜索未成功。  
  
### <a name="remarks"></a>备注  
 如果使用组合框但没有创建了一个所有者绘制样式[CBS_HASSTRINGS](../../mfc/reference/combo-box-styles.md)样式，`FindStringExact`尝试匹配的值的双字值`lpszFind`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&13;](../../mfc/reference/codesnippet/cpp/ccombobox-class_13.cpp)]  
  
##  <a name="getcomboboxinfo"></a>CComboBox::GetComboBoxInfo  
 检索信息`CComboBox`对象。  
  
```  
BOOL GetComboBoxInfo(PCOMBOBOXINFO pcbi) const;  
```  
  
### <a name="parameters"></a>参数  
 *pcbi*  
 一个指向[COMBOBOXINFO](http://msdn.microsoft.com/library/windows/desktop/bb775798)结构。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**成功时， **FALSE**失败。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[CB_GETCOMBOBOXINFO](http://msdn.microsoft.com/library/windows/desktop/bb775839)消息，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getcount"></a>CComboBox::GetCount  
 调用此成员函数以检索在组合框的列表框中部分中的项的数目。  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 项的数目。 因此返回的计数是一个大于 （索引是从零开始） 的最后一项的索引值。 它是**CB_ERR**如果发生错误。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&14;](../../mfc/reference/codesnippet/cpp/ccombobox-class_14.cpp)]  
  
##  <a name="getcuebanner"></a>CComboBox::GetCueBanner  
 获取组合框控件显示的提示文本。  
  
```  
CString GetCueBanner() const;  
  
BOOL GetCueBanner(
    LPTSTR lpszText,   
    int cchText) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[out] `lpszText`|指向该缓冲区用于接收的提示标志文本指针。|  
|[in] `cchText`|缓冲区的大小，`lpszText`参数指向。|  
  
### <a name="return-value"></a>返回值  
 在第一个重载中， [CString](../../atl-mfc-shared/using-cstring.md)对象，其中包含的提示标志文本，如果存在; 否则为`CString`长度为零的对象。  
  
 - 或 -  
  
 在第二个重载中，`true`如果此方法成功，否则为`false`。  
  
### <a name="remarks"></a>备注  
 提示文本是组合框控件的输入区域中显示的提示。 直至用户提供输入，则显示的提示文本。  
  
 此方法可发送[CB_GETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb775843)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getcursel"></a>CComboBox::GetCurSel  
 调用该成员函数以确定选择哪一项组合框中。  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>返回值  
 组合框的列表框中当前选定项的从零开始的索引或**CB_ERR**如果未不选定任何项。  
  
### <a name="remarks"></a>备注  
 `GetCurSel`插入列表中返回一个索引。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&15;](../../mfc/reference/codesnippet/cpp/ccombobox-class_15.cpp)]  
  
##  <a name="getdroppedcontrolrect"></a>CComboBox::GetDroppedControlRect  
 调用`GetDroppedControlRect`成员函数以检索下拉组合框的可见 （删除下） 列表框中的屏幕坐标。  
  
```  
void GetDroppedControlRect(LPRECT lprect) const;  
```  
  
### <a name="parameters"></a>参数  
 *lprect*  
 指向[RECT 结构](../../mfc/reference/rect-structure1.md)，是否要接收坐标。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&16;](../../mfc/reference/codesnippet/cpp/ccombobox-class_16.cpp)]  
  
##  <a name="getdroppedstate"></a>CComboBox::GetDroppedState  
 调用`GetDroppedState`成员函数可确定下拉组合框列表框是否可见的 （向下删除）。  
  
```  
BOOL GetDroppedState() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果列表框是否可见，则非零值否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&17;](../../mfc/reference/codesnippet/cpp/ccombobox-class_17.cpp)]  
  
##  <a name="getdroppedwidth"></a>CComboBox::GetDroppedWidth  
 调用此函数可检索的最小的允许宽度，以像素为单位的组合框的列表框。  
  
```  
int GetDroppedWidth() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，允许最小的宽度，以像素为单位。否则为**CB_ERR**。  
  
### <a name="remarks"></a>备注  
 此函数仅适用于组合框[CBS_DROPDOWN](../../mfc/reference/combo-box-styles.md)或[CBS_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md)样式。  
  
 默认情况下，下拉列表框中允许的最小宽度为 0。 可以通过调用设置允许的最小宽度[SetDroppedWidth](#setdroppedwidth)。 当显示组合框的列表框中部分时，其宽度为较大的允许的最小宽度或组合框的宽度。  
  
### <a name="example"></a>示例  
  请参阅示例[SetDroppedWidth](#setdroppedwidth)。  
  
##  <a name="geteditsel"></a>CComboBox::GetEditSel  
 获取编辑控件的组合框中当前所选内容的起始和结束字符位置。  
  
```  
DWORD GetEditSel() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个 32 位值，包含高序位字中的选定内容结尾之后的低序位字中的起始位置和未选定的第一个字符的位置。 如果没有一个编辑控件，组合框上使用此函数**CB_ERR**返回。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&18;](../../mfc/reference/codesnippet/cpp/ccombobox-class_18.cpp)]  
  
##  <a name="getextendedui"></a>CComboBox::GetExtendedUI  
 调用`GetExtendedUI`成员函数，以确定一个组合框的默认用户界面或扩展的用户界面。  
  
```  
BOOL GetExtendedUI() const;  
```  
  
### <a name="return-value"></a>返回值  
 组合框具有扩展的用户界面中; 如果非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 可以通过以下方式确定扩展的用户界面︰  
  
-   单击静态控件将显示列表框中只为组合框[CBS_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md)样式。  
  
-   按向下箭头键显示列表框 （禁用 F4）。  
  
 在项目列表不可见 （箭头键处于禁用状态） 时，禁用静态控件中滚动。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&19;](../../mfc/reference/codesnippet/cpp/ccombobox-class_19.cpp)]  
  
##  <a name="gethorizontalextent"></a>CComboBox::GetHorizontalExtent  
 从组合框检索在组合框的列表框中部分可以进行水平滚动的像素宽度。  
  
```  
UINT GetHorizontalExtent() const;  
```  
  
### <a name="return-value"></a>返回值  
 组合框，以像素为单位的列表框中部分的可滚动的宽度。  
  
### <a name="remarks"></a>备注  
 这是仅适用于组合框的列表框中部分具有水平滚动条。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&20;](../../mfc/reference/codesnippet/cpp/ccombobox-class_20.cpp)]  
  
##  <a name="getitemdata"></a>CComboBox::GetItemData  
 检索与指定的组合框项相关联的应用程序提供 32 位值。  
  
```  
DWORD_PTR GetItemData(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 包含组合框的列表框中某项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 该项目，与关联的 32 位值或**CB_ERR**出错时。  
  
### <a name="remarks"></a>备注  
 32 位值可以设置有`dwItemData`参数[SetItemData](#setitemdata)成员函数调用。 使用`GetItemDataPtr`成员函数，如果要检索的 32 位值是一个指针 ( **void\***)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&21;](../../mfc/reference/codesnippet/cpp/ccombobox-class_21.cpp)]  
  
##  <a name="getitemdataptr"></a>CComboBox::GetItemDataPtr  
 检索与指定的组合框项作为指针关联的应用程序提供 32 位值 ( **void\***)。  
  
```  
void* GetItemDataPtr(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 包含组合框的列表框中某项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 检索一个指针，则返回 –&1;，如果发生错误。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&22;](../../mfc/reference/codesnippet/cpp/ccombobox-class_22.cpp)]  
  
##  <a name="getitemheight"></a>CComboBox::GetItemHeight  
 调用`GetItemHeight`成员函数以检索在组合框中的列表项的高度。  
  
```  
int GetItemHeight(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定组合框的高度是要检索的组件。 如果`nIndex`参数为 –&1;，就会检索该组合框的编辑控件 （或静态文本） 部分的高度。 如果在组合框中[CBS_OWNERDRAWVARIABLE](../../mfc/reference/combo-box-styles.md)样式，`nIndex`指定其高度是要检索的列表项的从零开始的索引。 否则为`nIndex`应设置为 0。  
  
### <a name="return-value"></a>返回值  
 以像素为单位的组合框中指定的项高度。 返回值是 **CB_ERR** 如果发生错误。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox 第&23;](../../mfc/reference/codesnippet/cpp/ccombobox-class_23.cpp)]  
  
##  <a name="getlbtext"></a>CComboBox::GetLBText  
 从组合框的列表框中获取一个字符串。  
  
```  
int GetLBText(
    int nIndex,  
    LPTSTR lpszText) const;  
  
void GetLBText(
    int nIndex,  
    CString& rString) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 包含要复制的列表框中字符串的从零开始的索引。  
  
 `lpszText`  
 指向将接收该字符串的缓冲区。 缓冲区必须具有足够的空间的字符串和终止 null 字符。  
  
 `rString`  
 对引用`CString`。  
  
### <a name="return-value"></a>返回值  
 不包括终止 null 字符的字符串的长度 （以字节为单位）。 如果`nIndex`未指定一个有效的索引，则返回值是**CB_ERR**。  
  
### <a name="remarks"></a>备注  
 此成员的第二种形式函数填充`CString`用项的文本的对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&24;](../../mfc/reference/codesnippet/cpp/ccombobox-class_24.cpp)]  
  
##  <a name="getlbtextlen"></a>CComboBox::GetLBTextLen  
 获取组合框的列表框中字符串的长度。  
  
```  
int GetLBTextLen(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 包含列表框中字符串的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 以字节为单位，不包括终止 null 字符的字符串的长度。 如果`nIndex`未指定一个有效的索引，则返回值是**CB_ERR**。  
  
### <a name="example"></a>示例  
  请参阅示例[CComboBox::GetLBText](#getlbtext)。  
  
##  <a name="getlocale"></a>CComboBox::GetLocale  
 检索使用组合框的区域设置。  
  
```  
LCID GetLocale() const;  
```  
  
### <a name="return-value"></a>返回值  
 组合框中字符串的区域设置标识符 (LCID) 值。  
  
### <a name="remarks"></a>备注  
 使用区域设置是，例如，若要确定已排序的组合框中字符串的排序顺序。  
  
### <a name="example"></a>示例  
  请参阅示例[CComboBox::SetLocale](#setlocale)。  
  
##  <a name="getminvisible"></a>CComboBox::GetMinVisible  
 获取当前的组合框控件的下拉列表中的可见项的最小数量。  
  
```  
int GetMinVisible() const;  
```  
  
### <a name="return-value"></a>返回值  
 在当前的下拉列表中的可见项的最小数量。  
  
### <a name="remarks"></a>备注  
 此方法可发送[CB_GETMINVISIBLE](http://msdn.microsoft.com/library/windows/desktop/bb775915)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="gettopindex"></a>CComboBox::GetTopIndex  
 检索在组合框的列表框中部分中的第一个可见项的从零开始索引。  
  
```  
int GetTopIndex() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，该组合框的列表框中部分中的第一个可见项的从零开始索引**CB_ERR**否则为。  
  
### <a name="remarks"></a>备注  
 最初，0 项位于顶部的列表框中，但如果滚动列表框中，另一项可能会在顶部。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&25;](../../mfc/reference/codesnippet/cpp/ccombobox-class_25.cpp)]  
  
##  <a name="initstorage"></a>CComboBox::InitStorage  
 将列表框项存储在组合框的列表框中部分为分配内存。  
  
```  
int InitStorage(
    int nItems,  
    UINT nBytes);
```  
  
### <a name="parameters"></a>参数  
 `nItems`  
 指定要添加的项目数。  
  
 `nBytes`  
 以字节为单位，为项字符串分配指定内存的量。  
  
### <a name="return-value"></a>返回值  
 如果成功，最大项目数组合框的列表框中部分前所需内存重新分配，否则可以存储**CB_ERRSPACE**，这意味着没有足够的内存是可用。  
  
### <a name="remarks"></a>备注  
 将大量项添加到列表框部分之前调用此函数`CComboBox`。  
  
 仅 Windows 95/98:`wParam`参数最多为 16 位值。 这意味着列表框不能包含超过 32767 个项。 尽管限制的项数，则列表框中的项的总大小仅受可用内存限制。  
  
 此功能可帮助加快有大量的项 (超过 100) 的列表框中的初始化。 预先分配指定的以使后续的内存量[AddString](#addstring)， [InsertString](#insertstring)，和[Dir](#dir)函数采用最短的时间。 参数，可以使用估计值。 如果您要估计得高一些，则会分配一些额外的内存;如果您低估正常分配用于超出预分配的量的项。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&26;](../../mfc/reference/codesnippet/cpp/ccombobox-class_26.cpp)]  
  
##  <a name="insertstring"></a>CComboBox::InsertString  
 将字符串插入组合框的列表框。  
  
```  
int InsertString(
    int nIndex,  
    LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 包含一个索引（该索引从零开始），该索引指向列表框中将接收字符串的位置。 如果此参数为 –&1;，则字符串将被添加到列表末尾。  
  
 `lpszString`  
 指向要插入的以 null 结尾的字符串。  
  
### <a name="return-value"></a>返回值  
 插入该字符串的位置的索引（索引从零开始）。 返回值是 **CB_ERR** 如果发生错误。 如果没有足够空间可用于存储新的字符串，则返回值为 **CB_ERRSPACE** 。  
  
### <a name="remarks"></a>备注  
 与不同[AddString](#addstring)成员函数，`InsertString`成员函数不会导致与列表[CBS_SORT](../../mfc/reference/combo-box-styles.md)样式来进行排序。  
  
> [!NOTE]
>  Windows **ComboBoxEx** 控件不支持此函数。 此控件的详细信息，请参阅[ComboBoxEx 控件](http://msdn.microsoft.com/library/windows/desktop/bb775738)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&27;](../../mfc/reference/codesnippet/cpp/ccombobox-class_27.cpp)]  
  
##  <a name="limittext"></a>CComboBox::LimitText  
 限制用户可以输入到组合框中编辑控件的文本的长度以字节为单位。  
  
```  
BOOL LimitText(int nMaxChars);
```  
  
### <a name="parameters"></a>参数  
 `nMaxChars`  
 指定的用户可以输入的文本的长度 （以字节为单位）。 如果此参数为 0，则会将文本长度设置为 65535 字节。  
  
### <a name="return-value"></a>返回值  
 如果成功，非零值。 如果调用带有样式的组合框[CBS_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md)或组合框不编辑控件的情况下，返回值为**CB_ERR**。  
  
### <a name="remarks"></a>备注  
 如果对组合框不具有该样式[CBS_AUTOHSCROLL](../../mfc/reference/combo-box-styles.md)，设置文本限制为大于编辑控件的大小将没有任何效果。  
  
 `LimitText`仅限制用户可以输入的文本。 它不起任何文本已编辑控件中时将消息发送，也不会影响所选列表框中的字符串时，复制到编辑控件的文本的长度。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&28;](../../mfc/reference/codesnippet/cpp/ccombobox-class_28.cpp)]  
  
##  <a name="measureitem"></a>CComboBox::MeasureItem  
 创建带有所有者绘制样式的组合框时，由框架调用。  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpMeasureItemStruct`  
 指向长指针[MEASUREITEMSTRUCT](../../mfc/reference/measureitemstruct-structure.md)结构。  
  
### <a name="remarks"></a>备注  
 默认情况下，此成员函数没有任何影响。 重写该成员函数，并填写`MEASUREITEMSTRUCT`结构以通知 Windows 的维度的列表框中组合框。 如果使用组合框中创建了[CBS_OWNERDRAWVARIABLE](../../mfc/reference/combo-box-styles.md)样式，框架将调用此成员函数的列表框中的每一项。 否则，只有一次调用此成员。  
  
 使用**CBS_OWNERDRAWFIXED**中创建具有一个所有者绘制的组合框样式[SubclassDlgItem](../../mfc/reference/cwnd-class.md#subclassdlgitem)成员函数`CWnd`涉及进一步编程注意事项。 请参阅中的讨论[技术注意 14](../../mfc/tn014-custom-controls.md)。  
  
 请参阅[CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)有关的说明`MEASUREITEMSTRUCT`结构。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&29;](../../mfc/reference/codesnippet/cpp/ccombobox-class_29.cpp)]  
  
##  <a name="paste"></a>CComboBox::Paste  
 将数据从剪贴板插入的组合框，在当前光标位置的编辑控件。  
  
```  
void Paste();
```  
  
### <a name="remarks"></a>备注  
 只有当剪贴板包含中的数据插入数据**CF_TEXT**格式。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&30;](../../mfc/reference/codesnippet/cpp/ccombobox-class_30.cpp)]  
  
##  <a name="resetcontent"></a>CComboBox::ResetContent  
 删除所有项从列表框中，并编辑一个组合框控件。  
  
```  
void ResetContent();
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&31;](../../mfc/reference/codesnippet/cpp/ccombobox-class_31.cpp)]  
  
##  <a name="selectstring"></a>CComboBox::SelectString  
 搜索字符串的组合框，列表框中，如果找到该字符串，列表框中选择该字符串并将其复制到编辑控件。  
  
```  
int SelectString(
    int nStartAfter,  
    LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>参数  
 `nStartAfter`  
 包含要搜索的第一项之前的项的从零开始索引。 当搜索到达列表框的底部时，它将继续从列表框的顶部返回由指定的项`nStartAfter`。 如果为 –&1;，从一开始搜索整个列表框。  
  
 `lpszString`  
 指向以 null 结尾的字符串，其中包含要搜索的前缀。 搜索不区分大小写，因此此字符串可以包含任何的大写和小写字母组合。  
  
### <a name="return-value"></a>返回值  
 如果找到该字符串是选定的项的从零开始的索引。 如果搜索未成功，返回值是**CB_ERR**且未更改当前所选内容。  
  
### <a name="remarks"></a>备注  
 仅当其初始字符 （从起点） 匹配的前缀字符串中的字符，选择一个字符串。  
  
 请注意，`SelectString`和`FindString`成员函数查找一个字符串，但`SelectString`成员函数还将选择该字符串。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&32;](../../mfc/reference/codesnippet/cpp/ccombobox-class_32.cpp)]  
  
##  <a name="setcuebanner"></a>CComboBox::SetCueBanner  
 设置为组合框控件显示的提示文本。  
  
```  
BOOL SetCueBanner(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*lpszText*|指向包含提示文本的以 null 结尾的缓冲区的指针。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 提示文本是组合框控件的输入区域中显示的提示。 直至用户提供输入，则显示的提示文本。  
  
 此方法可发送[CB_SETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb775897)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_combobox`，也就是说，用来以编程方式访问组合框控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CComboBox_s&#1;&1;](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例设置组合框控件对应的提示标志。  
  
 [!code-cpp[NVC_MFC_CComboBox_s&#1;&2;](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]  
  
##  <a name="setcursel"></a>CComboBox::SetCurSel  
 组合框的列表框中选择一个字符串。  
  
```  
int SetCurSel(int nSelect);
```  
  
### <a name="parameters"></a>参数  
 `nSelect`  
 指定要选择的字符串的从零开始的索引。 如果为 –&1;，删除任何当前所选内容的列表框中，并清除编辑控件。  
  
### <a name="return-value"></a>返回值  
 如果消息已成功选中的项的从零开始的索引。 返回值是**CB_ERR**如果`nSelect`大于列表中的项的数目或者，如果`nSelect`设置为 –&1;，清除所选内容。  
  
### <a name="remarks"></a>备注  
 如有必要，列表框中滚动到视图字符串中 （如果列表框是否可见的）。 编辑控件的组合框中的文本被更改以反映新的选择。 将删除任何以前的选择列表框中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox 第&33;](../../mfc/reference/codesnippet/cpp/ccombobox-class_35.cpp)]  
  
##  <a name="setdroppedwidth"></a>CComboBox::SetDroppedWidth  
 调用此函数可设置的最小的允许宽度，以像素为单位的组合框的列表框。  
  
```  
int SetDroppedWidth(UINT nWidth);
```  
  
### <a name="parameters"></a>参数  
 `nWidth`  
 组合框，以像素为单位的列表框中部分的最小允许的宽度。  
  
### <a name="return-value"></a>返回值  
 如果成功，新的宽度的列表框中，否则**CB_ERR**。  
  
### <a name="remarks"></a>备注  
 此函数仅适用于组合框[CBS_DROPDOWN](../../mfc/reference/combo-box-styles.md)或[CBS_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md)样式。  
  
 默认情况下，下拉列表框中允许的最小宽度为 0。 当显示组合框的列表框中部分时，其宽度为较大的允许的最小宽度或组合框的宽度。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&34;](../../mfc/reference/codesnippet/cpp/ccombobox-class_36.cpp)]  
  
##  <a name="seteditsel"></a>CComboBox::SetEditSel  
 编辑控件的组合框中选择字符。  
  
```  
BOOL SetEditSel(
    int nStartChar,  
    int nEndChar);
```  
  
### <a name="parameters"></a>参数  
 `nStartChar`  
 指定的起始位置。 如果起始位置设置为 –&1;，则将移除任何现有的选择。  
  
 `nEndChar`  
 指定的结束位置。 如果结束位置到最后一个设置为-1，然后从起始位置的所有文本选择编辑控件中的字符。  
  
### <a name="return-value"></a>返回值  
 如果该成员函数成功，则非零值否则为 0。 它是**CB_ERR**如果`CComboBox`具有[CBS_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md)样式或不具有列表框。  
  
### <a name="remarks"></a>备注  
 位置将由从零开始。 若要选择的编辑控件的第一个字符，您可以指定 0 的起始位置。 结束位置的字符是恰好在要选择的最后一个字符后。 例如，若要选择的编辑控件的前四个字符，将使用的起始位置为 0 和 4 的结束位置。  
  
> [!NOTE]
>  Windows **ComboBoxEx** 控件不支持此函数。 此控件的详细信息，请参阅[ComboBoxEx 控件](http://msdn.microsoft.com/library/windows/desktop/bb775738)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CComboBox::GetEditSel](#geteditsel)。  
  
##  <a name="setextendedui"></a>CComboBox::SetExtendedUI  
 调用`SetExtendedUI`成员函数，以选择默认用户界面或组合框包含扩展的用户界面[CBS_DROPDOWN](../../mfc/reference/combo-box-styles.md)或[CBS_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md)样式。  
  
```  
int SetExtendedUI(BOOL bExtended = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *bExtended*  
 指定组合框是否应使用扩展的用户界面或默认用户界面。 值为**TRUE**选择扩展用户界面; 如果值为**FALSE**选择标准用户界面。  
  
### <a name="return-value"></a>返回值  
 **CB_OKAY**如果操作成功，或**CB_ERR**如果发生错误。  
  
### <a name="remarks"></a>备注  
 可以通过以下方式确定扩展的用户界面︰  
  
-   单击静态控件将显示列表框中只为组合框**CBS_DROPDOWNLIST**样式。  
  
-   按向下箭头键显示列表框 （禁用 F4）。  
  
 项目列表不可见时将会禁用静态控件中滚动 （禁用箭头键）。  
  
### <a name="example"></a>示例  
  请参阅示例[CComboBox::GetExtendedUI](#getextendedui)。  
  
##  <a name="sethorizontalextent"></a>CComboBox::SetHorizontalExtent  
 设置的宽度，以像素为单位，组合框的列表框中部分可以进行水平滚动。  
  
```  
void SetHorizontalExtent(UINT nExtent);
```  
  
### <a name="parameters"></a>参数  
 *nExtent*  
 指定组合框的列表框中部分可以进行水平滚动的像素数。  
  
### <a name="remarks"></a>备注  
 如果列表框的宽度小于此值，水平滚动条将水平滚动列表框中的项。 如果列表框的宽度等于或大于此值，将会隐藏水平滚动条或组合框是否[CBS_DISABLENOSCROLL](../../mfc/reference/combo-box-styles.md)样式，被禁用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&35;](../../mfc/reference/codesnippet/cpp/ccombobox-class_37.cpp)]  
  
##  <a name="setitemdata"></a>CComboBox::SetItemData  
 设置与组合框中指定的项相关联的 32 位值。  
  
```  
int SetItemData(
    int nIndex,  
    DWORD_PTR dwItemData);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 包含要设置的项的从零开始索引。  
  
 `dwItemData`  
 包含要与项关联的新值。  
  
### <a name="return-value"></a>返回值  
 **CB_ERR**出错时。  
  
### <a name="remarks"></a>备注  
 使用`SetItemDataPtr`成员函数，如果 32 位项将是一个指针。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&36;](../../mfc/reference/codesnippet/cpp/ccombobox-class_38.cpp)]  
  
##  <a name="setitemdataptr"></a>CComboBox::SetItemDataPtr  
 设置与要指定的指针的组合框中指定的项关联的 32 位值 ( **void\***)。  
  
```  
int SetItemDataPtr(
    int nIndex,  
    void* pData);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 包含项的从零开始索引。  
  
 `pData`  
 包含要与项关联的指针。  
  
### <a name="return-value"></a>返回值  
 **CB_ERR**出错时。  
  
### <a name="remarks"></a>备注  
 即使在组合框中项的相对位置可能会更改，如添加或移除项就保持有效的生存期内组合框中，该指针。 因此，在框内的项的索引可以改变，但指针保持可靠。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&37;](../../mfc/reference/codesnippet/cpp/ccombobox-class_39.cpp)]  
  
##  <a name="setitemheight"></a>CComboBox::SetItemHeight  
 调用`SetItemHeight`成员函数的组合框或组合框的编辑控件 （或静态文本） 部分的高度设置列表项的高度。  
  
```  
int SetItemHeight(
    int nIndex,  
    UINT cyItemHeight);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定是否设置列表项的高度或组合框的编辑控件 （或静态文本） 部分的高度。  
  
 如果在组合框中[CBS_OWNERDRAWVARIABLE](../../mfc/reference/combo-box-styles.md)样式，`nIndex`指定设置; 否则为其高度的列表项的从零开始索引`nIndex`必须是 0 和将设置项的所有列表的高度。  
  
 如果`nIndex`为 –&1;，编辑控件的高度或组合框的静态文本部分将进行设置。  
  
 `cyItemHeight`  
 指定的高度，以像素为单位，通过标识的组合框组件`nIndex`。  
  
### <a name="return-value"></a>返回值  
 **CB_ERR**如果索引或高度为无效; 否则为 0。  
  
### <a name="remarks"></a>备注  
 组合框的编辑控件 （或静态文本） 部分的高度设置独立于列表项的高度。 应用程序必须确保编辑控件 （或静态文本） 部分的高度不小于特定的列表框中项的高度。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&38;](../../mfc/reference/codesnippet/cpp/ccombobox-class_40.cpp)]  
  
##  <a name="setlocale"></a>CComboBox::SetLocale  
 设置此组合框的区域设置标识符。  
  
```  
LCID SetLocale(LCID nNewLocale);
```  
  
### <a name="parameters"></a>参数  
 `nNewLocale`  
 新区域设置标识符 (LCID) 要设置的值的组合框。  
  
### <a name="return-value"></a>返回值  
 此组合框以前的区域设置标识符 (LCID) 值。  
  
### <a name="remarks"></a>备注  
 如果**SetLocale**不调用，则默认值从系统中获取区域设置。 此系统默认区域设置可以修改通过使用控制面板中的区域 （或国际） 应用程序。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&39;](../../mfc/reference/codesnippet/cpp/ccombobox-class_41.cpp)]  
  
##  <a name="setminvisibleitems"></a>CComboBox::SetMinVisibleItems  
 设置可见项的最小数量的当前组合框下拉列表框控件中。  
  
```  
BOOL SetMinVisibleItems(int iMinVisible);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `iMinVisible`|指定可见项的最小数量。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[CB_SETMINVISIBLE](http://msdn.microsoft.com/library/windows/desktop/bb775915)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_combobox`，也就是说，用来以编程方式访问组合框控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CComboBox_s&#1;&1;](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例在一个组合框控件下拉列表中插入 20 个项。 然后，它指定当用户按下的下拉箭头，显示最少 10 项。  
  
 [!code-cpp[NVC_MFC_CComboBox_s&#1;&2;](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]  
  
##  <a name="settopindex"></a>CComboBox::SetTopIndex  
 确保特定项的组合框的列表框中部分中可见。  
  
```  
int SetTopIndex(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定列表框中项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为零或**CB_ERR**如果发生错误。  
  
### <a name="remarks"></a>备注  
 系统滚动列表框中，直到指定的任意一项`nIndex`显示顶部的列表框或最大滚动范围已达到。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox #&40;](../../mfc/reference/codesnippet/cpp/ccombobox-class_42.cpp)]  
  
##  <a name="showdropdown"></a>CComboBox::ShowDropDown  
 显示或隐藏了一个组合框的列表框中[CBS_DROPDOWN](../../mfc/reference/combo-box-styles.md)或[CBS_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md)样式。  
  
```  
void ShowDropDown(BOOL bShowIt = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *bShowIt*  
 指定是显示还是隐藏下拉列表框。 值为**TRUE**显示列表框。 值为**FALSE**隐藏列表框。  
  
### <a name="remarks"></a>备注  
 默认情况下，此样式组合框将显示列表框。  
  
 此成员函数不起使用创建组合框上[CBS_SIMPLE](../../mfc/reference/combo-box-styles.md)样式。  
  
### <a name="example"></a>示例  
  请参阅示例[CComboBox::GetDroppedState](#getdroppedstate)。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 CTRLBARS](../../visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CButton 类](../../mfc/reference/cbutton-class.md)   
 [CEdit 类](../../mfc/reference/cedit-class.md)   
 [CListBox 类](../../mfc/reference/clistbox-class.md)   
 [CScrollBar 类](../../mfc/reference/cscrollbar-class.md)   
 [CStatic 类](../../mfc/reference/cstatic-class.md)   
 [CDialog 类](../../mfc/reference/cdialog-class.md)

