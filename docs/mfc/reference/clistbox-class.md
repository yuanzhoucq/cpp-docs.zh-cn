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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: f4df970f2df35d399c0c700cf504a76482ad3f6d
ms.lasthandoff: 02/24/2017

---
# <a name="clistbox-class"></a>CListBox 类
提供 Windows 列表框功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CListBox : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CListBox::CListBox](#clistbox)|构造 `CListBox` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CListBox::AddString](#addstring)|将一个字符串添加到列表框中。|  
|[CListBox::CharToItem](#chartoitem)|重写以提供自定义`WM_CHAR`自绘列表框不都有字符串处理。|  
|[CListBox::CompareItem](#compareitem)|由框架来确定新项的已排序的所有者描述列表框中的位置调用。|  
|[CListBox::Create](#create)|创建 Windows 列表框中，并将其附加到`CListBox`对象。|  
|[CListBox::DeleteItem](#deleteitem)|当用户从所有者描述列表框中删除项时，由框架调用。|  
|[CListBox::DeleteString](#deletestring)|从列表框中删除一个字符串。|  
|[CListBox::Dir](#dir)|将文件名、 驱动器或从当前目录添加到列表框中。|  
|[CListBox::DrawItem](#drawitem)|由框架在自绘列表框中更改的可视方位时调用。|  
|[CListBox::FindString](#findstring)|搜索列表框中的字符串。|  
|[CListBox::FindStringExact](#findstringexact)|查找与指定的字符串匹配的第一个列表框中字符串。|  
|[CListBox::GetAnchorIndex](#getanchorindex)|检索列表框中当前的定位点项的从零开始的索引。|  
|[CListBox::GetCaretIndex](#getcaretindex)|确定具有多选列表框中的下的聚焦框的项的索引。|  
|[CListBox::GetCount](#getcount)|在列表框中返回字符串的数量。|  
|[CListBox::GetCurSel](#getcursel)|返回在列表框中当前所选字符串的从零开始的索引。|  
|[CListBox::GetHorizontalExtent](#gethorizontalextent)|返回以像素为单位可以水平滚动的列表框的宽度。|  
|[CListBox::GetItemData](#getitemdata)|返回与列表框项相关联的 32 位值。|  
|[CListBox::GetItemDataPtr](#getitemdataptr)|返回到列表框中项的指针。|  
|[CListBox::GetItemHeight](#getitemheight)|确定在列表框中的项的高度。|  
|[CListBox::GetItemRect](#getitemrect)|返回当前显示的列表框中项的边框。|  
|[CListBox::GetListBoxInfo](#getlistboxinfo)|检索每个列的项的数目。|  
|[CListBox::GetLocale](#getlocale)|检索列表框中的区域设置标识符。|  
|[CListBox::GetSel](#getsel)|返回一个列表框中项的选择状态。|  
|[CListBox::GetSelCount](#getselcount)|返回多选列表框中当前选定的字符串的数量。|  
|[CListBox::GetSelItems](#getselitems)|返回列表框中当前选定的字符串的索引。|  
|[CListBox::GetText](#gettext)|将列表框项复制到缓冲区中。|  
|[CListBox::GetTextLen](#gettextlen)|返回的长度以字节为单位的列表框项。|  
|[CListBox::GetTopIndex](#gettopindex)|在列表框中返回的第一个可见字符串的索引。|  
|[CListBox::InitStorage](#initstorage)|预先分配为列表框项和字符串的内存块的能力。|  
|[CListBox::InsertString](#insertstring)|在列表框中的特定位置插入的字符串。|  
|[CListBox::ItemFromPoint](#itemfrompoint)|返回最接近的点的列表框中项的索引。|  
|[CListBox::MeasureItem](#measureitem)|创建一个所有者描述列表框，来确定列表框中的维度时由框架调用。|  
|[CListBox::ResetContent](#resetcontent)|清除列表框中的所有条目。|  
|[CListBox::SelectString](#selectstring)|搜索并在单项选择列表框中选择一个字符串。|  
|[CListBox::SelItemRange](#selitemrange)|选择或取消选择各种多选列表框中的字符串。|  
|[CListBox::SetAnchorIndex](#setanchorindex)|设置中多选列表框，以便开始扩展所选内容的定位点。|  
|[CListBox::SetCaretIndex](#setcaretindex)|多选列表框中将聚焦框设置为指定索引处的项。|  
|[CListBox::SetColumnWidth](#setcolumnwidth)|设置多列的列表框中的列宽度。|  
|[CListBox::SetCurSel](#setcursel)|选择一个列表框中的字符串。|  
|[CListBox::SetHorizontalExtent](#sethorizontalextent)|以像素为单位可以水平滚动列表框中设置的宽度。|  
|[CListBox::SetItemData](#setitemdata)|设置与列表框项相关联的 32 位值。|  
|[CListBox::SetItemDataPtr](#setitemdataptr)|将指针设置到列表框项。|  
|[CListBox::SetItemHeight](#setitemheight)|在列表框中设置项的高度。|  
|[CListBox::SetLocale](#setlocale)|设置列表框中的区域设置标识符。|  
|[CListBox::SetSel](#setsel)|选择或取消选择多选列表框中的列表框项。|  
|[CListBox::SetTabStops](#settabstops)|设置在列表框中的制表位位置。|  
|[CListBox::SetTopIndex](#settopindex)|在列表框中设置的第一个可见字符串的从零开始索引。|  
|[CListBox::VKeyToItem](#vkeytoitem)|重写以提供自定义`WM_KEYDOWN`为列表框处理**LBS_WANTKEYBOARDINPUT**样式集。|  
  
## <a name="remarks"></a>备注  
 列表框中显示项，例如，用户可以查看和选择的文件名的列表。  
  
 在单项选择列表框中，用户可以选择只有一项。 在多选列表框中，您可以选择的项的范围。 当用户选择某个项时，它被突出显示和列表框中向父窗口发送一条通知消息。  
  
 您可以创建列表框中，对话框模板中或直接在代码中。 若要直接创建，构造`CListBox`对象，然后调用[创建](#create)成员函数来创建 Windows 列表框控件并将其附加到`CListBox`对象。 若要使用的列表框的对话框模板中，列表框中声明变量对话框类，然后使用`DDX_Control`在对话框类的`DoDataExchange`函数来连接到的控件的成员变量。 （这是为您自动完成时将控制变量添加到对话框类。）  
  
 构造可能是在派生类中的单步进程`CListBox`。 编写构造函数以及该派生的类调用**创建**从构造函数内。  
  
 如果你想要处理 Windows 通知消息发送到其父列表框中 (通常派生自该类[CDialog](../../mfc/reference/cdialog-class.md))，将消息映射条目和消息处理程序成员函数添加到每个消息的父类。  
  
 每个消息映射条目采用以下形式︰  
  
 `ON_Notification( id, memberFxn )`  
  
 其中`id`指定发送通知的列表框控件的子窗口 ID 和`memberFxn`留下来处理通知的父成员函数的名称。  
  
 父元素的函数原型是，如下所示︰  
  
 `afx_msg void memberFxn( );`  
  
 以下是潜在的消息映射条目，并会对父发送的用例的说明的列表︰  
  
- **ON_LBN_DBLCLK**用户双击列表框中的字符串。 有一个列表框[LBS_NOTIFY](../../mfc/reference/list-box-styles.md)样式将发送此通知消息。  
  
- **ON_LBN_ERRSPACE**列表框中无法分配足够的内存才能满足该请求。  
  
- **ON_LBN_KILLFOCUS**列表框中正在失去输入的焦点。  
  
- **ON_LBN_SELCANCEL**取消当前的列表框中所选内容。 列表框上时，将只会发送此消息**LBS_NOTIFY**样式。  
  
- **ON_LBN_SELCHANGE**列表框中的选择已更改。 如果通过更改所选内容不会发送此通知[CListBox::SetCurSel](#setcursel)成员函数。 此通知仅适用于具有一个列表框**LBS_NOTIFY**样式。 **LBN_SELCHANGE**通知消息被发送进行多选列表框每当用户按箭头键时，即使所选内容不会更改。  
  
- **ON_LBN_SETFOCUS**列表框中将接收输入的焦点。  
  
- **ON_WM_CHARTOITEM**接收不具有任何字符串自绘列表框`WM_CHAR`消息。  
  
- **ON_WM_VKEYTOITEM**具有的列表框**LBS_WANTKEYBOARDINPUT**样式接收`WM_KEYDOWN`消息。  
  
 如果您创建`CListBox`（通过对话框资源） 的对话框内的对象`CListBox`当用户关闭对话框中，将自动销毁对象。  
  
 如果您创建`CListBox`对象在窗口中，您可能需要销毁`CListBox`对象。 如果您创建`CListBox`对象在堆栈上，自动被销毁。 如果您创建`CListBox`使用堆上的对象**新**函数，则必须调用**删除**上要将其销毁，当用户关闭的父窗口的对象。  
  
 如果分配任何内存`CListBox`对象，请重写`CListBox`析构函数以释放分配。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CListBox`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="a-nameaddstringa--clistboxaddstring"></a><a name="addstring"></a>CListBox::AddString  
 将一个字符串添加到列表框中。  
  
```  
int AddString(LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>参数  
 `lpszItem`  
 指向要添加的以 null 结尾的字符串。  
  
### <a name="return-value"></a>返回值  
 列表框中的字符串的从零开始索引。 返回值是**LB_ERR**如果发生错误; 返回值是**LB_ERRSPACE**如果没有足够空间可用于存储新的字符串。  
  
### <a name="remarks"></a>备注  
 如果不通过创建列表框[LBS_SORT](../../mfc/reference/list-box-styles.md)样式，则字符串添加到列表的末尾。 否则为该字符串插入到列表中，并对列表进行排序。 如果使用列表框中创建了**LBS_SORT**但未设置样式[LBS_HASSTRINGS](../../mfc/reference/list-box-styles.md)样式，该框架对列表进行排序的一个或多个调用`CompareItem`成员函数。  
  
 使用[InsertString](#insertstring)插入到列表框内的特定位置的字符串。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&3;](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]  
  
##  <a name="a-namechartoitema--clistboxchartoitem"></a><a name="chartoitem"></a>CListBox::CharToItem  
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
 返回 – 1 或-2 没有进一步的操作或一个非负的数字来指定要对其按键执行默认操作的列表框项的索引。 默认实现返回 – 1。  
  
### <a name="remarks"></a>备注  
 `WM_CHARTOITEM`在接收时，列表框中即可发送消息`WM_CHAR`消息，但仅当列表框中满足所有以下条件的︰  
  
-   是一个所有者描述列表框。  
  
-   没有[LBS_HASSTRINGS](../../mfc/reference/list-box-styles.md)样式集。  
  
-   具有至少一个项。  
  
 你绝不应自己调用此函数。 重写此函数可提供您自己的自定义处理操作的键盘消息。  
  
 在重写中，您必须返回一个值，以通知框架所执行的操作。 返回值-1 或-2 表示将处理选择该项的所有方面，不需要进一步的操作的列表框。 之前返回 – 1 或-2，您可以设置所选内容或移动和 / 或插入符号。 若要设置所选内容，使用[SetCurSel](#setcursel)或[SetSel](#setsel)。 若要移动插入符号，请使用[SetCaretIndex](#setcaretindex)。  
  
 返回值 0 或更高版本的列表框中指定项的索引，并指明列表框中应为给定项的键击执行默认操作。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&4;](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]  
  
##  <a name="a-nameclistboxa--clistboxclistbox"></a><a name="clistbox"></a>CListBox::CListBox  
 构造 `CListBox` 对象。  
  
```  
CListBox();
```  
  
### <a name="remarks"></a>备注  
 您构造`CListBox`两个步骤中的对象。 首先，调用构造函数**ClistBox** ，然后调用**创建**，其中初始化 Windows 列表框中，并将其附加到`CListBox`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&1;](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]  
  
##  <a name="a-namecompareitema--clistboxcompareitem"></a><a name="compareitem"></a>CListBox::CompareItem  
 由框架来确定新项的已排序的所有者描述列表框中的相对位置调用。  
  
```  
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpCompareItemStruct`  
 指向长指针`COMPAREITEMSTRUCT`结构。  
  
### <a name="return-value"></a>返回值  
 指示中所述的两个项目的相对位置[COMPAREITEMSTRUCT](../../mfc/reference/compareitemstruct-structure.md)结构。 它可能是下列值之一︰  
  
|值|含义|  
|-----------|-------------|  
|–1|在第 2 项之前进行排序的第 1 项。|  
|0|第 1 项和第 2 项的排序相同。|  
|1|在项 2 之后，第 1 项进行排序。|  
  
 请参阅[CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)有关的说明`COMPAREITEMSTRUCT`结构。  
  
### <a name="remarks"></a>备注  
 默认情况下，此成员函数没有任何影响。 如果您创建一个带有自绘列表框**LBS_SORT**样式，您必须重写该成员函数以帮助框架添加到列表框中的新项进行排序。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&5;](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]  
  
##  <a name="a-namecreatea--clistboxcreate"></a><a name="create"></a>CListBox::Create  
 创建 Windows 列表框中，并将其附加到`CListBox`对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 指定列表框的样式。 应用的任意组合[列表框样式](../../mfc/reference/list-box-styles.md)的框。  
  
 `rect`  
 指定列表框的大小和位置。 可以是`CRect`对象或`RECT`结构。  
  
 `pParentWnd`  
 指定列表框中的父窗口 (通常`CDialog`对象)。 它不能**NULL**。  
  
 `nID`  
 指定列表框控件 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 您构造`CListBox`两个步骤中的对象。 首先，调用构造函数，然后调用**创建**，其中初始化 Windows 列表框中，并将其附加到`CListBox`对象。  
  
 当**创建**执行时，Windows 将发送[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)， [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)， [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)，和[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)发送到列表框控件的消息。  
  
 默认情况下，通过处理这些消息的消息[OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)， [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)， [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)，和[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成员函数中`CWnd`基类。 若要扩展的默认消息处理，从派生类`CListBox`、 将消息映射添加到新的类，并重写前面的消息处理程序成员函数。 重写`OnCreate`，例如，若要为新类执行所需的初始化。  
  
 将应用以下[窗口样式](../../mfc/reference/window-styles.md)到列表框控件。  
  
- **WS_CHILD**始终  
  
- **WS_VISIBLE**通常  
  
- **WS_DISABLED**很少  
  
- **WS_VSCROLL**添加垂直滚动条  
  
- **WS_HSCROLL**若要添加水平滚动条  
  
- **WS_GROUP**控件组合  
  
- **WS_TABSTOP**以允许到此控件的 tab 键次序  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&2;](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]  
  
##  <a name="a-namedeleteitema--clistboxdeleteitem"></a><a name="deleteitem"></a>CListBox::DeleteItem  
 当用户从所有者描述中删除项时由框架调用`CListBox`对象或销毁列表框。  
  
```  
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpDeleteItemStruct`  
 向 Windows 的长指针[DELETEITEMSTRUCT](../../mfc/reference/deleteitemstruct-structure.md)结构，其中包含有关已删除的项的信息。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现不执行任何操作。 重写此函数进行重绘一个所有者描述列表框，根据需要。  
  
 请参阅[CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem)有关的说明`DELETEITEMSTRUCT`结构。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&6;](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]  
  
##  <a name="a-namedeletestringa--clistboxdeletestring"></a><a name="deletestring"></a>CListBox::DeleteString  
 删除位置中的项`nIndex`从列表框。  
  
```  
int DeleteString(UINT nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定要删除的字符串的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 在列表中剩余的字符串的计数。 返回值是**LB_ERR**如果`nIndex`列表中指定索引大于项的数目。  
  
### <a name="remarks"></a>备注  
 后面的所有项`nIndex`现在将下移一个位置。 例如，如果列表框中包含两个项，则删除的第一项将导致现在将在第一个位置中剩余项。 `nIndex`=&0; 的第一个位置中的项。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&7;](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]  
  
##  <a name="a-namedira--clistboxdir"></a><a name="dir"></a>CListBox::Dir  
 添加列表的文件名、 驱动器或均为列表框中。  
  
```  
int Dir(
    UINT attr,  
    LPCTSTR lpszWildCard);
```  
  
### <a name="parameters"></a>参数  
 `attr`  
 可以是任意组合的`enum`值中所述**CFile::GetStatu**[s](../../mfc/reference/cfile-class.md#getstatus)，或下列值中的任意组合︰  
  
|值|含义|  
|-----------|-------------|  
|0x0000|可以读取或写入到文件。|  
|它需要&0;x0001|可以读取但不是会写入到文件。|  
|0x0002|文件处于隐藏状态，并且未出现在目录列表。|  
|0x0004|文件是系统文件。|  
|0x0010|指定的名称`lpszWildCard`指定的目录。|  
|0x0020|已存档文件。|  
|0x4000|包含与指定的名称相匹配的所有驱动器`lpszWildCard`。|  
|0x8000|排他标志。 如果设置了排他标志，仅指定类型的文件会列出。 否则，除了"正常"文件列出指定类型的文件。|  
  
 `lpszWildCard`  
 指向以文件规范字符串。 该字符串可以包含通配符 (例如，*。\*)。  
  
### <a name="return-value"></a>返回值  
 最后一个文件名添加到列表中的从零开始的索引。 返回值是**LB_ERR**如果发生错误; 返回值是**LB_ERRSPACE**如果没有足够空间可用于存储新的字符串。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&8;](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]  
  
##  <a name="a-namedrawitema--clistboxdrawitem"></a><a name="drawitem"></a>CListBox::DrawItem  
 由框架在自绘列表框中更改的可视方位时调用。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpDrawItemStruct`  
 指向长指针[DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md)结构，其中包含有关所需的绘图类型的信息。  
  
### <a name="remarks"></a>备注  
 **ItemAction**和**itemState**成员`DRAWITEMSTRUCT`结构定义要执行的绘制操作。  
  
 默认情况下，此成员函数没有任何影响。 重写该成员函数以实现所有者描述的绘图`CListBox`对象。 应用程序应还原选择用于显示上下文中提供的所有图形设备接口 (GDI) 对象`lpDrawItemStruct`之前此成员函数将终止。  
  
 请参阅[CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)有关的说明`DRAWITEMSTRUCT`结构。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&9;](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]  
  
##  <a name="a-namefindstringa--clistboxfindstring"></a><a name="findstring"></a>CListBox::FindString  
 在包含指定的前缀，而无需更改的列表框中选择一个列表框中查找第一个字符串。  
  
```  
int FindString(
    int nStartAfter,  
    LPCTSTR lpszItem) const;  
```  
  
### <a name="parameters"></a>参数  
 `nStartAfter`  
 包含要搜索的第一项之前的项的从零开始索引。 当搜索到达列表框的底部时，它将继续从列表框的顶部返回由指定的项`nStartAfter`。 如果`nStartAfter`为 –&1;，从一开始搜索整个列表框。  
  
 `lpszItem`  
 指向以 null 结尾的字符串，其中包含要搜索的前缀。 搜索不区分大小写，因此，此字符串可能包含的任何组合的大写和小写字母。  
  
### <a name="return-value"></a>返回值  
 匹配项的从零开始的索引或**LB_ERR**如果搜索未成功。  
  
### <a name="remarks"></a>备注  
 使用[SelectString](#selectstring)成员函数来查找和选择字符串。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&10;](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]  
  
##  <a name="a-namefindstringexacta--clistboxfindstringexact"></a><a name="findstringexact"></a>CListBox::FindStringExact  
 查找与中指定的字符串匹配的第一个列表框中字符串`lpszFind`。  
  
```  
int FindStringExact(
    int nIndexStart,  
    LPCTSTR lpszFind) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndexStart`  
 指定要搜索的第一项之前的项的从零开始索引。 当搜索到达列表框的底部时，它将继续从列表框的顶部返回由指定的项`nIndexStart`。 如果`nIndexStart`为 –&1;，从一开始搜索整个列表框。  
  
 `lpszFind`  
 指向以 null 结尾的字符串来搜索。 此字符串可以包含完整的文件名，包括扩展名。 搜索不区分大小写，因此该字符串可包含的任何组合的大写和小写字母。  
  
### <a name="return-value"></a>返回值  
 在匹配项的索引或**LB_ERR**如果搜索未成功。  
  
### <a name="remarks"></a>备注  
 如果使用列表框中但没有创建了一个所有者绘制样式[LBS_HASSTRINGS](../../mfc/reference/list-box-styles.md)样式，`FindStringExact`成员函数将尝试匹配的值的双字值`lpszFind`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&11;](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]  
  
##  <a name="a-namegetanchorindexa--clistboxgetanchorindex"></a><a name="getanchorindex"></a>CListBox::GetAnchorIndex  
 检索列表框中当前的定位点项的从零开始的索引。  
  
```  
int GetAnchorIndex() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则当前定位点项的索引否则为**LB_ERR**。  
  
### <a name="remarks"></a>备注  
 在多选列表框中，定位点项是连续的选定项的块中的第一个或最后一个项。  
  
### <a name="example"></a>示例  
  请参阅示例[CListBox::SetAnchorIndex](#setanchorindex)。  
  
##  <a name="a-namegetcaretindexa--clistboxgetcaretindex"></a><a name="getcaretindex"></a>CListBox::GetCaretIndex  
 确定具有多选列表框中的下的聚焦框的项的索引。  
  
```  
int GetCaretIndex() const;  
```  
  
### <a name="return-value"></a>返回值  
 列表框中具有聚焦框的项的从零开始的索引。 列表框是否单项选择列表框中，返回值将是选中，则项的索引，如果有的话。  
  
### <a name="remarks"></a>备注  
 该项目，也不会选择。  
  
### <a name="example"></a>示例  
  请参阅示例[CListBox::SetCaretIndex](#setcaretindex)。  
  
##  <a name="a-namegetcounta--clistboxgetcount"></a><a name="getcount"></a>CListBox::GetCount  
 检索列表框中的项的数目。  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 列表框中的项的数目或**LB_ERR**如果发生错误。  
  
### <a name="remarks"></a>备注  
 因此返回的计数是一个大于 （索引是从零开始） 的最后一项的索引值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&12;](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]  
  
##  <a name="a-namegetcursela--clistboxgetcursel"></a><a name="getcursel"></a>CListBox::GetCurSel  
 如果有单选列表框中，检索当前选定项的从零开始索引。  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果它是单项选择列表框的当前选定项的从零开始的索引。 它是`LB_ERR`如果当前没有选定任何项。  
  
 在多选列表框中，具有焦点的项的索引。  
  
### <a name="remarks"></a>备注  
 不要调用`GetCurSel`多选列表框中。 使用[CListBox::GetSelItems](#getselitems)相反。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&13;](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]  
  
##  <a name="a-namegethorizontalextenta--clistboxgethorizontalextent"></a><a name="gethorizontalextent"></a>CListBox::GetHorizontalExtent  
 从列表框中检索以像素为单位，它可以进行水平滚动的宽度。  
  
```  
int GetHorizontalExtent() const;  
```  
  
### <a name="return-value"></a>返回值  
 列表框，以像素为单位的滚动宽度。  
  
### <a name="remarks"></a>备注  
 这是仅适用于该列表框具有水平滚动条。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&14;](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]  
  
##  <a name="a-namegetitemdataa--clistboxgetitemdata"></a><a name="getitemdata"></a>CListBox::GetItemData  
 检索与指定的列表框项相关联的应用程序提供双字值。  
  
```  
DWORD_PTR GetItemData(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 在列表框中指定项的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 该项目，与关联的 32 位值或**LB_ERR**如果发生错误。  
  
### <a name="remarks"></a>备注  
 双字值`dwItemData`参数[SetItemData](#setitemdata)调用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&15;](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]  
  
##  <a name="a-namegetitemdataptra--clistboxgetitemdataptr"></a><a name="getitemdataptr"></a>CListBox::GetItemDataPtr  
 检索与指定的列表框项作为指针关联的应用程序提供 32 位值 ( **void\***)。  
  
```  
void* GetItemDataPtr(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 在列表框中指定项的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 检索一个指针，则返回 –&1;，如果发生错误。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&16;](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]  
  
##  <a name="a-namegetitemheighta--clistboxgetitemheight"></a><a name="getitemheight"></a>CListBox::GetItemHeight  
 确定在列表框中的项的高度。  
  
```  
int GetItemHeight(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 在列表框中指定项的从零开始的索引。 仅当该列表框包含使用此参数**LBS_OWNERDRAWVARIABLE**样式; 否则，它应设置为 0。  
  
### <a name="return-value"></a>返回值  
 以像素为单位的列表框中的项的高度。 如果该列表框包含[LBS_OWNERDRAWVARIABLE](../../mfc/reference/list-box-styles.md)样式，则返回值是由指定的项的高度`nIndex`。 如果发生错误，返回值是**LB_ERR**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&17;](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]  
  
##  <a name="a-namegetitemrecta--clistboxgetitemrect"></a><a name="getitemrect"></a>CListBox::GetItemRect  
 因为它当前显示在列表框窗口中检索的矩形的尺寸该边界列表框项。  
  
```  
int GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定项的从零开始的索引。  
  
 `lpRect`  
 指定指向的长指针[RECT 结构](../../mfc/reference/rect-structure1.md)，它接收的项的列表框中客户端坐标。  
  
### <a name="return-value"></a>返回值  
 **LB_ERR**如果发生错误。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&18;](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]  
  
##  <a name="a-namegetlistboxinfoa--clistboxgetlistboxinfo"></a><a name="getlistboxinfo"></a>CListBox::GetListBoxInfo  
 检索每个列的项的数目。  
  
```  
DWORD GetListBoxInfo() const;  
```  
  
### <a name="return-value"></a>返回值  
 每个列的项目数`CListBox`对象。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[LB_GETLISTBOXINFO](http://msdn.microsoft.com/library/windows/desktop/bb775208)消息，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetlocalea--clistboxgetlocale"></a><a name="getlocale"></a>CListBox::GetLocale  
 检索列表框中使用的区域设置。  
  
```  
LCID GetLocale() const;  
```  
  
### <a name="return-value"></a>返回值  
 在列表框中字符串的区域设置标识符 (LCID) 值。  
  
### <a name="remarks"></a>备注  
 使用区域设置是，例如，若要确定在已排序的列表框中字符串的排序顺序。  
  
### <a name="example"></a>示例  
  请参阅示例[CListBox::SetLocale](#setlocale)。  
  
##  <a name="a-namegetsela--clistboxgetsel"></a><a name="getsel"></a>CListBox::GetSel  
 检索项的选择状态。  
  
```  
int GetSel(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定项的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 如果指定的项处于选中状态，，正数否则，为 0。 返回值是`LB_ERR`如果发生错误。  
  
### <a name="remarks"></a>备注  
 此成员函数可使用这两个单个和多选列表框。  
  
 若要检索当前所选列表框中项的索引，请使用[CListBox::GetCurSel](#getcursel)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&19;](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]  
  
##  <a name="a-namegetselcounta--clistboxgetselcount"></a><a name="getselcount"></a>CListBox::GetSelCount  
 检索多选列表框中选定项的总数。  
  
```  
int GetSelCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 列表框中选定项的计数。 如果列表框为单项选择列表框中，返回值是**LB_ERR**。  
  
### <a name="example"></a>示例  
  请参阅示例[CListBox::GetSelItems](#getselitems)。  
  
##  <a name="a-namegetselitemsa--clistboxgetselitems"></a><a name="getselitems"></a>CListBox::GetSelItems  
 用指定的多选列表框中的选定项的物料编号的整数数组填充缓冲区。  
  
```  
int GetSelItems(
    int nMaxItems,  
    LPINT rgIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nMaxItems`  
 指定其项号被放在缓冲区中的选定项的最大数量。  
  
 `rgIndex`  
 指定指向缓冲区足够大的整数指定个数的指针`nMaxItems`。  
  
### <a name="return-value"></a>返回值  
 在缓冲区中放置项的实际数目。 如果列表框为单项选择列表框中，返回值是`LB_ERR`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&20;](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]  
  
##  <a name="a-namegettexta--clistboxgettext"></a><a name="gettext"></a>CListBox::GetText  
 从列表框中获取一个字符串。  
  
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
 指定要检索的字符串的从零开始索引。  
  
 `lpszBuffer`  
 指向接收字符串的缓冲区。 缓冲区必须具有足够的空间的字符串和终止 null 字符。 可通过调用提前确定字符串的大小`GetTextLen`成员函数。  
  
 `rString`  
 对 `CString` 对象的引用。  
  
### <a name="return-value"></a>返回值  
 不包括终止 null 字符的字符串的长度 （以字节为单位）。 如果`nIndex`未指定一个有效的索引，则返回值是**LB_ERR**。  
  
### <a name="remarks"></a>备注  
 此成员的第二种形式函数填充`CString`具有字符串文本对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&21;](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]  
  
##  <a name="a-namegettextlena--clistboxgettextlen"></a><a name="gettextlen"></a>CListBox::GetTextLen  
 获取列表框项中的字符串的长度。  
  
```  
int GetTextLen(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定的字符串的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 以字符为单位，不包括终止 null 字符的字符串的长度。 如果`nIndex`未指定一个有效的索引，则返回值是**LB_ERR**。  
  
### <a name="example"></a>示例  
  请参阅示例[CListBox::GetText](#gettext)。  
  
##  <a name="a-namegettopindexa--clistboxgettopindex"></a><a name="gettopindex"></a>CListBox::GetTopIndex  
 检索列表框中的第一个可见项的从零开始索引。  
  
```  
int GetTopIndex() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，列表框中的第一个可见项的从零开始索引**LB_ERR**否则为。  
  
### <a name="remarks"></a>备注  
 最初，0 项位于顶部的列表框中，但如果滚动列表框中，另一项可能会在顶部。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&22;](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]  
  
##  <a name="a-nameinitstoragea--clistboxinitstorage"></a><a name="initstorage"></a>CListBox::InitStorage  
 用于存储列表框中的项目中分配内存。  
  
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
 如果成功，最大项目数的列表框中可以存储之前所需内存重新分配，否则**LB_ERRSPACE**，这意味着没有足够的内存是可用。  
  
### <a name="remarks"></a>备注  
 在添加大量的项目添加到之前调用此函数`CListBox`。  
  
 此功能可帮助加快有大量的项 (超过 100) 的列表框中的初始化。 预先分配指定的以使后续的内存量[AddString](#addstring)， [InsertString](#insertstring)，和[Dir](#dir)函数采用最短的时间。 参数，可以使用估计值。 如果您要估计得高一些，则会分配一些额外的内存;如果您低估正常分配用于超出预分配的量的项。  
  
 仅 Windows 95/98:`nItems`参数最多为 16 位值。 这意味着列表框不能包含超过 32767 个项。 尽管限制的项数，则列表框中的项的总大小仅受可用内存限制。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox 第&23;](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]  
  
##  <a name="a-nameinsertstringa--clistboxinsertstring"></a><a name="insertstring"></a>CListBox::InsertString  
 将字符串插入到列表框。  
  
```  
int InsertString(
    int nIndex,  
    LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定的位置以将该字符串的从零开始索引。 如果此参数为 –&1;，则字符串将被添加到列表末尾。  
  
 `lpszItem`  
 指向要插入的以 null 结尾的字符串。  
  
### <a name="return-value"></a>返回值  
 插入该字符串的位置的索引（索引从零开始）。 返回值是**LB_ERR**如果发生错误; 返回值是**LB_ERRSPACE**如果没有足够空间可用于存储新的字符串。  
  
### <a name="remarks"></a>备注  
 与不同[AddString](#addstring)成员函数，`InsertString`不会导致与列表[LBS_SORT](../../mfc/reference/list-box-styles.md)样式来进行排序。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&24;](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]  
  
##  <a name="a-nameitemfrompointa--clistboxitemfrompoint"></a><a name="itemfrompoint"></a>CListBox::ItemFromPoint  
 确定最近的中指定的点的列表框项`pt`。  
  
```  
UINT ItemFromPoint(
    CPoint pt,  
    BOOL& bOutside) const;  
```  
  
### <a name="parameters"></a>参数  
 `pt`  
 从中找到最接近的项，请指定相对路径的列表框中的工作区的左上角的点。  
  
 `bOutside`  
 引用`BOOL`变量都将设置为`TRUE`如果`pt`是最近的列表框中项的工作区以外`FALSE`如果`pt`在最近的列表框中项的客户端区域内。  
  
### <a name="return-value"></a>返回值  
 中指定的点到最近的项的索引`pt`。  
  
### <a name="remarks"></a>备注  
 可以使用此函数来确定哪鼠标光标移到上一列表框项。  
  
### <a name="example"></a>示例  
  请参阅示例[CListBox::SetAnchorIndex](#setanchorindex)。  
  
##  <a name="a-namemeasureitema--clistboxmeasureitem"></a><a name="measureitem"></a>CListBox::MeasureItem  
 创建具有一个所有者绘制样式的列表框时，由框架调用。  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpMeasureItemStruct`  
 指向长指针[MEASUREITEMSTRUCT](../../mfc/reference/measureitemstruct-structure.md)结构。  
  
### <a name="remarks"></a>备注  
 默认情况下，此成员函数没有任何影响。 重写该成员函数，并填写`MEASUREITEMSTRUCT`来通知 Windows 列表框中维度的结构。 如果使用列表框中创建了[LBS_OWNERDRAWVARIABLE](../../mfc/reference/list-box-styles.md)样式，框架将调用此成员函数的列表框中的每一项。 否则，只有一次调用此成员。  
  
 有关详细信息使用[LBS_OWNERDRAWFIXED](../../mfc/reference/list-box-styles.md)中创建具有一个所有者描述列表框样式`SubclassDlgItem`成员函数`CWnd`，请参阅中的讨论[技术注意 14](../../mfc/tn014-custom-controls.md)。  
  
 请参阅[CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)有关的说明`MEASUREITEMSTRUCT`结构**。**  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&25;](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]  
  
##  <a name="a-nameresetcontenta--clistboxresetcontent"></a><a name="resetcontent"></a>CListBox::ResetContent  
 从列表框中移除所有项。  
  
```  
void ResetContent();
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&26;](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]  
  
##  <a name="a-nameselectstringa--clistboxselectstring"></a><a name="selectstring"></a>CListBox::SelectString  
 搜索列表框中项的匹配指定的字符串，并且如果找到匹配项，则将选择此项。  
  
```  
int SelectString(
    int nStartAfter,  
    LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>参数  
 `nStartAfter`  
 包含要搜索的第一项之前的项的从零开始索引。 当搜索到达列表框的底部时，它将继续从列表框的顶部返回由指定的项`nStartAfter`。 如果`nStartAfter`为 –&1;，从一开始搜索整个列表框。  
  
 `lpszItem`  
 指向以 null 结尾的字符串，其中包含要搜索的前缀。 搜索不区分大小写，因此，此字符串可能包含的任何组合的大写和小写字母。  
  
### <a name="return-value"></a>返回值  
 如果搜索成功的选定项的索引。 如果搜索未成功，返回值是**LB_ERR**且未更改当前所选内容。  
  
### <a name="remarks"></a>备注  
 如有必要，以将选定的项放到视图中，滚动列表框。  
  
 此成员函数不能用于具有一个列表框[LBS_MULTIPLESEL](../../mfc/reference/list-box-styles.md)样式。  
  
 仅当其初始字符 （从起点） 中指定的字符串的字符匹配选择了某项`lpszItem`。  
  
 使用`FindString`成员函数来查找一个字符串，而不选择该项。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&27;](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]  
  
##  <a name="a-nameselitemrangea--clistboxselitemrange"></a><a name="selitemrange"></a>CListBox::SelItemRange  
 多选列表框中选择多个连续的项。  
  
```  
int SelItemRange(
    BOOL bSelect,  
    int nFirstItem,  
    int nLastItem);
```  
  
### <a name="parameters"></a>参数  
 `bSelect`  
 指定如何设置所选内容。 如果`bSelect`是**TRUE**，该字符串是选中并突出显示; 如果**FALSE**，删除突出显示，并且该字符串不再处于选中状态。  
  
 `nFirstItem`  
 指定要设置的第一个项的从零开始索引。  
  
 `nLastItem`  
 指定要设置的最后一项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 **LB_ERR**如果发生错误。  
  
### <a name="remarks"></a>备注  
 此成员函数只能使用多选列表框。 如果您需要在多选列表框中选择只有一项 — 也就是说，如果`nFirstItem`是否等同于`nLastItem`— 调用[SetSel](#setsel)成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&28;](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]  
  
##  <a name="a-namesetanchorindexa--clistboxsetanchorindex"></a><a name="setanchorindex"></a>CListBox::SetAnchorIndex  
 设置中多选列表框，以便开始扩展所选内容的定位点。  
  
```  
void SetAnchorIndex(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定将作为锚点的列表框中项的从零开始索引。  
  
### <a name="remarks"></a>备注  
 在多选列表框中，定位点项是连续的选定项的块中的第一个或最后一个项。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&29;](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]  
  
##  <a name="a-namesetcaretindexa--clistboxsetcaretindex"></a><a name="setcaretindex"></a>CListBox::SetCaretIndex  
 多选列表框中将聚焦框设置为指定索引处的项。  
  
```  
int SetCaretIndex(
    int nIndex,  
    BOOL bScroll = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定要在列表框中接收聚焦框的项的从零开始索引。  
  
 *bScroll*  
 如果此值为 0，该项将滚动，直到完全可见。 如果此值不为 0，该项目滚动之前至少部分可见。  
  
### <a name="return-value"></a>返回值  
 **LB_ERR**如果发生错误。  
  
### <a name="remarks"></a>备注  
 如果该项不可见，则将其滚动到视图。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&30;](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]  
  
##  <a name="a-namesetcolumnwidtha--clistboxsetcolumnwidth"></a><a name="setcolumnwidth"></a>CListBox::SetColumnWidth  
 在多列的列表框中，以像素为单位的所有列的设置的宽度 (使用创建[LBS_MULTICOLUMN](../../mfc/reference/list-box-styles.md)样式)。  
  
```  
void SetColumnWidth(int cxWidth);
```  
  
### <a name="parameters"></a>参数  
 `cxWidth`  
 指定以像素为单位的所有列的宽度。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&31;](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]  
  
##  <a name="a-namesetcursela--clistboxsetcursel"></a><a name="setcursel"></a>CListBox::SetCurSel  
 选择一个字符串，并将其滚动到视图，如有必要。  
  
```  
int SetCurSel(int nSelect);
```  
  
### <a name="parameters"></a>参数  
 `nSelect`  
 指定要选择的字符串的从零开始的索引。 如果`nSelect`为 –&1;，列表框设置为具有未选择任何内容。  
  
### <a name="return-value"></a>返回值  
 `LB_ERR`如果发生错误。  
  
### <a name="remarks"></a>备注  
 当选择新的字符串时，列表框从以前所选字符串中删除突出显示。  
  
 此成员函数只能使用单选列表框。  
  
 若要设置或删除所选多选列表框中，使用[CListBox::SetSel](#setsel)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&32;](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]  
  
##  <a name="a-namesethorizontalextenta--clistboxsethorizontalextent"></a><a name="sethorizontalextent"></a>CListBox::SetHorizontalExtent  
 设置的宽度，以像素为单位，列表框中可以进行水平滚动。  
  
```  
void SetHorizontalExtent(int cxExtent);
```  
  
### <a name="parameters"></a>参数  
 *cxExtent*  
 指定列表框中可以进行水平滚动的像素数。  
  
### <a name="remarks"></a>备注  
 如果列表框的大小小于此值，水平滚动条将水平滚动的列表框中的项。 如果一样大，或者大于此值，列表框中，将会隐藏水平滚动条。  
  
 若要响应对的调用`SetHorizontalExtent`，列表框中必须使用定义[WS_HSCROLL](../../mfc/reference/window-styles.md)样式。  
  
 此成员函数不是适用于多列的列表框。 对于多列的列表框中，调用`SetColumnWidth`成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox 第&33;](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]  
  
##  <a name="a-namesetitemdataa--clistboxsetitemdata"></a><a name="setitemdata"></a>CListBox::SetItemData  
 设置与列表框中指定的项关联的 32 位值。  
  
```  
int SetItemData(
    int nIndex,  
    DWORD_PTR dwItemData);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定项的从零开始的索引。  
  
 `dwItemData`  
 指定要与项相关联的值。  
  
### <a name="return-value"></a>返回值  
 **LB_ERR**如果发生错误。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&34;](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]  
  
##  <a name="a-namesetitemdataptra--clistboxsetitemdataptr"></a><a name="setitemdataptr"></a>CListBox::SetItemDataPtr  
 设置与要指定的指针的列表框中的指定项相关联的 32 位值 ( **void\***)。  
  
```  
int SetItemDataPtr(
    int nIndex,  
    void* pData);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定项的从零开始的索引。  
  
 `pData`  
 指定要与项相关联的指针。  
  
### <a name="return-value"></a>返回值  
 **LB_ERR**如果发生错误。  
  
### <a name="remarks"></a>备注  
 即使在列表框中项的相对位置可能会更改，如添加或移除项就保持有效的生存期内列表框中，该指针。 因此，在框内的项的索引可以改变，但指针保持可靠。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&35;](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]  
  
##  <a name="a-namesetitemheighta--clistboxsetitemheight"></a><a name="setitemheight"></a>CListBox::SetItemHeight  
 在列表框中设置项的高度。  
  
```  
int SetItemHeight(
    int nIndex,  
    UINT cyItemHeight);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 在列表框中指定项的从零开始的索引。 仅当该列表框包含使用此参数**LBS_OWNERDRAWVARIABLE**样式; 否则，它应设置为 0。  
  
 `cyItemHeight`  
 指定高度，以像素为单位的项。  
  
### <a name="return-value"></a>返回值  
 **LB_ERR**如果索引或高度无效。  
  
### <a name="remarks"></a>备注  
 如果该列表框包含[LBS_OWNERDRAWVARIABLE](../../mfc/reference/list-box-styles.md)样式，此函数将由指定的项的高度`nIndex`。 否则，此函数将设置在列表框中的所有项的高度。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&36;](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]  
  
##  <a name="a-namesetlocalea--clistboxsetlocale"></a><a name="setlocale"></a>CListBox::SetLocale  
 设置此列表框中的区域设置标识符。  
  
```  
LCID SetLocale(LCID nNewLocale);
```  
  
### <a name="parameters"></a>参数  
 `nNewLocale`  
 新区域设置标识符 (LCID) 值设置为列表框。  
  
### <a name="return-value"></a>返回值  
 此列表框以前的区域设置标识符 (LCID) 值。  
  
### <a name="remarks"></a>备注  
 如果**SetLocale**不调用，则默认值从系统中获取区域设置。 此系统默认区域设置可以修改通过使用控制面板中的区域 （或国际） 应用程序。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&37;](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]  
  
##  <a name="a-namesetsela--clistboxsetsel"></a><a name="setsel"></a>CListBox::SetSel  
 多选列表框中选择一个字符串。  
  
```  
int SetSel(
    int nIndex,  
    BOOL bSelect = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 包含要设置的字符串的从零开始的索引。 如果为 –&1;，所选内容是添加或删除从所有字符串，具体取决于值`bSelect`。  
  
 `bSelect`  
 指定如何设置所选内容。 如果`bSelect`是`TRUE`，该字符串是选中并突出显示; 如果`FALSE`，删除突出显示，并且该字符串不再处于选中状态。 选择并突出显示默认情况下指定的字符串。  
  
### <a name="return-value"></a>返回值  
 `LB_ERR`如果发生错误。  
  
### <a name="remarks"></a>备注  
 此成员函数只能使用多选列表框。  
  
 若要从单选列表框中选择某个项目，使用[CListBox::SetCurSel](#setcursel)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&38;](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]  
  
##  <a name="a-namesettabstopsa--clistboxsettabstops"></a><a name="settabstops"></a>CListBox::SetTabStops  
 设置在列表框中的制表位位置。  
  
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
 指定在列表框中的制表位数。  
  
 `rgTabStops`  
 指向包含对话框单位中的制表位位置的整数的数组的第一个成员。 对话框单位是一个水平或垂直距离。 一个水平对话框单位等于当前对话框基本宽度单位的四分之一和一个垂直对话框单位等于当前对话框基本高度单位的&1; /&8;。 对话框基本单位根据当前系统字体的高度和宽度计算。 **GetDialogBaseUnits** Windows 函数以像素为单位返回当前对话框基本单位。 必须按递增顺序; 排序的制表位不允许向后制表位。  
  
### <a name="return-value"></a>返回值  
 如果设置了所有选项卡; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 若要设置为默认大小为 2 个对话框单位的制表位，调用此成员函数的无参数版本。 若要设置制表位 2 以外的大小，调用的版本与`cxEachStop`参数。  
  
 若要设置制表位大小的数组，使用与版本`rgTabStops`和`nTabStops`参数。 将为每个值中设置制表位`rgTabStops`，最多指定的数量`nTabStops`。  
  
 若要响应对的调用`SetTabStops`成员函数的列表框中必须已创建与[LBS_USETABSTOPS](../../mfc/reference/list-box-styles.md)样式。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&39;](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]  
  
##  <a name="a-namesettopindexa--clistboxsettopindex"></a><a name="settopindex"></a>CListBox::SetTopIndex  
 确保特定的列表框项可见。  
  
```  
int SetTopIndex(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定列表框中项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为零或**LB_ERR**如果发生错误。  
  
### <a name="remarks"></a>备注  
 系统滚动列表框中，直到指定的任意一项`nIndex`显示顶部的列表框或最大滚动范围已达到。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&40;](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]  
  
##  <a name="a-namevkeytoitema--clistboxvkeytoitem"></a><a name="vkeytoitem"></a>CListBox::VKeyToItem  
 当列表框中的父窗口接收时由框架调用`WM_VKEYTOITEM`从列表框中的消息。  
  
```  
virtual int VKeyToItem(
    UINT nKey,  
    UINT nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nKey`  
 该密钥的虚拟键代码用户按下。 有关标准虚拟键代码的列表，请参见 Winuser.h  
  
 `nIndex`  
 列表框中插入符号的当前位置。  
  
### <a name="return-value"></a>返回值  
 返回 – 2 表示不做进一步操作、 – 1 表示默认操作或一个非负的数字来指定要对其按键执行默认操作的列表框项的索引。  
  
### <a name="remarks"></a>备注  
 `WM_VKEYTOITEM`在接收时，列表框中即可发送消息`WM_KEYDOWN`消息，但仅是否列表框中满足下列两个条件︰  
  
-   具有[LBS_WANTKEYBOARDINPUT](../../mfc/reference/list-box-styles.md)样式集。  
  
-   具有至少一个项。  
  
 你绝不应自己调用此函数。 重写此函数可提供您自己的自定义处理操作的键盘消息。  
  
 您必须返回一个值，以通知框架重写中执行哪些操作。 返回值-2 指示，该应用程序处理选择该项的所有方面，并且不需要进一步的操作的列表框。 之前返回 – 2，您可以设置的选定内容或移动和 / 或插入符号。 若要设置所选内容，使用[SetCurSel](#setcursel)或[SetSel](#setsel)。 若要移动插入符号，请使用[SetCaretIndex](#setcaretindex)。  
  
 返回值-1 表示列表框中应执行击键的响应的默认操作。默认实现返回 – 1。  
  
 返回值 0 或更高版本的列表框中指定项的索引，并指明列表框中应为给定项的键击执行默认操作。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CListBox #&41;](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]  
  
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

