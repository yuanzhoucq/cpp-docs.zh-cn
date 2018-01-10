---
title: "CComboBox 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords:
- CComboBox [MFC], CComboBox
- CComboBox [MFC], AddString
- CComboBox [MFC], Clear
- CComboBox [MFC], CompareItem
- CComboBox [MFC], Copy
- CComboBox [MFC], Create
- CComboBox [MFC], Cut
- CComboBox [MFC], DeleteItem
- CComboBox [MFC], DeleteString
- CComboBox [MFC], Dir
- CComboBox [MFC], DrawItem
- CComboBox [MFC], FindString
- CComboBox [MFC], FindStringExact
- CComboBox [MFC], GetComboBoxInfo
- CComboBox [MFC], GetCount
- CComboBox [MFC], GetCueBanner
- CComboBox [MFC], GetCurSel
- CComboBox [MFC], GetDroppedControlRect
- CComboBox [MFC], GetDroppedState
- CComboBox [MFC], GetDroppedWidth
- CComboBox [MFC], GetEditSel
- CComboBox [MFC], GetExtendedUI
- CComboBox [MFC], GetHorizontalExtent
- CComboBox [MFC], GetItemData
- CComboBox [MFC], GetItemDataPtr
- CComboBox [MFC], GetItemHeight
- CComboBox [MFC], GetLBText
- CComboBox [MFC], GetLBTextLen
- CComboBox [MFC], GetLocale
- CComboBox [MFC], GetMinVisible
- CComboBox [MFC], GetTopIndex
- CComboBox [MFC], InitStorage
- CComboBox [MFC], InsertString
- CComboBox [MFC], LimitText
- CComboBox [MFC], MeasureItem
- CComboBox [MFC], Paste
- CComboBox [MFC], ResetContent
- CComboBox [MFC], SelectString
- CComboBox [MFC], SetCueBanner
- CComboBox [MFC], SetCurSel
- CComboBox [MFC], SetDroppedWidth
- CComboBox [MFC], SetEditSel
- CComboBox [MFC], SetExtendedUI
- CComboBox [MFC], SetHorizontalExtent
- CComboBox [MFC], SetItemData
- CComboBox [MFC], SetItemDataPtr
- CComboBox [MFC], SetItemHeight
- CComboBox [MFC], SetLocale
- CComboBox [MFC], SetMinVisibleItems
- CComboBox [MFC], SetTopIndex
- CComboBox [MFC], ShowDropDown
ms.assetid: 4e73b5df-0d2e-4658-9706-38133fb10513
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fffa5c09f1572200ca7850c8870b7daee9e3e75f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ccombobox-class"></a>CComboBox 类
提供 Windows 组合框功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CComboBox : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CComboBox::CComboBox](#ccombobox)|构造 `CComboBox` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Ccombobox::](#addstring)|将字符串添加到组合框，或在列表框的排序位置的列表框中列表的末尾**CBS_SORT**样式。|  
|[CComboBox::Clear](#clear)|删除 （清除） 当前选定内容，如果有的话，编辑控件中。|  
|[CComboBox::CompareItem](#compareitem)|由框架调用以确定新列表项的已排序的所有者描述组合框中的相对位置。|  
|[CComboBox::Copy](#copy)|如果有的话，到在剪贴板中复制当前选定内容， **CF_TEXT**格式。|  
|[CComboBox::Create](#create)|创建组合框，并将其附加到`CComboBox`对象。|  
|[CComboBox::Cut](#cut)|删除 （操作会剪切） 当前选定内容，如果任何，正在编辑控制，并将复制到剪贴板中删除的文本**CF_TEXT**格式。|  
|[CComboBox::DeleteItem](#deleteitem)|从一个所有者描述的组合框中删除列表项时，由框架调用。|  
|[CComboBox::DeleteString](#deletestring)|从组合框的列表中删除一个字符串。|  
|[CComboBox::Dir](#dir)|将文件名称的列表添加到组合框的列表框中。|  
|[CComboBox::DrawItem](#drawitem)|由框架在所有者描述的组合框中更改的可视方面时调用。|  
|[CComboBox::FindString](#findstring)|查找包含组合框列表框中指定的前缀的第一个字符串。|  
|[CComboBox::FindStringExact](#findstringexact)|查找第一个列表框中的字符串 （组合框） 与指定的字符串匹配。|  
|[CComboBox::GetComboBoxInfo](#getcomboboxinfo)|有关检索信息`CComboBox`对象。|  
|[CComboBox::GetCount](#getcount)|检索在组合框的列表框中的项的数目。|  
|[CComboBox::GetCueBanner](#getcuebanner)|获取组合框控件显示的提示文本。|  
|[CComboBox::GetCurSel](#getcursel)|如果有的话，组合框列表框中，检索的当前选定项的索引。|  
|[CComboBox::GetDroppedControlRect](#getdroppedcontrolrect)|检索下拉组合框的可见 （已关闭删除） 的列表框的屏幕坐标。|  
|[CComboBox::GetDroppedState](#getdroppedstate)|确定下拉组合框的列表框中是可见的 （向下删除）。|  
|[CComboBox::GetDroppedWidth](#getdroppedwidth)|检索允许组合框的下拉列表框部分的宽度的最小。|  
|[CComboBox::GetEditSel](#geteditsel)|获取组合框编辑控件中当前所选内容的起始和结束字符位置。|  
|[CComboBox::GetExtendedUI](#getextendedui)|确定一个组合框是否具有默认用户界面或扩展的用户界面。|  
|[CComboBox::GetHorizontalExtent](#gethorizontalextent)|返回以像素为单位可水平滚动的组合框的列表框部分的宽度。|  
|[CComboBox::GetItemData](#getitemdata)|检索与指定的组合框项关联的应用程序提供 32 位值。|  
|[CComboBox::GetItemDataPtr](#getitemdataptr)|检索与指定的组合框项关联的应用程序提供 32 位指针。|  
|[CComboBox::GetItemHeight](#getitemheight)|检索在组合框的列表项的高度。|  
|[CComboBox::GetLBText](#getlbtext)|从组合框的列表中获取的字符串。|  
|[CComboBox::GetLBTextLen](#getlbtextlen)|获取组合框的列表框中的字符串的长度。|  
|[CComboBox::GetLocale](#getlocale)|检索一个组合框的区域设置标识符。|  
|[CComboBox::GetMinVisible](#getminvisible)|获取当前的组合框的下拉列表中的可见项的最小数目。|  
|[CComboBox::GetTopIndex](#gettopindex)|在组合框的列表框部分中返回的第一个可见项的索引。|  
|[CComboBox::InitStorage](#initstorage)|预分配项和组合框的列表框部分中的字符串的内存块的能力。|  
|[CComboBox::InsertString](#insertstring)|将字符串插入组合框的列表框。|  
|[CComboBox::LimitText](#limittext)|限制用户可以输入到组合框编辑控件的文本的长度。|  
|[CComboBox::MeasureItem](#measureitem)|由框架调用以确定组合框维度，创建一个所有者描述的组合框时。|  
|[CComboBox::Paste](#paste)|将数据从剪贴板插入当前光标位置处的编辑控件。 只有当剪贴板包含中的数据插入数据**CF_TEXT**格式。|  
|[CComboBox::ResetContent](#resetcontent)|中移除所有项从列表框中字符和编辑组合框控件。|  
|[CComboBox::SelectString](#selectstring)|搜索的字符串的组合框列表框中，如果找到该字符串，在列表框中选择字符串，并将字符串复制到编辑控件。|  
|[CComboBox::SetCueBanner](#setcuebanner)|设置为组合框控件显示的提示文本。|  
|[CComboBox::SetCurSel](#setcursel)|组合框的列表框中选择一个字符串。|  
|[CComboBox::SetDroppedWidth](#setdroppedwidth)|设置允许组合框的下拉列表框部分的宽度的最小。|  
|[CComboBox::SetEditSel](#seteditsel)|选择组合框编辑控件中的字符。|  
|[CComboBox::SetExtendedUI](#setextendedui)|选择默认用户界面或组合框具有扩展的用户界面**CBS_DROPDOWN**或**CBS_DROPDOWNLIST**样式。|  
|[CComboBox::SetHorizontalExtent](#sethorizontalextent)|以组合框的列表框部分可被水平滚动的像素为单位设置宽度。|  
|[CComboBox::SetItemData](#setitemdata)|设置与组合框中指定的项关联的 32 位值。|  
|[CComboBox::SetItemDataPtr](#setitemdataptr)|设置与组合框中指定的项关联的 32 位指针。|  
|[CComboBox::SetItemHeight](#setitemheight)|设置的列表项的高度以组合框或组合框的编辑控件 （或静态文本） 部分的高度。|  
|[CComboBox::SetLocale](#setlocale)|设置组合框的区域设置标识符。|  
|[CComboBox::SetMinVisibleItems](#setminvisibleitems)|设置当前的组合框的下拉列表中的可见项的最小数目。|  
|[CComboBox::SetTopIndex](#settopindex)|告知组合框，以在顶部显示具有指定索引的项的列表框部分。|  
|[CComboBox::ShowDropDown](#showdropdown)|显示或隐藏具有组合框的列表框**CBS_DROPDOWN**或**CBS_DROPDOWNLIST**样式。|  
  
## <a name="remarks"></a>备注  
 组合框包含与静态控件或编辑控件组合在一个列表框。 控件的列表框部分可能会显示在所有时间或可能仅下拉当用户选择控件旁边的下拉箭头。  
  
 列表框中的当前选定的项 （如果有） 显示在静态或者编辑控件。 此外，如果组合框的下拉列表样式，用户可以在列表中，键入项目之一的初始字符和列表框中，如果可见，将突出显示该初始字符的下一项。  
  
 下表比较了三个的组合框[样式](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)。  
  
|样式|在列表框中是可见的|静态或编辑控件|  
|-----------|-------------------------------|-----------------------------|  
|简单|Always|Edit|  
|Drop-down|当下拉|Edit|  
|下拉列表|当下拉|Static|  
  
 你可以创建`CComboBox`通过对话框模板或直接在代码中的对象。 在这两种情况下，第一次调用的构造函数`CComboBox`构造`CComboBox`对象; 然后调用[创建](#create)成员函数以创建控件并将其附加到`CComboBox`对象。  
  
 如果你想要处理 Windows 通知消息发送到其父组合框 (通常从派生的类`CDialog`)，将消息映射条目和消息处理程序成员函数添加到每条消息的父类。  
  
 每个消息映射条目采用以下形式：  
  
 **ON_**通知**(**`id`**，**`memberFxn`**)**  
  
 其中`id`指定发送通知的组合框控件的子窗口 ID 和`memberFxn`是父成员函数编写以处理通知的名称。  
  
 父元素的函数原型如下所示：  
  
 **afx_msg** `void` `memberFxn` **（);**  
  
 无法预测将发送某些通知的顺序。 具体而言， **CBN_SELCHANGE**之前或之后，可能会出现通知**CBN_CLOSEUP**通知。  
  
 潜在的消息映射条目如下所示：  
  
- **ON_CBN_CLOSEUP** (Windows 3.1 及更高版本。)组合框的列表框中已关闭。 此通知消息不会发送具有组合框[CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式。  
  
- **ON_CBN_DBLCLK**用户双击某个字符串的组合框列表框中。 此通知消息将只发送与组合框**CBS_SIMPLE**样式。 有关带有的组合框[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式，不能出现一次双击因为一次单击隐藏列表框。  
  
- **ON_CBN_DROPDOWN**组合框的列表框中即将下拉列表 （要使其可见）。 此通知消息可能仅为组合框与**CBS_DROPDOWN**或**CBS_DROPDOWNLIST**样式。  
  
- **ON_CBN_EDITCHANGE**用户已执行可能更改编辑控件一部分组合框中的文本的操作。 与不同**CBN_EDITUPDATE** ，此消息之后发送消息 Windows 更新屏幕。 它不会发送如果组合框中具有**CBS_DROPDOWNLIST**样式。  
  
- **ON_CBN_EDITUPDATE**组合框的编辑控件部分即将显示修改后的文本。 控件设置文本格式后但在其显示文本之前，此通知消息被发送。 它不会发送如果组合框中具有**CBS_DROPDOWNLIST**样式。  
  
- **ON_CBN_ERRSPACE**组合框无法分配足够的内存来满足特定的请求。  
  
- **ON_CBN_SELENDCANCEL** (Windows 3.1 及更高版本。)指示应取消用户的选择。 用户单击的项，然后单击另一个窗口或控件隐藏组合框的列表框。 此通知消息发送之前**CBN_CLOSEUP**通知消息，以指示应忽略用户的选择。 **CBN_SELENDCANCEL**或**CBN_SELENDOK**发送通知消息即使**CBN_CLOSEUP**不发送通知消息 (在带有的组合框的情况下为**CBS_SIMPLE**样式)。  
  
- **ON_CBN_SELENDOK**用户选择某一项然后按 ENTER 键或单击向下箭头键以隐藏组合框的列表框。 此通知消息发送之前**CBN_CLOSEUP**消息，以指示，用户的选择应视为有效。 **CBN_SELENDCANCEL**或**CBN_SELENDOK**发送通知消息即使**CBN_CLOSEUP**不发送通知消息 (在带有的组合框的情况下为**CBS_SIMPLE**样式)。  
  
- **ON_CBN_KILLFOCUS**组合框失去输入的焦点。  
  
- **ON_CBN_SELCHANGE**组合框列表框中的选择即将因用户在列表框中单击或通过使用箭头键更改所选内容而更改。 当处理此消息，在组合框编辑控件中的文本，仅可通过检索`GetLBText`或另一个类似函数。 `GetWindowText`不能使用。  
  
- **ON_CBN_SETFOCUS**组合框接收到输入的焦点。  
  
 如果你创建`CComboBox`（通过对话框资源） 对话框中的对象`CComboBox`当用户关闭对话框中，将自动销毁对象。  
  
 如果您嵌入`CComboBox`另一个窗口中的对象的对象，不需要将其销毁。 如果你创建`CComboBox`对象在堆栈上，自动销毁。 如果你创建`CComboBox`使用堆上的对象**新**函数，必须调用**删除**上要在销毁 Windows 组合框时销毁它的对象。  
  
 **请注意**如果你想要处理`WM_KEYDOWN`和`WM_CHAR`的消息，你具有子类化组合框的编辑和列表框控件中，派生的类`CEdit`和`CListBox`，并将这些消息的处理程序添加到派生类。 有关详细信息，请参阅[http://support.microsoft.com/default.aspxscid=kb;en-us;Q174667](http://support.microsoft.com/default.aspxscid=kb;en-us;q174667)和[CWnd::SubclassWindow](../../mfc/reference/cwnd-class.md#subclasswindow)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CComboBox`  
  
## <a name="requirements"></a>惠?  
 **标头:** afxwin.h  
  
##  <a name="addstring"></a>Ccombobox::  
 将字符串添加到组合框的列表框中。  
  
```  
int AddString(LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>参数  
 `lpszString`  
 指向要添加的以 null 结尾的字符串。  
  
### <a name="return-value"></a>返回值  
 如果返回值是大于或等于 0，它是到列表框中的字符串的从零开始索引。 返回值是**CB_ERR**如果发生错误; 返回值是**CB_ERRSPACE**如果没有足够的空间来存储新的字符串。  
  
### <a name="remarks"></a>备注  
 如果使用列表框不创建了[CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式，则字符串添加到列表的末尾。 否则为该字符串插入到列表中，并对列表进行排序。  
  
> [!NOTE]
>  Windows **ComboBoxEx** 控件不支持此函数。 此控件的详细信息，请参阅[ComboBoxEx 控件](http://msdn.microsoft.com/library/windows/desktop/bb775738)Windows SDK 中。  
  
 若要插入列表中的特定位置的一个字符串，请使用[InsertString](#insertstring)成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#3](../../mfc/reference/codesnippet/cpp/ccombobox-class_1.cpp)]  
  
##  <a name="ccombobox"></a>CComboBox::CComboBox  
 构造 `CComboBox` 对象。  
  
```  
CComboBox();
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_2.cpp)]  
  
##  <a name="clear"></a>CComboBox::Clear  
 删除 （清除） 当前选定内容，如果有的话，组合框编辑控件中。  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>备注  
 若要删除当前所选内容并将放到剪贴板上的已删除的内容，使用[剪切](#cut)成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#4](../../mfc/reference/codesnippet/cpp/ccombobox-class_3.cpp)]  
  
##  <a name="compareitem"></a>CComboBox::CompareItem  
 由框架调用以确定已排序的所有者描述组合框的列表框部分中的新项的相对位置。  
  
```  
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpCompareItemStruct`  
 指向的长指针[COMPAREITEMSTRUCT](../../mfc/reference/compareitemstruct-structure.md)结构。  
  
### <a name="return-value"></a>返回值  
 指示中所述的两个项的相对位置`COMPAREITEMSTRUCT`结构。 它可以是任何以下值：  
  
|“值”|含义|  
|-----------|-------------|  
|- 1|项 2 之前进行排序的第 1 项。|  
|0|项 1 和 2 的项进行排序相同。|  
|1|项 2 后进行排序的第 1 项。|  
  
 请参阅[CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)有关的说明`COMPAREITEMSTRUCT`。  
  
### <a name="remarks"></a>备注  
 默认情况下，此成员函数没有任何影响。 如果你创建一个带有所有者描述组合框**LBS_SORT**样式，你必须重写该成员函数以帮助 framework 排序新项添加到列表框中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#5](../../mfc/reference/codesnippet/cpp/ccombobox-class_4.cpp)]  
  
##  <a name="copy"></a>CComboBox::Copy  
 如果有的话，组合框到剪贴板中的编辑控件中复制当前选定内容**CF_TEXT**格式。  
  
```  
void Copy();
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#6](../../mfc/reference/codesnippet/cpp/ccombobox-class_5.cpp)]  
  
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
 指定组合框的样式。 应用的任意组合[组合框样式](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)在框中。  
  
 `rect`  
 指向的位置和大小的组合框。 可以是[RECT 结构](../../mfc/reference/rect-structure1.md)或`CRect`对象。  
  
 `pParentWnd`  
 指定组合框的父窗口 (通常`CDialog`)。 它不能**NULL**。  
  
 `nID`  
 指定组合框控件 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 构造`CComboBox`两个步骤中的对象。 首先，调用的构造函数，然后调用**创建**，它创建 Windows 组合框，并将其附加到`CComboBox`对象。  
  
 当**创建**执行 Windows 发送[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)， [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)， [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)，和[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)到组合框的消息。  
  
 默认情况下，通过处理这些消息的消息[OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)， [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)， [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)，和[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成员函数在`CWnd`基类。 若要扩展的默认消息处理，从派生类`CComboBox`、 将消息映射添加到新的类中，和重写前面的消息处理程序成员函数。 重写`OnCreate`，例如，若要为新类执行所需的初始化。  
  
 将应用以下[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)到组合框控件。 :  
  
- **WS_CHILD**始终  
  
- **WS_VISIBLE**通常  
  
- **WS_DISABLED**很少  
  
- **WS_VSCROLL**若要添加的列表框中组合框的垂直滚动  
  
- **WS_HSCROLL**若要添加水平滚动的列表框中组合框  
  
- **WS_GROUP**与组控件  
  
- **WS_TABSTOP**要包括在 tab 键顺序中的组合框  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_6.cpp)]  
  
##  <a name="cut"></a>CComboBox::Cut  
 删除 （操作会剪切） 当前选定内容，如果任何，组合框中编辑控制，并将复制到剪贴板中删除的文本**CF_TEXT**格式。  
  
```  
void Cut();
```  
  
### <a name="remarks"></a>备注  
 若要删除当前所选内容，而无需将到剪贴板上删除的文本，调用[清除](#clear)成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#7](../../mfc/reference/codesnippet/cpp/ccombobox-class_7.cpp)]  
  
##  <a name="deleteitem"></a>CComboBox::DeleteItem  
 当用户从所有者描述中删除项时，由框架调用`CComboBox`对象或销毁组合框。  
  
```  
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpDeleteItemStruct`  
 向 Windows 的长指针[DELETEITEMSTRUCT](../../mfc/reference/deleteitemstruct-structure.md)结构，它包含有关已删除的项的信息。 请参阅[CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem)有关此结构的说明。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现不执行任何操作。 重写此函数可根据需要重绘组合框。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#8](../../mfc/reference/codesnippet/cpp/ccombobox-class_8.cpp)]  
  
##  <a name="deletestring"></a>CComboBox::DeleteString  
 删除位置中的项`nIndex`从组合框。  
  
```  
int DeleteString(UINT nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定要删除的字符串的索引。  
  
### <a name="return-value"></a>返回值  
 如果返回值是大于或等于 0，则会在列表中剩余的字符串的计数。 返回值是**CB_ERR**如果`nIndex`指定列表中的索引大于项的数目。  
  
### <a name="remarks"></a>备注  
 后面的所有项`nIndex`现在下移一个位置。 例如，如果组合框包含两个项，则删除第一项将导致剩余的项现在处于的第一个位置。 `nIndex`= 0 中的第一个位置的项。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#9](../../mfc/reference/codesnippet/cpp/ccombobox-class_9.cpp)]  
  
##  <a name="dir"></a>CComboBox::Dir  
 将文件名或驱动器的列表添加到组合框的列表框中。  
  
```  
int Dir(
    UINT attr,  
    LPCTSTR lpszWildCard);
```  
  
### <a name="parameters"></a>参数  
 `attr`  
 可以是任意组合的`enum`值中所述[cfile:: Getstatus](../../mfc/reference/cfile-class.md#getstatus)或以下值的任意组合：  
  
- **DDL_READWRITE**可以读取或写入到文件。  
  
- **DDL_READONLY**可以从读取但不是会写入到文件。  
  
- **DDL_HIDDEN**文件将被隐藏，未出现在目录列表。  
  
- **DDL_SYSTEM**文件是系统文件。  
  
- **DDL_DIRECTORY**指定的名称`lpszWildCard`指定的目录。  
  
- **DDL_ARCHIVE**已存档文件。  
  
- **DDL_DRIVES**包括与指定的名称匹配的所有驱动器`lpszWildCard`。  
  
- **DDL_EXCLUSIVE**独占标志。 如果设置独占标志，仅指定类型的文件会列出。 否则，除"正常"的文件之外还列出指定类型的文件。  
  
 `lpszWildCard`  
 指向文件规范的字符串。 字符串可以包含通配符 (例如，*。\*)。  
  
### <a name="return-value"></a>返回值  
 如果返回值是大于或等于 0，则最后一个文件名添加到列表中的从零开始的索引。 返回值是**CB_ERR**如果发生错误; 返回值是**CB_ERRSPACE**如果没有足够的空间来存储新的字符串。  
  
### <a name="remarks"></a>备注  
 Windows **ComboBoxEx** 控件不支持此函数。 此控件的详细信息，请参阅[ComboBoxEx 控件](http://msdn.microsoft.com/library/windows/desktop/bb775738)Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#10](../../mfc/reference/codesnippet/cpp/ccombobox-class_10.cpp)]  
  
##  <a name="drawitem"></a>CComboBox::DrawItem  
 由框架的所有者描述组合框中更改的可视方面时调用。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpDrawItemStruct`  
 指向的指针[DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md)结构，其中包含有关所需的绘图的类型的信息。  
  
### <a name="remarks"></a>备注  
 **ItemAction**的成员`DRAWITEMSTRUCT`结构定义要执行的绘制操作。 请参阅[CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)有关此结构的说明。  
  
 默认情况下，此成员函数没有任何影响。 重写该成员函数以实现所有者描述的绘图`CComboBox`对象。 此成员函数将终止之前，应用程序应还原选择的显示上下文中提供的所有图形设备接口 (GDI) 对象`lpDrawItemStruct`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#11](../../mfc/reference/codesnippet/cpp/ccombobox-class_11.cpp)]  
  
##  <a name="findstring"></a>CComboBox::FindString  
 找到，但不会选择第一个字符串，其中包含一个组合框的列表框中指定的前缀。  
  
```  
int FindString(
    int nStartAfter,  
    LPCTSTR lpszString) const;  
```  
  
### <a name="parameters"></a>参数  
 `nStartAfter`  
 包含要搜索的第一项之前的项的从零开始索引。 如果搜索到达搜索列表框的底部，它将继续从列表框的顶部回由指定的项`nStartAfter`。 如果为-1，从开始处搜索整个列表框。  
  
 `lpszString`  
 指向以 null 结尾的字符串，其中包含要搜索的前缀。 搜索是独立的因此此字符串可以包含任何组合的大写和小写字母。  
  
### <a name="return-value"></a>返回值  
 如果返回值是大于或等于 0，则匹配项的从零开始索引。 它是**CB_ERR**如果搜索未成功。  
  
### <a name="remarks"></a>备注  
 Windows **ComboBoxEx** 控件不支持此函数。 此控件的详细信息，请参阅[ComboBoxEx 控件](http://msdn.microsoft.com/library/windows/desktop/bb775738)Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#12](../../mfc/reference/codesnippet/cpp/ccombobox-class_12.cpp)]  
  
##  <a name="findstringexact"></a>CComboBox::FindStringExact  
 调用`FindStringExact`成员函数，以便查找第一个列表框中的字符串 （组合框） 中指定的字符串匹配`lpszFind`。  
  
```  
int FindStringExact(
    int nIndexStart,  
    LPCTSTR lpszFind) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndexStart`  
 指定要搜索的第一项之前的项的从零开始索引。 如果搜索到达搜索列表框的底部，它将继续从列表框的顶部回由指定的项`nIndexStart`。 如果`nIndexStart`为-1，从开始处搜索整个列表框。  
  
 `lpszFind`  
 指向要搜索的以 null 结尾的字符串。 此字符串可以包含完整的文件名，包括扩展名。 搜索不区分大小写，因此此字符串可以包含任何组合的大写和小写字母。  
  
### <a name="return-value"></a>返回值  
 匹配的项的从零开始索引或**CB_ERR**如果搜索未成功。  
  
### <a name="remarks"></a>备注  
 如果组合框但没有创建了一个所有者绘制样式[CBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式，`FindStringExact`尝试与双字值的值相匹配`lpszFind`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#13](../../mfc/reference/codesnippet/cpp/ccombobox-class_13.cpp)]  
  
##  <a name="getcomboboxinfo"></a>CComboBox::GetComboBoxInfo  
 检索信息`CComboBox`对象。  
  
```  
BOOL GetComboBoxInfo(PCOMBOBOXINFO pcbi) const;  
```  
  
### <a name="parameters"></a>参数  
 *pcbi*  
 指向的指针[COMBOBOXINFO](http://msdn.microsoft.com/library/windows/desktop/bb775798)结构。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**成功后， **FALSE**失败。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[CB_GETCOMBOBOXINFO](http://msdn.microsoft.com/library/windows/desktop/bb775839)消息时，Windows SDK 中所述。  
  
##  <a name="getcount"></a>CComboBox::GetCount  
 调用此成员函数以检索在组合框的列表框部分中的项的数目。  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 项的数目。 因此返回的计数是一个大于 （索引是从零开始） 的最后一项的索引值。 它是**CB_ERR**如果发生错误。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#14](../../mfc/reference/codesnippet/cpp/ccombobox-class_14.cpp)]  
  
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
|[out] `lpszText`|为接收提示横幅文本的缓冲区的指针。|  
|[in] `cchText`|缓冲区的大小，`lpszText`参数指向。|  
  
### <a name="return-value"></a>返回值  
 在第一个重载中， [CString](../../atl-mfc-shared/using-cstring.md)对象，其中包含提示横幅文本，如果存在; 否则为`CString`长度为零的对象。  
  
 或  
  
 在第二个重载中，`true`如果此方法成功; 否则为`false`。  
  
### <a name="remarks"></a>备注  
 提示文本是组合框控件的输入区域中显示的提示。 直至用户提供输入，则会显示的提示文本。  
  
 此方法可发送[CB_GETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb775843)消息，Windows SDK 中介绍。  
  
##  <a name="getcursel"></a>CComboBox::GetCurSel  
 调用此成员函数可确定选择组合框中的哪一项。  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>返回值  
 组合框，列表框中当前选定项的从零开始索引或**CB_ERR**如果未不选定任何项。  
  
### <a name="remarks"></a>备注  
 `GetCurSel`返回到列表的索引。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#15](../../mfc/reference/codesnippet/cpp/ccombobox-class_15.cpp)]  
  
##  <a name="getdroppedcontrolrect"></a>CComboBox::GetDroppedControlRect  
 调用`GetDroppedControlRect`成员函数可检索下拉组合框的可见 （删除下） 列表框中的屏幕坐标。  
  
```  
void GetDroppedControlRect(LPRECT lprect) const;  
```  
  
### <a name="parameters"></a>参数  
 *lprect*  
 指向[RECT 结构](../../mfc/reference/rect-structure1.md)，是否要接收坐标。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#16](../../mfc/reference/codesnippet/cpp/ccombobox-class_16.cpp)]  
  
##  <a name="getdroppedstate"></a>CComboBox::GetDroppedState  
 调用`GetDroppedState`成员函数来确定下拉组合框的列表框中是可见的 （向下删除）。  
  
```  
BOOL GetDroppedState() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果列表框中可见; 则为非 0否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#17](../../mfc/reference/codesnippet/cpp/ccombobox-class_17.cpp)]  
  
##  <a name="getdroppedwidth"></a>CComboBox::GetDroppedWidth  
 调用此函数可检索的最小的允许宽度，以像素为单位，组合框的列表框。  
  
```  
int GetDroppedWidth() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，最小的允许宽度，以像素为单位;否则为**CB_ERR**。  
  
### <a name="remarks"></a>备注  
 此函数仅适用于组合框[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式。  
  
 默认情况下，下拉列表框中允许的最小宽度为 0。 可以通过调用设置允许的最小宽度[SetDroppedWidth](#setdroppedwidth)。 组合框的列表框部分显示时，其宽度为较大的允许的最小宽度或组合框宽度。  
  
### <a name="example"></a>示例  
  请参阅示例[SetDroppedWidth](#setdroppedwidth)。  
  
##  <a name="geteditsel"></a>CComboBox::GetEditSel  
 获取组合框编辑控件中当前所选内容的起始和结束字符位置。  
  
```  
DWORD GetEditSel() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个 32 位值，之后的高序位字中的选定内容的末尾包含低序位字中的起始位置和未选定的第一个字符的位置。 如果此函数使用而无需编辑控件，组合框上**CB_ERR**返回。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#18](../../mfc/reference/codesnippet/cpp/ccombobox-class_18.cpp)]  
  
##  <a name="getextendedui"></a>CComboBox::GetExtendedUI  
 调用`GetExtendedUI`成员函数，以确定一个组合框的默认用户界面或扩展的用户界面。  
  
```  
BOOL GetExtendedUI() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果组合框中具有扩展的用户界面中; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 可以通过以下方式确定扩展的用户界面：  
  
-   单击静态控件将显示仅与组合框的列表框[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式。  
  
-   按向下箭头键显示 （F4 为禁用） 的列表框。  
  
 静态控件中滚动才被禁用时的项列表不可见 （箭头将禁用键）。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#19](../../mfc/reference/codesnippet/cpp/ccombobox-class_19.cpp)]  
  
##  <a name="gethorizontalextent"></a>CComboBox::GetHorizontalExtent  
 从组合框检索以依据组合框的列表框部分可以水平滚动的像素为单位的宽度。  
  
```  
UINT GetHorizontalExtent() const;  
```  
  
### <a name="return-value"></a>返回值  
 组合框，以像素为单位的列表框部分可滚动宽度。  
  
### <a name="remarks"></a>备注  
 这是仅适用于组合框的列表框部分具有水平滚动条。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#20](../../mfc/reference/codesnippet/cpp/ccombobox-class_20.cpp)]  
  
##  <a name="getitemdata"></a>CComboBox::GetItemData  
 检索与指定的组合框项关联的应用程序提供 32 位值。  
  
```  
DWORD_PTR GetItemData(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 包含组合框的列表框中的项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 该项目，与关联的 32 位值或**CB_ERR**如果发生错误。  
  
### <a name="remarks"></a>备注  
 32 位值可以设置与`dwItemData`参数[SetItemData](#setitemdata)成员函数调用。 使用`GetItemDataPtr`成员函数要检索的 32 位值是否为指针 ( **void\***)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#21](../../mfc/reference/codesnippet/cpp/ccombobox-class_21.cpp)]  
  
##  <a name="getitemdataptr"></a>CComboBox::GetItemDataPtr  
 检索与为指针指定的组合框项关联的应用程序提供 32 位值 ( **void\***)。  
  
```  
void* GetItemDataPtr(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 包含组合框的列表框中的项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 检索一个指针，则为-1，如果发生错误。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#22](../../mfc/reference/codesnippet/cpp/ccombobox-class_22.cpp)]  
  
##  <a name="getitemheight"></a>CComboBox::GetItemHeight  
 调用`GetItemHeight`成员函数以检索在组合框的列表项的高度。  
  
```  
int GetItemHeight(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定组合框的高度是要检索的组件。 如果`nIndex`参数的值为-1，检索的组合框的编辑控件 （或静态文本） 部分的高度。 如果组合框中具有[CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式，`nIndex`指定其高度是要检索的列表项的从零开始索引。 否则为`nIndex`应设置为 0。  
  
### <a name="return-value"></a>返回值  
 以像素为单位，组合框中指定的项的高度。 返回值是 **CB_ERR** 如果发生错误。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#23](../../mfc/reference/codesnippet/cpp/ccombobox-class_23.cpp)]  
  
##  <a name="getlbtext"></a>CComboBox::GetLBText  
 从组合框的列表中获取的字符串。  
  
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
 指向以将接收字符串的缓冲区。 缓冲区必须具有足够空间的字符串和终止 null 字符。  
  
 `rString`  
 对 `CString` 的引用。  
  
### <a name="return-value"></a>返回值  
 不包括终止 null 字符的字符串的长度 （以字节为单位）。 如果`nIndex`未指定有效的索引，则返回值是**CB_ERR**。  
  
### <a name="remarks"></a>备注  
 此成员的第二种形式函数填充`CString`用项的文本的对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#24](../../mfc/reference/codesnippet/cpp/ccombobox-class_24.cpp)]  
  
##  <a name="getlbtextlen"></a>CComboBox::GetLBTextLen  
 获取组合框的列表框中的字符串的长度。  
  
```  
int GetLBTextLen(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 包含列表框中字符串的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 以字节为单位，不包括终止 null 字符的字符串的长度。 如果`nIndex`未指定有效的索引，则返回值是**CB_ERR**。  
  
### <a name="example"></a>示例  
  请参阅示例[CComboBox::GetLBText](#getlbtext)。  
  
##  <a name="getlocale"></a>CComboBox::GetLocale  
 检索使用组合框的区域设置。  
  
```  
LCID GetLocale() const;  
```  
  
### <a name="return-value"></a>返回值  
 组合框中的字符串的区域设置标识符 (LCID) 值。  
  
### <a name="remarks"></a>备注  
 则使用区域设置，例如，若要确定已排序的组合框中的字符串的排序顺序。  
  
### <a name="example"></a>示例  
  请参阅示例[CComboBox::SetLocale](#setlocale)。  
  
##  <a name="getminvisible"></a>CComboBox::GetMinVisible  
 获取当前的组合框控件的下拉列表中的可见项的最小数目。  
  
```  
int GetMinVisible() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前的下拉列表中的可见项的最小数目。  
  
### <a name="remarks"></a>备注  
 此方法可发送[CB_GETMINVISIBLE](http://msdn.microsoft.com/library/windows/desktop/bb775915)消息，Windows SDK 中介绍。  
  
##  <a name="gettopindex"></a>CComboBox::GetTopIndex  
 检索在组合框的列表框部分中的第一个可见项的从零开始索引。  
  
```  
int GetTopIndex() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，组合框的列表框部分中的第一个可见项的从零开始索引**CB_ERR**否则为。  
  
### <a name="remarks"></a>备注  
 最初，0 项位于顶部的列表框中，但如果滚动列表框中，另一项可能在顶部。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#25](../../mfc/reference/codesnippet/cpp/ccombobox-class_25.cpp)]  
  
##  <a name="initstorage"></a>CComboBox::InitStorage  
 在组合框的列表框部分中存储的列表框项的分配内存。  
  
```  
int InitStorage(
    int nItems,  
    UINT nBytes);
```  
  
### <a name="parameters"></a>参数  
 `nItems`  
 指定要添加的项的数目。  
  
 `nBytes`  
 以字节为单位，分配项字符串中指定内存的量。  
  
### <a name="return-value"></a>返回值  
 如果成功，最大项数的组合框的列表框部分可以存储之前需要内存重新分配，否则**CB_ERRSPACE**，这意味着没有足够的内存是可用。  
  
### <a name="remarks"></a>备注  
 将大量的项添加到列表框部分之前调用此函数`CComboBox`。  
  
 仅 Windows 95/98:`wParam`参数最多为 16 位值。 这意味着列表框不能包含多个 32,767 的项。 尽管限制项的数目，则列表框中的项的总大小仅受可用内存。  
  
 此函数可帮助加快拥有大量的项 (超过 100) 的列表框的初始化。 它预分配指定的数量的内存，因此后续[AddString](#addstring)， [InsertString](#insertstring)，和[Dir](#dir)函数采用最短的时间。 你可以使用估计值的参数。 如果你要估计得高一些，一些额外的内存分配;如果你低估，正常分配用于超过预分配的量的项。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#26](../../mfc/reference/codesnippet/cpp/ccombobox-class_26.cpp)]  
  
##  <a name="insertstring"></a>CComboBox::InsertString  
 将字符串插入组合框的列表框。  
  
```  
int InsertString(
    int nIndex,  
    LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 包含一个索引（该索引从零开始），该索引指向列表框中将接收字符串的位置。 如果此参数为-1，则字符串被添加到列表的末尾。  
  
 `lpszString`  
 指向要插入的以 null 结尾的字符串。  
  
### <a name="return-value"></a>返回值  
 插入该字符串的位置的索引（索引从零开始）。 返回值是 **CB_ERR** 如果发生错误。 如果没有足够空间可用于存储新的字符串，则返回值为 **CB_ERRSPACE** 。  
  
### <a name="remarks"></a>备注  
 与不同[AddString](#addstring)成员函数，`InsertString`成员函数不会导致与列表[CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式进行排序。  
  
> [!NOTE]
>  Windows **ComboBoxEx** 控件不支持此函数。 此控件的详细信息，请参阅[ComboBoxEx 控件](http://msdn.microsoft.com/library/windows/desktop/bb775738)Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#27](../../mfc/reference/codesnippet/cpp/ccombobox-class_27.cpp)]  
  
##  <a name="limittext"></a>CComboBox::LimitText  
 限制用户可以输入到组合框编辑控件的文本的长度以字节为单位。  
  
```  
BOOL LimitText(int nMaxChars);
```  
  
### <a name="parameters"></a>参数  
 `nMaxChars`  
 指定用户可以输入的文本的长度 （以字节为单位）。 如果此参数为 0，则会将文本长度设置为 65535 字节。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为非 0。 如果调用了带有样式的组合框[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或而无需编辑控件组合框，则返回值为**CB_ERR**。  
  
### <a name="remarks"></a>备注  
 如果组合框没有样式[CBS_AUTOHSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)，设置文本限制为大于编辑控件的大小将产生任何影响。  
  
 `LimitText`仅限制用户可以输入的文本。 它不起任何文本已在编辑控件时发送消息，也不会影响复制到编辑控件中，选中列表框中的字符串文本的长度。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#28](../../mfc/reference/codesnippet/cpp/ccombobox-class_28.cpp)]  
  
##  <a name="measureitem"></a>CComboBox::MeasureItem  
 创建带有所有者绘制样式的组合框时，由框架调用。  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpMeasureItemStruct`  
 指向的长指针[MEASUREITEMSTRUCT](../../mfc/reference/measureitemstruct-structure.md)结构。  
  
### <a name="remarks"></a>备注  
 默认情况下，此成员函数没有任何影响。 重写该成员函数，并填写`MEASUREITEMSTRUCT`结构以通知 Windows 的维度的列表框中组合框。 如果使用创建组合框[CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式，框架会调用此成员函数为列表框中的每个项。 否则，此成员是只能调用一次。  
  
 使用**CBS_OWNERDRAWFIXED**中创建一个所有者描述的组合框样式[SubclassDlgItem](../../mfc/reference/cwnd-class.md#subclassdlgitem)成员函数`CWnd`涉及进一步编程注意事项。 请参阅中的讨论[技术注意 14](../../mfc/tn014-custom-controls.md)。  
  
 请参阅[CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)有关的说明`MEASUREITEMSTRUCT`结构。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#29](../../mfc/reference/codesnippet/cpp/ccombobox-class_29.cpp)]  
  
##  <a name="paste"></a>CComboBox::Paste  
 将数据从剪贴板插入当前光标位置处的组合框编辑控件。  
  
```  
void Paste();
```  
  
### <a name="remarks"></a>备注  
 只有当剪贴板包含中的数据插入数据**CF_TEXT**格式。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#30](../../mfc/reference/codesnippet/cpp/ccombobox-class_30.cpp)]  
  
##  <a name="resetcontent"></a>CComboBox::ResetContent  
 中移除所有项从列表框中字符和编辑组合框控件。  
  
```  
void ResetContent();
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#31](../../mfc/reference/codesnippet/cpp/ccombobox-class_31.cpp)]  
  
##  <a name="selectstring"></a>CComboBox::SelectString  
 组合框，列表框中的字符串搜索，并找到该字符串，如果在列表框中选择字符串并将其复制到编辑控件。  
  
```  
int SelectString(
    int nStartAfter,  
    LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>参数  
 `nStartAfter`  
 包含要搜索的第一项之前的项的从零开始索引。 如果搜索到达搜索列表框的底部，它将继续从列表框的顶部回由指定的项`nStartAfter`。 如果为-1，从开始处搜索整个列表框。  
  
 `lpszString`  
 指向以 null 结尾的字符串，其中包含要搜索的前缀。 搜索是独立的因此此字符串可以包含任何组合的大写和小写字母。  
  
### <a name="return-value"></a>返回值  
 如果已找到该字符串的选定项的从零开始的索引。 如果搜索未成功，则返回值是**CB_ERR**且未更改当前所选内容。  
  
### <a name="remarks"></a>备注  
 仅当其初始字符 （从起始点） 与匹配的前缀字符串中的字符，选择一个字符串。  
  
 请注意，`SelectString`和`FindString`成员函数查找字符串，但`SelectString`成员函数还将选择字符串。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#32](../../mfc/reference/codesnippet/cpp/ccombobox-class_32.cpp)]  
  
##  <a name="setcuebanner"></a>CComboBox::SetCueBanner  
 设置为组合框控件显示的提示文本。  
  
```  
BOOL SetCueBanner(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*lpszText*|为包含提示文本的以 null 结尾的缓冲区的指针。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 提示文本是组合框控件的输入区域中显示的提示。 直至用户提供输入，则会显示的提示文本。  
  
 此方法可发送[CB_SETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb775897)消息，Windows SDK 中介绍。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_combobox`，即用于以编程方式访问组合框控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例设置组合框控件的提示横幅。  
  
 [!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]  
  
##  <a name="setcursel"></a>CComboBox::SetCurSel  
 组合框的列表框中选择一个字符串。  
  
```  
int SetCurSel(int nSelect);
```  
  
### <a name="parameters"></a>参数  
 `nSelect`  
 指定要选择的字符串的从零开始的索引。 如果为-1，删除任何当前的选择列表框中，并清除编辑控件。  
  
### <a name="return-value"></a>返回值  
 如果消息已成功中选定的项的从零开始的索引。 返回值是**CB_ERR**如果`nSelect`大于列表中的项的数目或如果`nSelect`设置为-1，清除选择。  
  
### <a name="remarks"></a>备注  
 如有必要，列表框中滚动到视图字符串中 （如果该列表框是可见的）。 组合框编辑控件中的文本更改以反映新的选择。 删除任何以前的选择列表框中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#33](../../mfc/reference/codesnippet/cpp/ccombobox-class_35.cpp)]  
  
##  <a name="setdroppedwidth"></a>CComboBox::SetDroppedWidth  
 调用此函数可设置的最小的允许宽度，以像素为单位，组合框的列表框。  
  
```  
int SetDroppedWidth(UINT nWidth);
```  
  
### <a name="parameters"></a>参数  
 `nWidth`  
 组合框，以像素为单位的列表框部分的最小允许宽度。  
  
### <a name="return-value"></a>返回值  
 如果成功，新宽度的列表框中，否则**CB_ERR**。  
  
### <a name="remarks"></a>备注  
 此函数仅适用于组合框[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式。  
  
 默认情况下，下拉列表框中允许的最小宽度为 0。 组合框的列表框部分显示时，其宽度为较大的允许的最小宽度或组合框宽度。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#34](../../mfc/reference/codesnippet/cpp/ccombobox-class_36.cpp)]  
  
##  <a name="seteditsel"></a>CComboBox::SetEditSel  
 选择组合框编辑控件中的字符。  
  
```  
BOOL SetEditSel(
    int nStartChar,  
    int nEndChar);
```  
  
### <a name="parameters"></a>参数  
 `nStartChar`  
 指定的起始位置。 如果起始位置设置为-1，则将移除任何现有的选择。  
  
 `nEndChar`  
 指定的结束位置。 如果结束位置到最后一个设置为-1，然后从起始位置的所有文本选择编辑控件中的字符。  
  
### <a name="return-value"></a>返回值  
 如果该成员函数成功，则非零否则为 0。 它是**CB_ERR**如果`CComboBox`具有[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式或不是列表框。  
  
### <a name="remarks"></a>备注  
 位置是从零开始。 若要选择的编辑控件的第一个字符，你可以指定 0 的起始位置。 结束位置后的字符只是要选择的最后一个字符。 例如，若要选择的编辑控件的前四个字符，会使用 0 的起始位置和结束位置的 4。  
  
> [!NOTE]
>  Windows **ComboBoxEx** 控件不支持此函数。 此控件的详细信息，请参阅[ComboBoxEx 控件](http://msdn.microsoft.com/library/windows/desktop/bb775738)Windows SDK 中。  
  
### <a name="example"></a>示例  
  请参阅示例[CComboBox::GetEditSel](#geteditsel)。  
  
##  <a name="setextendedui"></a>CComboBox::SetExtendedUI  
 调用`SetExtendedUI`成员函数以选择的默认用户界面或组合框具有扩展的用户界面[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式。  
  
```  
int SetExtendedUI(BOOL bExtended = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *bExtended*  
 指定组合框是否应使用扩展的用户界面或默认用户界面。 值为**TRUE**选择扩展用户界面; 如果值为**FALSE**选择标准用户界面。  
  
### <a name="return-value"></a>返回值  
 **CB_OKAY**如果操作成功，或**CB_ERR**如果发生错误。  
  
### <a name="remarks"></a>备注  
 可以通过以下方式确定扩展的用户界面：  
  
-   单击静态控件将显示仅与组合框的列表框**CBS_DROPDOWNLIST**样式。  
  
-   按向下箭头键显示 （F4 为禁用） 的列表框。  
  
 项列表不可见时，静态控件中滚动会禁用 （禁用箭头键）。  
  
### <a name="example"></a>示例  
  请参阅示例[CComboBox::GetExtendedUI](#getextendedui)。  
  
##  <a name="sethorizontalextent"></a>CComboBox::SetHorizontalExtent  
 设置的宽度，以像素为单位，所依据的组合框的列表框部分可被滚动水平。  
  
```  
void SetHorizontalExtent(UINT nExtent);
```  
  
### <a name="parameters"></a>参数  
 *nExtent*  
 指定所依据的组合框的列表框部分可以水平滚动的像素数。  
  
### <a name="remarks"></a>备注  
 如果列表框的宽度小于此值，水平滚动条将水平滚动列表框中的项。 如果列表框的宽度等于或大于此值，将会隐藏水平滚动条或组合框中具有[CBS_DISABLENOSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式，禁用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#35](../../mfc/reference/codesnippet/cpp/ccombobox-class_37.cpp)]  
  
##  <a name="setitemdata"></a>CComboBox::SetItemData  
 设置与组合框中指定的项关联的 32 位值。  
  
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
 **CB_ERR**如果发生错误。  
  
### <a name="remarks"></a>备注  
 使用`SetItemDataPtr`成员函数，如果 32 位项将是指针。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#36](../../mfc/reference/codesnippet/cpp/ccombobox-class_38.cpp)]  
  
##  <a name="setitemdataptr"></a>CComboBox::SetItemDataPtr  
 设置与为指定的指针的组合框中指定的项关联的 32 位值 ( **void\***)。  
  
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
 **CB_ERR**如果发生错误。  
  
### <a name="remarks"></a>备注  
 此指针就保持有效的组合框中，整个生命周期的即使在添加或删除项时，可能会更改项的组合框内的相对位置。 因此，可以更改在框中的项的索引，但指针保持可靠。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#37](../../mfc/reference/codesnippet/cpp/ccombobox-class_39.cpp)]  
  
##  <a name="setitemheight"></a>CComboBox::SetItemHeight  
 调用`SetItemHeight`成员函数将列表项的高度设置组合框或组合框的编辑控件 （或静态文本） 部分的高度。  
  
```  
int SetItemHeight(
    int nIndex,  
    UINT cyItemHeight);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定是否已设置的列表项的高度或组合框的编辑控件 （或静态文本） 部分的高度。  
  
 如果组合框中具有[CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式，`nIndex`指定其高度，则为设置; 否则为列表项的从零开始索引`nIndex`必须是 0 和将设置项的所有列表的高度。  
  
 如果`nIndex`为-1，编辑控件的高度或组合框的静态文本一部分将设置。  
  
 `cyItemHeight`  
 以像素为单位，组合框组件由标识指定的高度， `nIndex`。  
  
### <a name="return-value"></a>返回值  
 **CB_ERR**如果索引或高度为无效; 否则为 0。  
  
### <a name="remarks"></a>备注  
 组合框的编辑控件 （或静态文本） 部分的高度设置独立于列表项的高度。 应用程序必须确保编辑控件 （或静态文本） 部分的高度不小于的特定列表框项的高度。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#38](../../mfc/reference/codesnippet/cpp/ccombobox-class_40.cpp)]  
  
##  <a name="setlocale"></a>CComboBox::SetLocale  
 设置此组合框的区域设置标识符。  
  
```  
LCID SetLocale(LCID nNewLocale);
```  
  
### <a name="parameters"></a>参数  
 `nNewLocale`  
 新区域设置标识符 (LCID) 要设置的值的组合框。  
  
### <a name="return-value"></a>返回值  
 此组合框的上一个区域设置标识符 (LCID) 的值。  
  
### <a name="remarks"></a>备注  
 如果**SetLocale**不调用，默认值从系统获取区域设置。 可以使用控制面板中的修改此系统默认区域设置区域 （或国际） 应用程序。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#39](../../mfc/reference/codesnippet/cpp/ccombobox-class_41.cpp)]  
  
##  <a name="setminvisibleitems"></a>CComboBox::SetMinVisibleItems  
 在下拉列表中当前的组合框控件设置可见项的最小数目。  
  
```  
BOOL SetMinVisibleItems(int iMinVisible);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in] `iMinVisible`|指定可见项的最小数目。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[CB_SETMINVISIBLE](http://msdn.microsoft.com/library/windows/desktop/bb775915)消息，Windows SDK 中介绍。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_combobox`，即用于以编程方式访问组合框控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例在一个组合框控件的下拉列表中插入 20 个项。 然后，它指定当用户按下的下拉箭头时，显示最少 10 项。  
  
 [!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]  
  
##  <a name="settopindex"></a>CComboBox::SetTopIndex  
 确保特定项的组合框的列表框部分中可见。  
  
```  
int SetTopIndex(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定列表框项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为零或**CB_ERR**如果发生错误。  
  
### <a name="remarks"></a>备注  
 系统滚动列表框中指定的任意一项之前`nIndex`显示顶部的列表框或最大滚动范围已达到。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CComboBox#40](../../mfc/reference/codesnippet/cpp/ccombobox-class_42.cpp)]  
  
##  <a name="showdropdown"></a>CComboBox::ShowDropDown  
 显示或隐藏具有组合框的列表框[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式。  
  
```  
void ShowDropDown(BOOL bShowIt = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *bShowIt*  
 指定是否可显示或隐藏下拉列表框。 值为**TRUE**显示列表框。 值为**FALSE**隐藏列表框。  
  
### <a name="remarks"></a>备注  
 默认情况下，此样式组合框将显示列表框。  
  
 此成员函数不起使用创建一个组合框[CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式。  
  
### <a name="example"></a>示例  
  请参阅示例[CComboBox::GetDroppedState](#getdroppedstate)。  
  
## <a name="see-also"></a>请参阅  
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
