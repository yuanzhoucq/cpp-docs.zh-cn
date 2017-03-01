---
title: "CWinAppEx 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinAppEx
dev_langs:
- C++
helpviewer_keywords:
- CWinAppEx class
ms.assetid: a3d3e053-3e22-463f-9444-c73abb1bb9d7
caps.latest.revision: 37
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
ms.openlocfilehash: 6931f1e794116882722e402c9cb95acec1ebdfd5
ms.lasthandoff: 02/24/2017

---
# <a name="cwinappex-class"></a>CWinAppEx 类
`CWinAppEx`处理应用程序状态、 将状态保存到注册表、 从注册表加载此状态，初始化应用程序管理器，并提供到同样的应用程序管理器链接。  
  
## <a name="syntax"></a>语法  
  
```  
class CWinAppEx : public CWinApp  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CWinAppEx::CWinAppEx](#cwinappex)|构造 `CWinAppEx` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CWinAppEx::CleanState](#cleanstate)|从 Windows 注册表中删除有关该应用程序的信息。|  
|[CWinAppEx::EnableLoadWindowPlacement](#enableloadwindowplacement)|指定是否应用程序将初始大小和主框架窗口的位置从注册表加载。|  
|[CWinAppEx::EnableTearOffMenus](#enabletearoffmenus)|启用可拖曳菜单，应用程序。|  
|[CWinAppEx::EnableUserTools](#enableusertools)|使用户能够在应用程序中创建的自定义菜单命令。|  
|[CWinAppEx::ExitInstance](#exitinstance)|在由框架调用`Run`成员函数以退出应用程序的此实例。 (重写[CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)。)|  
|[CWinAppEx::GetBinary](#getbinary)|读取指定的注册表值关联的二进制数据。|  
|[CWinAppEx::GetContextMenuManager](#getcontextmenumanager)|将指针返回到全局[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)对象。|  
|[CWinAppEx::GetDataVersion](#getdataversion)||  
|[CWinAppEx::GetDataVersionMajor](#getdataversionmajor)|返回保存在 Windows 注册表中的应用程序的主版本。|  
|[CWinAppEx::GetDataVersionMinor](#getdataversionminor)|返回保存在 Windows 注册表中的应用程序的次要版本。|  
|[CWinAppEx::GetInt](#getint)|读取注册表中指定的值与关联的数值数据。|  
|[CWinAppEx::GetKeyboardManager](#getkeyboardmanager)|将指针返回到全局[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)对象。|  
|[CWinAppEx::GetMouseManager](#getmousemanager)|将指针返回到全局[CMouseManager](../../mfc/reference/cmousemanager-class.md)对象。|  
|[CWinAppEx::GetObject](#getobject)|读取`CObject`-派生与注册表中指定的值相关联的数据。|  
|[CWinAppEx::GetRegSectionPath](#getregsectionpath)|返回一个字符串，该注册表项的路径。 此路径连接的应用程序路径提供的相对路径。|  
|[CWinAppEx::GetRegistryBase](#getregistrybase)|返回应用程序的注册表路径。|  
|[CWinAppEx::GetSectionBinary](#getsectionbinary)|读取具有指定的键和从注册表值相关联的二进制数据。|  
|[CWinAppEx::GetSectionInt](#getsectionint)|从与指定的键和值关联的注册表中读取数字数据。|  
|[CWinAppEx::GetSectionObject](#getsectionobject)|读取`CObject`与指定的键和从注册表值相关联的数据。|  
|[CWinAppEx::GetSectionString](#getsectionstring)|读取具有指定的键和从注册表值相关联的字符串数据。|  
|[CWinAppEx::GetShellManager](#getshellmanager)|将指针返回到全局[CShellManager](../../mfc/reference/cshellmanager-class.md)对象。|  
|[CWinAppEx::GetString](#getstring)|读取注册表中指定的值与关联的字符串数据。|  
|[CWinAppEx::GetTooltipManager](#gettooltipmanager)|将指针返回到全局[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)对象。|  
|[CWinAppEx::GetUserToolsManager](#getusertoolsmanager)|将指针返回到全局[CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)对象。|  
|[CWinAppEx::InitContextMenuManager](#initcontextmenumanager)|初始化`CContextMenuManager`对象。|  
|[CWinAppEx::InitKeyboardManager](#initkeyboardmanager)|初始化`CKeyboardManager`对象。|  
|[CWinAppEx::InitMouseManager](#initmousemanager)|初始化`CMouseManager`对象。|  
|[CWinAppEx::InitShellManager](#initshellmanager)|初始化`CShellManager`类|  
|[CWinAppEx::InitTooltipManager](#inittooltipmanager)|初始化`CTooltipManager`类。|  
|[CWinAppEx::IsResourceSmartUpdate](#isresourcesmartupdate)||  
|[CWinAppEx::IsStateExists](#isstateexists)|指示指定的键是否是在注册表中。|  
|[CWinAppEx::LoadState](#loadstate)|从注册表加载的应用程序状态。|  
|[CWinAppEx::OnAppContextHelp](#onappcontexthelp)|由框架调用，当用户请求的上下文帮助**自定义**对话框。|  
|[CWinAppEx::OnViewDoubleClick](#onviewdoubleclick)|当用户双击应用程序中的任意位置，请调用用户定义的命令。|  
|[CWinAppEx::OnWorkspaceIdle](#onworkspaceidle)||  
|[CWinAppEx::SaveState](#savestate)|将应用程序框架的状态写入 Windows 注册表。|  
|[CWinAppEx::SetRegistryBase](#setregistrybase)|设置默认的注册表项的路径。 此项将作为后续注册表的所有调用的根。|  
|[CWinAppEx::ShowPopupMenu](#showpopupmenu)|显示弹出菜单。|  
|[CWinAppEx::WriteBinary](#writebinary)|将二进制数据写入指定的注册表值。|  
|[CWinAppEx::WriteInt](#writeint)|将数字数据写入指定的注册表值。|  
|[CWinAppEx::WriteObject](#writeobject)|将派生自的数据写入[CObject 类](../../mfc/reference/cobject-class.md)为指定的注册表值。|  
|[CWinAppEx::WriteSectionBinary](#writesectionbinary)|将二进制数据写入指定的注册表项值。|  
|[CWinAppEx::WriteSectionInt](#writesectionint)|将数字数据写入指定的注册表项值。|  
|[CWinAppEx::WriteSectionObject](#writesectionobject)|写入数据派生自`CObject`类传递给一个的值指定的注册表项。|  
|[CWinAppEx::WriteSectionString](#writesectionstring)|将字符串数据写入指定的注册表项值。|  
|[CWinAppEx::WriteString](#writestring)|将字符串数据写入指定的注册表值。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CWinAppEx::LoadCustomState](#loadcustomstate)|已加载的应用程序状态时，由框架调用。|  
|[CWinAppEx::LoadWindowPlacement](#loadwindowplacement)|从注册表加载的大小和位置的应用程序时由框架调用。 加载的数据包括在您的应用程序上次关闭的时的大小和位置的主框架。|  
|[CWinAppEx::OnClosingMainFrame](#onclosingmainframe)|当主框架窗口正在处理时由框架调用`WM_CLOSE`。|  
|[CWinAppEx::PreLoadState](#preloadstate)|由框架调用之前加载的应用程序状态。|  
|[CWinAppEx::PreSaveState](#presavestate)|由框架调用之前立即保存应用程序状态。|  
|[CWinAppEx::ReloadWindowPlacement](#reloadwindowplacement)|重新加载的大小和位置的注册表中提供的窗口|  
|[CWinAppEx::SaveCustomState](#savecustomstate)|由框架调用之后它将写入注册表的应用程序状态。|  
|[CWinAppEx::StoreWindowPlacement](#storewindowplacement)|由框架来写入注册表的大小和位置的主框架调用。|  
  
### <a name="data-members"></a>数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CWinAppEx::m_bForceImageReset](#m_bforceimagereset)|指定是否该框架将重置工具栏上的所有图像包含的工具栏的框架窗口加载时。|  
  
## <a name="remarks"></a>备注  
 很多 MFC 框架中提供的功能取决于`CWinAppEx`类。 您可以将合并`CWinAppEx`合并到应用程序在两种方式之一中的类︰  
  
-   构造`CWinAppEx`主线程中的类。  
  
-   派生的主应用程序类别`CWinAppEx`。  
  
 您将合并后`CWinAppEx`合并到应用程序，可以将其初始化任一应用程序管理器。 使用应用程序管理器之前，必须通过调用适当的 initialize 方法对其进行初始化。 若要获取特定的管理器的指针，调用相关联的 get 方法。 `CWinAppEx`类管理以下应用程序管理器︰ [CMouseManager 类](../../mfc/reference/cmousemanager-class.md)， [CContextMenuManager 类](../../mfc/reference/ccontextmenumanager-class.md)， [CKeyboardManager 类](../../mfc/reference/ckeyboardmanager-class.md)， [CUserToolsManager 类](../../mfc/reference/cusertoolsmanager-class.md)，和[CMenuTearOffManager 类](../../mfc/reference/cmenutearoffmanager-class.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWinThread](../../mfc/reference/cwinthread-class.md)  
  
 [CWinApp](../../mfc/reference/cwinapp-class.md)  
  
 [CWinAppEx](../../mfc/reference/cwinappex-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxwinappex.h  
  
##  <a name="a-namecleanstatea--cwinappexcleanstate"></a><a name="cleanstate"></a>CWinAppEx::CleanState  
 从 Windows 注册表中删除有关该应用程序的所有信息。  
  
```  
virtual BOOL CleanState(LPCTSTR lpszSectionName=NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszSectionName`  
 一个字符串，包含该注册表项的路径。  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法会清除注册表的特定节中的应用程序数据。 您可以指定部分以通过使用参数清除`lpszSectionName`。 如果`lpszSectionName`是`NULL`，此方法将使用默认的注册表路径存储在`CWinAppEx`对象。 若要获取默认注册表路径，请使用[CWinAppEx::GetRegistryBase](#getregistrybase)。  
  
##  <a name="a-namecwinappexa--cwinappexcwinappex"></a><a name="cwinappex"></a>CWinAppEx::CWinAppEx  
 构造 `CWinAppEx` 对象。  
  
```  
CWinAppEx(BOOL bResourceSmartUpdate = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bResourceSmartUpdate`  
 一个布尔型参数，指定是否应检测并处理资源更新工作区对象。  
  
### <a name="remarks"></a>备注  
 `CWinAppEx`类具有初始化的方法，提供功能的保存和加载应用程序信息写入注册表，并控制全局应用程序设置。 它还使您能够使用全局经理如[CKeyboardManager 类](../../mfc/reference/ckeyboardmanager-class.md)和[CUserToolsManager 类](../../mfc/reference/cusertoolsmanager-class.md)。 每个应用程序可以只有一个实例`CWinAppEx`类。  
  
##  <a name="a-nameenableloadwindowplacementa--cwinappexenableloadwindowplacement"></a><a name="enableloadwindowplacement"></a>CWinAppEx::EnableLoadWindowPlacement  
 指定是否应用程序将初始大小和主框架窗口的位置从注册表加载。  
  
```  
void EnableLoadWindowPlacement(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 指定应用程序从注册表中是否加载的初始大小和位置的主框架窗口。  
  
### <a name="remarks"></a>备注  
 默认情况下，大小和位置的主框架是从注册表中加载以及其他应用程序设置。 时会出现此情况[CWinAppEx::LoadState](#loadstate)。 如果您不想要从注册表加载的窗口中初始位置，调用此方法与`bEnable`设置为`false`。  
  
##  <a name="a-nameenabletearoffmenusa--cwinappexenabletearoffmenus"></a><a name="enabletearoffmenus"></a>CWinAppEx::EnableTearOffMenus  
 创建并初始化[CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md)对象。  
  
```  
BOOL EnableTearOffMenus(
    LPCTSTR lpszRegEntry,  
    const UINT uiCmdFirst,  
    const UINT uiCmdLast);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszRegEntry`  
 一个字符串，包含路径的注册表项。 应用程序使用此注册表项来存储信息拖曳菜单。  
  
 [in] `uiCmdFirst`  
 关闭菜单第一个 tear id。  
  
 [in] `uiCmdLast`  
 最后一个菜单关闭 tear id。  
  
### <a name="return-value"></a>返回值  
 `True`如果`CMenuTearOffManager`将创建并初始化成功，则`false`如果出错或者`CMenuTearOffManager`已存在。  
  
### <a name="remarks"></a>备注  
 使用此函数以启用应用程序中的可拖曳菜单。 应调用该函数从`InitInstance`。  
  
##  <a name="a-nameenableusertoolsa--cwinappexenableusertools"></a><a name="enableusertools"></a>CWinAppEx::EnableUserTools  
 使用户能够创建自定义菜单命令，从而减少应用程序中的击键。 此方法创建[CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)对象。  
  
```  
BOOL EnableUserTools(
    const UINT uiCmdToolsDummy,  
    const UINT uiCmdFirst,  
    const UINT uiCmdLast,  
    CRuntimeClass* pToolRTC = RUNTIME_CLASS(CUserTool),  
    UINT uArgMenuID = 0,  
    UINT uInitDirMenuID = 0);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmdToolsDummy`  
 无符号的整数，该框架作为占位符用于用户的工具菜单的命令 ID。  
  
 [in] `uiCmdFirst`  
 第一个用户工具命令的命令 ID。  
  
 [in] `uiCmdLast`  
 最后一个用户工具命令的命令 ID。  
  
 [in] `pToolRTC`  
 一个类，该类`CUserToolsManager`对象用于创建新的用户工具。  
  
 [in] `uArgMenuID`  
 参数菜单 id。  
  
 [in] `uInitDirMenuID`  
 初始工具目录菜单 ID。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此方法创建并初始化`CUserToolsManager`对象;`FALSE`如果方法失败或者`CUserToolsManager`对象已存在。  
  
### <a name="remarks"></a>备注  
 启用用户定义的工具时，该框架将自动支持动态菜单，可以自定义期间进行扩展。 框架将每个新项与外部命令相关联。 当用户选择从合适的项目时，框架将调用这些命令**工具**菜单。  
  
 每次用户添加新项时，框架将创建一个新的对象。 新的对象的类类型定义通过`pToolRTC`。 `pToolRTC`类类型必须派生自[CUserTool 类](../../mfc/reference/cusertool-class.md)。  
  
 有关用户工具以及如何将它们合并到您的应用程序的详细信息，请参阅[用户定义的工具](../../mfc/user-defined-tools.md)。  
  
##  <a name="a-nameexitinstancea--cwinappexexitinstance"></a><a name="exitinstance"></a>CWinAppEx::ExitInstance  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int ExitInstance();
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetbinarya--cwinappexgetbinary"></a><a name="getbinary"></a>CWinAppEx::GetBinary  
 从指定的注册表项中读取二进制数据。  
  
```  
BOOL GetBinary(
    LPCTSTR lpszEntry,  
    LPBYTE* ppData,  
    UINT* pBytes);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszEntry`  
 一个字符串，包含注册表项的名称。  
  
 [out] `ppData`  
 指向方法填充的二进制数据的缓冲区的指针。  
  
 [out] `pBytes`  
 指向一个无符号整数，该方法用来编写读取的字节数的指针。  
  
### <a name="return-value"></a>返回值  
 `True`如果成功，则，`false`否则为。  
  
### <a name="remarks"></a>备注  
 此方法读取写入到注册表的二进制数据。 若要对注册表中写入数据，请使用方法[CWinAppEx::WriteBinary](#writebinary)和[CWinAppEx::WriteSectionBinary](#writesectionbinary)。  
  
 `lpszEntry`参数是位于您的应用程序默认注册表项下的注册表项的名称。 若要获取或设置默认的注册表项，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分别。  
  
##  <a name="a-namegetcontextmenumanagera--cwinappexgetcontextmenumanager"></a><a name="getcontextmenumanager"></a>CWinAppEx::GetContextMenuManager  
 将指针返回到全局[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)对象。  
  
```  
CContextMenuManager* GetContextMenuManager();
```  
  
### <a name="return-value"></a>返回值  
 指向全局`CContextMenuManager`对象。  
  
### <a name="remarks"></a>备注  
 如果未初始化 CContextMenuManager 对象，此函数将调用[CWinAppEx::InitContextMenuManager](#initcontextmenumanager)返回的指针之前。  
  
##  <a name="a-namegetdataversiona--cwinappexgetdataversion"></a><a name="getdataversion"></a>CWinAppEx::GetDataVersion  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetDataVersion() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetdataversionmajora--cwinappexgetdataversionmajor"></a><a name="getdataversionmajor"></a>CWinAppEx::GetDataVersionMajor  
 返回将保存在 Windows 注册表中，当您调用的应用程序的主版本[CWinAppEx::SaveState](#savestate)。  
  
```  
int GetDataVersionMajor() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个包含主版本号的整数值。  
  
##  <a name="a-namegetdataversionminora--cwinappexgetdataversionminor"></a><a name="getdataversionminor"></a>CWinAppEx::GetDataVersionMinor  
 返回的应用程序将保存在 Windows 注册表中，当您调用的次版本[CWinAppEx::SaveState](#savestate)。  
  
```  
int GetDataVersionMinor() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个包含的次版本号的整数值。  
  
##  <a name="a-namegetinta--cwinappexgetint"></a><a name="getint"></a>CWinAppEx::GetInt  
 从指定的注册表项中读取的整数数据。  
  
```  
int GetInt(
    LPCTSTR lpszEntry,  
    int nDefault = 0);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszEntry`  
 一个字符串，包含注册表项的名称。  
  
 [in] `nDefault`  
 该方法将返回指定的注册表项不存在默认值。  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则注册表数据否则为`nDefault`。  
  
### <a name="remarks"></a>备注  
 此方法从注册表中读取的整数数据。 如果没有与所指示的注册表项相关联的整数数据`lpszEntry`，此方法返回`nDefault`。 若要对注册表中写入数据，请使用方法[CWinAppEx::WriteSectionInt](#writesectionint)和[CWinAppEx::WriteInt](#writeint)。  
  
 `lpszEntry`参数是位于您的应用程序默认注册表项下的注册表项的名称。 若要获取或设置默认的注册表项，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分别。  
  
##  <a name="a-namegetkeyboardmanagera--cwinappexgetkeyboardmanager"></a><a name="getkeyboardmanager"></a>CWinAppEx::GetKeyboardManager  
 将指针返回到全局[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)对象。  
  
```  
CKeyboardManager* GetKeyboardManager();
```  
  
### <a name="return-value"></a>返回值  
 指向全局`CKeyboardManager`对象。  
  
### <a name="remarks"></a>备注  
 如果未初始化键盘管理器，此函数将调用[CWinAppEx::InitKeyboardManager](#initkeyboardmanager)返回的指针之前。  
  
##  <a name="a-namegetmousemanagera--cwinappexgetmousemanager"></a><a name="getmousemanager"></a>CWinAppEx::GetMouseManager  
 将指针返回到全局[CMouseManager](../../mfc/reference/cmousemanager-class.md)对象。  
  
```  
CMouseManager* GetMouseManager();
```  
  
### <a name="return-value"></a>返回值  
 指向全局`CMouseManager`对象。  
  
### <a name="remarks"></a>备注  
 如果未初始化鼠标管理器，此函数将调用[CWinAppEx::InitMouseManager](#initmousemanager)返回的指针之前。  
  
##  <a name="a-namegetobjecta--cwinappexgetobject"></a><a name="getobject"></a>CWinAppEx::GetObject  
 读取[CObject](../../mfc/reference/cobject-class.md)-dervied 注册表中的数据。  
  
```  
BOOL GetObject(
    LPCTSTR lpszEntry,  
    CObject& obj);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszEntry`  
 一个字符串，包含注册表项的相对路径。  
  
 [out] `obj`  
 对引用`CObject`。 该方法使用此引用存储注册表数据。  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法从派生自的注册表中读取数据`CObject`。 若要编写`CObject`数据到注册表中，使用两种[CWinAppEx::WriteObject](#writeobject)或[CWinAppEx::WriteSectionObject](#writesectionobject)。  
  
 `lpszEntry`参数是一个位于您的应用程序在默认注册表项下的注册表项的名称。 若要获取或设置默认的注册表项，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分别。  
  
##  <a name="a-namegetregistrybasea--cwinappexgetregistrybase"></a><a name="getregistrybase"></a>CWinAppEx::GetRegistryBase  
 检索应用程序的默认注册表路径。  
  
```  
LPCTSTR GetRegistryBase();
```  
  
### <a name="return-value"></a>返回值  
 一个字符串，其中包含默认注册表位置的路径。  
  
### <a name="remarks"></a>备注  
 所有方法[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)访问到默认位置中的注册表开头。 使用此方法可检索默认注册表位置的路径。 使用[CWinAppEx::SetRegistryBase](#setregistrybase)要更改默认注册表位置。  
  
##  <a name="a-namegetregsectionpatha--cwinappexgetregsectionpath"></a><a name="getregsectionpath"></a>CWinAppEx::GetRegSectionPath  
 创建并返回注册表项的绝对路径。  
  
```  
CString GetRegSectionPath(LPCTSTR szSectionAdd = _T(""));
```  
  
### <a name="parameters"></a>参数  
 [in] `szSectionAdd`  
 一个字符串，包含注册表项的相对路径。  
  
### <a name="return-value"></a>返回值  
 一个`CString`，其中包含的注册表项的绝对路径。  
  
### <a name="remarks"></a>备注  
 此方法通过追加中的相对路径定义该注册表项的绝对路径`szSectionAdd`到您的应用程序的默认注册表位置。 若要获取默认的注册表项，请使用[CWinAppEx::GetRegistryBase](#getregistrybase)。  
  
##  <a name="a-namegetsectionbinarya--cwinappexgetsectionbinary"></a><a name="getsectionbinary"></a>CWinAppEx::GetSectionBinary  
 从注册表中读取二进制数据。  
  
```  
BOOL GetSectionBinary(
    LPCTSTR lpszSubSection,  
    LPCTSTR lpszEntry,  
    LPBYTE* ppData,  
    UINT* pBytes);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszSubSection`  
 一个字符串，包含注册表项的相对路径。  
  
 [in] `lpszEntry`  
 一个字符串，包含要读取的值。  
  
 [out] `ppData`  
 指向该方法存储数据的位置的缓冲区的指针。  
  
 [out] `pBytes`  
 指向一个无符号整数的指针。 该方法将写入的大小`ppData`给此参数。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 `True`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法将写入到注册表使用方法的二进制数据读入[CWinAppEx::WriteBinary](#writebinary)和[CWinAppEx::WriteSectionBinary](#writesectionbinary)。  
  
 `lpszSubSection`参数不是注册表项的绝对路径。 它是附加到您的应用程序的默认注册表项末尾的相对路径。 若要获取或设置默认的注册表项，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分别。  
  
##  <a name="a-namegetsectioninta--cwinappexgetsectionint"></a><a name="getsectionint"></a>CWinAppEx::GetSectionInt  
 从注册表中读取的整数数据。  
  
```  
int GetSectionInt(
    LPCTSTR lpszSubSection,  
    LPCTSTR lpszEntry,  
    int nDefault = 0);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszSubSection`  
 一个字符串，包含注册表项的相对路径。  
  
 [in] `lpszEntry`  
 一个字符串，包含要读取的值。  
  
 [in] `nDefault`  
 要返回指定的值不存在的默认值。  
  
### <a name="return-value"></a>返回值  
 存储在指定的注册表值; 整数数据`nDefault`如果数据不存在。  
  
### <a name="remarks"></a>备注  
 使用方法[CWinAppEx::WriteInt](#writeint)和[CWinAppEx::WriteSectionInt](#writesectionint)整数数据写入注册表。  
  
 `lpszSubSection`参数不是注册表项的绝对路径。 它是相对路径添加到您的应用程序的默认注册表项的末尾。 若要获取或设置默认的注册表项，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分别。  
  
##  <a name="a-namegetsectionobjecta--cwinappexgetsectionobject"></a><a name="getsectionobject"></a>CWinAppEx::GetSectionObject  
 读取[CObject](../../mfc/reference/cobject-class.md)注册表中的注册表数据。  
  
```  
BOOL GetSectionObject(
    LPCTSTR lpszSubSection,  
    LPCTSTR lpszEntry,  
    CObject& obj);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszSubSection`  
 一个字符串，包含注册表项的相对路径。  
  
 [in] `lpszEntry`  
 一个字符串，包含要读取的值。  
  
 [out] `obj`  
 对引用`CObject`。 该方法使用此`CObject`存储注册表数据。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法从注册表中读取数据。 读取的数据是`CObject`数据或从派生的类数据`CObject`。 若要编写`CObject`数据到注册表中，使用两种[CWinAppEx::WriteObject](#writeobject)或[CWinAppEx::WriteSectionObject](#writesectionobject)。  
  
 `lpszSubSection`参数不是注册表项的绝对路径。 它是附加到您的应用程序的默认注册表项末尾的相对路径。 若要获取或设置默认的注册表项，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分别。  
  
##  <a name="a-namegetsectionstringa--cwinappexgetsectionstring"></a><a name="getsectionstring"></a>CWinAppEx::GetSectionString  
 读取的字符串从注册表的数据。  
  
```  
CString GetSectionString(
    LPCTSTR lpszSubSection,  
    LPCTSTR lpszEntry,  
    LPCTSTR lpszDefault = _T(""));
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszSubSection`  
 一个字符串，包含注册表项的相对路径。  
  
 [in] `lpszEntry`  
 一个字符串，包含要读取的值。  
  
 [in] `lpszDefault`  
 要返回指定的值不存在的默认值。  
  
### <a name="return-value"></a>返回值  
 存储在指定的注册表值中，如果数据存在，则该字符串数据否则为`lpszDefault`。  
  
### <a name="remarks"></a>备注  
 此方法读取字符串数据写入到注册表。 使用[CWinAppEx::WriteString](#writestring)和[CWinAppEx::WriteSectionString](#writesectionstring)字符串数据写入注册表。  
  
 `lpszSubSection`参数不是注册表项的绝对路径。 它是附加到您的应用程序的默认注册表项末尾的相对路径。 若要获取或设置默认的注册表项，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分别。  
  
##  <a name="a-namegetshellmanagera--cwinappexgetshellmanager"></a><a name="getshellmanager"></a>CWinAppEx::GetShellManager  
 将指针返回到全局[CShellManager](../../mfc/reference/cshellmanager-class.md)对象。  
  
```  
CShellManager* GetShellManager();
```  
  
### <a name="return-value"></a>返回值  
 指向全局`CShellManager`对象。  
  
### <a name="remarks"></a>备注  
 如果`CShellManager`对象未初始化，此函数将调用[CWinAppEx::InitShellManager](#initshellmanager)返回的指针之前。  
  
##  <a name="a-namegetstringa--cwinappexgetstring"></a><a name="getstring"></a>CWinAppEx::GetString  
 读取的字符串中指定的注册表项的数据。  
  
```  
CString GetString(
    LPCTSTR lpszEntry,  
    LPCTSTR lpzDefault= _T(""));
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszEntry`  
 一个字符串，包含注册表项的名称  
  
 [in] `lpzDefault`  
 该方法将返回指定的注册表项不存在默认值。  
  
### <a name="return-value"></a>返回值  
 如果成功，则在注册表中存储的字符串数据`lpszDefault`否则为。  
  
### <a name="remarks"></a>备注  
 此方法读取字符串数据写入到注册表。 若要对注册表中写入数据，请使用方法[CWinAppEx::WriteString](#writestring)或[CWinAppEx::WriteSectionString](#writesectionstring)。  
  
 `lpszEntry`参数是位于您的应用程序默认注册表项下的注册表项的名称。 若要获取或设置默认的注册表项，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分别。  
  
##  <a name="a-namegettooltipmanagera--cwinappexgettooltipmanager"></a><a name="gettooltipmanager"></a>CWinAppEx::GetTooltipManager  
 将指针返回到全局[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)对象。  
  
```  
CTooltipManager* GetTooltipManager();
```  
  
### <a name="return-value"></a>返回值  
 指向全局`CTooltipManager`对象。  
  
### <a name="remarks"></a>备注  
 如果`CTooltipManager`对象未初始化，此函数将调用[CWinAppEx::InitTooltipManager](#inittooltipmanager)返回的指针之前。  
  
##  <a name="a-namegetusertoolsmanagera--cwinappexgetusertoolsmanager"></a><a name="getusertoolsmanager"></a>CWinAppEx::GetUserToolsManager  
 将指针返回到全局[CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)对象。  
  
```  
CUserToolsManager* GetUserToolsManager();
```  
  
### <a name="return-value"></a>返回值  
 指向全局`CUserToolsManager`对象;`NULL`如果用户工具管理未启用应用程序。  
  
### <a name="remarks"></a>备注  
 检索指向的指针之前`CUserToolsManager`对象时，必须通过调用初始化管理器[CWinAppEx::EnableUserTools](#enableusertools)。  
  
##  <a name="a-nameinitcontextmenumanagera--cwinappexinitcontextmenumanager"></a><a name="initcontextmenumanager"></a>CWinAppEx::InitContextMenuManager  
 初始化[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)对象。  
  
```  
BOOL InitContextMenuManager();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果该方法将创建 CContextMenuManager 对象中;0`CContextMenuManager`对象已存在。  
  
### <a name="remarks"></a>备注  
 如果调用[CWinAppEx::GetContextMenuManager](#getcontextmenumanager)，该方法的默认实现调用`InitContextMenuManager`。  
  
 如果您的应用程序已具有上下文菜单管理器并调用`InitContextMenuManager`，您的应用程序将具有[ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c)失败。 因此，不应调用`InitContextMenuManager`如果您创建`CContextMenuManager`直接对象。 如果您没有使用自定义`CContextMenuManager`，应使用`GetContextMenuManager`创建`CContextMenuManager`对象。  
  
##  <a name="a-nameinitkeyboardmanagera--cwinappexinitkeyboardmanager"></a><a name="initkeyboardmanager"></a>CWinAppEx::InitKeyboardManager  
 初始化[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)对象。  
  
```  
BOOL InitKeyboardManager();
```  
  
### <a name="return-value"></a>返回值  
 如果该方法将创建为非`CKeyboardManager`对象; 0`CKeyboardManager`对象已存在。  
  
### <a name="remarks"></a>备注  
 如果调用[CWinAppEx::GetKeyboardManager](#getkeyboardmanager)，该方法的默认实现调用`InitKeyboardManager`。  
  
 如果您的应用程序已具有一个键盘管理器并调用`InitKeyboardManager`，您的应用程序将具有[ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c)失败。 因此，不应调用`InitKeyboardManager`如果您创建`CKeyboardManager`直接对象。 如果您没有使用自定义`CKeyboardManager`，应使用`GetKeyboardManager`创建`CKeyboardManager`对象。  
  
##  <a name="a-nameinitmousemanagera--cwinappexinitmousemanager"></a><a name="initmousemanager"></a>CWinAppEx::InitMouseManager  
 初始化[CMouseManager](../../mfc/reference/cmousemanager-class.md)对象。  
  
```  
BOOL InitMouseManager();
```  
  
### <a name="return-value"></a>返回值  
 如果该方法将创建为非`CMouseManager`对象; 0`CMouseManager`对象已存在。  
  
### <a name="remarks"></a>备注  
 如果调用[CWinAppEx::GetMouseManager](#getmousemanager)，该方法的默认实现调用`InitMouseManager`。  
  
 如果您的应用程序已具有鼠标管理器并调用`InitMouseManager`，您的应用程序将具有[ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c)失败。 因此不应调用`InitMouseManager`如果您创建`CMouseManager`直接对象。 如果您没有使用自定义`CMouseManager`，应使用`GetMouseManager`创建`CMouseManager`对象。  
  
##  <a name="a-nameinitshellmanagera--cwinappexinitshellmanager"></a><a name="initshellmanager"></a>CWinAppEx::InitShellManager  
 初始化[CShellManager](../../mfc/reference/cshellmanager-class.md)对象。  
  
```  
BOOL InitShellManager();
```  
  
### <a name="return-value"></a>返回值  
 如果该方法将创建为非`CShellManager`对象; 0`CShellManager`对象已存在。  
  
### <a name="remarks"></a>备注  
 如果调用[CWinAppEx::GetShellManager](#getshellmanager)，该方法的默认实现调用`InitShellManager`。  
  
 如果您的应用程序已具有 shell 管理器并调用`InitShellManager`，应用程序将引发[ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c)失败。 因此，不要调用`InitShellManager`如果您创建`CShellManager`直接对象。 如果您没有使用自定义`CShellManager`，使用`GetShellManager`创建`CShellManager`对象。  
  
##  <a name="a-nameinittooltipmanagera--cwinappexinittooltipmanager"></a><a name="inittooltipmanager"></a>CWinAppEx::InitTooltipManager  
 初始化[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)对象。  
  
```  
BOOL InitTooltipManager();
```  
  
### <a name="return-value"></a>返回值  
 如果该方法将创建为非`CTooltipManager`对象; 0`CTooltipManager`对象已存在。  
  
### <a name="remarks"></a>备注  
 如果调用[CWinAppEx::GetTooltipManager](#gettooltipmanager)，该方法的默认实现调用`InitTooltipManager`。  
  
 如果您的应用程序已具有工具提示管理器并调用`InitTooltipManager`，您的应用程序将具有[ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c)失败。 因此，不应调用`InitTooltipManager`如果您创建`CTooltipManager`直接对象。 如果您没有使用自定义`CTooltipManager`，应使用`GetTooltipManager`创建`CTooltipManager`对象。  
  
##  <a name="a-nameisresourcesmartupdatea--cwinappexisresourcesmartupdate"></a><a name="isresourcesmartupdate"></a>CWinAppEx::IsResourceSmartUpdate  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsResourceSmartUpdate() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameisstateexistsa--cwinappexisstateexists"></a><a name="isstateexists"></a>CWinAppEx::IsStateExists  
 指示指定的键是否是在注册表中。  
  
```  
BOOL IsStateExists(LPCTSTR lpszSectionName);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszSectionName`  
 一个字符串，包含该注册表项的路径。  
  
### <a name="return-value"></a>返回值  
 非零，如果该密钥是在注册表中;否则为 0。  
  
##  <a name="a-nameloadcustomstatea--cwinappexloadcustomstate"></a><a name="loadcustomstate"></a>CWinAppEx::LoadCustomState  
 从注册表加载的应用程序的状态后，框架将调用此方法。  
  
```  
virtual void LoadCustomState();
```  
  
### <a name="remarks"></a>备注  
 如果您想要执行的任何处理，应用程序从注册表加载此状态后，重写此方法。 默认情况下，此方法没有任何效果。  
  
 从注册表加载自定义状态信息，以便信息必须先保存使用[CWinAppEx::SaveCustomState](#savecustomstate)。  
  
##  <a name="a-nameloadstatea--cwinappexloadstate"></a><a name="loadstate"></a>CWinAppEx::LoadState  
 从 Windows 注册表中读取应用程序状态。  
  
```  
BOOL LoadState(
    CMDIFrameWndEx* pFrame,  
    LPCTSTR lpszSectionName = NULL);

 
BOOL LoadState(
    CFrameWndEx* pFrame,  
    LPCTSTR lpszSectionName = NULL);

 
BOOL LoadState(
    COleIPFrameWndEx* pFrame,  
    LPCTSTR lpszSectionName = NULL);

 
virtual BOOL LoadState(
    LPCTSTR lpszSectionName = NULL,  
    CFrameImpl* pFrameImpl = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `pFrame`  
 指向框架窗口对象的指针。 此方法适用于该框架窗口在注册表中的状态信息。  
  
 [in] `lpszSectionName`  
 一个字符串，包含注册表项的相对路径。  
  
 [in] `pFrameImpl`  
 一个指向`CFrameImpl`对象。 此方法适用于该框架窗口在注册表中的状态信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法加载的应用程序和框架窗口的任何状态信息的状态。 框架窗口的加载的信息应用于提供的框架窗口中。 如果未提供的框架窗口，将加载应用程序的状态信息。 应用程序信息包括状态的[CMouseManager 类](../../mfc/reference/cmousemanager-class.md)， [CContextMenuManager 类](../../mfc/reference/ccontextmenumanager-class.md)， [CKeyboardManager 类](../../mfc/reference/ckeyboardmanager-class.md)，和[CUserToolsManager 类](../../mfc/reference/cusertoolsmanager-class.md)。  
  
 默认实现`CFrameImpl::OnLoadFrame`调用`LoadState`。  
  
 `lpszSectionName`参数不是注册表项的绝对路径。 它是相对路径添加到您的应用程序的默认注册表项的末尾。 若要获取或设置默认的注册表项，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分别。  
  
##  <a name="a-nameloadwindowplacementa--cwinappexloadwindowplacement"></a><a name="loadwindowplacement"></a>CWinAppEx::LoadWindowPlacement  
 从注册表加载的大小和位置的主框架窗口时，由框架调用。  
  
```  
virtual BOOL LoadWindowPlacement(
    CRect& rectNormalPosition,  
    int& nFlags,  
    int& nShowCmd);
```  
  
### <a name="parameters"></a>参数  
 [out] `rectNormalPosition`  
 一个包含主框架窗口的坐标，在还原位置中时的矩形。  
  
 [out] `nFlags`  
 控制的最小化的窗口以及操作系统如何最小化的窗口和还原的窗口之间切换的位置的标志。  
  
 [out] `nShowCmd`  
 一个整数，指定窗口中的显示状态。 有关可能的值的详细信息，请参阅[CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow)。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 默认情况下，MFC 将自动加载的以前的位置和主框架窗口的状态时启动该应用程序。 有关如何将此信息存储在注册表中的详细信息，请参阅[CWinAppEx::StoreWindowPlacement](#storewindowplacement)。  
  
 如果您想要加载的主框架窗口的附加信息，请重写此方法。  
  
##  <a name="a-namembforceimagereseta--cwinappexmbforceimagereset"></a><a name="m_bforceimagereset"></a>CWinAppEx::m_bForceImageReset  
 指定是否框架时重置工具栏上的所有映像重新加载包含的工具栏的框架窗口。  
  
```  
BOOL m_bForceImageReset;  
```  
  
### <a name="remarks"></a>备注  
 `m_bForceImageReset`数据成员是受保护的变量。  
  
##  <a name="a-nameonappcontexthelpa--cwinappexonappcontexthelp"></a><a name="onappcontexthelp"></a>CWinAppEx::OnAppContextHelp  
 框架将调用此方法，当用户请求的上下文帮助**自定义**对话框。  
  
```  
virtual void OnAppContextHelp(
    CWnd* pWndControl,  
    const DWORD dwHelpIDArray[]);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndControl`  
 指向为其用户调用上下文帮助的窗口对象的指针。  
  
 [in] `dwHelpIDArray[]`  
 保留的值。  
  
### <a name="remarks"></a>备注  
 此方法当前保留供将来使用。 默认实现不执行任何操作，它当前未由框架调用。  
  
##  <a name="a-nameonclosingmainframea--cwinappexonclosingmainframe"></a><a name="onclosingmainframe"></a>CWinAppEx::OnClosingMainFrame  
 在处理框架窗口时，框架将调用此方法`WM_CLOSE`。  
  
```  
virtual void OnClosingMainFrame(CFrameImpl* pFrameImpl);
```  
  
### <a name="parameters"></a>参数  
 [in] `pFrameImpl`  
 一个指向`CFrameImpl`对象。  
  
### <a name="remarks"></a>备注  
 此方法的默认实现将保存的状态`pFrameImpl`。  
  
##  <a name="a-nameonviewdoubleclicka--cwinappexonviewdoubleclick"></a><a name="onviewdoubleclick"></a>CWinAppEx::OnViewDoubleClick  
 调用是与视图相关联，当用户双击该视图中的任意位置的用户定义的命令。  
  
```  
virtual BOOL OnViewDoubleClick(
    CWnd* pWnd,  
    int iViewId);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWnd`  
 指针指向的对象派生自[CView 类](../../mfc/reference/cview-class.md)。  
  
 [in] `iViewId`  
 视图 id。  
  
### <a name="return-value"></a>返回值  
 `True`如果框架找到命令;否则为 false。  
  
### <a name="remarks"></a>备注  
 若要支持自定义鼠标行为，您必须调用此函数进行处理时`WM_LBUTTONDBLCLK`消息。 此方法将执行与由提供的视图 ID 关联的命令`iViewId`。 有关自定义鼠标行为的详细信息，请参阅[键盘和鼠标自定义](../../mfc/keyboard-and-mouse-customization.md)。  
  
##  <a name="a-nameonworkspaceidlea--cwinappexonworkspaceidle"></a><a name="onworkspaceidle"></a>CWinAppEx::OnWorkspaceIdle  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnWorkspaceIdle(CWnd*);
```  
  
### <a name="parameters"></a>参数  
 [in] `CWnd*`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namepreloadstatea--cwinappexpreloadstate"></a><a name="preloadstate"></a>CWinAppEx::PreLoadState  
 框架将调用此方法之前从注册表中加载的应用程序的状态。  
  
```  
virtual void PreLoadState();
```  
  
### <a name="remarks"></a>备注  
 如果您想要执行的任何处理之前框架中加载的应用程序状态，重写此方法。  
  
##  <a name="a-namepresavestatea--cwinappexpresavestate"></a><a name="presavestate"></a>CWinAppEx::PreSaveState  
 它将保存应用程序状态之前，框架将调用此方法。  
  
```  
virtual void PreSaveState();
```  
  
### <a name="remarks"></a>备注  
 如果您想要执行的任何处理之前该框架将保存应用程序状态，重写此方法。  
  
##  <a name="a-namereloadwindowplacementa--cwinappexreloadwindowplacement"></a><a name="reloadwindowplacement"></a>CWinAppEx::ReloadWindowPlacement  
 重新加载的大小和位置从注册表的窗口。  
  
```  
virtual BOOL ReloadWindowPlacement(CFrameWnd* pFrame);
```  
  
### <a name="parameters"></a>参数  
 [in] `pFrame`  
 指向框架窗口的指针。  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则非零值如果负载失败，或者没有要加载的数据为 0。  
  
### <a name="remarks"></a>备注  
 使用函数[CWinAppEx::StoreWindowPlacement](#storewindowplacement)写入注册表的大小和窗口的位置。  
  
##  <a name="a-namesavecustomstatea--cwinappexsavecustomstate"></a><a name="savecustomstate"></a>CWinAppEx::SaveCustomState  
 它将保存到注册表的应用程序的状态后，框架将调用此方法。  
  
```  
virtual void SaveCustomState();
```  
  
### <a name="remarks"></a>备注  
 如果您想要执行的任何处理，应用程序将状态保存到注册表后，重写此方法。 默认情况下，此方法没有任何效果。  
  
##  <a name="a-namesavestatea--cwinappexsavestate"></a><a name="savestate"></a>CWinAppEx::SaveState  
 将应用程序状态写入 Windows 注册表。  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszSectionName = NULL,  
    CFrameImpl* pFrameImpl = NULL);

 
BOOL SaveState(
    CMDIFrameWndEx* pFrame,  
    LPCTSTR lpszSectionName = NULL);

 
BOOL SaveState(
    CFrameWndEx* pFrame,  
    LPCTSTR lpszSectionName = NULL);

 
BOOL SaveState(
    COleIPFrameWndEx* pFrame,  
    LPCTSTR lpszSectionName = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszSectionName`  
 一个字符串，包含注册表项的相对路径。  
  
 [in] `pFrameImpl`  
 一个指向`CFrameImpl`对象。 此帧将保存到 Windows 注册表中。  
  
 [in] `pFrame`  
 指向框架窗口对象的指针。 此帧将保存到 Windows 注册表中。  
  
### <a name="return-value"></a>返回值  
 `True`如果成功，则，`false`否则为。  
  
### <a name="remarks"></a>备注  
 此方法将保存应用程序和提供的框架窗口的任何状态信息的状态。 如果未提供的框架窗口，该方法将仅保存应用程序状态。 应用程序信息包括状态的[CMouseManager 类](../../mfc/reference/cmousemanager-class.md)， [CContextMenuManager 类](../../mfc/reference/ccontextmenumanager-class.md)， [CKeyboardManager 类](../../mfc/reference/ckeyboardmanager-class.md)，和[CUserToolsManager 类](../../mfc/reference/cusertoolsmanager-class.md)。  
  
 `lpszSectionName`参数不是注册表项的绝对路径。 它是附加到您的应用程序的默认注册表项末尾的相对路径。 若要获取或设置默认的注册表项，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分别。  
  
##  <a name="a-namesetregistrybasea--cwinappexsetregistrybase"></a><a name="setregistrybase"></a>CWinAppEx::SetRegistryBase  
 设置应用程序的默认注册表路径。  
  
```  
LPCTSTR SetRegistryBase(LPCTSTR lpszSectionName = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszSectionName`  
 一个字符串，包含路径的注册表项。  
  
### <a name="return-value"></a>返回值  
 一个字符串，其中包含默认注册表位置的路径。  
  
### <a name="remarks"></a>备注  
 所有方法[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)访问到默认位置中的注册表开头。 使用此方法可以更改该默认注册表位置。 使用[CWinAppEx::GetRegistryBase](#getregistrybase)来检索默认注册表位置。  
  
##  <a name="a-nameshowpopupmenua--cwinappexshowpopupmenu"></a><a name="showpopupmenu"></a>CWinAppEx::ShowPopupMenu  
 显示弹出菜单。  
  
```  
virtual BOOL ShowPopupMenu(
    UINT uiMenuResId,  
    const CPoint& point,  
    CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiMenuResId`  
 菜单上的资源 id。  
  
 [in] `point`  
 一个[CPoint](../../atl-mfc-shared/reference/cpoint-class.md) ，它指定屏幕坐标中的菜单上的位置。  
  
 [in] `pWnd`  
 指向拥有的弹出菜单的窗口的指针。  
  
### <a name="return-value"></a>返回值  
 非零，如果成功，则显示弹出菜单否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法会显示与关联的菜单`uiMenuResId`。  
  
 若要支持弹出菜单，您必须[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)对象。 如果您未初始化`CContextMenuManager`对象，`ShowPopupMenu`将失败。  
  
##  <a name="a-namestorewindowplacementa--cwinappexstorewindowplacement"></a><a name="storewindowplacement"></a>CWinAppEx::StoreWindowPlacement  
 由框架来写入注册表的大小和位置的主框架窗口调用。  
  
```  
virtual BOOL StoreWindowPlacement(
    const CRect& rectNormalPosition,  
    int nFlags,  
    int nShowCmd);
```  
  
### <a name="parameters"></a>参数  
 [in] `nFlags`  
 控制的最小化的窗口以及操作系统如何最小化的窗口和还原的窗口之间切换的位置的标志。  
  
 [in] `nShowCmd`  
 一个整数，指定窗口中的显示状态。 有关可能的值的详细信息，请参阅[CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow)。  
  
 [in] `rectNormalPosition`  
 一个包含主框架窗口的坐标，当它处于还原状态的矩形。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 默认情况下，MFC 会自动保存的位置和应用程序退出之前的主框架窗口的状态。 此信息存储在您的应用程序在默认注册表位置 WindowPlacement 项下的 Windows 注册表中。 有关您的应用程序的默认注册表位置的详细信息，请参阅[CWinAppEx::GetRegistryBase](#getregistrybase)。  
  
 如果您想要存储有关主框架窗口的其他信息，请重写此方法。  
  
##  <a name="a-namewritebinarya--cwinappexwritebinary"></a><a name="writebinary"></a>CWinAppEx::WriteBinary  
 将二进制数据写入注册表。  
  
```  
BOOL WriteBinary(
    LPCTSTR lpszEntry,  
    LPBYTE pData,  
    UINT nBytes);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszEntry`  
 一个字符串，包含注册表项的名称。  
  
 [in] `pData`  
 要存储的数据。  
  
 [in] `nBytes`  
 大小`pData`以字节为单位。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则此方法否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 `lpszEntry`参数是一个位于您的应用程序在默认注册表项下的注册表项的名称。 若要获取或设置默认的注册表项，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分别。  
  
 如果指定的键`lpszEntry`不存在，此方法将创建它。  
  
##  <a name="a-namewriteinta--cwinappexwriteint"></a><a name="writeint"></a>CWinAppEx::WriteInt  
 将数字数据写入注册表。  
  
```  
BOOL WriteInt(
    LPCTSTR lpszEntry,  
    int nValue);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszEntry`  
 一个字符串，包含注册表项的名称。  
  
 [in] `nValue`  
 要存储的数据。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则此方法否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 `lpszEntry`参数是位于您的应用程序默认注册表项下的注册表项的名称。 若要获取或设置默认的注册表项，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分别。  
  
 如果指定的键`lpszEntry`不存在，此方法将创建它。  
  
##  <a name="a-namewriteobjecta--cwinappexwriteobject"></a><a name="writeobject"></a>CWinAppEx::WriteObject  
 写入数据派生自[CObject 类](../../mfc/reference/cobject-class.md)到注册表。  
  
```  
BOOL WriteObject(
    LPCTSTR lpszEntry,  
    CObject& obj);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszEntry`  
 一个字符串，包含要设置的值。  
  
 [in] `obj`  
 对引用`CObject`方法将存储的数据。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则此方法否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法将写入`obj`到默认注册表项下指定的值的数据。 使用[CWinAppEx::GetRegistryBase](#getregistrybase)来确定当前的注册表项。  
  
##  <a name="a-namewritesectionbinarya--cwinappexwritesectionbinary"></a><a name="writesectionbinary"></a>CWinAppEx::WriteSectionBinary  
 将二进制数据写入注册表中的值。  
  
```  
BOOL WriteSectionBinary(
    LPCTSTR lpszSubSection,  
    LPCTSTR lpszEntry,  
    LPBYTE pData,  
    UINT nBytes);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszSubSection`  
 一个字符串，包含注册表项的名称  
  
 [in] `lpszEntry`  
 一个字符串，包含要设置的值。  
  
 [in] `pData`  
 要向注册表写入的数据。  
  
 [in] `nBytes`  
 大小`pData`以字节为单位。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则此方法否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 `lpszSubSection`参数不是注册表项的绝对路径。 它是附加到您的应用程序的默认注册表项末尾的相对路径。 若要获取或设置默认的注册表项，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分别。  
  
 如果指定的键`lpszEntry`不存在，此方法将创建它。  
  
##  <a name="a-namewritesectioninta--cwinappexwritesectionint"></a><a name="writesectionint"></a>CWinAppEx::WriteSectionInt  
 将数字数据写入注册表。  
  
```  
BOOL WriteSectionInt(
    LPCTSTR lpszSubSection,  
    LPCTSTR lpszEntry,  
    int nValue);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszSubSection`  
 一个字符串，包含注册表项的相对路径。  
  
 [in] `lpszEntry`  
 一个字符串，包含要设置的值。  
  
 [in] `nValue`  
 要向注册表写入的数据。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则此方法否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 `lpszSubSection`参数不是注册表项的绝对路径。 它是追加到您的应用程序的默认注册表项的相对路径。 若要获取或设置默认的注册表项，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分别。  
  
 如果指定的键`lpszEntry`不存在，此方法将创建它。  
  
##  <a name="a-namewritesectionobjecta--cwinappexwritesectionobject"></a><a name="writesectionobject"></a>CWinAppEx::WriteSectionObject  
 写入数据派生自[CObject 类](../../mfc/reference/cobject-class.md)为特定的注册表值。  
  
```  
BOOL WriteSectionObject(
    LPCTSTR lpszSubSection,  
    LPCTSTR lpszEntry,  
    CObject& obj);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszSubSection`  
 一个字符串，包含注册表项的名称。  
  
 [in] `lpszEntry`  
 一个字符串，包含要设置的值的名称。  
  
 [in] `obj`  
 要存储的数据。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则此方法否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 `lpszSubSection`参数不是注册表项的绝对路径。 它是附加到您的应用程序的默认注册表项末尾的相对路径。 若要获取或设置默认的注册表项，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分别。  
  
 如果指定的值`lpszEntry`下由指定的注册表项不存在`lpszSubSection`，此方法将创建该值。  
  
##  <a name="a-namewritesectionstringa--cwinappexwritesectionstring"></a><a name="writesectionstring"></a>CWinAppEx::WriteSectionString  
 将字符串数据写入注册表中的值。  
  
```  
BOOL WriteSectionString(
    LPCTSTR lpszSubSection,  
    LPCTSTR lpszEntry,  
    LPCTSTR lpszValue);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszSubSection`  
 一个字符串，包含注册表项的名称。  
  
 [in] `lpszEntry`  
 一个字符串，包含要设置的值。  
  
 [in] `lpszValue`  
 要向注册表写入的字符串数据。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则此方法否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 `lpszSubSection`参数不是注册表项的绝对路径。 它是附加到您的应用程序的默认注册表项末尾的相对路径。 若要获取或设置默认的注册表项，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分别。  
  
 如果指定的值`lpszEntry`下不存在`lpszSubSection`，此方法将创建它。  
  
##  <a name="a-namewritestringa--cwinappexwritestring"></a><a name="writestring"></a>CWinAppEx::WriteString  
 将字符串数据写入注册表。  
  
```  
BOOL WriteString(
    LPCTSTR lpszEntry,  
    LPCTSTR lpszValue);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszEntry`  
 一个字符串，包含注册表项的名称。  
  
 [in] `lpszValue`  
 要存储的数据。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则此方法否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 `lpszEntry`参数是位于您的应用程序默认注册表项下的注册表项的名称。 若要获取或设置默认的注册表项，使用方法[CWinAppEx::GetRegistryBase](#getregistrybase)和[CWinAppEx::SetRegistryBase](#setregistrybase)分别。  
  
 如果指定的键`lspzEntry`不存在，此方法将创建它。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CWinApp 类](../../mfc/reference/cwinapp-class.md)   
 [CMouseManager 类](../../mfc/reference/cmousemanager-class.md)   
 [CContextMenuManager 类](../../mfc/reference/ccontextmenumanager-class.md)   
 [CKeyboardManager 类](../../mfc/reference/ckeyboardmanager-class.md)   
 [CUserToolsManager 类](../../mfc/reference/cusertoolsmanager-class.md)

