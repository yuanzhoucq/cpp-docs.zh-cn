---
title: CContextMenuManager 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CContextMenuManager [MFC], CContextMenuManager
- CContextMenuManager [MFC], AddMenu
- CContextMenuManager [MFC], GetMenuById
- CContextMenuManager [MFC], GetMenuByName
- CContextMenuManager [MFC], GetMenuNames
- CContextMenuManager [MFC], LoadState
- CContextMenuManager [MFC], ResetState
- CContextMenuManager [MFC], SaveState
- CContextMenuManager [MFC], SetDontCloseActiveMenu
- CContextMenuManager [MFC], ShowPopupMenu
- CContextMenuManager [MFC], TrackPopupMenu
ms.assetid: 1de20640-243c-47e1-85de-1baa4153bc83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3a9088ced647dd0e6694181cd7ab7857047c720
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713275"
---
# <a name="ccontextmenumanager-class"></a>CContextMenuManager 类
`CContextMenuManager`对象管理快捷菜单，也称为上下文菜单。  
  
## <a name="syntax"></a>语法  
  
```  
class CContextMenuManager : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CContextMenuManager::CContextMenuManager](#ccontextmenumanager)|构造 `CContextMenuManager` 对象。|  
|`CContextMenuManager::~CContextMenuManager`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CContextMenuManager::AddMenu](#addmenu)|添加一个新的快捷菜单。|  
|[CContextMenuManager::GetMenuById](#getmenubyid)|返回的句柄与提供的资源 id。 关联的菜单|  
|[CContextMenuManager::GetMenuByName](#getmenubyname)|返回的句柄与提供的菜单名称相匹配的菜单。|  
|[CContextMenuManager::GetMenuNames](#getmenunames)|返回菜单名称的列表。|  
|[CContextMenuManager::LoadState](#loadstate)|加载存储在 Windows 注册表中的快捷菜单。|  
|[CContextMenuManager::ResetState](#resetstate)|清除从上下文菜单管理器的快捷菜单。|  
|[CContextMenuManager::SaveState](#savestate)|将快捷方式菜单保存到 Windows 注册表。|  
|[CContextMenuManager::SetDontCloseActiveMenu](#setdontcloseactivemenu)|控件是否`CContextMenuManager`时显示新的快捷菜单关闭的活动的快捷菜单。|  
|[CContextMenuManager::ShowPopupMenu](#showpopupmenu)|显示指定的快捷菜单。|  
|[CContextMenuManager::TrackPopupMenu](#trackpopupmenu)|显示指定的快捷菜单。 返回所选的菜单命令的索引。|  
  
## <a name="remarks"></a>备注  
 `CContextMenuManager` 管理快捷菜单，并确保它们具有一致的外观。  
  
 不应创建`CContextMenuManager`手动对象。 你的应用程序框架创建`CContextMenuManager`对象。 但是，应调用[CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager)初始化你的应用程序时。 初始化上下文管理器之后, 使用的方法[CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager)以获取你的应用程序的上下文管理器的指针。  
  
 您可以通过调用在运行时创建快捷方式菜单`AddMenu`。 如果你想要显示无需第一个接收用户输入菜单上，调用`ShowPopupMenu`。 `TrackPopupMenu` 当你想要创建一个菜单，并等待用户输入时使用。 `TrackPopupMenu` 返回所选的命令或 0 的索引，如果用户未选择任何项目的情况下退出。  
  
 `CContextMenuManager`还可以保存和加载到 Windows 注册表及其状态。  
  
## <a name="example"></a>示例  
 下面的示例演示如何将添加到菜单`CContextMenuManager`对象，以及如何不关闭活动的弹出菜单时`CContextMenuManager`对象显示一个新的弹出菜单。 此代码片段属于[自定义页面示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_CustomPages#4](../../mfc/reference/codesnippet/cpp/ccontextmenumanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CContextMenuManager`  
  
## <a name="requirements"></a>要求  
 **标头：** afxcontextmenumanager.h  
  
##  <a name="addmenu"></a>  CContextMenuManager::AddMenu  
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
*uiMenuNameResId*<br/>
[in]包含为该新菜单的名称的字符串资源 ID。  
  
*uiMenuResId*<br/>
[in]菜单资源 id。  
  
*lpszName*<br/>
[in]一个字符串，包含为该新菜单的名称。  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则非零值如果该方法将失败，则为 0。  
  
### <a name="remarks"></a>备注  
 如果此方法将失败*uiMenuResId*无效或具有相同名称的另一个菜单如果已处于`CContextMenuManager`。  
  
##  <a name="ccontextmenumanager"></a>  CContextMenuManager::CContextMenuManager  
 构造[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)对象。  
  
```  
CContextMenuManager();
```  
  
### <a name="remarks"></a>备注  
 在大多数情况下，不应创建`CContextMenuManager`手动。 你的应用程序框架创建`CContextMenuManager`对象。 应调用[CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager)你的应用程序的初始化过程。 若要获取上下文管理器为一个指针，调用[CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager)。  
  
##  <a name="getmenubyid"></a>  CContextMenuManager::GetMenuById  
 返回的句柄与给定的资源 id。 关联的菜单  
  
```  
HMENU GetMenuById(UINT nMenuResId) const;  
```  
  
### <a name="parameters"></a>参数  
*nMenuResId*<br/>
[in]在菜单资源 ID。  
  
### <a name="return-value"></a>返回值  
 句柄关联的菜单或`NULL`如果找不到菜单。  
  
##  <a name="getmenubyname"></a>  CContextMenuManager::GetMenuByName  
 返回特定菜单的句柄。  
  
```  
HMENU GetMenuByName(
    LPCTSTR lpszName,  
    UINT* puiOrigResID = NULL) const;  
```  
  
### <a name="parameters"></a>参数  
*lpszName*<br/>
[in]一个字符串，包含要检索的菜单的名称。  
  
*puiOrigResID*<br/>
[out]UINT 指向的指针。 此参数包含指定的菜单中，资源 ID，如果找到。  
  
### <a name="return-value"></a>返回值  
 所指定的名称匹配的菜单的句柄*lpszName*。 如果调用没有菜单，则为 NULL *lpszName*。  
  
### <a name="remarks"></a>备注  
 如果此方法找到匹配的菜单*lpszName*，`GetMenuByName`参数中存储的菜单资源 ID *puiOrigResID*。  
  
##  <a name="getmenunames"></a>  CContextMenuManager::GetMenuNames  
 返回的菜单名称添加到列表[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)。  
  
```  
void GetMenuNames(CStringList& listOfNames) const;  
```  
  
### <a name="parameters"></a>参数  
*listOfNames*<br/>
[out]对引用[CStringList](../../mfc/reference/cstringlist-class.md)参数。 此方法将写入到此参数的菜单名称的列表。  
  
##  <a name="loadstate"></a>  CContextMenuManager::LoadState  
 加载与关联的信息[CContextMenuManager 类](../../mfc/reference/ccontextmenumanager-class.md)从 Windows 注册表。  
  
```  
virtual BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>参数  
*lpszProfileName*<br/>
[in]一个字符串，包含注册表项的相对路径。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 *LpszProfileName*参数不是注册表项的绝对路径。 它是被添加到你的应用程序的默认注册表项的结尾相对路径。 若要获取或设置默认注册表项，使用方法[CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase)并[CWinAppEx::SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase)分别。  
  
 使用方法[CContextMenuManager::SaveState](#savestate)将保存到注册表的快捷菜单。  
  
##  <a name="resetstate"></a>  CContextMenuManager::ResetState  
 清除与关联的快捷菜单中的所有项[CContextMenuManager 类](../../mfc/reference/ccontextmenumanager-class.md)。  
  
```  
virtual BOOL ResetState();
```  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则为 TRUE如果发生故障，则为 FALSE。  
  
### <a name="remarks"></a>备注  
 此方法清除弹出菜单，并将其从`CContextMenuManager`。  
  
##  <a name="savestate"></a>  CContextMenuManager::SaveState  
 保存信息与相关联[CContextMenuManager 类](../../mfc/reference/ccontextmenumanager-class.md)到 Windows 注册表。  
  
```  
virtual BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>参数  
*lpszProfileName*<br/>
[in]一个字符串，包含注册表项的相对路径。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 *LpszProfileName*参数不是注册表项的绝对路径。 它是被添加到你的应用程序的默认注册表项的结尾相对路径。 若要获取或设置默认注册表项，使用方法[CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase)并[CWinAppEx::SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase)分别。  
  
 使用方法[CContextMenuManager::LoadState](#loadstate)从注册表加载的快捷菜单。  
  
##  <a name="setdontcloseactivemenu"></a>  CContextMenuManager::SetDontCloseActiveMenu  
 控件是否[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)时它将显示一个新的弹出菜单关闭活动的弹出菜单。  
  
```  
void SetDontCloseActiveMenu (BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>参数  
*bSet*<br/>
[in]一个布尔型参数，用于控制是否要关闭活动的弹出菜单。 值为 TRUE 表示未关闭活动的弹出菜单。 FALSE 表示活动的弹出菜单已关闭。  
  
### <a name="remarks"></a>备注  
 默认情况下，`CContextMenuManager`关闭活动的弹出菜单。  
  
##  <a name="showpopupmenu"></a>  CContextMenuManager::ShowPopupMenu  
 显示指定的快捷菜单。  
  
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
*uiMenuResId*<br/>
[in]此方法将显示的菜单资源 ID。  
  
*x*<br/>
[in]水平工作区坐标中的快捷菜单的偏移量。  
  
*y*<br/>
[in]垂直偏移量的工作区坐标中的快捷菜单  
  
*pWndOwner*<br/>
[in]指向快捷菜单的父窗口的指针。  
  
*bOwnMessage*<br/>
[in]一个布尔参数，指示如何路由消息。 如果*bOwnMessage*是 FALSE，标准 MFC 使用路由。 否则为*pWndOwner*接收的消息。  
  
*hmenuPopup*<br/>
[in]此方法将显示菜单的句柄。  
  
*bAutoDestroy*<br/>
[in]一个布尔参数，指示是否将自动销毁菜单。  
  
*bRightAlign*<br/>
[in]一个布尔参数，指示菜单项的对齐方式。 如果*bRightAlign*为 TRUE 时，菜单是从右到左的阅读顺序为右对齐。  
  
### <a name="return-value"></a>返回值  
 第一个方法重载方法返回非零，如果该方法成功，则显示的菜单否则为 0。 第二个方法重载方法返回一个指向[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)如果快捷方式菜单显示正确; 否则为 NULL。  
  
### <a name="remarks"></a>备注  
 此方法类似于方法[CContextMenuManager::TrackPopupMenu](#trackpopupmenu)在于这两种方法显示快捷菜单。 但是，`TrackPopupMenu`返回所选的菜单命令的索引。  
  
 如果将参数*bAutoDestroy*为 FALSE，则必须手动调用继承`DestroyMenu`方法来释放内存资源。 默认实现`ShowPopupMenu`不使用参数*bAutoDestroy*。 提供以供将来使用或的自定义派生自的类提供`CContextMenuManager`类。  
  
##  <a name="trackpopupmenu"></a>  CContextMenuManager::TrackPopupMenu  
 显示指定的快捷菜单，并返回所选的快捷菜单命令的索引。  
  
```  
virtual UINT TrackPopupMenu(
    HMENU hmenuPopup,  
    int x,  
    int y,  
    CWnd* pWndOwner,  
    BOOL bRightAlign = FALSE);
```  
  
### <a name="parameters"></a>参数  
*hmenuPopup*<br/>
[in]此方法显示的快捷菜单的句柄。  
  
*x*<br/>
[in]水平工作区坐标中的快捷菜单的偏移量。  
  
*y*<br/>
[in]垂直工作区坐标中的快捷菜单的偏移量。  
  
*pWndOwner*<br/>
[in]指向快捷菜单的父窗口的指针。  
  
*bRightAlign*<br/>
[in]一个布尔参数，指示菜单项的对齐方式。 如果*bRightAlign*为 TRUE 时，菜单是从右到左的阅读顺序为右对齐。 如果*bRightAlign*为 FALSE 时，菜单是从左到右读取顺序为左对齐。  
  
### <a name="return-value"></a>返回值  
 用户选择; 命令的菜单命令 ID如果用户关闭而不选择菜单命令的快捷菜单，则为 0。  
  
### <a name="remarks"></a>备注  
 此方法的函数作为模式调用以显示快捷菜单。 应用程序不会继续在代码中的以下行直到用户关闭快捷菜单，或选择命令。 可用于显示快捷菜单的替代方法是[CContextMenuManager::ShowPopupMenu](#showpopupmenu)。 该方法不是模式调用并不会返回所选的命令的 ID。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx 类](../../mfc/reference/cwinappex-class.md)
