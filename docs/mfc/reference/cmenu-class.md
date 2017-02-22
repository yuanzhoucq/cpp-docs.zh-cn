---
title: "CMenu Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMenu"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMenu class"
  - "HMENU"
  - "菜单, 基类"
  - "菜单, class"
  - "菜单, 创建"
  - "菜单, 管理"
ms.assetid: 40cacfdc-d45c-4ec7-bf28-991c72812499
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CMenu Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Windows `HMENU`的封装。  
  
## 语法  
  
```  
class CMenu : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMenu::CMenu](../Topic/CMenu::CMenu.md)|构造 `CMenu` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMenu::AppendMenu](../Topic/CMenu::AppendMenu.md)|追加新项目到此菜单的末尾。|  
|[CMenu::Attach](../Topic/CMenu::Attach.md)|附加Windows菜单句柄 `CMenu` 对象。|  
|[CMenu::CheckMenuItem](../Topic/CMenu::CheckMenuItem.md)|将一个复选标记旁边或在弹出菜单的菜单项移除选中标记。|  
|[CMenu::CheckMenuRadioItem](../Topic/CMenu::CheckMenuRadioItem.md)|在菜单项旁边的组中将一个单选按钮并从任何其他菜单项移除单选按钮。|  
|[CMenu::CreateMenu](../Topic/CMenu::CreateMenu.md)|创建一个空菜单并将它附加到 `CMenu` 对象。|  
|[CMenu::CreatePopupMenu](../Topic/CMenu::CreatePopupMenu.md)|创建空的弹出菜单并将它附加到 `CMenu` 对象。|  
|[CMenu::DeleteMenu](../Topic/CMenu::DeleteMenu.md)|从菜单中删除指定的项目。  如果菜单项都有一个关联的弹出菜单，销毁句柄弹出菜单和释放它所使用的内存。|  
|[CMenu::DeleteTempMap](../Topic/CMenu::DeleteTempMap.md)|删除 `FromHandle` 成员函数创建的所有瞬态 `CMenu` 对象。|  
|[CMenu::DestroyMenu](../Topic/CMenu::DestroyMenu.md)|销毁菜单附加到 `CMenu` 对象并释放菜单占用的所有内存。|  
|[CMenu::Detach](../Topic/CMenu::Detach.md)|分离 `CMenu` 对象的一个Windows菜单句柄并返回处理。|  
|[CMenu::DrawItem](../Topic/CMenu::DrawItem.md)|调用由结构，在一个所有者描述的菜单的可视方面是更改。|  
|[CMenu::EnableMenuItem](../Topic/CMenu::EnableMenuItem.md)|启用，禁用或灰显\(灰色\)菜单项。|  
|[CMenu::FromHandle](../Topic/CMenu::FromHandle.md)|返回指向给定的 `CMenu` 对象Windows菜单句柄。|  
|[CMenu::GetDefaultItem](../Topic/CMenu::GetDefaultItem.md)|确定在指定的菜单的默认菜单项。|  
|[CMenu::GetMenuContextHelpId](../Topic/CMenu::GetMenuContextHelpId.md)|检索帮助上下文ID与菜单。|  
|[CMenu::GetMenuInfo](../Topic/CMenu::GetMenuInfo.md)|检索有关特定菜单的信息。|  
|[CMenu::GetMenuItemCount](../Topic/CMenu::GetMenuItemCount.md)|确定项的数目在弹出或顶层菜单上的。|  
|[CMenu::GetMenuItemID](../Topic/CMenu::GetMenuItemID.md)|获取菜单项的菜单项ID位于所指定的位置。|  
|[CMenu::GetMenuItemInfo](../Topic/CMenu::GetMenuItemInfo.md)|检索有关菜单项的信息。|  
|[CMenu::GetMenuState](../Topic/CMenu::GetMenuState.md)|返回指定的菜单项的状态或项的数目在弹出菜单中的。|  
|[CMenu::GetMenuString](../Topic/CMenu::GetMenuString.md)|检索指定的菜单项的标签。|  
|[CMenu::GetSafeHmenu](../Topic/CMenu::GetSafeHmenu.md)|返回此 `CMenu` 对象包装的 `m_hMenu`。|  
|[CMenu::GetSubMenu](../Topic/CMenu::GetSubMenu.md)|检索指向弹出菜单。|  
|[CMenu::InsertMenu](../Topic/CMenu::InsertMenu.md)|插入新菜单项在指定的位置，移动其他项目级别菜单。|  
|[CMenu::InsertMenuItem](../Topic/CMenu::InsertMenuItem.md)|插入新菜单项在菜单中的指定位置。|  
|[CMenu::LoadMenu](../Topic/CMenu::LoadMenu.md)|从可执行文件加载一个菜单资源并将它附加到 `CMenu` 对象。|  
|[CMenu::LoadMenuIndirect](../Topic/CMenu::LoadMenuIndirect.md)|从菜单模板加载一个菜单在内存并将它附加到 `CMenu` 对象。|  
|[CMenu::MeasureItem](../Topic/CMenu::MeasureItem.md)|调用由框架放置menu维度，在一个所有者描述的菜单创建。|  
|[CMenu::ModifyMenu](../Topic/CMenu::ModifyMenu.md)|更改现有菜单项在指定的位置。|  
|[CMenu::RemoveMenu](../Topic/CMenu::RemoveMenu.md)|从指定的菜单删除与一个关联的弹出菜单的菜单项。|  
|[CMenu::SetDefaultItem](../Topic/CMenu::SetDefaultItem.md)|将指定的菜单的默认菜单项。|  
|[CMenu::SetMenuContextHelpId](../Topic/CMenu::SetMenuContextHelpId.md)|将关联的帮助上下文ID与菜单。|  
|[CMenu::SetMenuInfo](../Topic/CMenu::SetMenuInfo.md)|设置有关特定菜单的信息。|  
|[CMenu::SetMenuItemBitmaps](../Topic/CMenu::SetMenuItemBitmaps.md)|将指定的复选标记位图与菜单项。|  
|[CMenu::SetMenuItemInfo](../Topic/CMenu::SetMenuItemInfo.md)|有关更改菜单项的信息。|  
|[CMenu::TrackPopupMenu](../Topic/CMenu::TrackPopupMenu.md)|在指定的位置显示一个浮动的弹出菜单和跟踪项目的选择在弹出菜单中的。|  
|[CMenu::TrackPopupMenuEx](../Topic/CMenu::TrackPopupMenuEx.md)|在指定的位置显示一个浮动的弹出菜单和跟踪项目的选择在弹出菜单中的。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CMenu::operator HMENU](../Topic/CMenu::operator%20HMENU.md)|检索菜单对象的句柄。|  
|[CMenu::operator \!\=](../Topic/CMenu::operator%20!=.md)|确定两个菜单对象是否不相等。|  
|[CMenu::operator \=\=](../Topic/CMenu::operator%20==.md)|确定两个菜单对象是否相等。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CMenu::m\_hMenu](../Topic/CMenu::m_hMenu.md)|指定句柄Windows菜单附加到 `CMenu` 对象。|  
  
## 备注  
 它用于创建，跟踪，更新和销毁菜单提供成员函数。  
  
 创建在堆栈帧的 `CMenu` 对象作为本地，然后调用 `CMenu`的成员函数操作新菜单根据需要。  接下来，调用 [CWnd::SetMenu](../Topic/CWnd::SetMenu.md) 设置菜单到窗口，后面紧跟对 `CMenu` 对象的 [分离](../Topic/CMenu::Detach.md) 成员函数。  `CWnd::SetMenu` 成员函数上设置windows菜单到新的菜单，使窗口都重绘反映菜单更改，并通过菜单的所有权到窗口。  为 **Detach** 的调用分离 `CMenu` 对象的 `HMENU`，因此，当本地 `CMenu` 变量超出范围时，它将不再拥有的 `CMenu` 对象析构函数不尝试销毁菜单。  菜单，当销毁时，自动销毁窗口。  
  
 您在内存中使用 [LoadMenuIndirect](../Topic/CMenu::LoadMenuIndirect.md) 成员函数从模板创建一个菜单，但是，从资源创建的菜单调用 [LoadMenu](../Topic/CMenu::LoadMenu.md) 更轻松地维护，并且，菜单资源可以在菜单编辑器创建和修改。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMenu`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [MFC示例CTRLTEST](../../top/visual-cpp-samples.md)   
 [MFC示例DYNAMENU](../../top/visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)