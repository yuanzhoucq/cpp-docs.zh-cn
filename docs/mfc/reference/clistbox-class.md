---
title: "CListBox 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CListBox
- AFXWIN/CListBox
- AFXWIN/CListBox::CListBox
- AFXWIN/CListBox::AddString
- AFXWIN/CListBox::CharToItem
- AFXWIN/CListBox::CompareItem
- AFXWIN/CListBox::Create
- AFXWIN/CListBox::DeleteItem
- AFXWIN/CListBox::DeleteString
- AFXWIN/CListBox::Dir
- AFXWIN/CListBox::DrawItem
- AFXWIN/CListBox::FindString
- AFXWIN/CListBox::FindStringExact
- AFXWIN/CListBox::GetAnchorIndex
- AFXWIN/CListBox::GetCaretIndex
- AFXWIN/CListBox::GetCount
- AFXWIN/CListBox::GetCurSel
- AFXWIN/CListBox::GetHorizontalExtent
- AFXWIN/CListBox::GetItemData
- AFXWIN/CListBox::GetItemDataPtr
- AFXWIN/CListBox::GetItemHeight
- AFXWIN/CListBox::GetItemRect
- AFXWIN/CListBox::GetListBoxInfo
- AFXWIN/CListBox::GetLocale
- AFXWIN/CListBox::GetSel
- AFXWIN/CListBox::GetSelCount
- AFXWIN/CListBox::GetSelItems
- AFXWIN/CListBox::GetText
- AFXWIN/CListBox::GetTextLen
- AFXWIN/CListBox::GetTopIndex
- AFXWIN/CListBox::InitStorage
- AFXWIN/CListBox::InsertString
- AFXWIN/CListBox::ItemFromPoint
- AFXWIN/CListBox::MeasureItem
- AFXWIN/CListBox::ResetContent
- AFXWIN/CListBox::SelectString
- AFXWIN/CListBox::SelItemRange
- AFXWIN/CListBox::SetAnchorIndex
- AFXWIN/CListBox::SetCaretIndex
- AFXWIN/CListBox::SetColumnWidth
- AFXWIN/CListBox::SetCurSel
- AFXWIN/CListBox::SetHorizontalExtent
- AFXWIN/CListBox::SetItemData
- AFXWIN/CListBox::SetItemDataPtr
- AFXWIN/CListBox::SetItemHeight
- AFXWIN/CListBox::SetLocale
- AFXWIN/CListBox::SetSel
- AFXWIN/CListBox::SetTabStops
- AFXWIN/CListBox::SetTopIndex
- AFXWIN/CListBox::VKeyToItem
dev_langs:
- C++
helpviewer_keywords:
- CListBox class
- list boxes
ms.assetid: 7ba3c699-c286-4cd9-9066-532c41ec05d1
caps.latest.revision: 26
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
ms.openlocfilehash: 4b1b1963af7740820b1285c3df8724f9ea4332b1
ms.lasthandoff: 04/01/2017

---
# <a name="clistbox-class"></a>CListBox 类
提供 Windows 列表框功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CListBox : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CListBox::CListBox](#clistbox)|构造 `CListBox` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CListBox::AddString](#addstring)|将字符串添加到列表框中。|  
|[CListBox::CharToItem](#chartoitem)|重写以提供自定义`WM_CHAR`为所有者描述列表框未字符串处理。|  
|[CListBox::CompareItem](#compareitem)|由框架调用以确定新项的已排序的所有者描述列表框中的位置。|  
|[CListBox::Create](#create)|创建 Windows 列表框并将其附加到`CListBox`对象。|  
|[CListBox::DeleteItem](#deleteitem)|当用户从一个所有者描述列表框中删除项时，由框架调用。|  
|[CListBox::DeleteString](#deletestring)|从列表框中删除一个字符串。|  
|[CListBox::Dir](#dir)|将文件名和 / 从当前目录或驱动器，添加到列表框中。|  
|[CListBox::DrawItem](#drawitem)|由框架的所有者描述列表框中更改的可视方面时调用。|  
|[CListBox::FindString](#findstring)|列表框中的字符串的搜索。|  
|[CListBox::FindStringExact](#findstringexact)|查找与指定的字符串匹配的第一个列表框字符串。|  
|[CListBox::GetAnchorIndex](#getanchorindex)|检索列表框中当前的定位点项的从零开始索引。|  
|[CListBox::GetCaretIndex](#getcaretindex)|确定在多选列表框中具有焦点矩形的项的索引。|  
|[CListBox::GetCount](#getcount)|在列表框中返回字符串的数量。|  
|[CListBox::GetCurSel](#getcursel)|在列表框中返回当前选定的字符串的从零开始的索引。|  
|[CListBox::GetHorizontalExtent](#gethorizontalextent)|返回以像素为单位可水平滚动列表框的宽度。|  
|[CListBox::GetItemData](#getitemdata)|返回与列表框项关联的 32 位值。|  
|[CListBox::GetItemDataPtr](#getitemdataptr)|将指针返回到列表框项。|  
|[CListBox::GetItemHeight](#getitemheight)|确定列表框中项的高度。|  
|[CListBox::GetItemRect](#getitemrect)|返回当前显示的列表框项的边框。|  
|[CListBox::GetListBoxInfo](#getlistboxinfo)|检索每个列的项的数目。|  
|[CListBox::GetLocale](#getlocale)|检索列表框中的区域设置标识符。|  
|[CListBox::GetSel](#getsel)|返回一个列表框项的选择状态。|  
|[CListBox::GetSelCount](#getselcount)|返回多选列表框中当前选定的字符串的数量。|  
|[CListBox::GetSelItems](#getselitems)|返回列表框中当前选定的字符串的索引。|  
|[CListBox::GetText](#gettext)|将列表框项复制到缓冲区。|  
|[CListBox::GetTextLen](#gettextlen)|返回以字节为单位的列表框项的长度。|  
|[CListBox::GetTopIndex](#gettopindex)|在列表框中返回的第一个可见字符串的索引。|  
|[CListBox::InitStorage](#initstorage)|预分配列表框项和字符串的内存块的能力。|  
|[CListBox::InsertString](#insertstring)|在列表框中的特定位置插入一个字符串。|  
|[CListBox::ItemFromPoint](#itemfrompoint)|返回最接近的点的列表框项的索引。|  
|[CListBox::MeasureItem](#measureitem)|当所有者描述列表框创建来确定列表框中维度时，由框架调用。|  
|[CListBox::ResetContent](#resetcontent)|清除从列表框中的所有条目。|  
|[CListBox::SelectString](#selectstring)|搜索并在单项选择列表框中选择一个字符串。|  
|[CListBox::SelItemRange](#selitemrange)|选择或取消选择一系列多选列表框中的字符串。|  
|[CListBox::SetAnchorIndex](#setanchorindex)|在多选列表框中开始的扩展的选择设置定位点。|  
|[CListBox::SetCaretIndex](#setcaretindex)|在多选列表框中将焦点矩形设置为指定索引处的项。|  
|[CListBox::SetColumnWidth](#setcolumnwidth)|设置多列的列表框中的列宽度。|  
|[CListBox::SetCurSel](#setcursel)|选择一个列表框中的字符串。|  
|[CListBox::SetHorizontalExtent](#sethorizontalextent)|以一个列表框可被水平滚动的像素为单位设置宽度。|  
|[CListBox::SetItemData](#setitemdata)|设置与列表框项关联的 32 位值。|  
|[CListBox::SetItemDataPtr](#setitemdataptr)|将指针设置为列表框项。|  
|[CListBox::SetItemHeight](#setitemheight)|列表框中设置的项的高度。|  
|[CListBox::SetLocale](#setlocale)|设置列表框中的区域设置标识符。|  
|[CListBox::SetSel](#setsel)|选择或取消选择多选列表框中的列表框项。|  
|[CListBox::SetTabStops](#settabstops)|设置列表框中的制表位位置。|  
|[CListBox::SetTopIndex](#settopindex)|列表框中设置第一个可见字符串的从零开始索引。|  
|[CListBox::VKeyToItem](#vkeytoitem)|重写以提供自定义`WM_KEYDOWN`为列表框处理**LBS_WANTKEYBOARDINPUT**样式集。|  
  
## <a name="remarks"></a>备注  
 列表框中显示项，如文件名，用户可以查看和选择的列表。  
  
 在单选择列表框中，用户可以选择只有一项。 在多选列表框中，可以选择一系列项。 当用户选择一个项时，则会突出显示和列表框向父窗口发送通知消息。  
  
 从对话框模板或直接在代码中，可以创建一个列表框。 若要直接创建它，请构造`CListBox`对象，然后调用[创建](#create)成员函数以创建 Windows 列表框控件并将其附加到`CListBox`对象。 若要使用的对话框模板中的列表框，列表框中声明变量对话框类，然后使用`DDX_Control`在自己对话框类的`DoDataExchange`函数连接到该控件的成员变量。 （这是为你自动完成时将控制变量添加到对话框类。）  
  
 构造可以是派生自类中的一步过程`CListBox`。 编写派生的类和调用构造函数**创建**从构造函数中。  
  
 如果你想要处理 Windows 通知消息发送到其父列表框 (通常从派生的类[CDialog](../../mfc/reference/cdialog-class.md))，将消息映射条目和消息处理程序成员函数添加到每条消息的父类。  
  
 每个消息映射条目采用以下形式︰  
  
 `ON_Notification( id, memberFxn )`  
  
 其中`id`指定发送通知的列表框控件的子窗口 ID 和`memberFxn`是父成员函数编写以处理通知的名称。  
  
 父元素的函数原型如下所示︰  
  
 `afx_msg void memberFxn( );`  
  
 以下是潜在的消息映射项和将给父级发送的用例的说明的列表︰  
  
- **ON_LBN_DBLCLK**用户双击列表框中的字符串。 具有的列表框[LBS_NOTIFY](../../mfc/reference/list-box-styles.md)样式将发送该通知消息。  
  
- **ON_LBN_ERRSPACE**列表框中无法分配足够的内存来满足请求。  
  
- **ON_LBN_KILLFOCUS**列表框中失去输入的焦点。  
  
- **ON_LBN_SELCANCEL**取消当前的列表框中选择。 列表框上时，此消息将只发送**LBS_NOTIFY**样式。  
  
- **ON_LBN_SELCHANGE**列表框中的选项已更改。 如果被更改所选内容不会发送此通知[CListBox::SetCurSel](#setcursel)成员函数。 此通知仅适用于具有一个列表框**LBS_NOTIFY**样式。 **LBN_SELCHANGE**通知消息被发送进行多选列表框每当用户按箭头键，即使所选内容不会更改。  
  
- **ON_LBN_SETFOCUS**列表框中将接收输入的焦点。  
  
- **ON_WM_CHARTOITEM**具有没有字符串一个所有者描述列表框接收`WM_CHAR`消息。  
  
- **ON_WM_VKEYTOITEM**在列表框中**LBS_WANTKEYBOARDINPUT**样式接收`WM_KEYDOWN`消息。  
  
 如果你创建`CListBox`（通过对话框资源） 对话框中的对象`CListBox`当用户关闭对话框中，将自动销毁对象。  
  
 如果你创建`CListBox`对象在窗口中，你可能需要在销毁`CListBox`对象。 如果你创建`CListBox`对象在堆栈上，自动销毁。 如果你创建`CListBox`使用堆上的对象**新**函数，必须调用**删除**上要销毁它，当用户关闭的父窗口的对象。  
  
 如果分配任何内存`CListBox`对象，请重写`CListBox`析构函数，若要释放的分配。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CListBox`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="addstring"></a>CListBox::AddString  
 将字符串添加到列表框中。  
  
```  
int AddString(LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>参数  
 `lpszItem`  
 指向要添加的以 null 结尾的字符串。  
  
### <a name="return-value"></a>返回值  
 指向列表框中的字符串的从零开始索引。 返回值是**LB_ERR**如果发生错误; 返回值是**LB_ERRSPACE**如果没有足够的空间来存储新的字符串。  
  
### <a name="remarks"></a>备注  
 如果使用列表框不创建了[LBS_SORT](../../mfc/reference/list-box-styles.md)样式，则字符串添加到列表的末尾。 否则为该字符串插入到列表中，并对列表进行排序。 如果使用列表框中创建了**LBS_SORT**但不是样式[LBS_HASSTRINGS](../../mfc/reference/list-box-styles.md)样式，框架对列表进行排序通过一个或多个调用`CompareItem`成员函数。  
  
 使用[InsertString](#insertstring)将字符串插入到列表框中的特定位置。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 3](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]  
  
##  <a name="chartoitem"></a>CListBox::CharToItem  
 当列表框中的父窗口接收时由框架调用`WM_CHARTOITEM`从列表框中的消息。  
  
```  
virtual int CharToItem(
    UINT nKey,  
    UINT nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nKey`  
 用户键入的字符的 ANSI 代码。  
  
 `nIndex`  
 列表框中插入符号的当前位置。  
  
### <a name="return-value"></a>返回值  
 返回-1 或 2 任何进一步的操作或一个非负的数字以指定要对其键击执行默认操作的列表框项的索引。 默认实现返回-1。  
  
### <a name="remarks"></a>备注  
 `WM_CHARTOITEM`在接收时，消息由列表框中发送`WM_CHAR`消息，但仅当列表的框满足所有这些条件︰  
  
-   是一个所有者描述列表框。  
  
-   没有[LBS_HASSTRINGS](../../mfc/reference/list-box-styles.md)样式集。  
  
-   具有至少一个项。  
  
 你绝不应自己调用此函数。 重写此函数可提供你自己的自定义处理操作的键盘消息。  
  
 在替代中，您必须返回一个值，以告知框架执行哪些操作。 返回值-1 或 2 表示将处理的选择项的所有方面，需要由列表框中的任何进一步的操作。 然后再返回-1 或-2，你无法设置所选内容或移动插入符号或两个。 若要设置所选内容，使用[SetCurSel](#setcursel)或[SetSel](#setsel)。 若要移动插入符号，使用[SetCaretIndex](#setcaretindex)。  
  
 返回值 0 或更高版本的列表框中指定项的索引，并指明列表框中，应在给定的项键击执行默认操作。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 4](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]  
  
##  <a name="clistbox"></a>CListBox::CListBox  
 构造 `CListBox` 对象。  
  
```  
CListBox();
```  
  
### <a name="remarks"></a>备注  
 构造`CListBox`两个步骤中的对象。 首先，调用的构造函数**ClistBox** ，然后调用**创建**，其中初始化 Windows 列表框并将其附加到`CListBox`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 1](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]  
  
##  <a name="compareitem"></a>CListBox::CompareItem  
 由框架调用以确定已排序的所有者描述列表框中的新项的相对位置。  
  
```  
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpCompareItemStruct`  
 指向的长指针`COMPAREITEMSTRUCT`结构。  
  
### <a name="return-value"></a>返回值  
 指示中所述的两个项的相对位置[COMPAREITEMSTRUCT](../../mfc/reference/compareitemstruct-structure.md)结构。 它可能是以下值之一︰  
  
|值|含义|  
|-----------|-------------|  
|-1|项 2 之前进行排序的第 1 项。|  
|0|项 1 和 2 的项进行排序相同。|  
|1|项 2 后进行排序的第 1 项。|  
  
 请参阅[CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)有关的说明`COMPAREITEMSTRUCT`结构。  
  
### <a name="remarks"></a>备注  
 默认情况下，此成员函数没有任何影响。 如果你创建一个带有所有者描述列表框**LBS_SORT**样式，你必须重写该成员函数以帮助 framework 排序新项添加到列表框中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 5](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]  
  
##  <a name="create"></a>CListBox::Create  
 创建 Windows 列表框并将其附加到`CListBox`对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 指定列表框的样式。 应用的任意组合[列表框样式](../../mfc/reference/list-box-styles.md)在框中。  
  
 `rect`  
 指定列表框的大小和位置。 可以是`CRect`对象或`RECT`结构。  
  
 `pParentWnd`  
 指定列表框中的父窗口 (通常`CDialog`对象)。 它不能**NULL**。  
  
 `nID`  
 指定列表框的控件 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 构造`CListBox`两个步骤中的对象。 首先，调用的构造函数，然后调用**创建**，其中初始化 Windows 列表框并将其附加到`CListBox`对象。  
  
 当**创建**执行 Windows 发送[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)， [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)， [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)，和[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)到该列表框控件的消息。  
  
 默认情况下，通过处理这些消息的消息[OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)， [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)， [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)，和[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成员函数中`CWnd`基类。 若要扩展的默认消息处理，从派生类`CListBox`、 将消息映射添加到新的类中，和重写前面的消息处理程序成员函数。 重写`OnCreate`，例如，若要为新类执行所需的初始化。  
  
 将应用以下[窗口样式](../../mfc/reference/window-styles.md)到列表框控件。  
  
- **WS_CHILD**始终  
  
- **WS_VISIBLE**通常  
  
- **WS_DISABLED**很少  
  
- **WS_VSCROLL**添加垂直滚动条  
  
- **WS_HSCROLL**添加水平滚动条  
  
- **WS_GROUP**与组控件  
  
- **WS_TABSTOP**以允许 tab 键移到此控件  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 2](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]  
  
##  <a name="deleteitem"></a>CListBox::DeleteItem  
 当用户从所有者描述中删除项时，由框架调用`CListBox`对象或销毁列表框。  
  
```  
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpDeleteItemStruct`  
 向 Windows 的长指针[DELETEITEMSTRUCT](../../mfc/reference/deleteitemstruct-structure.md)结构，它包含有关已删除的项的信息。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现不执行任何操作。 重写此函数可重绘根据需要一个所有者描述列表框。  
  
 请参阅[CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem)有关的说明`DELETEITEMSTRUCT`结构。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 6](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]  
  
##  <a name="deletestring"></a>CListBox::DeleteString  
 删除位置中的项`nIndex`从列表框。  
  
```  
int DeleteString(UINT nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定要删除的字符串的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 在列表中剩余的字符串的计数。 返回值是**LB_ERR**如果`nIndex`指定列表中的索引大于项的数目。  
  
### <a name="remarks"></a>备注  
 后面的所有项`nIndex`现在下移一个位置。 例如，如果列表框中包含两个项，则删除第一项将导致剩余的项现在处于的第一个位置。 `nIndex`= 0 中的第一个位置的项。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 7](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]  
  
##  <a name="dir"></a>CListBox::Dir  
 添加文件名、 驱动器或这两项的列表框的列表。  
  
```  
int Dir(
    UINT attr,  
    LPCTSTR lpszWildCard);
```  
  
### <a name="parameters"></a>参数  
 `attr`  
 可以是任意组合的`enum`值中所述**CFile::GetStatu**[s](../../mfc/reference/cfile-class.md#getstatus)，或以下值的任意组合︰  
  
|值|含义|  
|-----------|-------------|  
|0x0000|可以读取或写入到文件。|  
|从 0x0001|可以从读取但不是会写入到文件。|  
|0x0002|文件不在目录列表中显示和隐藏。|  
|0x0004|文件是系统文件。|  
|0x0010|指定的名称`lpszWildCard`指定的目录。|  
|0x0020|已存档文件。|  
|0x4000|包含与指定的名称匹配的所有驱动器`lpszWildCard`。|  
|0x8000|独占标志。 如果设置独占标志，仅指定类型的文件会列出。 否则，除"正常"的文件之外还列出指定类型的文件。|  
  
 `lpszWildCard`  
 指向文件规范的字符串。 字符串可以包含通配符 (例如，*。\*)。  
  
### <a name="return-value"></a>返回值  
 最后一个文件名添加到列表中的从零开始的索引。 返回值是**LB_ERR**如果发生错误; 返回值是**LB_ERRSPACE**如果没有足够的空间来存储新的字符串。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 8](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]  
  
##  <a name="drawitem"></a>CListBox::DrawItem  
 由框架的所有者描述列表框中更改的可视方面时调用。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpDrawItemStruct`  
 指向的长指针[DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md)结构，其中包含有关所需的绘图的类型的信息。  
  
### <a name="remarks"></a>备注  
 **ItemAction**和**itemState**的成员`DRAWITEMSTRUCT`结构定义要执行的绘制操作。  
  
 默认情况下，此成员函数没有任何影响。 重写该成员函数以实现所有者描述的绘图`CListBox`对象。 应用程序应还原选择的显示上下文中提供的所有图形设备接口 (GDI) 对象`lpDrawItemStruct`之前此成员函数将终止。  
  
 请参阅[CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)有关的说明`DRAWITEMSTRUCT`结构。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 9](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]  
  
##  <a name="findstring"></a>CListBox::FindString  
 在包含指定的前缀，而无需更改的列表框中选择的列表框中查找第一个字符串。  
  
```  
int FindString(
    int nStartAfter,  
    LPCTSTR lpszItem) const;  
```  
  
### <a name="parameters"></a>参数  
 `nStartAfter`  
 包含要搜索的第一项之前的项的从零开始索引。 如果搜索到达搜索列表框的底部，它将继续从列表框的顶部回由指定的项`nStartAfter`。 如果`nStartAfter`为-1，从开始处搜索整个列表框。  
  
 `lpszItem`  
 指向以 null 结尾的字符串，其中包含要搜索的前缀。 搜索是独立的因此此字符串可能包含任何组合的大写和小写字母。  
  
### <a name="return-value"></a>返回值  
 匹配的项的从零开始索引或**LB_ERR**如果搜索未成功。  
  
### <a name="remarks"></a>备注  
 使用[SelectString](#selectstring)查找和选择字符串的成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 10](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]  
  
##  <a name="findstringexact"></a>CListBox::FindStringExact  
 查找与中指定的字符串匹配的第一个列表框字符串`lpszFind`。  
  
```  
int FindStringExact(
    int nIndexStart,  
    LPCTSTR lpszFind) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndexStart`  
 指定要搜索的第一项之前的项的从零开始索引。 如果搜索到达搜索列表框的底部，它将继续从列表框的顶部回由指定的项`nIndexStart`。 如果`nIndexStart`为-1，从开始处搜索整个列表框。  
  
 `lpszFind`  
 指向要搜索的以 null 结尾的字符串。 此字符串可以包含完整的文件名，包括扩展名。 搜索不区分大小写，因此该字符串可包含的任何组合的大写和小写字母。  
  
### <a name="return-value"></a>返回值  
 匹配的项的索引或**LB_ERR**如果搜索未成功。  
  
### <a name="remarks"></a>备注  
 如果使用列表框中但不是创建了一个所有者绘制样式[LBS_HASSTRINGS](../../mfc/reference/list-box-styles.md)样式，`FindStringExact`成员函数尝试与双字值的值相匹配`lpszFind`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 11](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]  
  
##  <a name="getanchorindex"></a>CListBox::GetAnchorIndex  
 检索列表框中当前的定位点项的从零开始索引。  
  
```  
int GetAnchorIndex() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则当前定位点项的索引否则为**LB_ERR**。  
  
### <a name="remarks"></a>备注  
 在多选列表框中，定位点项是连续的选定项的块中的第一个或最后一个项。  
  
### <a name="example"></a>示例  
  请参阅示例[CListBox::SetAnchorIndex](#setanchorindex)。  
  
##  <a name="getcaretindex"></a>CListBox::GetCaretIndex  
 确定在多选列表框中具有焦点矩形的项的索引。  
  
```  
int GetCaretIndex() const;  
```  
  
### <a name="return-value"></a>返回值  
 列表框中具有焦点矩形的项的从零开始的索引。 如果列表框为单选择列表框中，返回值将是项的为选定的索引，如果有的话。  
  
### <a name="remarks"></a>备注  
 该项可能或可能不能选择。  
  
### <a name="example"></a>示例  
  请参阅示例[CListBox::SetCaretIndex](#setcaretindex)。  
  
##  <a name="getcount"></a>CListBox::GetCount  
 检索列表框中的项的数目。  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 列表框中的项的数目或**LB_ERR**如果发生错误。  
  
### <a name="remarks"></a>备注  
 因此返回的计数是一个大于 （索引是从零开始） 的最后一项的索引值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 12](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]  
  
##  <a name="getcursel"></a>CListBox::GetCurSel  
 如果有的话，单项选择列表框中，检索的当前选定项的从零开始索引。  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果它是单项选择列表框的当前选定项的从零开始的索引。 它是`LB_ERR`如果当前不选定任何项。  
  
 在多选列表框中，具有焦点的项的索引。  
  
### <a name="remarks"></a>备注  
 不要调用`GetCurSel`多选列表框中。 使用[CListBox::GetSelItems](#getselitems)相反。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 13](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]  
  
##  <a name="gethorizontalextent"></a>CListBox::GetHorizontalExtent  
 从列表框中检索以依据它可以水平滚动的像素为单位的宽度。  
  
```  
int GetHorizontalExtent() const;  
```  
  
### <a name="return-value"></a>返回值  
 列表框，以像素为单位的可滚动宽度。  
  
### <a name="remarks"></a>备注  
 这是仅适用于列表框中具有水平滚动条。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 14](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]  
  
##  <a name="getitemdata"></a>CListBox::GetItemData  
 检索与指定的列表框项关联的应用程序提供双字值。  
  
```  
DWORD_PTR GetItemData(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 在列表框中指定项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 该项目，与关联的 32 位值或**LB_ERR**如果发生错误。  
  
### <a name="remarks"></a>备注  
 双字值`dwItemData`参数[SetItemData](#setitemdata)调用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 15](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]  
  
##  <a name="getitemdataptr"></a>CListBox::GetItemDataPtr  
 检索与为指针的指定的列表框项关联的应用程序提供 32 位值 ( **void\***)。  
  
```  
void* GetItemDataPtr(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 在列表框中指定项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 检索一个指针，则为-1，如果发生错误。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 16](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]  
  
##  <a name="getitemheight"></a>CListBox::GetItemHeight  
 确定列表框中项的高度。  
  
```  
int GetItemHeight(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 在列表框中指定项的从零开始索引。 仅当该列表框时，才使用此参数**LBS_OWNERDRAWVARIABLE**样式; 否则，它应设置为 0。  
  
### <a name="return-value"></a>返回值  
 以像素为单位，列表框中的项的高度。 如果该列表框[LBS_OWNERDRAWVARIABLE](../../mfc/reference/list-box-styles.md)样式，则返回值是由指定的项的高度`nIndex`。 如果出错，则返回值是**LB_ERR**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 17](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]  
  
##  <a name="getitemrect"></a>CListBox::GetItemRect  
 检索当前显示在列表框窗口中的矩形的尺寸该边界列表框项。  
  
```  
int GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定项的从零开始索引。  
  
 `lpRect`  
 指定指向的长指针[RECT 结构](../../mfc/reference/rect-structure1.md)接收项的列表框中客户端坐标。  
  
### <a name="return-value"></a>返回值  
 **LB_ERR**如果发生错误。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 18](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]  
  
##  <a name="getlistboxinfo"></a>CListBox::GetListBoxInfo  
 检索每个列的项的数目。  
  
```  
DWORD GetListBoxInfo() const;  
```  
  
### <a name="return-value"></a>返回值  
 每个列的项目数`CListBox`对象。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LB_GETLISTBOXINFO](http://msdn.microsoft.com/library/windows/desktop/bb775208)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getlocale"></a>CListBox::GetLocale  
 检索列表框中使用的区域设置。  
  
```  
LCID GetLocale() const;  
```  
  
### <a name="return-value"></a>返回值  
 列表框中字符串的区域设置标识符 (LCID) 值。  
  
### <a name="remarks"></a>备注  
 则使用区域设置，例如，若要确定已排序的列表框中的字符串的排序顺序。  
  
### <a name="example"></a>示例  
  请参阅示例[CListBox::SetLocale](#setlocale)。  
  
##  <a name="getsel"></a>CListBox::GetSel  
 检索项的选择状态。  
  
```  
int GetSel(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 如果选定了指定的项;，正数否则，则为 0。 返回值是`LB_ERR`如果发生错误。  
  
### <a name="remarks"></a>备注  
 此成员函数可使用这两个单和多选列表框。  
  
 若要检索的当前所选列表框项的索引，请使用[CListBox::GetCurSel](#getcursel)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 19](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]  
  
##  <a name="getselcount"></a>CListBox::GetSelCount  
 检索多选列表框中选定项的总数。  
  
```  
int GetSelCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 列表框中选定项的计数。 如果列表框为单选择列表框中，返回值是**LB_ERR**。  
  
### <a name="example"></a>示例  
  请参阅示例[CListBox::GetSelItems](#getselitems)。  
  
##  <a name="getselitems"></a>CListBox::GetSelItems  
 用在多选列表框中指定的选定项的物料编号的整数数组填充缓冲区。  
  
```  
int GetSelItems(
    int nMaxItems,  
    LPINT rgIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nMaxItems`  
 指定其项的数字是要放入缓冲区的选定项的最大数目。  
  
 `rgIndex`  
 指定指向缓冲区足够大小以容纳的指定的整数个数的指针`nMaxItems`。  
  
### <a name="return-value"></a>返回值  
 在缓冲区中放置项的实际数目。 如果列表框为单选择列表框中，返回值是`LB_ERR`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 20](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]  
  
##  <a name="gettext"></a>CListBox::GetText  
 从列表框中获取的字符串。  
  
```  
int GetText(
    int nIndex,  
    LPTSTR lpszBuffer) const;  
  
void GetText(
    int nIndex,  
    CString& rString) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定要检索的字符串的从零开始的索引。  
  
 `lpszBuffer`  
 指向接收字符串的缓冲区。 缓冲区必须具有足够空间的字符串和终止 null 字符。 字符串的大小可以提前确定通过调用`GetTextLen`成员函数。  
  
 `rString`  
 对 `CString` 对象的引用。  
  
### <a name="return-value"></a>返回值  
 不包括终止 null 字符的字符串的长度 （以字节为单位）。 如果`nIndex`未指定有效的索引，则返回值是**LB_ERR**。  
  
### <a name="remarks"></a>备注  
 此成员的第二种形式函数填充`CString`具有字符串文本对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 21](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]  
  
##  <a name="gettextlen"></a>CListBox::GetTextLen  
 列表框项中获取一个字符串的长度。  
  
```  
int GetTextLen(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定字符串的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 以字符为单位，不包括终止 null 字符的字符串的长度。 如果`nIndex`未指定有效的索引，则返回值是**LB_ERR**。  
  
### <a name="example"></a>示例  
  请参阅示例[CListBox::GetText](#gettext)。  
  
##  <a name="gettopindex"></a>CListBox::GetTopIndex  
 检索列表框中的第一个可见项的从零开始索引。  
  
```  
int GetTopIndex() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，列表框中的第一个可见项的从零开始索引**LB_ERR**否则为。  
  
### <a name="remarks"></a>备注  
 最初，0 项位于顶部的列表框中，但如果滚动列表框中，另一项可能在顶部。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 22](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]  
  
##  <a name="initstorage"></a>CListBox::InitStorage  
 用于存储列表框项分配内存。  
  
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
 如果成功，最大项目数的列表框中可以存储之前需要内存重新分配，否则**LB_ERRSPACE**，这意味着没有足够的内存是可用。  
  
### <a name="remarks"></a>备注  
 在添加大量的项之前调用此函数`CListBox`。  
  
 此函数可帮助加快拥有大量的项 (超过 100) 的列表框的初始化。 它预分配指定的数量的内存，因此后续[AddString](#addstring)， [InsertString](#insertstring)，和[Dir](#dir)函数采用最短的时间。 你可以使用估计值的参数。 如果你要估计得高一些，一些额外的内存分配;如果你低估，正常分配用于超过预分配的量的项。  
  
 仅 Windows 95/98:`nItems`参数最多为 16 位值。 这意味着列表框不能包含多个 32,767 的项。 尽管限制项的数目，则列表框中的项的总大小仅受可用内存。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 23](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]  
  
##  <a name="insertstring"></a>CListBox::InsertString  
 将字符串插入到列表框。  
  
```  
int InsertString(
    int nIndex,  
    LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定要将该字符串的位置的从零开始索引。 如果此参数为-1，则字符串被添加到列表的末尾。  
  
 `lpszItem`  
 指向要插入的以 null 结尾的字符串。  
  
### <a name="return-value"></a>返回值  
 插入该字符串的位置的索引（索引从零开始）。 返回值是**LB_ERR**如果发生错误; 返回值是**LB_ERRSPACE**如果没有足够的空间来存储新的字符串。  
  
### <a name="remarks"></a>备注  
 与不同[AddString](#addstring)成员函数，`InsertString`不会导致与列表[LBS_SORT](../../mfc/reference/list-box-styles.md)样式进行排序。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 24](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]  
  
##  <a name="itemfrompoint"></a>CListBox::ItemFromPoint  
 确定最接近的中指定的点的列表框项`pt`。  
  
```  
UINT ItemFromPoint(
    CPoint pt,  
    BOOL& bOutside) const;  
```  
  
### <a name="parameters"></a>参数  
 `pt`  
 为其查找最近的项，指定相对于列表框中的客户端区域的左上角的点。  
  
 `bOutside`  
 引用`BOOL`变量都将设置为`TRUE`如果`pt`最接近的列表框项，工作区以外`FALSE`如果`pt`在最近的列表框项的客户端区域内。  
  
### <a name="return-value"></a>返回值  
 中指定的点到最近的项的索引`pt`。  
  
### <a name="remarks"></a>备注  
 无法使用此函数可确定哪鼠标光标移到上一列表框项。  
  
### <a name="example"></a>示例  
  请参阅示例[CListBox::SetAnchorIndex](#setanchorindex)。  
  
##  <a name="measureitem"></a>CListBox::MeasureItem  
 创建具有所有者绘制样式的列表框时，由框架调用。  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpMeasureItemStruct`  
 指向的长指针[MEASUREITEMSTRUCT](../../mfc/reference/measureitemstruct-structure.md)结构。  
  
### <a name="remarks"></a>备注  
 默认情况下，此成员函数没有任何影响。 重写该成员函数，并填写`MEASUREITEMSTRUCT`以通知 Windows 列表框中维度的结构。 如果使用列表框中创建了[LBS_OWNERDRAWVARIABLE](../../mfc/reference/list-box-styles.md)样式，框架会调用此成员函数为列表框中的每个项。 否则，此成员是只能调用一次。  
  
 有关使用的详细信息[LBS_OWNERDRAWFIXED](../../mfc/reference/list-box-styles.md)中创建一个所有者描述列表框样式`SubclassDlgItem`成员函数`CWnd`，请参阅中的讨论[技术注意 14](../../mfc/tn014-custom-controls.md)。  
  
 请参阅[CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)有关的说明`MEASUREITEMSTRUCT`结构**。**  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 25](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]  
  
##  <a name="resetcontent"></a>CListBox::ResetContent  
 从列表框中移除所有项。  
  
```  
void ResetContent();
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 26](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]  
  
##  <a name="selectstring"></a>CListBox::SelectString  
 搜索列表框项匹配的指定的字符串，并且如果找到匹配项，则它选择的项。  
  
```  
int SelectString(
    int nStartAfter,  
    LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>参数  
 `nStartAfter`  
 包含要搜索的第一项之前的项的从零开始索引。 如果搜索到达搜索列表框的底部，它将继续从列表框的顶部回由指定的项`nStartAfter`。 如果`nStartAfter`为-1，从开始处搜索整个列表框。  
  
 `lpszItem`  
 指向以 null 结尾的字符串，其中包含要搜索的前缀。 搜索是独立的因此此字符串可能包含任何组合的大写和小写字母。  
  
### <a name="return-value"></a>返回值  
 如果搜索成功，所选的项的索引。 如果搜索未成功，则返回值是**LB_ERR**且未更改当前所选内容。  
  
### <a name="remarks"></a>备注  
 如有必要，以将选定的项放到视图中，滚动列表框。  
  
 此成员函数不能用于具有一个列表框[LBS_MULTIPLESEL](../../mfc/reference/list-box-styles.md)样式。  
  
 仅当其初始字符 （从起始点） 与匹配的指定字符串中的字符选择项`lpszItem`。  
  
 使用`FindString`成员函数查找字符串，而不选择该项。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 27](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]  
  
##  <a name="selitemrange"></a>CListBox::SelItemRange  
 在多选列表框中选择多个连续的项。  
  
```  
int SelItemRange(
    BOOL bSelect,  
    int nFirstItem,  
    int nLastItem);
```  
  
### <a name="parameters"></a>参数  
 `bSelect`  
 指定如何设置所选内容。 如果`bSelect`是**TRUE**，则选定字符串并将其突出显示; 如果**FALSE**，删除突出显示，并且该字符串不再处于选中状态。  
  
 `nFirstItem`  
 指定要设置的第一个项的从零开始索引。  
  
 `nLastItem`  
 指定要设置的最后一个项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 **LB_ERR**如果发生错误。  
  
### <a name="remarks"></a>备注  
 此成员函数只能使用多选列表框。 如果你需要在多选列表框中选择只有一项 — 也就是说，如果`nFirstItem`等同于`nLastItem`-调用[SetSel](#setsel)成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 28](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]  
  
##  <a name="setanchorindex"></a>CListBox::SetAnchorIndex  
 在多选列表框中开始的扩展的选择设置定位点。  
  
```  
void SetAnchorIndex(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定将定位点的列表框项的从零开始索引。  
  
### <a name="remarks"></a>备注  
 在多选列表框中，定位点项是连续的选定项的块中的第一个或最后一个项。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 29](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]  
  
##  <a name="setcaretindex"></a>CListBox::SetCaretIndex  
 在多选列表框中将焦点矩形设置为指定索引处的项。  
  
```  
int SetCaretIndex(
    int nIndex,  
    BOOL bScroll = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定要接收焦点矩形的列表框中的项的从零开始索引。  
  
 *bScroll*  
 如果此值为 0，则会将项滚动直到完全可见。 如果此值不为 0，项滚动之前至少部分可见。  
  
### <a name="return-value"></a>返回值  
 **LB_ERR**如果发生错误。  
  
### <a name="remarks"></a>备注  
 如果该项不是可见的它被滚动到视图中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 30](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]  
  
##  <a name="setcolumnwidth"></a>CListBox::SetColumnWidth  
 在多列的列表框中，以像素为单位的所有列设置的宽度 (使用创建[LBS_MULTICOLUMN](../../mfc/reference/list-box-styles.md)样式)。  
  
```  
void SetColumnWidth(int cxWidth);
```  
  
### <a name="parameters"></a>参数  
 `cxWidth`  
 指定以像素为单位的所有列的宽度。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 31](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]  
  
##  <a name="setcursel"></a>CListBox::SetCurSel  
 选择一个字符串，并将它滚动到视图中，如有必要。  
  
```  
int SetCurSel(int nSelect);
```  
  
### <a name="parameters"></a>参数  
 `nSelect`  
 指定要选择的字符串的从零开始的索引。 如果`nSelect`为-1，列表框设置为具有未选择任何内容。  
  
### <a name="return-value"></a>返回值  
 `LB_ERR`如果发生错误。  
  
### <a name="remarks"></a>备注  
 选择新的字符串时，列表框从以前选择的字符串中删除突出显示。  
  
 此成员函数只能使用单选列表框。  
  
 若要设置或删除所选多选列表框中，使用[CListBox::SetSel](#setsel)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 32](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]  
  
##  <a name="sethorizontalextent"></a>CListBox::SetHorizontalExtent  
 设置的宽度，以像素为单位，所依据的列表框可以滚动水平。  
  
```  
void SetHorizontalExtent(int cxExtent);
```  
  
### <a name="parameters"></a>参数  
 *cxExtent*  
 指定所依据的列表框中可以水平滚动的像素数。  
  
### <a name="remarks"></a>备注  
 如果列表框的大小小于此值，水平滚动条将水平滚动列表框中的项。 如果列表框中，为大型或大于此值会隐藏水平滚动条。  
  
 响应调用`SetHorizontalExtent`，列表框中必须已定义为将[WS_HSCROLL](../../mfc/reference/window-styles.md)样式。  
  
 此成员函数不用于多列的列表框。 对于多列的列表框中，调用`SetColumnWidth`成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 33](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]  
  
##  <a name="setitemdata"></a>CListBox::SetItemData  
 设置与列表框中指定的项关联的 32 位值。  
  
```  
int SetItemData(
    int nIndex,  
    DWORD_PTR dwItemData);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定项的从零开始索引。  
  
 `dwItemData`  
 指定要与项相关联的值。  
  
### <a name="return-value"></a>返回值  
 **LB_ERR**如果发生错误。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 34](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]  
  
##  <a name="setitemdataptr"></a>CListBox::SetItemDataPtr  
 设置与为指定的指针的列表框中指定项关联的 32 位值 ( **void\***)。  
  
```  
int SetItemDataPtr(
    int nIndex,  
    void* pData);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定项的从零开始索引。  
  
 `pData`  
 指定要与项关联的指针。  
  
### <a name="return-value"></a>返回值  
 **LB_ERR**如果发生错误。  
  
### <a name="remarks"></a>备注  
 即使在列表框中的项的相对位置可能会更改添加或删除项时，此指针就保持有效的列表框中，整个生命周期。 因此，可以更改在框中的项的索引，但指针保持可靠。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 35](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]  
  
##  <a name="setitemheight"></a>CListBox::SetItemHeight  
 列表框中设置的项的高度。  
  
```  
int SetItemHeight(
    int nIndex,  
    UINT cyItemHeight);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 在列表框中指定项的从零开始索引。 仅当该列表框时，才使用此参数**LBS_OWNERDRAWVARIABLE**样式; 否则，它应设置为 0。  
  
 `cyItemHeight`  
 指定高度，以像素为单位的项。  
  
### <a name="return-value"></a>返回值  
 **LB_ERR**索引或高度是否无效。  
  
### <a name="remarks"></a>备注  
 如果该列表框[LBS_OWNERDRAWVARIABLE](../../mfc/reference/list-box-styles.md)样式，此函数将由指定的项的高度`nIndex`。 否则，此函数将设置列表框中的所有项的高度。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 36](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]  
  
##  <a name="setlocale"></a>CListBox::SetLocale  
 设置此列表框的区域设置标识符。  
  
```  
LCID SetLocale(LCID nNewLocale);
```  
  
### <a name="parameters"></a>参数  
 `nNewLocale`  
 新区域设置标识符 (LCID) 要设置的值的列表框。  
  
### <a name="return-value"></a>返回值  
 此列表框的上一个区域设置标识符 (LCID) 值。  
  
### <a name="remarks"></a>备注  
 如果**SetLocale**不调用，默认值从系统获取区域设置。 可以使用控制面板中的修改此系统默认区域设置区域 （或国际） 应用程序。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 37](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]  
  
##  <a name="setsel"></a>CListBox::SetSel  
 在多选列表框中选择一个字符串。  
  
```  
int SetSel(
    int nIndex,  
    BOOL bSelect = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 包含要设置的字符串的从零开始的索引。 如果为-1，所选内容添加到或从所有字符串，具体取决于的值中删除`bSelect`。  
  
 `bSelect`  
 指定如何设置所选内容。 如果`bSelect`是`TRUE`，则选定字符串并将其突出显示; 如果`FALSE`，删除突出显示，并且该字符串不再处于选中状态。 指定的字符串是选择，默认情况下突出显示。  
  
### <a name="return-value"></a>返回值  
 `LB_ERR`如果发生错误。  
  
### <a name="remarks"></a>备注  
 此成员函数只能使用多选列表框。  
  
 若要从单项选择列表框中选择一个项，使用[CListBox::SetCurSel](#setcursel)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 38](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]  
  
##  <a name="settabstops"></a>CListBox::SetTabStops  
 设置列表框中的制表位位置。  
  
```  
void SetTabStops();  
BOOL SetTabStops(const int& cxEachStop);

 
BOOL SetTabStops(
    int nTabStops,  
    LPINT rgTabStops);
```  
  
### <a name="parameters"></a>参数  
 `cxEachStop`  
 制表位设置为每个`cxEachStop`对话框单位。 请参阅*rgTabStops*有关对话框单位的说明。  
  
 `nTabStops`  
 指定的数制表位能够在列表框中。  
  
 `rgTabStops`  
 指向包含对话框单位的制表位位置的整数的数组的第一个成员。 对话框单位是水平或垂直距离。 一个水平对话框单位等于 1 / 4 的当前对话框基本宽度单位，且一个垂直对话框单位等于当前对话框基本高度单位的八分之一。 对话框基本单位根据当前系统字体的高度和宽度计算。 **GetDialogBaseUnits** Windows 函数以像素为单位返回当前对话框基本单位。 必须按升序排列; 排序的制表位不允许向后制表位。  
  
### <a name="return-value"></a>返回值  
 如果设置了所有选项卡; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 若要设置为 2 个对话框单位的默认大小的制表位，调用此成员函数的无参数版本。 若要设置为 2 以外大小的制表位，调用的版本与`cxEachStop`自变量。  
  
 若要设置制表位为数组的大小，使用的版本与`rgTabStops`和`nTabStops`自变量。 将为每个值中设置制表位`rgTabStops`，最多指定的数`nTabStops`。  
  
 响应调用`SetTabStops`成员函数的列表框中必须具有已创建具有[LBS_USETABSTOPS](../../mfc/reference/list-box-styles.md)样式。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 39](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]  
  
##  <a name="settopindex"></a>CListBox::SetTopIndex  
 确保特定的列表框项可见。  
  
```  
int SetTopIndex(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定列表框项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为零或**LB_ERR**如果发生错误。  
  
### <a name="remarks"></a>备注  
 系统滚动列表框中指定的任意一项之前`nIndex`显示顶部的列表框或最大滚动范围已达到。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 40](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]  
  
##  <a name="vkeytoitem"></a>CListBox::VKeyToItem  
 当列表框中的父窗口接收时由框架调用`WM_VKEYTOITEM`从列表框中的消息。  
  
```  
virtual int VKeyToItem(
    UINT nKey,  
    UINT nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nKey`  
 密钥的虚拟键代码用户按下。 有关标准虚拟键代码的列表，请参见 Winuser.h  
  
 `nIndex`  
 列表框中插入符号的当前位置。  
  
### <a name="return-value"></a>返回值  
 返回的没有任何进一步操作的 2、-1 表示默认操作或一个非负的数字以指定要对其键击执行默认操作的列表框项的索引。  
  
### <a name="remarks"></a>备注  
 `WM_VKEYTOITEM`在接收时，消息由列表框中发送`WM_KEYDOWN`消息，但仅当列表的框满足下列两个条件︰  
  
-   具有[LBS_WANTKEYBOARDINPUT](../../mfc/reference/list-box-styles.md)样式集。  
  
-   具有至少一个项。  
  
 你绝不应自己调用此函数。 重写此函数可提供你自己的自定义处理操作的键盘消息。  
  
 您必须返回一个值，以告知框架重写执行什么操作。 返回值-2 表示应用程序处理的选择项的所有方面，并需要由列表框中的任何进一步的操作。 之前返回-2，无法设置所选内容或移动插入符号或两个。 若要设置所选内容，使用[SetCurSel](#setcursel)或[SetSel](#setsel)。 若要移动插入符号，使用[SetCaretIndex](#setcaretindex)。  
  
 返回值-1 表示列表框在击键响应中应执行默认操作。默认实现返回-1。  
  
 返回值 0 或更高版本的列表框中指定项的索引，并指明列表框中，应在给定的项键击执行默认操作。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox # 41](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 CTRLTEST](../../visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CButton 类](../../mfc/reference/cbutton-class.md)   
 [CComboBox 类](../../mfc/reference/ccombobox-class.md)   
 [CEdit 类](../../mfc/reference/cedit-class.md)   
 [CScrollBar 类](../../mfc/reference/cscrollbar-class.md)   
 [CStatic 类](../../mfc/reference/cstatic-class.md)

