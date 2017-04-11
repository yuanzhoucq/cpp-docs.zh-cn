---
title: "CContainedWindowT 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CContainedWindowT
- ATLWIN/ATL::CContainedWindowT
- ATLWIN/ATL::CContainedWindowT::CContainedWindowT
- ATLWIN/ATL::CContainedWindowT::Create
- ATLWIN/ATL::CContainedWindowT::DefWindowProc
- ATLWIN/ATL::CContainedWindowT::GetCurrentMessage
- ATLWIN/ATL::CContainedWindowT::RegisterWndSuperclass
- ATLWIN/ATL::CContainedWindowT::SubclassWindow
- ATLWIN/ATL::CContainedWindowT::SwitchMessageMap
- ATLWIN/ATL::CContainedWindowT::UnsubclassWindow
- ATLWIN/ATL::CContainedWindowT::WindowProc
- ATLWIN/ATL::CContainedWindowT::m_dwMsgMapID
- ATLWIN/ATL::CContainedWindowT::m_lpszClassName
- ATLWIN/ATL::CContainedWindowT::m_pfnSuperWindowProc
- ATLWIN/ATL::CContainedWindowT::m_pObject
dev_langs:
- C++
helpviewer_keywords:
- CContainedWindow class
- contained windows
- CContainedWindowT class
ms.assetid: cde0ca36-9347-4068-995a-d294dae57ca9
caps.latest.revision: 23
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
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: ab2b20591ded82dd17a38f5258dfe593f7e88fc8
ms.lasthandoff: 03/31/2017

---
# <a name="ccontainedwindowt-class"></a>CContainedWindowT 类
此类实现包含在另一个对象的窗口。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template <class TBase = CWindow, class TWinTraits = CControlWinTraits>  
class CContainedWindowT : public TBase
```  
  
#### <a name="parameters"></a>参数  
 *TBase*  
 在新类的基类。 默认基类是`CWindow`。  
  
 `TWinTraits`  
 定义窗口样式的特征类。 默认值为 `CControlWinTraits`。  
  
> [!NOTE]
> [CContainedWindow](ccontainedwindowt-class.md)的专用化`CContainedWindowT`。 如果你想要更改的基类或特征，使用`CContainedWindowT`直接。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CContainedWindowT::CContainedWindowT](#ccontainedwindowt)|构造函数。 初始化数据成员，以指定哪些消息映射将用于处理包含的窗口的消息。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CContainedWindowT::Create](#create)|创建一个窗口。|  
|[CContainedWindowT::DefWindowProc](#defwindowproc)|提供默认消息处理。|  
|[CContainedWindowT::GetCurrentMessage](#getcurrentmessage)|返回当前消息。|  
|[CContainedWindowT::RegisterWndSuperclass](#registerwndsuperclass)|注册所包含窗口的窗口类。|  
|[CContainedWindowT::SubclassWindow](#subclasswindow)|对窗口子类化。|  
|[CContainedWindowT::SwitchMessageMap](#switchmessagemap)|更改哪些消息映射用于处理包含的窗口的消息。|  
|[CContainedWindowT::UnsubclassWindow](#unsubclasswindow)|还原先前子类化的窗口。|  
|[CContainedWindowT::WindowProc](#windowproc)|（静态）处理发送到包含窗口的消息。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CContainedWindowT::m_dwMsgMapID](#m_dwmsgmapid)|标识哪些消息映射将用于处理包含的窗口的消息。|  
|[CContainedWindowT::m_lpszClassName](#m_lpszclassname)|指定新的窗口类将基于现有窗口类的名称。|  
|[CContainedWindowT::m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|指向窗口类的原始窗口过程。|  
|[CContainedWindowT::m_pObject](#m_pobject)|指向包含的对象。|  
  
## <a name="remarks"></a>备注  
 `CContainedWindowT`实现包含在另一个对象的窗口。 `CContainedWindowT`窗口过程使用消息映射直接将消息到相应的处理程序的包含对象中。 在构造时`CContainedWindowT`对象，您可以指定应使用哪些消息映射。  
  
 `CContainedWindowT`可以通过创建超类现有窗口类创建一个新窗口。 **创建**方法第一次注册的窗口类，基于现有类，但使用`CContainedWindowT::WindowProc`。 **创建**然后创建基于此新的窗口类的一个窗口。 每个实例`CContainedWindowT`可以超类不同的窗口类。  
  
 `CContainedWindowT` 还支持窗口子类化。 `SubclassWindow` 方法将现有的窗口附加到 `CContainedWindowT` 对象并将窗口过程更改为 `CContainedWindowT::WindowProc`。 `CContainedWindowT` 的每个实例可以子类化其他窗口。  
  
> [!NOTE]
>  对于任何给定`CContainedWindowT`对象，请调用**创建**或`SubclassWindow`。 不应调用这两种方法对同一对象。  
  
 当你使用**添加基于控制**选项在 ATL 项目向导中，该向导将自动添加`CContainedWindowT`实现控件的类数据成员。 下面的示例演示如何声明包含的窗口︰  
  
 [!code-cpp[NVC_ATL_Windowing # 38](../../atl/codesnippet/cpp/ccontainedwindowt-class_1.h)]  
  
 [!code-cpp[NVC_ATL_Windowing # 39](../../atl/codesnippet/cpp/ccontainedwindowt-class_2.h)]  
  
 [!code-cpp[NVC_ATL_Windowing # 40](../../atl/codesnippet/cpp/ccontainedwindowt-class_3.h)]  
  
|有关以下内容的详细信息|请参阅|  
|--------------------------------|---------|  
|创建控件|[ATL 教程](../../atl/active-template-library-atl-tutorial.md)|  
|使用 ATL 中的窗口|[ATL 窗口类](../../atl/atl-window-classes.md)|  
|ATL 项目向导|[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)|  
|Windows|[Windows](http://msdn.microsoft.com/library/windows/desktop/ms632595)和后续主题中的[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `TBase`  
  
 `CContainedWindowT`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlwin.h  
  
##  <a name="ccontainedwindowt"></a>CContainedWindowT::CContainedWindowT  
 构造函数初始化数据成员。  
  
```
CContainedWindowT(
    LPTSTR lpszClassName,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);

CContainedWindowT(
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0)
    CContainedWindowT();
```     
  
### <a name="parameters"></a>参数  
 `lpszClassName`  
 [in]包含窗口将基于现有窗口类的名称。  
  
 `pObject`  
 [in]指向声明的消息映射到包含对象的指针。 此对象的类必须派生自[CMessageMap](../../atl/reference/cmessagemap-class.md)。  
  
 `dwMsgMapID`  
 [in]标识将处理包含的窗口的消息的消息映射。 默认值为 0，指定与声明的默认消息映射[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)。 若要使用的备用消息映射声明与[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)，传递`msgMapID`。  
  
### <a name="remarks"></a>备注  
 如果你想要创建新窗口通过[创建](#create)，必须将一个现有的窗口类，用于名称传递给`lpszClassName`参数。 有关示例，请参阅[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)概述。  
  
 有三个构造函数︰  
  
-   带三个自变量的构造函数是一个通常名。  
  
-   带两个自变量的构造函数使用的类名称**TBase::GetWndClassName**。  
  
-   如果你想要更高版本提供自变量，使用不带任何参数的构造函数。 更高版本调用时，你必须提供的窗口类名、 消息映射对象和消息映射 ID**创建**。  
  
 如果子类化现有窗口通过[SubclassWindow](#subclasswindow)、`lpszClassName`未使用值; 因此，你可以传递**NULL**为此参数。  
  
##  <a name="create"></a>CContainedWindowT::Create  
 调用[RegisterWndSuperclass](#registerwndsuperclass)注册的窗口类，基于现有类，但使用[CContainedWindowT::WindowProc](#windowproc)。  
  
```
HWND Create(  
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);

HWND Create(
    CMessageMap* pObject,
    DWORD dwMsgMapID,
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);

HWND Create(
    LPCTSTR lpszClassName,
    CMessageMap* pObject,
    DWORD dwMsgMapID,
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszClassName`  
 [in]包含窗口将基于现有窗口类的名称。  
  
 `pObject`  
 [in]指向声明的消息映射到包含对象的指针。 此对象的类必须派生自[CMessageMap](../../atl/reference/cmessagemap-class.md)。  
  
 `dwMsgMapID`  
 [in]标识将处理包含的窗口的消息的消息映射。 默认值为 0，指定与声明的默认消息映射[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)。 若要使用的备用消息映射声明与[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)，传递`msgMapID`。  
  
 `hWndParent`  
 [in]父或所有者窗口的句柄。  
  
 `rect`  
 [in]A [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它指定窗口的位置。 `RECT` ，可以通过指针或按引用传递。  
  
 `szWindowName`  
 [in]指定的窗口的名称。 默认值是**NULL**。  
  
 `dwStyle`  
 [in]窗口的样式。 默认值是**WS_CHILD |WS_VISIBLE**。 有关可能的值的列表，请参阅[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwExStyle`  
 [in]扩展的窗口样式。 默认值为 0，这意味着无扩展的样式。 有关可能的值的列表，请参阅[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `MenuOrID`  
 [in]子窗口，窗口标识符。 对于顶级窗口，窗口的菜单句柄。 默认值是**0U**。  
  
 `lpCreateParam`  
 [in]指向窗口创建数据的指针。 完整说明，请参见到最后一个参数的说明[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)。  
  
### <a name="return-value"></a>返回值  
 如果成功，新创建的窗口中; 的句柄否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 现有的窗口类名称保存在[m_lpszClassName](#m_lpszclassname)。 **创建**然后创建基于此新类的一个窗口。 新创建的窗口会自动附加到`CContainedWindowT`对象。  
  
> [!NOTE]
>  不要调用**创建**如果已调用了[SubclassWindow](#subclasswindow)。  
  
> [!NOTE]
>  如果为的值，则使用 0`MenuOrID`参数，必须将它指定为 0U （默认值） 若要避免编译器错误。  
  
##  <a name="defwindowproc"></a>CContainedWindowT::DefWindowProc  
 由调用[WindowProc](#windowproc)未处理的消息映射处理这些消息。  
  
```
LRESULT DefWindowProc()
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```  
  
### <a name="parameters"></a>参数  
 `uMsg`  
 [in]发送到窗口的消息。  
  
 `wParam`  
 [in]消息特定的附加信息。  
  
 `lParam`  
 [in]消息特定的附加信息。  
  
### <a name="return-value"></a>返回值  
 消息处理的结果。  
  
### <a name="remarks"></a>备注  
 默认情况下，`DefWindowProc`调用[CallWindowProc](http://msdn.microsoft.com/library/windows/desktop/ms633571) Win32 函数的消息信息发送到中指定的窗口过程[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。  
  
##  <a name="getcurrentmessage"></a>CContainedWindowT::GetCurrentMessage  
 返回当前消息 ( **m_pCurrentMsg**)。  
  
```
const _ATL_MSG* GetCurrentMessage();
```  
  
### <a name="return-value"></a>返回值  
 当前消息，并打包在`MSG`结构。  
  
##  <a name="m_dwmsgmapid"></a>CContainedWindowT::m_dwMsgMapID  
 包含当前正在使用包含窗口的消息映射的标识符。  
  
```
DWORD m_dwMsgMapID;
```  
  
### <a name="remarks"></a>备注  
 此消息映射必须声明中包含的对象。  
  
 使用默认消息映射中，声明[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)，始终由零。 使用声明的备用消息映射， [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)，由标识`msgMapID`。  
  
 `m_dwMsgMapID`首次初始化由构造函数，并可以通过调用更改[SwitchMessageMap](#switchmessagemap)。 有关示例，请参阅[CContainedWindowT 概述](../../atl/reference/ccontainedwindowt-class.md)。  
  
##  <a name="m_lpszclassname"></a>CContainedWindowT::m_lpszClassName  
 指定现有窗口类的名称。  
  
```
LPTSTR m_lpszClassName;
```  
  
### <a name="remarks"></a>备注  
 当你创建一个窗口，[创建](#create)注册新的窗口类来基于该现有类，但使用[CContainedWindowT::WindowProc](#windowproc)。  
  
 `m_lpszClassName`由构造函数初始化。 有关示例，请参阅[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)概述。  
  
##  <a name="m_pfnsuperwindowproc"></a>CContainedWindowT::m_pfnSuperWindowProc  
 如果对包含的窗口子类化，`m_pfnSuperWindowProc`指向窗口类的原始窗口过程。  
  
```
WNDPROC m_pfnSuperWindowProc;
```  
  
### <a name="remarks"></a>备注  
 如果组件后，超类包含窗口中，这意味着它基于的窗口类，还将修改现有的类，`m_pfnSuperWindowProc`指向现有窗口类的窗口过程。  
  
 [DefWindowProc](#defwindowproc)方法向保存在窗口过程发送消息信息`m_pfnSuperWindowProc`。  
  
##  <a name="m_pobject"></a>CContainedWindowT::m_pObject  
 指向对象，其中包含`CContainedWindowT`对象。  
  
```
CMessageMap* m_pObject;
```  
  
### <a name="remarks"></a>备注  
 此容器、 其类必须派生自[CMessageMap](../../atl/reference/cmessagemap-class.md)，声明由包含窗口的消息映射。  
  
 `m_pObject`由构造函数初始化。 有关示例，请参阅[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)概述。  
  
##  <a name="registerwndsuperclass"></a>CContainedWindowT::RegisterWndSuperclass  
 由调用[创建](#create)以注册包含窗口的窗口类。  
  
```
ATOM RegisterWndSuperClass();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，atom 唯一标识正在注册窗口类否则为零。  
  
### <a name="remarks"></a>备注  
 此窗口类基于现有类，但使用[CContainedWindowT::WindowProc](#windowproc)。 现有窗口类的名称和窗口过程保存在[m_lpszClassName](#m_lpszclassname)和[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)分别。  
  
##  <a name="subclasswindow"></a>CContainedWindowT::SubclassWindow  
 窗口由的子类`hWnd`和将其附加到`CContainedWindowT`对象。  
  
```
BOOL SubclassWindow(HWND hWnd);
```  
  
### <a name="parameters"></a>参数  
 `hWnd`  
 [in]正在子类化窗口的句柄。  
  
### <a name="return-value"></a>返回值  
 **TRUE**窗口是否成功子类化; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 子类化的窗口现在使用[CContainedWindowT::WindowProc](#windowproc)。 原始窗口过程将保存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。  
  
> [!NOTE]
>  不要调用`SubclassWindow`如果已调用了[创建](#create)。  
  
##  <a name="switchmessagemap"></a>CContainedWindowT::SwitchMessageMap  
 更改哪些消息映射将用于处理包含的窗口的消息。  
  
```
void SwitchMessageMap(DWORD dwMsgMapID);
```  
  
### <a name="parameters"></a>参数  
 `dwMsgMapID`  
 [in]消息映射标识符。 若要使用的默认消息映射声明与[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)，传递零。 若要使用的备用消息映射声明与[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)，传递`msgMapID`。  
  
### <a name="remarks"></a>备注  
 消息映射必须中包含的对象定义。  
  
 你最初构造函数中指定的消息映射标识符。  
  
##  <a name="unsubclasswindow"></a>CContainedWindowT::UnsubclassWindow  
 分离从子类化的窗口`CContainedWindowT`对象，并还原原始窗口过程中，保存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。  
  
```
HWND UnsubclassWindow(BOOL bForce = FALSE);
```  
  
### <a name="parameters"></a>参数  
 `bForce`  
 [in]设置为**TRUE**强制要还原的原始窗口过程即使此窗口过程`CContainedWindowT`对象不是当前处于活动状态。 如果`bForce`设置为**FALSE**和此窗口过程`CContainedWindowT`对象不是当前处于活动状态，将不会还原原始窗口过程。  
  
### <a name="return-value"></a>返回值  
 以前子类化窗口的句柄。 如果`bForce`设置为**FALSE**和此窗口过程`CContainedWindowT`对象不是当前处于活动状态，返回**NULL**。  
  
### <a name="remarks"></a>备注  
 仅当你想要还原的原始窗口过程，窗口被销毁之前，请使用此方法。 否则为[WindowProc](#windowproc)将自动执行此操作时销毁窗口。  
  
##  <a name="windowproc"></a>CContainedWindowT::WindowProc  
 此静态方法实现的窗口过程。  
  
```
static LRESULT CALLBACK WindowProc(  
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```  
  
### <a name="parameters"></a>参数  
 `hWnd`  
 [in]窗口句柄。  
  
 `uMsg`  
 [in]发送到窗口的消息。  
  
 `wParam`  
 [in]消息特定的附加信息。  
  
 `lParam`  
 [in]消息特定的附加信息。  
  
### <a name="return-value"></a>返回值  
 消息处理的结果。  
  
### <a name="remarks"></a>备注  
 `WindowProc`将定向到由标识消息映射消息[m_dwMsgMapID](#m_dwmsgmapid)。 如有必要，`WindowProc`调用[DefWindowProc](#defwindowproc)为其他消息处理。  
  
## <a name="see-also"></a>另请参阅  
 [CWindow 类](../../atl/reference/cwindow-class.md)   
 [CWindowImpl 类](../../atl/reference/cwindowimpl-class.md)   
 [CMessageMap 类](../../atl/reference/cmessagemap-class.md)   
 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)   
 [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)   
 [类概述](../../atl/atl-class-overview.md)

