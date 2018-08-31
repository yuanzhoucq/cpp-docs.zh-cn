---
title: CMenu 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMenu
- AFXWIN/CMenu
- AFXWIN/CMenu::CMenu
- AFXWIN/CMenu::AppendMenu
- AFXWIN/CMenu::Attach
- AFXWIN/CMenu::CheckMenuItem
- AFXWIN/CMenu::CheckMenuRadioItem
- AFXWIN/CMenu::CreateMenu
- AFXWIN/CMenu::CreatePopupMenu
- AFXWIN/CMenu::DeleteMenu
- AFXWIN/CMenu::DeleteTempMap
- AFXWIN/CMenu::DestroyMenu
- AFXWIN/CMenu::Detach
- AFXWIN/CMenu::DrawItem
- AFXWIN/CMenu::EnableMenuItem
- AFXWIN/CMenu::FromHandle
- AFXWIN/CMenu::GetDefaultItem
- AFXWIN/CMenu::GetMenuContextHelpId
- AFXWIN/CMenu::GetMenuInfo
- AFXWIN/CMenu::GetMenuItemCount
- AFXWIN/CMenu::GetMenuItemID
- AFXWIN/CMenu::GetMenuItemInfo
- AFXWIN/CMenu::GetMenuState
- AFXWIN/CMenu::GetMenuString
- AFXWIN/CMenu::GetSafeHmenu
- AFXWIN/CMenu::GetSubMenu
- AFXWIN/CMenu::InsertMenu
- AFXWIN/CMenu::InsertMenuItem
- AFXWIN/CMenu::LoadMenu
- AFXWIN/CMenu::LoadMenuIndirect
- AFXWIN/CMenu::MeasureItem
- AFXWIN/CMenu::ModifyMenu
- AFXWIN/CMenu::RemoveMenu
- AFXWIN/CMenu::SetDefaultItem
- AFXWIN/CMenu::SetMenuContextHelpId
- AFXWIN/CMenu::SetMenuInfo
- AFXWIN/CMenu::SetMenuItemBitmaps
- AFXWIN/CMenu::SetMenuItemInfo
- AFXWIN/CMenu::TrackPopupMenu
- AFXWIN/CMenu::TrackPopupMenuEx
- AFXWIN/CMenu::m_hMenu
dev_langs:
- C++
helpviewer_keywords:
- CMenu [MFC], CMenu
- CMenu [MFC], AppendMenu
- CMenu [MFC], Attach
- CMenu [MFC], CheckMenuItem
- CMenu [MFC], CheckMenuRadioItem
- CMenu [MFC], CreateMenu
- CMenu [MFC], CreatePopupMenu
- CMenu [MFC], DeleteMenu
- CMenu [MFC], DeleteTempMap
- CMenu [MFC], DestroyMenu
- CMenu [MFC], Detach
- CMenu [MFC], DrawItem
- CMenu [MFC], EnableMenuItem
- CMenu [MFC], FromHandle
- CMenu [MFC], GetDefaultItem
- CMenu [MFC], GetMenuContextHelpId
- CMenu [MFC], GetMenuInfo
- CMenu [MFC], GetMenuItemCount
- CMenu [MFC], GetMenuItemID
- CMenu [MFC], GetMenuItemInfo
- CMenu [MFC], GetMenuState
- CMenu [MFC], GetMenuString
- CMenu [MFC], GetSafeHmenu
- CMenu [MFC], GetSubMenu
- CMenu [MFC], InsertMenu
- CMenu [MFC], InsertMenuItem
- CMenu [MFC], LoadMenu
- CMenu [MFC], LoadMenuIndirect
- CMenu [MFC], MeasureItem
- CMenu [MFC], ModifyMenu
- CMenu [MFC], RemoveMenu
- CMenu [MFC], SetDefaultItem
- CMenu [MFC], SetMenuContextHelpId
- CMenu [MFC], SetMenuInfo
- CMenu [MFC], SetMenuItemBitmaps
- CMenu [MFC], SetMenuItemInfo
- CMenu [MFC], TrackPopupMenu
- CMenu [MFC], TrackPopupMenuEx
- CMenu [MFC], m_hMenu
ms.assetid: 40cacfdc-d45c-4ec7-bf28-991c72812499
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0c94542fdac3734644771f2659d894d1c8c6f907
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220797"
---
# <a name="cmenu-class"></a>CMenu 类
封装 Windows `HMENU`。  
  
## <a name="syntax"></a>语法  
  
```  
class CMenu : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMenu::CMenu](#cmenu)|构造 `CMenu` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMenu::AppendMenu](#appendmenu)|将新项追加到此菜单的末尾。|  
|[CMenu::Attach](#attach)|将附加的 Windows 菜单句柄`CMenu`对象。|  
|[CMenu::CheckMenuItem](#checkmenuitem)|旁边放置一个复选标记，或者从弹出菜单中的菜单项移除复选标记。|  
|[CMenu::CheckMenuRadioItem](#checkmenuradioitem)|将菜单项旁边的单选按钮，并从所有组中的其他菜单项中移除的单选按钮。|  
|[CMenu::CreateMenu](#createmenu)|创建空菜单，并将其附加到`CMenu`对象。|  
|[CMenu::CreatePopupMenu](#createpopupmenu)|创建空的弹出菜单，并将其附加到`CMenu`对象。|  
|[CMenu::DeleteMenu](#deletemenu)|从菜单中删除指定的项。 如果菜单项具有相关联的弹出菜单，销毁弹出菜单的句柄并释放其占用的内存。|  
|[CMenu::DeleteTempMap](#deletetempmap)|删除任何临时`CMenu`创建的对象`FromHandle`成员函数。|  
|[CMenu::DestroyMenu](#destroymenu)|销毁附加到的菜单`CMenu`对象并释放任何菜单所占用的内存。|  
|[CMenu::Detach](#detach)|从 Windows 菜单句柄中分离`CMenu`对象并返回句柄。|  
|[CMenu::DrawItem](#drawitem)|由框架在所有者描述菜单更改的可视方面时调用。|  
|[CMenu::EnableMenuItem](#enablemenuitem)|启用、 禁用，或变暗 （灰色） 菜单项。|  
|[CMenu::FromHandle](#fromhandle)|返回一个指向`CMenu`给定 Windows 菜单句柄的对象。|  
|[CMenu::GetDefaultItem](#getdefaultitem)|确定指定的菜单上的默认菜单项。|  
|[CMenu::GetMenuContextHelpId](#getmenucontexthelpid)|检索与菜单关联的帮助上下文 ID。|  
|[CMenu::GetMenuInfo](#getmenuinfo)|检索特定菜单上的信息。|  
|[CMenu::GetMenuItemCount](#getmenuitemcount)|确定弹出窗口或顶级菜单中项的数量。|  
|[CMenu::GetMenuItemID](#getmenuitemid)|获取位于指定位置的菜单项的菜单项标识符。|  
|[CMenu::GetMenuItemInfo](#getmenuiteminfo)|检索菜单项有关的信息。|  
|[CMenu::GetMenuState](#getmenustate)|在弹出菜单中返回指定的菜单项或项的数目的状态。|  
|[CMenu::GetMenuString](#getmenustring)|检索指定的菜单项的标签。|  
|[CMenu::GetSafeHmenu](#getsafehmenu)|返回`m_hMenu`包装此`CMenu`对象。|  
|[CMenu::GetSubMenu](#getsubmenu)|检索指向一个弹出菜单。|  
|[CMenu::InsertMenu](#insertmenu)|向菜单下移动其他项中指定位置处插入新菜单项。|  
|[CMenu::InsertMenuItem](#insertmenuitem)|在菜单中的指定位置处插入新菜单项。|  
|[CMenu::LoadMenu](#loadmenu)|从可执行文件加载菜单资源，并将其附加到`CMenu`对象。|  
|[CMenu::LoadMenuIndirect](#loadmenuindirect)|从内存中的菜单模板加载一个菜单，并将其附加到`CMenu`对象。|  
|[CMenu::MeasureItem](#measureitem)|由框架调用以创建一个所有者描述菜单时确定菜单维度。|  
|[CMenu::ModifyMenu](#modifymenu)|更改现有菜单项中指定的位置。|  
|[CMenu::RemoveMenu](#removemenu)|从指定的菜单中删除具有相关联的弹出菜单的菜单项。|  
|[CMenu::SetDefaultItem](#setdefaultitem)|设置指定的菜单的默认菜单项。|  
|[CMenu::SetMenuContextHelpId](#setmenucontexthelpid)|设置要与菜单相关联的帮助上下文 ID。|  
|[CMenu::SetMenuInfo](#setmenuinfo)|设置特定菜单上的信息。|  
|[CMenu::SetMenuItemBitmaps](#setmenuitembitmaps)|将指定的选中标记位图的菜单项与相关联。|  
|[CMenu::SetMenuItemInfo](#setmenuiteminfo)|更改菜单项有关的信息。|  
|[CMenu::TrackPopupMenu](#trackpopupmenu)|在指定位置显示一个浮动的弹出菜单，并在弹出菜单上跟踪选定的项。|  
|[CMenu::TrackPopupMenuEx](#trackpopupmenuex)|在指定位置显示一个浮动的弹出菜单，并在弹出菜单上跟踪选定的项。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CMenu::operator HMENU](#operator_hmenu)|检索菜单对象的句柄。|  
|[CMenu::operator ！ =](#operator_neq)|确定两个菜单对象是否不相等。|  
|[CMenu::operator = =](#operator_eq_eq)|确定两个菜单对象是否相等。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CMenu::m_hMenu](#m_hmenu)|指定的句柄附加到的 Windows 菜单`CMenu`对象。|  
  
## <a name="remarks"></a>备注  
 它提供用于创建、 跟踪、 更新和销毁一个菜单，成员函数。  
  
 创建`CMenu`对象上为本地的堆栈帧，然后调用`CMenu`的成员函数以操作的新菜单中，根据需要。 接下来，调用[CWnd::SetMenu](../../mfc/reference/cwnd-class.md#setmenu)若要将菜单设置为一个窗口，然后输入调用`CMenu`对象的[分离](#detach)成员函数。 `CWnd::SetMenu`成员函数将窗口的菜单设置为的新菜单中，将使窗口重绘以反映此菜单更改，并还将菜单的所有权传递给窗口。 在调用`Detach`分离从 HMENU`CMenu`对象，这样，当本地`CMenu`变量超出范围，`CMenu`对象析构函数不会尝试销毁它不再拥有一个菜单。 窗口被破坏时自动销毁自身的菜单。  
  
 可以使用[LoadMenuIndirect](#loadmenuindirect)成员函数来创建模板在内存中，从一个菜单，但通过调用创建的资源菜单[LoadMenu](#loadmenu)更易于维护和菜单资源本身可以创建和修改通过在菜单编辑器。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMenu`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="appendmenu"></a>  CMenu::AppendMenu  
 菜单的末尾追加新项。  
  
```  
BOOL AppendMenu(
    UINT nFlags,  
    UINT_PTR nIDNewItem = 0,  
    LPCTSTR lpszNewItem = NULL);

 
BOOL AppendMenu(
    UINT nFlags,  
    UINT_PTR nIDNewItem,  
    const CBitmap* pBmp);
```  
  
### <a name="parameters"></a>参数  
 *nFlags*  
 添加到菜单时，请指定新的菜单项的状态信息。 它包含一个或多个备注部分中列出的值。  
  
 *nIDNewItem*  
 指定新的菜单项的命令 ID; 如果*nFlags*设置为 MF_POPUP，菜单句柄 ( `HMENU`) 的弹出菜单。 *NIDNewItem*参数将忽略 （不需要），如果*nFlags*设置为 MF_SEPARATOR。  
  
 *lpszNewItem*  
 指定新的菜单项的内容。 *NFlags*参数用于解释*lpszNewItem*如下所示：  
  
|nFlags|LpszNewItem 的解释|  
|------------|-----------------------------------|  
|MF_OWNERDRAW|包含一个应用程序提供的 32 位值，该应用程序可用于维护与菜单项关联的其他数据。 此 32 位值可供该应用程序处理 WM_MEASUREITEM 和 WM_DRAWITEM 消息时。 值存储在`itemData`提供与这些消息的结构的成员。|  
|MF_STRING|包含指向以 null 结尾的字符串的指针。 这是默认值解释。|  
|MF_SEPARATOR|*LpszNewItem*参数将被忽略 （不需要）。|  
  
 *pBmp*  
 指向`CBitmap`将用作菜单项的对象。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 应用程序可以通过设置中的值指定菜单项的状态*nFlags*。 当*nIDNewItem*指定弹出菜单中，它将成为追加到菜单上的一部分。 如果该菜单将被销毁，还会销毁附加的菜单。 应从分离附加的菜单`CMenu`对象，以避免冲突。 请注意 MF_STRING 和 MF_OWNERDRAW 不是有效的位图版本`AppendMenu`。  
  
 以下列表描述了可能会在设置的标志*nFlags*:  
  
- MF_CHECKED 可作为一个切换 MF_UNCHECKED 放置默认值与选中的项旁边的标记。 当应用程序提供选中标记位图 (请参阅[SetMenuItemBitmaps](#setmenuitembitmaps)成员函数)，显示"上的复选标记"位图。  
  
- MF_UNCHECKED 充当一个开关与 MF_CHECKED 若要删除的项旁边的复选标记。 当应用程序提供选中标记位图 (请参阅`SetMenuItemBitmaps`成员函数)，显示"复选标记关闭"位图。  
  
- MF_DISABLED 禁用菜单项，以便它不能选择，但它不 dim。  
  
- MF_ENABLED 启用菜单项，使它可以选择并将其还原从其灰显状态。  
  
- MF_GRAYED 禁用菜单项，以便它不能选择，并将使其变灰。  
  
- MF_MENUBARBREAK 将项放置在静态菜单或弹出菜单中的新列中在新行上。 由一垂直条分隔线，将与旧列分隔新的弹出菜单列。  
  
- MF_MENUBREAK 将项放置在静态菜单或弹出菜单中的新列中在新行上。 无分隔线位于各列之间。  
  
- MF_OWNERDRAW 指定项目的所有者描述项。 当第一次显示菜单时，拥有菜单的窗口接收 WM_MEASUREITEM 消息时，它检索的高度和宽度的菜单项。 WM_DRAWITEM 消息是发送只要所有者必须更新菜单项的可视外观。 此选项不是有效的顶级菜单项。  
  
- MF_POPUP 指定菜单项具有与其关联一个弹出菜单。 ID 参数指定一个要与项相关联的弹出菜单的句柄。 这用于将顶级弹出菜单或层次结构的弹出菜单添加到弹出菜单项。  
  
- MF_SEPARATOR 绘制水平的分隔线。 仅在弹出菜单中使用。 不能变暗、 禁用或突出显示此行。 将忽略其他参数。  
  
- MF_STRING 指定菜单项是一个字符串。  
  
 以下组的每个列出是互斥的不能一起使用的标志：  
  
- MF_DISABLED、 MF_ENABLED 和 MF_GRAYED  
  
- MF_STRING、 MF_OWNERDRAW、 MF_SEPARATOR 和位图版本  
  
- MF_MENUBARBREAK 和 MF_MENUBREAK  
  
- MF_CHECKED 和 MF_UNCHECKED  
  
 每当驻留在的菜单窗口更改时 （无论是否显示在窗口），该应用程序应调用[CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar)。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CMenu::CreateMenu](#createmenu)。  
  
##  <a name="attach"></a>  CMenu::Attach  
 将附加到现有 Windows 菜单`CMenu`对象。  
  
```  
BOOL Attach(HMENU hMenu);
```  
  
### <a name="parameters"></a>参数  
 *hMenu*  
 指定 Windows 菜单的句柄。  
  
### <a name="return-value"></a>返回值  
 如果操作成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 如果菜单已附加到，不应调用此函数`CMenu`对象。 菜单句柄存储在`m_hMenu`数据成员。  
  
 如果你想要操作的菜单已与窗口关联，则可以使用[CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu)函数可获取菜单的句柄。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]  
  
##  <a name="checkmenuitem"></a>  CMenu::CheckMenuItem  
 添加复选标记或删除从弹出菜单中的菜单项的复选标记。  
  
```  
UINT CheckMenuItem(
    UINT nIDCheckItem,  
    UINT nCheck);
```  
  
### <a name="parameters"></a>参数  
 *nIDCheckItem*  
 指定要检查的菜单项，由*n 请查看*。  
  
 *n 请查看*  
 指定如何检查菜单项以及如何确定在菜单中的项的位置。 *N 请查看*参数可以是 MF_CHECKED 或 MF_UNCHECKED 与 MF_BYPOSITION 或 MF_BYCOMMAND 标志的组合。 可以通过使用按位 OR 运算符组合这些标志。 它们具有以下含义：  
  
- MF_BYCOMMAND 指定参数提供了现有的菜单项的命令 ID。 这是默认设置。  
  
- MF_BYPOSITION 指定参数提供了现有的菜单项的位置。 第一项位于位置 0。  
  
- MF_CHECKED 可作为一个切换 MF_UNCHECKED 放置默认值与选中的项旁边的标记。  
  
- MF_UNCHECKED 充当一个开关与 MF_CHECKED 若要删除的项旁边的复选标记。  
  
### <a name="return-value"></a>返回值  
 项的前一状态： MF_CHECKED 或 MF_UNCHECKED，或 0xFFFFFFFF 如果菜单项不存在。  
  
### <a name="remarks"></a>备注  
 *NIDCheckItem*参数指定要修改的项。  
  
 *NIDCheckItem*参数可识别的弹出菜单项，以及一个菜单项。 检查弹出菜单项不需任何特殊步骤。 无法检查顶级菜单项。 必须按位置检查弹出菜单项，因为它不具有与之关联的菜单项标识符。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CMenu::GetMenuState](#getmenustate)。  
  
##  <a name="checkmenuradioitem"></a>  CMenu::CheckMenuRadioItem  
 检查指定的菜单项并使其成为单选项。  
  
```  
BOOL CheckMenuRadioItem(
    UINT nIDFirst,  
    UINT nIDLast,  
    UINT nIDItem,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>参数  
 *nIDFirst*  
 指定 (作为一个 ID 或偏移量，具体取决于值*nFlags*) 中的单选按钮组的第一个菜单项。  
  
 *nIDLast*  
 指定 (作为一个 ID 或偏移量，具体取决于值*nFlags*) 中的单选按钮组的最后一个菜单项。  
  
 *nIDItem*  
 指定 (作为一个 ID 或偏移量，具体取决于值*nFlags*) 将进行检查，使用单选按钮的组中的项。  
  
 *nFlags*  
 指定解释*nIDFirst*， *nIDLast*，并*nIDItem*如下所示：  
  
|nFlags|解释|  
|------------|--------------------|  
|MF_BYCOMMAND|指定参数提供了现有的菜单项的命令 ID。 如果设置 MF_BYCOMMAND 既不 MF_BYPOSITION，这是默认值。|  
|MF_BYPOSITION|指定参数提供了现有的菜单项的位置。 第一项位于位置 0。|  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值否则为，将 0  
  
### <a name="remarks"></a>备注  
 同时，在该函数取消选中相关联的组中的所有其他菜单项并清除这些项的单选项类型标志。 使用单选按钮 （或项目符号） 位图，而不选中标记位图显示选中的项。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[ON_COMMAND_RANGE](message-map-macros-mfc.md#on_command_range)。  
  
##  <a name="cmenu"></a>  CMenu::CMenu  
 创建空菜单，并将其附加到`CMenu`对象。  
  
```  
CMenu();
```  
  
### <a name="remarks"></a>备注  
 直到调用其中一个创建或加载的成员函数不创建菜单 `CMenu:`  
  
- [CreateMenu](#createmenu)  
  
- [CreatePopupMenu](#createpopupmenu)  
  
- [LoadMenu](#loadmenu)  
  
- [LoadMenuIndirect](#loadmenuindirect)  
  
- [附加](#attach)  
  
##  <a name="createmenu"></a>  CMenu::CreateMenu  
 创建一个菜单，并将其附加到`CMenu`对象。  
  
```  
BOOL CreateMenu();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果成功，则创建菜单否则为 0。  
  
### <a name="remarks"></a>备注  
 菜单是最初为空。 可以使用添加菜单项`AppendMenu`或`InsertMenu`成员函数。  
  
 如果菜单分配给一个窗口，它时自动销毁窗口被破坏。  
  
 退出之前，应用程序必须释放系统资源与菜单关联，如果菜单未分配给一个窗口。 应用程序通过调用释放一个菜单[DestroyMenu](#destroymenu)成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#22](../../mfc/reference/codesnippet/cpp/cmenu-class_2.cpp)]  
  
##  <a name="createpopupmenu"></a>  CMenu::CreatePopupMenu  
 创建弹出菜单，并将其附加到`CMenu`对象。  
  
```  
BOOL CreatePopupMenu();
```  
  
### <a name="return-value"></a>返回值  
 如果已成功创建弹出菜单; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 菜单是最初为空。 可以使用添加菜单项`AppendMenu`或`InsertMenu`成员函数。 应用程序可以将弹出菜单添加到现有菜单或弹出菜单。 `TrackPopupMenu`为浮动的弹出菜单中显示此菜单以及弹出菜单上跟踪的选择使用成员函数。  
  
 如果菜单分配给一个窗口，它时自动销毁窗口被破坏。 如果菜单添加到现有菜单中，自动销毁时销毁该菜单。  
  
 退出之前，应用程序必须释放系统资源，如果菜单未分配给一个窗口弹出菜单与相关联。 应用程序通过调用释放一个菜单[DestroyMenu](#destroymenu)成员函数。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CMenu::CreateMenu](#createmenu)。  
  
##  <a name="deletemenu"></a>  CMenu::DeleteMenu  
 从菜单中删除的项。  
  
```  
BOOL DeleteMenu(
    UINT nPosition,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>参数  
 *位置*  
 指定的菜单项，是要删除由*nFlags*。  
  
 *nFlags*  
 用于解释*位置*如下所示：  
  
|nFlags|位置的解释|  
|------------|---------------------------------|  
|MF_BYCOMMAND|指定参数提供了现有的菜单项的命令 ID。 如果设置 MF_BYCOMMAND 既不 MF_BYPOSITION，这是默认值。|  
|MF_BYPOSITION|指定参数提供了现有的菜单项的位置。 第一项位于位置 0。|  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果菜单项具有相关联的弹出菜单中，`DeleteMenu`销毁弹出菜单的句柄并释放的内存使用的弹出菜单。  
  
 每当驻留在的菜单窗口更改时 （无论是否显示在窗口），该应用程序必须调用[CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar)。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu)。  
  
##  <a name="deletetempmap"></a>  CMenu::DeleteTempMap  
 自动调用`CWinApp`空闲时间处理程序中，删除任何临时`CMenu`创建的对象[FromHandle](#fromhandle)成员函数。  
  
```  
static void PASCAL DeleteTempMap();
```  
  
### <a name="remarks"></a>备注  
 `DeleteTempMap` 分离 Windows 菜单对象附加到一个临时`CMenu`对象删除之前`CMenu`对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#23](../../mfc/reference/codesnippet/cpp/cmenu-class_3.cpp)]  
  
##  <a name="destroymenu"></a>  CMenu::DestroyMenu  
 销毁菜单和任何使用的 Windows 资源。  
  
```  
BOOL DestroyMenu();
```  
  
### <a name="return-value"></a>返回值  
 销毁菜单; 如果非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 从分离菜单`CMenu`对象之前被销毁。 Windows`DestroyMenu`函数自动调用`CMenu`析构函数。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CMenu::CreateMenu](#createmenu)。  
  
##  <a name="detach"></a>  CMenu::Detach  
 从 Windows 菜单中分离`CMenu`对象并返回句柄。  
  
```  
HMENU Detach();
```  
  
### <a name="return-value"></a>返回值  
 Windows 菜单中，如果成功，则 HMENU，类型的句柄否则为，为 NULL。  
  
### <a name="remarks"></a>备注  
 `m_hMenu`数据成员设置为 NULL。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]  
  
##  <a name="drawitem"></a>  CMenu::DrawItem  
 由框架在所有者描述菜单更改的可视方面时调用。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>参数  
 *lpDrawItemStruct*  
 一个指向[DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md)结构，其中包含有关绘图所需的类型的信息。  
  
### <a name="remarks"></a>备注  
 `itemAction`的成员`DRAWITEMSTRUCT`结构定义要执行的绘制操作。 重写此成员函数以实现绘制所有者描述的`CMenu`对象。 应用程序应还原所有图形设备接口 (GDI) 对象的显示上下文中提供选定*lpDrawItemStruct*之前终止此成员函数。  
  
 请参阅[CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)有关的说明`DRAWITEMSTRUCT`结构。  
  
### <a name="example"></a>示例  
 下面的代码是从 MFC [CTRLTEST](../../visual-cpp-samples.md)示例：  
  
 [!code-cpp[NVC_MFCWindowing#24](../../mfc/reference/codesnippet/cpp/cmenu-class_4.cpp)]  
  
##  <a name="enablemenuitem"></a>  CMenu::EnableMenuItem  
 启用、 禁用，或变暗的菜单项。  
  
```  
UINT EnableMenuItem(
    UINT nIDEnableItem,  
    UINT nEnable);
```  
  
### <a name="parameters"></a>参数  
 *nIDEnableItem*  
 指定菜单项，若要启用，由*nEnable*。 弹出菜单项，以及标准菜单项，可以指定此参数。  
  
 *nEnable*  
 指定要执行的操作。 它可以是 MF_DISABLED、 MF_ENABLED 或 MF_GRAYED MF_BYCOMMAND 或 MF_BYPOSITION 的组合。 可以通过使用按位 OR 运算符组合这些值。 这些值的含义如下：  
  
- MF_BYCOMMAND 指定参数提供了现有的菜单项的命令 ID。 这是默认设置。  
  
- MF_BYPOSITION 指定参数提供了现有的菜单项的位置。 第一项位于位置 0。  
  
- MF_DISABLED 禁用菜单项，以便它不能选择，但它不 dim。  
  
- MF_ENABLED 启用菜单项，使它可以选择并将其还原从其灰显状态。  
  
- MF_GRAYED 禁用菜单项，以便它不能选择，并将使其变灰。  
  
### <a name="return-value"></a>返回值  
 以前的状态 （MF_DISABLED、 MF_ENABLED 或 MF_GRAYED） 或为-1 是否有效。  
  
### <a name="remarks"></a>备注  
 [CreateMenu](#createmenu)， [InsertMenu](#insertmenu)， [ModifyMenu](#modifymenu)，以及[LoadMenuIndirect](#loadmenuindirect)成员函数还可以设置的状态 （已启用，已禁用，或变暗） 的菜单项。  
  
 使用 MF_BYPOSITION 值需要应用程序使用的正确`CMenu`。 如果`CMenu`的菜单栏，受影响的顶级菜单项 （在菜单栏中的项）。 若要按位置弹出窗口或嵌套的弹出菜单中设置项的状态，应用程序必须指定`CMenu`的弹出菜单。  
  
 当应用程序指定 MF_BYCOMMAND 标志时，Windows 将检查所有属于的弹出菜单项`CMenu`; 因此，除非存在重复的菜单项时，使用`CMenu`的菜单栏就足够。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#25](../../mfc/reference/codesnippet/cpp/cmenu-class_5.cpp)]  
  
##  <a name="fromhandle"></a>  CMenu::FromHandle  
 返回一个指向`CMenu`到菜单中提供的 Windows 句柄的对象。  
  
```  
static CMenu* PASCAL FromHandle(HMENU hMenu);
```  
  
### <a name="parameters"></a>参数  
 *hMenu*  
 Windows 句柄菜单。  
  
### <a name="return-value"></a>返回值  
 一个指向`CMenu`这可能是临时的还是永久。  
  
### <a name="remarks"></a>备注  
 如果`CMenu`对象尚未附加到 Windows 菜单对象，临时`CMenu`创建并附加对象。  
  
 此临时`CMenu`对象下一次该应用程序在其事件循环中，此时会删除所有临时对象具有空闲时间之前才有效。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CMenu::CreateMenu](#createmenu)。  
  
##  <a name="getdefaultitem"></a>  CMenu::GetDefaultItem  
 确定指定的菜单上的默认菜单项。  
  
```  
UINT GetDefaultItem(
    UINT gmdiFlags,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>参数  
 *gmdiFlags*  
 值，该值指定该函数搜索菜单项的方式。 此参数可以是 none、 一个，或以下值的组合：  
  
|“值”|含义|  
|-----------|-------------|  
|GMDI_GOINTOPOPUPS|指定，是否默认项是指打开子菜单，该函数将在相应的子菜单以递归方式搜索。 如果子菜单中没有默认项，则返回值标识用于打开子菜单项。<br /><br /> 默认情况下，该函数返回在指定的菜单中，而不管它是用于打开子菜单项的第一个默认项。|  
|GMDI_USEDISABLED|指定该函数将返回默认项，即使它处于禁用状态。<br /><br /> 默认情况下，该函数将跳过已禁用或灰项。|  
  
 *fByPos*  
 值，该值指定是否检索菜单项的标识符或其位置。 如果此参数为 FALSE，返回的标识符。 否则，返回的位置。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，返回值是标识符或菜单项的位置。 如果函数失败，返回值为-1。  
  
### <a name="remarks"></a>备注  
 此成员函数可实现 Win32 函数的行为[GetMenuDefaultItem](/windows/desktop/api/winuser/nf-winuser-getmenudefaultitem)，如 Windows SDK 中所述。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CMenu::InsertMenu](#insertmenu)。  
  
##  <a name="getmenucontexthelpid"></a>  CMenu::GetMenuContextHelpId  
 检索与关联 ID 的上下文帮助`CMenu`。  
  
```  
DWORD GetMenuContextHelpId() const;  
```  
  
### <a name="return-value"></a>返回值  
 与当前关联 ID 的上下文帮助`CMenu`如果有的话; 否则为零。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CMenu::InsertMenu](#insertmenu)。  
  
##  <a name="getmenuinfo"></a>  CMenu::GetMenuInfo  
 检索菜单的信息。  
  
```  
BOOL GetMenuInfo(LPMENUINFO lpcmi) const;  
```  
  
### <a name="parameters"></a>参数  
 *lpcmi*  
 一个指向[MENUINFO](/windows/desktop/api/winuser/ns-winuser-tagmenuinfo)结构，它包含菜单上的信息。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，返回值为非零值;否则，返回值为零。  
  
### <a name="remarks"></a>备注  
 调用此函数可检索菜单有关的信息。  
  
##  <a name="getmenuitemcount"></a>  CMenu::GetMenuItemCount  
 确定弹出窗口或顶级菜单中项的数量。  
  
```  
UINT GetMenuItemCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则在菜单中的项的数目否则为-1。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu)。  
  
##  <a name="getmenuitemid"></a>  CMenu::GetMenuItemID  
 获取位于由定义的位置的菜单项的菜单项标识符*nPos*。  
  
```  
UINT GetMenuItemID(int nPos) const;  
```  
  
### <a name="parameters"></a>参数  
 *nPos*  
 指定的位置 （从零开始） 菜单项中要检索其 ID。  
  
### <a name="return-value"></a>返回值  
 如果函数运行成功的弹出菜单中指定的项的项 ID。 如果指定的项，将弹出菜单 （而不是弹出菜单中的项） 的返回值为-1。 如果*nPos*对应分隔符的菜单项，返回值为 0。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CMenu::InsertMenu](#insertmenu)。  
  
##  <a name="getmenuiteminfo"></a>  CMenu::GetMenuItemInfo  
 检索菜单项有关的信息。  
  
```  
BOOL GetMenuItemInfo(
    UINT uItem,  
    LPMENUITEMINFO lpMenuItemInfo,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>参数  
 *uItem*  
 标识符或要获取其相关信息的菜单项的位置。 此参数的含义取决于值`ByPos`。  
  
 *lpMenuItemInfo*  
 一个指向[MENUITEMINFO](/windows/desktop/api/winuser/ns-winuser-tagmenuiteminfoa)，如下所述在 Windows SDK 中，其中包含关于菜单的信息。  
  
 *fByPos*  
 值，该值指定的含义`nIDItem`。 默认情况下，`ByPos`为 FALSE，指示该 uItem 是菜单项标识符。 如果`ByPos`未设置为 FALSE，它表示菜单项位置。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则返回值为非零值。 如果函数失败，则返回值为零。 若要获得扩展错误信息，请使用 Win32 函数[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)，如 Windows SDK 中所述。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 函数[GetMenuItemInfo](/windows/desktop/api/winuser/nf-winuser-getmenuiteminfoa)，如 Windows SDK 中所述。 请注意，在的 MFC 实现`GetMenuItemInfo`，不要使用到菜单的句柄。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#26](../../mfc/reference/codesnippet/cpp/cmenu-class_6.cpp)]  
  
##  <a name="getmenustate"></a>  CMenu::GetMenuState  
 在弹出菜单中返回指定的菜单项或项的数目的状态。  
  
```  
UINT GetMenuState(
    UINT nID,  
    UINT nFlags) const;  
```  
  
### <a name="parameters"></a>参数  
 *nID*  
 指定菜单项 ID，由*nFlags*。  
  
 *nFlags*  
 指定的性质*nID*。 它可以是下列值之一：  
  
- MF_BYCOMMAND 指定参数提供了现有的菜单项的命令 ID。 这是默认设置。  
  
- MF_BYPOSITION 指定参数提供了现有的菜单项的位置。 第一项位于位置 0。  
  
### <a name="return-value"></a>返回值  
 值为 0xFFFFFFFF，如果指定的项不存在。 如果*nId*标识弹出菜单中，高位字节包含弹出菜单中的项的数目，低序位字节包含弹出菜单与关联的菜单标志。 否则返回值都属于以下列表中的值的掩码 （布尔值或） (此掩码描述状态的菜单项*nId*标识):  
  
- MF_CHECKED 可作为一个切换 MF_UNCHECKED 放置默认值与选中的项旁边的标记。 当应用程序提供选中标记位图 (请参阅`SetMenuItemBitmaps`成员函数)，显示"上的复选标记"位图。  
  
- MF_DISABLED 禁用菜单项，以便它不能选择，但它不 dim。  
  
- MF_ENABLED 启用菜单项，使它可以选择并将其还原从其灰显状态。 请注意此常量的值为 0;使用此值时，应用程序不应测试针对失败的 0。  
  
- MF_GRAYED 禁用菜单项，以便它不能选择，并将使其变灰。  
  
- MF_MENUBARBREAK 将项放置在静态菜单或弹出菜单中的新列中在新行上。 由一垂直条分隔线，将与旧列分隔新的弹出菜单列。  
  
- MF_MENUBREAK 将项放置在静态菜单或弹出菜单中的新列中在新行上。 无分隔线位于各列之间。  
  
- MF_SEPARATOR 绘制水平的分隔线。 仅在弹出菜单中使用。 不能变暗、 禁用或突出显示此行。 将忽略其他参数。  
  
- MF_UNCHECKED 充当一个开关与 MF_CHECKED 若要删除的项旁边的复选标记。 当应用程序提供选中标记位图 (请参阅`SetMenuItemBitmaps`成员函数)，显示"复选标记关闭"位图。 请注意此常量的值为 0;使用此值时，应用程序不应测试针对失败的 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#27](../../mfc/reference/codesnippet/cpp/cmenu-class_7.cpp)]  
  
##  <a name="getmenustring"></a>  CMenu::GetMenuString  
 将指定的菜单项的标签复制到指定的缓冲区。  
  
```  
int GetMenuString(
    UINT nIDItem,  
    LPTSTR lpString,  
    int nMaxCount,  
    UINT nFlags) const;  
  
int GetMenuString(
    UINT nIDItem,  
    CString& rString,  
    UINT nFlags) const;  
```  
  
### <a name="parameters"></a>参数  
 *nIDItem*  
 在菜单中，具体取决于的值指定菜单项的整数标识符或菜单项的偏移量*nFlags*。  
  
 *lpString*  
 指向将接收该标签的缓冲区。  
  
 *rString*  
 对引用`CString`要接收复制的菜单字符串的对象。  
  
 *nMaxCount*  
 指定要复制的标签的最大长度 （以字符为单位）。 如果标签的长度超过中指定的最大*nMaxCount*，额外的字符将被截断。  
  
 *nFlags*  
 指定的解释*nIDItem*参数。 它可以是下列值之一：  
  
|nFlags|NIDItem 的解释|  
|------------|-------------------------------|  
|MF_BYCOMMAND|指定参数提供了现有的菜单项的命令 ID。 如果设置 MF_BYCOMMAND 既不 MF_BYPOSITION，这是默认值。|  
|MF_BYPOSITION|指定参数提供了现有的菜单项的位置。 第一项位于位置 0。|  
  
### <a name="return-value"></a>返回值  
 指定实际将复制到缓冲区，不包括 null 终止符的字符数。  
  
### <a name="remarks"></a>备注  
 *NMaxCount*参数应为一个大于要容纳终止字符串的空字符的标签中的字符数。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CMenu::InsertMenu](#insertmenu)。  
  
##  <a name="getsafehmenu"></a>  CMenu::GetSafeHmenu  
 返回包装此 HMENU`CMenu`对象或为空`CMenu`指针。  
  
```  
HMENU GetSafeHmenu() const;  
```  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CMenu::LoadMenu](#loadmenu)。  
  
##  <a name="getsubmenu"></a>  CMenu::GetSubMenu  
 检索`CMenu`弹出菜单的对象。  
  
```  
CMenu* GetSubMenu(int nPos) const;  
```  
  
### <a name="parameters"></a>参数  
 *nPos*  
 指定的菜单中包含的弹出菜单的位置。 位置值从 0 开始，第一个菜单项。 不能在此函数中使用弹出菜单的标识符。  
  
### <a name="return-value"></a>返回值  
 一个指向`CMenu`对象，其`m_hMenu`成员如果弹出菜单中的给定位置存在包含弹出菜单的句柄; 否则为 NULL。 如果`CMenu`对象不存在，则会创建一个临时。 `CMenu`不应存储返回的指针。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CMenu::TrackPopupMenu](#trackpopupmenu)。  
  
##  <a name="insertmenu"></a>  CMenu::InsertMenu  
 指定的位置处插入新菜单项*位置*菜单中向下移动其他项。  
  
```  
BOOL InsertMenu(
    UINT nPosition,  
    UINT nFlags,  
    UINT_PTR nIDNewItem = 0,  
    LPCTSTR lpszNewItem = NULL);

 
BOOL InsertMenu(
    UINT nPosition,  
    UINT nFlags,  
    UINT_PTR nIDNewItem,  
    const CBitmap* pBmp);
```  
  
### <a name="parameters"></a>参数  
 *位置*  
 指定要在其前面的新菜单项是要插入的菜单项。 *NFlags*参数可用于解释*位置*以下方面：  
  
|nFlags|位置的解释|  
|------------|---------------------------------|  
|MF_BYCOMMAND|指定参数提供了现有的菜单项的命令 ID。 如果设置 MF_BYCOMMAND 既不 MF_BYPOSITION，这是默认值。|  
|MF_BYPOSITION|指定参数提供了现有的菜单项的位置。 第一项位于位置 0。 如果*位置*为-1，新的菜单项追加到菜单的末尾。|  
  
 *nFlags*  
 指定如何*位置*解释，并添加到菜单时指定新的菜单项的状态信息。 可能设置的标志的列表，请参阅[AppendMenu](#appendmenu)成员函数。 若要指定多个值，请使用按位 OR 运算符合并 MF_BYCOMMAND 或 MF_BYPOSITION 标志。  
  
 *nIDNewItem*  
 指定新的菜单项的命令 ID; 如果*nFlags*设置为 MF_POPUP，弹出菜单的菜单句柄 (HMENU)。 *NIDNewItem*参数将忽略 （不需要），如果*nFlags*设置为 MF_SEPARATOR。  
  
 *lpszNewItem*  
 指定新的菜单项的内容。 *nFlags*可用于解释*lpszNewItem*以下方面：  
  
|nFlags|LpszNewItem 的解释|  
|------------|-----------------------------------|  
|MF_OWNERDRAW|包含一个应用程序提供的 32 位值，该应用程序可用于维护与菜单项关联的其他数据。 此 32 位的值是可用于在应用程序`itemData`提供的结构中的成员[WM_MEASUREITEM](/windows/desktop/Controls/wm-measureitem)并[WM_DRAWITEM](/windows/desktop/Controls/wm-drawitem)消息。 菜单项的初始显示或更改时，将发送这些消息。|  
|MF_STRING|包含指向以 null 结尾的字符串的长指针。 这是默认值解释。|  
|MF_SEPARATOR|*LpszNewItem*参数将被忽略 （不需要）。|  
  
 *pBmp*  
 指向`CBitmap`将用作菜单项的对象。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 应用程序可以通过设置中的值指定菜单项的状态*nFlags*。  
  
 每当驻留在的菜单窗口更改时 （无论是否显示在窗口），该应用程序应调用`CWnd::DrawMenuBar`。  
  
 当*nIDNewItem*指定弹出菜单中，它将成为在插入的菜单的一部分。 如果该菜单将被销毁，插入菜单上也将被破坏。 应从分离插入的菜单`CMenu`对象，以避免冲突。  
  
 如果多文档界面 (MDI) 子窗口最大化的活动点和应用程序插入到 MDI 应用程序的菜单上，通过调用此函数并指定 MF_BYPOSITION 标志，菜单弹出菜单插入更远比保留的一个位置预期。 这是因为活动的 MDI 子窗口的控件菜单插入 MDI 框架窗口的菜单栏中的第一个位置。 若要正确放置菜单，该应用程序必须将 1 添加到位置值，否则将使用该值。 应用程序可以使用 WM_MDIGETACTIVE 消息来确定当前处于活动状态的子窗口已最大化。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#28](../../mfc/reference/codesnippet/cpp/cmenu-class_8.cpp)]  
  
##  <a name="insertmenuitem"></a>  CMenu::InsertMenuItem  
 在菜单中的指定位置处插入新菜单项。  
  
```  
BOOL InsertMenuItem(
    UINT uItem,  
    LPMENUITEMINFO lpMenuItemInfo,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>参数  
 *uItem*  
 请参阅的说明*uItem*中[InsertMenuItem](/windows/desktop/api/winuser/nf-winuser-insertmenuitema) Windows SDK 中。  
  
 *lpMenuItemInfo*  
 请参阅的说明*lpmii*中`InsertMenuItem`Windows SDK 中。  
  
 *fByPos*  
 请参阅的说明*fByPosition*中`InsertMenuItem`Windows SDK 中。  
  
### <a name="remarks"></a>备注  
 此函数包装[InsertMenuItem](/windows/desktop/api/winuser/nf-winuser-insertmenuitema)Windows SDK 中所述。  
  
##  <a name="loadmenu"></a>  CMenu::LoadMenu  
 从应用程序的可执行文件加载菜单资源，并将其附加到`CMenu`对象。  
  
```  
BOOL LoadMenu(LPCTSTR lpszResourceName);  
BOOL LoadMenu(UINT nIDResource);
```  
  
### <a name="parameters"></a>参数  
 *lpszResourceName*  
 指向以 null 终止的字符串，其中包含要加载的菜单资源的名称。  
  
 *nIDResource*  
 指定要加载该菜单资源菜单 ID。  
  
### <a name="return-value"></a>返回值  
 如果成功，则加载该菜单资源，非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 退出之前，应用程序必须释放系统资源与菜单关联，如果菜单未分配给一个窗口。 应用程序通过调用释放一个菜单[DestroyMenu](#destroymenu)成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#29](../../mfc/reference/codesnippet/cpp/cmenu-class_9.cpp)]  
  
##  <a name="loadmenuindirect"></a>  CMenu::LoadMenuIndirect  
 从内存中的菜单模板加载资源，并将其附加到`CMenu`对象。  
  
```  
BOOL LoadMenuIndirect(const void* lpMenuTemplate);
```  
  
### <a name="parameters"></a>参数  
 *lpMenuTemplate*  
 指向菜单模板 (即单个[MENUITEMTEMPLATEHEADER](/windows/desktop/api/winuser/ns-winuser-menuitemtemplateheader)结构和集合的一个或多个[MENUITEMTEMPLATE](/windows/desktop/api/winuser/ns-winuser-menuitemtemplate)结构)。 有关这些两个结构的详细信息，请参阅 Windows SDK。  
  
### <a name="return-value"></a>返回值  
 如果成功，则加载该菜单资源，非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 菜单模板是后跟一个或多个集合的标头[MENUITEMTEMPLATE](/windows/desktop/api/winuser/ns-winuser-menuitemtemplate)结构，其中每个可能包含一个或多个菜单项和弹出菜单。  
  
 版本号应为 0。  
  
 `mtOption`标志应包括 MF_END 弹出列表中的最后一项以及主列表中的最后一项。 请参阅`AppendMenu`其他标志的成员函数。 `mtId` MF_POPUP 中指定时，必须从 MENUITEMTEMPLATE 结构省略成员`mtOption`。  
  
 为 MENUITEMTEMPLATE 结构必须足够大的分配的空间`mtString`以包含菜单项作为以 null 结尾的字符串的名称。  
  
 退出之前，应用程序必须释放系统资源与菜单关联，如果菜单未分配给一个窗口。 应用程序通过调用释放一个菜单[DestroyMenu](#destroymenu)成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#30](../../mfc/reference/codesnippet/cpp/cmenu-class_10.cpp)]  
  
##  <a name="m_hmenu"></a>  CMenu::m_hMenu  
 指定附加到的 Windows 菜单的 HMENU 句柄`CMenu`对象。  
  
```  
HMENU m_hMenu;  
```  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CMenu::LoadMenu](#loadmenu)。  
  
##  <a name="measureitem"></a>  CMenu::MeasureItem  
 创建所有者绘制样式的菜单时由框架调用。  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>参数  
 *lpMeasureItemStruct*  
 一个指向`MEASUREITEMSTRUCT`结构。  
  
### <a name="remarks"></a>备注  
 默认情况下，此成员函数没有任何影响。 重写此成员函数，并填充`MEASUREITEMSTRUCT`结构以通知 Windows 菜单的维度。  
  
 请参阅[CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)有关的说明`MEASUREITEMSTRUCT`结构。  
  
### <a name="example"></a>示例  
 下面的代码是从 MFC [CTRLTEST](../../visual-cpp-samples.md)示例：  
  
 [!code-cpp[NVC_MFCWindowing#31](../../mfc/reference/codesnippet/cpp/cmenu-class_11.cpp)]  
  
##  <a name="modifymenu"></a>  CMenu::ModifyMenu  
 更改现有菜单项中指定的位置*位置*。  
  
```  
BOOL ModifyMenu(
    UINT nPosition,  
    UINT nFlags,  
    UINT_PTR nIDNewItem = 0,  
    LPCTSTR lpszNewItem = NULL);

 
BOOL ModifyMenu(
    UINT nPosition,  
    UINT nFlags,  
    UINT_PTR nIDNewItem,  
    const CBitmap* pBmp);
```  
  
### <a name="parameters"></a>参数  
 *位置*  
 指定要更改的菜单项。 *NFlags*参数可用于解释*位置*以下方面：  
  
|nFlags|位置的解释|  
|------------|---------------------------------|  
|MF_BYCOMMAND|指定参数提供了现有的菜单项的命令 ID。 如果设置 MF_BYCOMMAND 既不 MF_BYPOSITION，这是默认值。|  
|MF_BYPOSITION|指定参数提供了现有的菜单项的位置。 第一项位于位置 0。|  
  
 *nFlags*  
 指定如何*位置*解释，并提供有关要与此菜单项进行的更改的信息。 可以设置的标志的列表，请参阅[AppendMenu](#appendmenu)成员函数。  
  
 *nIDNewItem*  
 指定修改后的菜单项的命令 ID; 如果*nFlags*设置为 MF_POPUP，弹出菜单的菜单句柄 (HMENU)。 *NIDNewItem*参数将忽略 （不需要），如果*nFlags*设置为 MF_SEPARATOR。  
  
 *lpszNewItem*  
 指定新的菜单项的内容。 *NFlags*参数可用于解释*lpszNewItem*以下方面：  
  
|nFlags|LpszNewItem 的解释|  
|------------|-----------------------------------|  
|MF_OWNERDRAW|包含一个应用程序提供的 32 位值，该应用程序可用于维护与菜单项关联的其他数据。 此 32 位值可供该应用程序处理 MF_MEASUREITEM 和 MF_DRAWITEM 时。|  
|MF_STRING|包含长指针到以 null 结尾的字符串或`CString`。|  
|MF_SEPARATOR|*LpszNewItem*参数将被忽略 （不需要）。|  
  
 *pBmp*  
 指向`CBitmap`将用作菜单项的对象。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 应用程序中设置的值指定菜单项的新状态*nFlags*。 如果此函数取代弹出菜单的菜单项与相关联，它销毁旧的弹出菜单，并释放的内存使用的弹出菜单。  
  
 当*nIDNewItem*指定弹出菜单中，它将成为在插入的菜单的一部分。 如果该菜单将被销毁，插入菜单上也将被破坏。 应从分离插入的菜单`CMenu`对象，以避免冲突。  
  
 每当驻留在的菜单窗口更改时 （无论是否显示在窗口），该应用程序应调用`CWnd::DrawMenuBar`。 若要更改现有的菜单项的属性，是使用更快`CheckMenuItem`和`EnableMenuItem`成员函数。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CMenu::InsertMenu](#insertmenu)。  
  
##  <a name="operator_hmenu"></a>  CMenu::operator HMENU  
 使用此运算符将检索的句柄`CMenu`对象。  
  
```  
operator HMENU() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功的句柄`CMenu`对象; 否则为 NULL。  
  
### <a name="remarks"></a>备注  
 句柄可用于直接调用 Windows Api。  
  
##  <a name="operator_neq"></a>  CMenu::operator ！ =  
 确定两个菜单是否以逻辑方式不相等。  
  
```  
BOOL operator!=(const CMenu& menu) const;  
```  
  
### <a name="parameters"></a>参数  
 *菜单*  
 一个`CMenu`比较的对象。  
  
### <a name="remarks"></a>备注  
 测试在左侧的菜单对象是否不等于右侧的菜单对象。  
  
##  <a name="operator_eq_eq"></a>  CMenu::operator = =  
 确定两个菜单是否从逻辑上相等。  
  
```  
BOOL operator==(const CMenu& menu) const;  
```  
  
### <a name="parameters"></a>参数  
 *菜单*  
 一个`CMenu`比较的对象。  
  
### <a name="remarks"></a>备注  
 测试在左侧菜单对象是否相等 （在方面的 HMENU 值） 右侧的菜单对象。  
  
##  <a name="removemenu"></a>  CMenu::RemoveMenu  
 从菜单中删除具有相关联的弹出菜单的菜单项。  
  
```  
BOOL RemoveMenu(
    UINT nPosition,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>参数  
 *位置*  
 指定要移除的菜单项。 *NFlags*参数可用于解释*位置*以下方面：  
  
|nFlags|位置的解释|  
|------------|---------------------------------|  
|MF_BYCOMMAND|指定参数提供了现有的菜单项的命令 ID。 如果设置 MF_BYCOMMAND 既不 MF_BYPOSITION，这是默认值。|  
|MF_BYPOSITION|指定参数提供了现有的菜单项的位置。 第一项位于位置 0。|  
  
 *nFlags*  
 指定如何*位置*解释。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 它不会销毁一个弹出菜单的句柄，以便可以重用菜单。 之前调用此函数时，应用程序可能调用`GetSubMenu`成员函数以检索弹出窗口中`CMenu`以供重复使用的对象。  
  
 每当驻留在的菜单窗口更改时 （无论是否显示在窗口），该应用程序必须调用`CWnd::DrawMenuBar`。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CMenu::InsertMenu](#insertmenu)。  
  
##  <a name="setdefaultitem"></a>  CMenu::SetDefaultItem  
 设置指定的菜单的默认菜单项。  
  
```  
BOOL SetDefaultItem(
    UINT uItem,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>参数  
 *uItem*  
 标识符或新的默认菜单项或-1 表示没有默认项的位置。 此参数的含义取决于的值*fByPos*。  
  
 *fByPos*  
 值，该值指定的含义*uItem*。 如果此参数为 FALSE 时， *uItem*是菜单项标识符。 否则，它是菜单项位置。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则返回值为非零值。 如果函数失败，则返回值为零。 若要获得扩展错误信息，请使用 Win32 函数[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)，如 Windows SDK 中所述。  
  
### <a name="remarks"></a>备注  
 此成员函数可实现 Win32 函数的行为[SetMenuDefaultItem](/windows/desktop/api/winuser/nf-winuser-setmenudefaultitem)，如 Windows SDK 中所述。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CMenu::InsertMenu](#insertmenu)。  
  
##  <a name="setmenucontexthelpid"></a>  CMenu::SetMenuContextHelpId  
 将与上下文的帮助 ID 相关联`CMenu`。  
  
```  
BOOL SetMenuContextHelpId(DWORD dwContextHelpId);
```  
  
### <a name="parameters"></a>参数  
 *dwContextHelpId*  
 要将与相关联的上下文的帮助 ID `CMenu`。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值否则为，将 0  
  
### <a name="remarks"></a>备注  
 在菜单中的所有项都共享此标识符，不能将附加到单个菜单项的帮助上下文标识符。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CMenu::InsertMenu](#insertmenu)。  
  
##  <a name="setmenuinfo"></a>  CMenu::SetMenuInfo  
 设置菜单的信息。  
  
```  
BOOL SetMenuInfo(LPCMENUINFO lpcmi);
```  
  
### <a name="parameters"></a>参数  
 *lpcmi*  
 一个指向[MENUINFO](/windows/desktop/api/winuser/ns-winuser-tagmenuinfo)结构，它包含菜单上的信息。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，返回值为非零值;否则，返回值为零。  
  
### <a name="remarks"></a>备注  
 调用此函数可设置有关菜单的特定信息。  
  
##  <a name="setmenuitembitmaps"></a>  CMenu::SetMenuItemBitmaps  
 将指定的位图的菜单项与相关联。  
  
```  
BOOL SetMenuItemBitmaps(
    UINT nPosition,  
    UINT nFlags,  
    const CBitmap* pBmpUnchecked,  
    const CBitmap* pBmpChecked);
```  
  
### <a name="parameters"></a>参数  
 *位置*  
 指定要更改的菜单项。 *NFlags*参数可用于解释*位置*以下方面：  
  
|nFlags|位置的解释|  
|------------|---------------------------------|  
|MF_BYCOMMAND|指定参数提供了现有的菜单项的命令 ID。 如果设置 MF_BYCOMMAND 既不 MF_BYPOSITION，这是默认值。|  
|MF_BYPOSITION|指定参数提供了现有的菜单项的位置。 第一项位于位置 0。|  
  
 *nFlags*  
 指定如何*位置*解释。  
  
 *pBmpUnchecked*  
 指定要为未选中的菜单项使用的位图。  
  
 *pBmpChecked*  
 指定要用于选中的菜单项的位图。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 选中或取消选中菜单项是否，Windows 将显示菜单项旁边相应的位图。  
  
 如果任一*pBmpUnchecked*或*pBmpChecked*为 NULL，则 Windows 会显示相应的属性的菜单项旁边的任何内容。 如果这两个参数均为 NULL，Windows 将使用默认复选标记，当项被选中且未选中该项目时删除复选标记。  
  
 当销毁菜单时，这些位图不会被销毁;应用程序必须销毁它们。  
  
 Windows`GetMenuCheckMarkDimensions`函数检索菜单项的默认复选框的维度。 应用程序使用这些值来确定与此函数提供位图的适当大小。 获取的大小，创建位图，然后将其设置。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#32](../../mfc/reference/codesnippet/cpp/cmenu-class_12.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing#33](../../mfc/reference/codesnippet/cpp/cmenu-class_13.cpp)]  
  
##  <a name="setmenuiteminfo"></a>  CMenu::SetMenuItemInfo  
 更改菜单项有关的信息。  
  
```  
BOOL SetMenuItemInfo(
    UINT uItem,  
    LPMENUITEMINFO lpMenuItemInfo,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>参数  
 *uItem*  
 请参阅的说明*uItem*中[SetMenuItemInfo](/windows/desktop/api/winuser/nf-winuser-setmenuiteminfoa) Windows SDK 中。  
  
 *lpMenuItemInfo*  
 请参阅的说明*lpmii*中`SetMenuItemInfo`Windows SDK 中。  
  
 *fByPos*  
 请参阅的说明*fByPosition*中`SetMenuItemInfo`Windows SDK 中。  
  
### <a name="remarks"></a>备注  
 此函数包装[SetMenuItemInfo](/windows/desktop/api/winuser/nf-winuser-setmenuiteminfoa)Windows SDK 中所述。  
  
##  <a name="trackpopupmenu"></a>  CMenu::TrackPopupMenu  
 在指定位置显示一个浮动的弹出菜单，并在弹出菜单上跟踪选定的项。  
  
```  
BOOL TrackPopupMenu(
    UINT nFlags,  
    int x,  
    int y,  
    CWnd* pWnd,  
    LPCRECT lpRect = 0);
```  
  
### <a name="parameters"></a>参数  
 *nFlags*  
 指定屏幕位置和鼠标位置的标志。 请参阅[TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu)有关可用标志的列表。  
  
 *x*  
 指定弹出菜单的屏幕坐标的水平位置。 具体取决于值*nFlags*参数菜单可以为左对齐、 右对齐或居中相对于此位置。  
  
 *y*  
 在屏幕上指定的菜单顶部屏幕坐标的垂直位置。  
  
 *pWnd*  
 标识拥有弹出菜单的窗口。 此参数不能为 NULL，即使指定了 TPM_NONOTIFY 标志。 此窗口菜单中接收所有 WM_COMMAND 消息。 在 Windows 3.1 及更高版本，在窗口不会收到 WM_COMMAND 消息直到`TrackPopupMenu`返回。 在 Windows 3.0 中，窗口收到 WM_COMMAND 消息之前`TrackPopupMenu`返回。  
  
 *lpRect*  
 已忽略。  
  
### <a name="return-value"></a>返回值  
 此方法返回调用的结果[TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu) Windows SDK 中。  
  
### <a name="remarks"></a>备注  
 浮动的弹出菜单可以出现在屏幕上的任何位置。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#34](../../mfc/reference/codesnippet/cpp/cmenu-class_14.cpp)]  
  
##  <a name="trackpopupmenuex"></a>  CMenu::TrackPopupMenuEx  
 在指定位置显示一个浮动的弹出菜单，并在弹出菜单上跟踪选定的项。  
  
```  
BOOL TrackPopupMenuEx(
    UINT fuFlags,  
    int x,  
    int y,  
    CWnd* pWnd,  
    LPTPMPARAMS lptpm);
```  
  
### <a name="parameters"></a>参数  
 *fuFlags*  
 指定有关扩展菜单上的各种函数。 所有值的列表和它们的含义，请参阅[TrackPopupMenuEx](/windows/desktop/api/winuser/nf-winuser-trackpopupmenuex)。  
  
 *x*  
 指定弹出菜单的屏幕坐标的水平位置。  
  
 *y*  
 在屏幕上指定的菜单顶部屏幕坐标的垂直位置。  
  
 *pWnd*  
 指向拥有的弹出菜单和创建菜单上从接收消息的窗口的指针。 此窗口可以是从当前应用程序的任何窗口，但不能为 NULL。 如果指定在 TPM_NONOTIFY *fuFlags*参数，该函数不会发送到任何消息*pWnd*。 该函数必须返回为指向窗口*pWnd*接收 WM_COMMAND 消息。  
  
 *lptpm*  
 指向[TPMPARAMS](/windows/desktop/api/winuser/ns-winuser-tagtpmparams)不应重叠结构，它指定菜单的屏幕区域。 此参数可以为 NULL。  
  
### <a name="return-value"></a>返回值  
 如果指定在 TPM_RETURNCMD *fuFlags*参数，则返回值是用户选择的项的菜单项标识符。 如果用户取消菜单不做任何选择，或如果出错，则返回值为 0。  
  
 如果未指定在 TPM_RETURNCMD *fuFlags*参数，返回值为非零，如果函数成功，0 失败。 若要获得扩展错误信息，请调用[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
### <a name="remarks"></a>备注  
 浮动的弹出菜单可以出现在屏幕上的任何位置。 创建弹出菜单时处理错误的详细信息，请参阅[TrackPopupMenuEx](/windows/desktop/api/winuser/nf-winuser-trackpopupmenuex)。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 CTRLTEST](../../visual-cpp-samples.md)   
 [MFC 示例 DYNAMENU](../../visual-cpp-samples.md)   
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [CObject 类](../../mfc/reference/cobject-class.md)
