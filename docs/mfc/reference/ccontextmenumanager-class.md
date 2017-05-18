---
title: "CContextMenuManager 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager::CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager::AddMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuById
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuByName
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuNames
- AFXCONTEXTMENUMANAGER/CContextMenuManager::LoadState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::ResetState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::SaveState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::SetDontCloseActiveMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::ShowPopupMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::TrackPopupMenu
dev_langs:
- C++
helpviewer_keywords:
- CContextMenuManager class
ms.assetid: 1de20640-243c-47e1-85de-1baa4153bc83
caps.latest.revision: 32
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: fab322d0c60b33454504620170d9c77a98401ec8
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="ccontextmenumanager-class"></a>CContextMenuManager 类
`CContextMenuManager`对象管理快捷菜单，也称为上下文菜单。  
  
## <a name="syntax"></a>语法  
  
```  
class CContextMenuManager : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CContextMenuManager::CContextMenuManager](#ccontextmenumanager)|构造 `CContextMenuManager` 对象。|  
|`CContextMenuManager::~CContextMenuManager`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CContextMenuManager::AddMenu](#addmenu)|添加一个新的快捷菜单。|  
|[CContextMenuManager::GetMenuById](#getmenubyid)|返回的句柄与提供的资源 id。 关联的菜单|  
|[CContextMenuManager::GetMenuByName](#getmenubyname)|返回菜单提供的菜单名称相匹配的句柄。|  
|[CContextMenuManager::GetMenuNames](#getmenunames)|返回菜单名称的列表。|  
|[CContextMenuManager::LoadState](#loadstate)|加载存储在 Windows 注册表中的快捷菜单。|  
|[CContextMenuManager::ResetState](#resetstate)|清除从上下文菜单管理器的快捷菜单。|  
|[CContextMenuManager::SaveState](#savestate)|将快捷菜单保存到 Windows 注册表。|  
|[CContextMenuManager::SetDontCloseActiveMenu](#setdontcloseactivemenu)|控件是否`CContextMenuManager`显示新的快捷菜单时，将关闭的活动的快捷菜单。|  
|[CContextMenuManager::ShowPopupMenu](#showpopupmenu)|显示指定快捷方式菜单。|  
|[CContextMenuManager::TrackPopupMenu](#trackpopupmenu)|显示指定快捷方式菜单。 返回所选的菜单命令的索引。|  
  
## <a name="remarks"></a>备注  
 `CContextMenuManager`管理快捷菜单，并确保它们具有一致的外观。  
  
 不应创建`CContextMenuManager`手动对象。 您的应用程序框架创建`CContextMenuManager`对象。 但是，应调用[CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager)初始化您的应用程序时。 初始化后上下文管理器，使用方法[CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager)以获取指向您的应用程序的上下文管理器。  
  
 您可以通过调用在运行时创建快捷方式菜单`AddMenu`。 如果您想要显示无需第一个接收用户输入菜单上，调用`ShowPopupMenu`。 `TrackPopupMenu`你想要创建一个菜单，然后等待用户输入时使用。 `TrackPopupMenu`返回所选的命令或 0 的索引，如果用户未选择任何项目的情况下退出。  
  
 `CContextMenuManager`还可以保存并加载其状态为 Windows 注册表。  
  
## <a name="example"></a>示例  
 下面的示例演示如何添加到菜单`CContextMenuManager`对象以及如何在不关闭活动的弹出菜单时`CContextMenuManager`对象显示一个新的弹出菜单。 此代码段属于[的自定义页示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_CustomPages #&4;](../../mfc/reference/codesnippet/cpp/ccontextmenumanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CContextMenuManager`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxcontextmenumanager.h  
  
##  <a name="addmenu"></a>CContextMenuManager::AddMenu  
 添加到一个新快捷方式菜单[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)。  
  
```  
BOOL AddMenu(
    UINT uiMenuNameResId,  
    UINT uiMenuResId);

 
BOOL AddMenu(
    LPCTSTR lpszName,  
    UINT uiMenuResId);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiMenuNameResId`  
 包含新建菜单的名称的字符串资源 ID。  
  
 [in] `uiMenuResId`  
 菜单上的资源 id。  
  
 [in] `lpszName`  
 一个字符串，包含新建菜单的名称。  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则非零值如果该方法将失败，则为 0。  
  
### <a name="remarks"></a>备注  
 如果此方法将失败`uiMenuResId`无效或为具有相同名称的另一个菜单如果已处于`CContextMenuManager`。  
  
##  <a name="ccontextmenumanager"></a>CContextMenuManager::CContextMenuManager  
 构造[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)对象。  
  
```  
CContextMenuManager();
```  
  
### <a name="remarks"></a>备注  
 在大多数情况下，不应创建`CContextMenuManager`手动。 您的应用程序框架创建`CContextMenuManager`对象。 应调用[CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager)在您的应用程序的初始化过程。 若要获取指向上下文管理器的指针，调用[CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager)。  
  
##  <a name="getmenubyid"></a>CContextMenuManager::GetMenuById  
 返回与给定的资源 id。 关联的菜单的句柄  
  
```  
HMENU GetMenuById(UINT nMenuResId) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `nMenuResId`  
 菜单上的资源 ID。  
  
### <a name="return-value"></a>返回值  
 关联菜单上的句柄或`NULL`如果找不到菜单。  
  
##  <a name="getmenubyname"></a>CContextMenuManager::GetMenuByName  
 返回特定菜单上的句柄。  
  
```  
HMENU GetMenuByName(
    LPCTSTR lpszName,  
    UINT* puiOrigResID = NULL) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszName`  
 一个字符串，包含要检索的菜单的名称。  
  
 [out] `puiOrigResID`  
 一个指向 `UINT` 的指针。 此参数包含指定的菜单中，资源 ID，如果找到。  
  
### <a name="return-value"></a>返回值  
 菜单上的名称相匹配所指定的句柄`lpszName`。 `NULL`如果没有调用没有菜单`lpszName`。  
  
### <a name="remarks"></a>备注  
 如果此方法找到匹配的菜单`lpszName`，`GetMenuByName`参数中存储的菜单资源 ID `puiOrigResID`。  
  
##  <a name="getmenunames"></a>CContextMenuManager::GetMenuNames  
 返回的菜单名添加到列表[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)。  
  
```  
void GetMenuNames(CStringList& listOfNames) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `listOfNames`  
 对引用[CStringList](../../mfc/reference/cstringlist-class.md)参数。 此方法将写入此参数的菜单名的列表。  
  
##  <a name="loadstate"></a>CContextMenuManager::LoadState  
 加载与关联的信息[CContextMenuManager 类](../../mfc/reference/ccontextmenumanager-class.md)从 Windows 注册表。  
  
```  
virtual BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszProfileName`  
 一个字符串，包含注册表项的相对路径。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 `lpszProfileName`参数不是注册表项的绝对路径。 它是相对路径添加到您的应用程序的默认注册表项的末尾。 若要获取或设置默认的注册表项，使用方法[CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase)和[CWinAppEx::SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase)分别。  
  
 使用方法[CContextMenuManager::SaveState](#savestate)将保存到注册表的快捷菜单。  
  
##  <a name="resetstate"></a>CContextMenuManager::ResetState  
 清除与关联的快捷菜单中的所有项[CContextMenuManager 类](../../mfc/reference/ccontextmenumanager-class.md)。  
  
```  
virtual BOOL ResetState();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则此方法`FALSE`如果发生故障。  
  
### <a name="remarks"></a>备注  
 此方法清除弹出菜单，并将其从`CContextMenuManager`。  
  
##  <a name="savestate"></a>CContextMenuManager::SaveState  
 将保存与关联的信息[CContextMenuManager 类](../../mfc/reference/ccontextmenumanager-class.md)对 Windows 注册表。  
  
```  
virtual BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszProfileName`  
 一个字符串，包含注册表项的相对路径。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 `lpszProfileName`参数不是注册表项的绝对路径。 它是相对路径添加到您的应用程序的默认注册表项的末尾。 若要获取或设置默认的注册表项，使用方法[CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase)和[CWinAppEx::SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase)分别。  
  
 使用方法[CContextMenuManager::LoadState](#loadstate)来从注册表加载的快捷菜单。  
  
##  <a name="setdontcloseactivemenu"></a>CContextMenuManager::SetDontCloseActiveMenu  
 控件是否[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)时它会显示一个新的弹出菜单，将关闭活动的弹出菜单。  
  
```  
void SetDontCloseActiveMenu (BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bSet`  
 一个布尔型参数，用于控制是否关闭的活动的弹出菜单。 值为`TRUE`指示未关闭的活动的弹出菜单。 `FALSE`指示活动的弹出菜单已关闭。  
  
### <a name="remarks"></a>备注  
 默认情况下，`CContextMenuManager`关闭活动的弹出菜单。  
  
##  <a name="showpopupmenu"></a>CContextMenuManager::ShowPopupMenu  
 显示指定快捷方式菜单。  
  
```  
virtual BOOL ShowPopupMenu(
    UINT uiMenuResId,  
    int x,  
    int y,  
    CWnd* pWndOwner,  
    BOOL bOwnMessage = FALSE,  
    BOOL bRightAlign = FALSE);

 
virtual CMFCPopupMenu* ShowPopupMenu(
    HMENU hmenuPopup,  
    int x,  
    int y,  
    CWnd* pWndOwner,  
    BOOL bOwnMessage = FALSE,  
    BOOL bAutoDestroy = TRUE,  
    BOOL bRightAlign = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiMenuResId`  
 此方法将显示的菜单资源 ID。  
  
 [in] `x`  
 水平工作区坐标中的快捷菜单的偏移量。  
  
 [in] `y`  
 垂直偏移量在客户端坐标中的快捷菜单  
  
 [in] `pWndOwner`  
 指向快捷菜单的父窗口的指针。  
  
 [in] `bOwnMessage`  
 一个布尔型参数，该值指示如何路由消息。 如果`bOwnMessage`是`FALSE`，使用标准 MFC 路由。 否则为`pWndOwner`接收的消息。  
  
 [in] `hmenuPopup`  
 此方法将显示的菜单句柄。  
  
 [in] `bAutoDestroy`  
 一个布尔型参数，该值指示是否将自动销毁菜单。  
  
 [in] `bRightAlign`  
 一个布尔型参数，该值指示菜单项的对齐方式。 如果`bRightAlign`是`TRUE`，菜单是右对齐的右到左阅读顺序。  
  
### <a name="return-value"></a>返回值  
 第一个方法重载返回非零，如果该方法成功，则显示的菜单否则为 0。 第二个方法重载方法返回一个指向[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)快捷菜单会显示正确; 否则为如果`NULL`。  
  
### <a name="remarks"></a>备注  
 此方法类似于方法[CContextMenuManager::TrackPopupMenu](#trackpopupmenu)在于这两种方法显示的快捷菜单。 但是，`TrackPopupMenu`返回选定的菜单命令的索引。  
  
 如果该参数`bAutoDestroy`是`FALSE`，您必须手动调用继承`DestroyMenu`方法来释放内存资源。 默认实现`ShowPopupMenu`不使用参数`bAutoDestroy`。 它旨在供将来使用或自定义派生的类从`CContextMenuManager`类。  
  
##  <a name="trackpopupmenu"></a>CContextMenuManager::TrackPopupMenu  
 显示指定的快捷菜单并返回所选的快捷菜单命令的索引。  
  
```  
virtual UINT TrackPopupMenu(
    HMENU hmenuPopup,  
    int x,  
    int y,  
    CWnd* pWndOwner,  
    BOOL bRightAlign = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `hmenuPopup`  
 此方法显示的快捷菜单句柄。  
  
 [in] `x`  
 水平工作区坐标中的快捷菜单的偏移量。  
  
 [in] `y`  
 垂直工作区坐标中的快捷菜单的偏移量。  
  
 [in] `pWndOwner`  
 指向快捷菜单的父窗口的指针。  
  
 [in] `bRightAlign`  
 一个布尔型参数，该值指示菜单项的对齐方式。 如果`bRightAlign`是`TRUE`，菜单是右对齐的右到左阅读顺序。 如果`bRightAlign`是`FALSE`，菜单是从左到右读取顺序为左对齐。  
  
### <a name="return-value"></a>返回值  
 用户选择; 命令的菜单命令 ID如果用户关闭而不选择菜单命令的快捷菜单，则为 0。  
  
### <a name="remarks"></a>备注  
 此方法可用作执行模式的调用，以显示快捷菜单。 直到用户关闭快捷菜单或选择一个命令时，应用程序不会继续到下一行代码中。 可用于显示快捷菜单上的替代方法是[CContextMenuManager::ShowPopupMenu](#showpopupmenu)。 该方法不是模式调用，并将不会返回所选的命令的 ID。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx 类](../../mfc/reference/cwinappex-class.md)

