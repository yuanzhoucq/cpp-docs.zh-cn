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
- CContainedWindow
- CContainedWindowT
- ATL.CContainedWindowT
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: e10aa4b455696fd217f88b6eb1de2421fccda6de
ms.lasthandoff: 02/24/2017

---
# <a name="ccontainedwindowt-class"></a>CContainedWindowT 类
此类实现包含在另一个对象内的窗口。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
template <class TBase = CWindow, class TWinTraits = CControlWinTraits>  
class CContainedWindowT : public TBase
```  
  
#### <a name="parameters"></a>参数  
 *TBase*  
 您的新类的基类。 默认基类为`CWindow`。  
  
 `TWinTraits`  
 一个定义窗口样式的特征类。 默认值为 `CControlWinTraits`。  
  
> [!NOTE]
> [CContainedWindow](ccontainedwindowt-class.md)专用化的`CContainedWindowT`。 如果你想要更改的基类或特征，使用`CContainedWindowT`直接。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CContainedWindowT::CContainedWindowT](#ccontainedwindowt)|构造函数。 数据成员初始化为指定的消息映射将用于处理包含的窗口的消息。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CContainedWindowT::Create](#create)|创建一个窗口。|  
|[CContainedWindowT::DefWindowProc](#defwindowproc)|提供默认消息处理。|  
|[CContainedWindowT::GetCurrentMessage](#getcurrentmessage)|返回当前消息。|  
|[CContainedWindowT::RegisterWndSuperclass](#registerwndsuperclass)|注册所包含窗口的窗口类。|  
|[CContainedWindowT::SubclassWindow](#subclasswindow)|对窗口子类化。|  
|[CContainedWindowT::SwitchMessageMap](#switchmessagemap)|更改哪些消息映射用于处理包含的窗口的消息。|  
|[CContainedWindowT::UnsubclassWindow](#unsubclasswindow)|还原先前子类化的窗口。|  
|[CContainedWindowT::WindowProc](#windowproc)|（静态）处理发送到包含窗口中的消息。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CContainedWindowT::m_dwMsgMapID](#m_dwmsgmapid)|标识哪些消息映射将用于处理包含的窗口的消息。|  
|[CContainedWindowT::m_lpszClassName](#m_lpszclassname)|指定新的窗口类将基于现有窗口类的名称。|  
|[CContainedWindowT::m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|指向窗口类的原始窗口过程。|  
|[CContainedWindowT::m_pObject](#m_pobject)|指向包含的对象。|  
  
## <a name="remarks"></a>备注  
 `CContainedWindowT`实现包含在另一个对象内的窗口。 `CContainedWindowT`窗口过程使用一条消息映射中包含的对象直接将消息到相应的处理程序。 在构造时`CContainedWindowT`对象，您可以指定应使用哪些消息映射。  
  
 `CContainedWindowT`允许您通过创建超类现有窗口类创建一个新窗口。 **创建**方法第一次注册的窗口类，基于现有类，但使用`CContainedWindowT::WindowProc`。 **创建**然后创建一个基于此新的窗口类的窗口。 每个实例`CContainedWindowT`可以超类不同的窗口类。  
  
 `CContainedWindowT` 还支持窗口子类化。 `SubclassWindow` 方法将现有的窗口附加到 `CContainedWindowT` 对象并将窗口过程更改为 `CContainedWindowT::WindowProc`。 `CContainedWindowT` 的每个实例可以子类化其他窗口。  
  
> [!NOTE]
>  对于任何给定`CContainedWindowT`对象，请调用**创建**或`SubclassWindow`。 不应调用这两种方法对同一个对象。  
  
 当您使用**将控件添加**选项在 ATL 项目向导中，向导将自动添加`CContainedWindowT`于实现该控件的类数据成员。 下面的示例演示如何声明包含的窗口︰  
  
 [!code-cpp[NVC_ATL_Windowing #&38;](../../atl/codesnippet/cpp/ccontainedwindowt-class_1.h)]  
  
 [!code-cpp[NVC_ATL_Windowing #&39;](../../atl/codesnippet/cpp/ccontainedwindowt-class_2.h)]  
  
 [!code-cpp[NVC_ATL_Windowing #&40;](../../atl/codesnippet/cpp/ccontainedwindowt-class_3.h)]  
  
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
  
##  <a name="a-nameccontainedwindowta--ccontainedwindowtccontainedwindowt"></a><a name="ccontainedwindowt"></a>CContainedWindowT::CContainedWindowT  
 构造函数会初始化数据成员。  
  
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
 [in]包含窗口中将基于现有窗口类的名称。  
  
 `pObject`  
 [in]指向包含声明的消息映射的对象的指针。 此对象的类必须派生自[CMessageMap](../../atl/reference/cmessagemap-class.md)。  
  
 `dwMsgMapID`  
 [in]标识将处理所包含的窗口消息的消息映射。 默认值为 0，指定与声明的默认消息映射[BEGIN_MSG_MAP](http://msdn.microsoft.com/library/8bbb5af9-18b1-48c6-880e-166f599ee554)。 若要使用的替换消息映射声明与[ALT_MSG_MAP(msgMapID)](http://msdn.microsoft.com/library/2c8871bf-abc0-4d52-bcf7-6b2ab9eb5af8)，传递`msgMapID`。  
  
### <a name="remarks"></a>备注  
 如果您想要创建新的窗口，通过[创建](#create)，必须通过为现有窗口类名称`lpszClassName`参数。 有关示例，请参阅[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)概述。  
  
 有三个构造函数︰  
  
-   带有三个参数构造函数是一个通常名。  
  
-   带有两个参数的构造函数将类名与**TBase::GetWndClassName**。  
  
-   如果您想要更高版本提供参数，则使用不带任何参数的构造函数。 稍后调用时，您必须提供的窗口类名称、 消息映射对象和消息映射 ID**创建**。  
  
 如果子类化现有窗口通过[SubclassWindow](#subclasswindow)、`lpszClassName`未使用值; 因此，您可通过**NULL**为此参数。  
  
##  <a name="a-namecreatea--ccontainedwindowtcreate"></a><a name="create"></a>CContainedWindowT::Create  
 调用[RegisterWndSuperclass](#registerwndsuperclass)要注册的窗口类，基于现有类，但使用[CContainedWindowT::WindowProc](#windowproc)。  
  
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
 [in]包含窗口中将基于现有窗口类的名称。  
  
 `pObject`  
 [in]指向包含声明的消息映射的对象的指针。 此对象的类必须派生自[CMessageMap](../../atl/reference/cmessagemap-class.md)。  
  
 `dwMsgMapID`  
 [in]标识将处理所包含的窗口消息的消息映射。 默认值为 0，指定与声明的默认消息映射[BEGIN_MSG_MAP](http://msdn.microsoft.com/library/8bbb5af9-18b1-48c6-880e-166f599ee554)。 若要使用的替换消息映射声明与[ALT_MSG_MAP(msgMapID)](http://msdn.microsoft.com/library/2c8871bf-abc0-4d52-bcf7-6b2ab9eb5af8)，传递`msgMapID`。  
  
 `hWndParent`  
 [in]父或所有者窗口的句柄。  
  
 `rect`  
 [in]一个[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它指定窗口的位置。 `RECT`可以通过指针还是通过引用传递。  
  
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
 现有的窗口类名称保存在[m_lpszClassName](#m_lpszclassname)。 **创建**然后创建一个基于此新类的窗口。 新创建的窗口会自动附加到`CContainedWindowT`对象。  
  
> [!NOTE]
>  不要调用**创建**如果您调用了[SubclassWindow](#subclasswindow)。  
  
> [!NOTE]
>  如果为的值使用 0`MenuOrID`参数，则必须指定为 0U （默认值） 以避免编译器错误。  
  
##  <a name="a-namedefwindowproca--ccontainedwindowtdefwindowproc"></a><a name="defwindowproc"></a>CContainedWindowT::DefWindowProc  
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
 默认情况下，`DefWindowProc`调用[CallWindowProc](http://msdn.microsoft.com/library/windows/desktop/ms633571) Win32 函数以将消息信息发送到窗口过程中指定[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。  
  
##  <a name="a-namegetcurrentmessagea--ccontainedwindowtgetcurrentmessage"></a><a name="getcurrentmessage"></a>CContainedWindowT::GetCurrentMessage  
 返回当前消息 ( **m_pCurrentMsg**)。  
  
```
const _ATL_MSG* GetCurrentMessage();
```  
  
### <a name="return-value"></a>返回值  
 当前消息，打包在`MSG`结构。  
  
##  <a name="a-namemdwmsgmapida--ccontainedwindowtmdwmsgmapid"></a><a name="m_dwmsgmapid"></a>CContainedWindowT::m_dwMsgMapID  
 保存当前正在使用包含窗口中的消息映射的标识符。  
  
```
DWORD m_dwMsgMapID;
```  
  
### <a name="remarks"></a>备注  
 此消息映射必须声明中包含的对象。  
  
 使用默认消息映射中，声明[BEGIN_MSG_MAP](http://msdn.microsoft.com/library/8bbb5af9-18b1-48c6-880e-166f599ee554)，总会识别被零除。 使用替换消息映射声明[ALT_MSG_MAP(msgMapID)](http://msdn.microsoft.com/library/2c8871bf-abc0-4d52-bcf7-6b2ab9eb5af8)，由标识`msgMapID`。  
  
 `m_dwMsgMapID`首次初始化由构造函数，并可以通过调用更改[SwitchMessageMap](#switchmessagemap)。 有关示例，请参阅[CContainedWindowT 概述](../../atl/reference/ccontainedwindowt-class.md)。  
  
##  <a name="a-namemlpszclassnamea--ccontainedwindowtmlpszclassname"></a><a name="m_lpszclassname"></a>CContainedWindowT::m_lpszClassName  
 指定现有窗口类的名称。  
  
```
LPTSTR m_lpszClassName;
```  
  
### <a name="remarks"></a>备注  
 当您创建一个窗口，[创建](#create)注册新的窗口类，基于该现有类，但使用[CContainedWindowT::WindowProc](#windowproc)。  
  
 `m_lpszClassName`由构造函数初始化。 有关示例，请参阅[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)概述。  
  
##  <a name="a-namempfnsuperwindowproca--ccontainedwindowtmpfnsuperwindowproc"></a><a name="m_pfnsuperwindowproc"></a>CContainedWindowT::m_pfnSuperWindowProc  
 如果包含窗口中进行了子类化，`m_pfnSuperWindowProc`指向窗口类的原始窗口过程。  
  
```
WNDPROC m_pfnSuperWindowProc;
```  
  
### <a name="remarks"></a>备注  
 如果包含的窗口是超类，意味着它将基于修改现有的类的窗口类`m_pfnSuperWindowProc`指向现有窗口类的窗口过程。  
  
 [DefWindowProc](#defwindowproc)方法将消息发送到窗口过程中保存`m_pfnSuperWindowProc`。  
  
##  <a name="a-namempobjecta--ccontainedwindowtmpobject"></a><a name="m_pobject"></a>CContainedWindowT::m_pObject  
 指向对象，其中包含`CContainedWindowT`对象。  
  
```
CMessageMap* m_pObject;
```  
  
### <a name="remarks"></a>备注  
 此容器、 其类必须派生自[CMessageMap](../../atl/reference/cmessagemap-class.md)，声明由包含窗口中使用的消息映射。  
  
 `m_pObject`由构造函数初始化。 有关示例，请参阅[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)概述。  
  
##  <a name="a-nameregisterwndsuperclassa--ccontainedwindowtregisterwndsuperclass"></a><a name="registerwndsuperclass"></a>CContainedWindowT::RegisterWndSuperclass  
 由调用[创建](#create)以注册所包含窗口的窗口类。  
  
```
ATOM RegisterWndSuperClass();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，一个原子，用于唯一标识正在注册的窗口类否则为为零。  
  
### <a name="remarks"></a>备注  
 此窗口类基于现有类，但使用[CContainedWindowT::WindowProc](#windowproc)。 现有窗口类的名称和窗口过程将保存在[m_lpszClassName](#m_lpszclassname)和[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)分别。  
  
##  <a name="a-namesubclasswindowa--ccontainedwindowtsubclasswindow"></a><a name="subclasswindow"></a>CContainedWindowT::SubclassWindow  
 由窗口中标识的子类`hWnd`并将其附加到`CContainedWindowT`对象。  
  
```
BOOL SubclassWindow(HWND hWnd);
```  
  
### <a name="parameters"></a>参数  
 `hWnd`  
 [in]正在子类化窗口的句柄。  
  
### <a name="return-value"></a>返回值  
 **TRUE**成功子类化; 否则为此窗口是否**FALSE**。  
  
### <a name="remarks"></a>备注  
 子类化的窗口现在使用[CContainedWindowT::WindowProc](#windowproc)。 在中保存的原始窗口过程[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。  
  
> [!NOTE]
>  不要调用`SubclassWindow`如果您调用了[创建](#create)。  
  
##  <a name="a-nameswitchmessagemapa--ccontainedwindowtswitchmessagemap"></a><a name="switchmessagemap"></a>CContainedWindowT::SwitchMessageMap  
 更改将使用哪些消息映射来处理包含的窗口的消息。  
  
```
void SwitchMessageMap(DWORD dwMsgMapID);
```  
  
### <a name="parameters"></a>参数  
 `dwMsgMapID`  
 [in]消息映射标识符。 若要使用的默认消息映射声明与[BEGIN_MSG_MAP](http://msdn.microsoft.com/library/8bbb5af9-18b1-48c6-880e-166f599ee554)，传递零。 若要使用的替换消息映射声明与[ALT_MSG_MAP(msgMapID)](http://msdn.microsoft.com/library/2c8871bf-abc0-4d52-bcf7-6b2ab9eb5af8)，传递`msgMapID`。  
  
### <a name="remarks"></a>备注  
 必须包含对象中定义的消息映射。  
  
 您最初的构造函数中指定的消息映射标识符。  
  
##  <a name="a-nameunsubclasswindowa--ccontainedwindowtunsubclasswindow"></a><a name="unsubclasswindow"></a>CContainedWindowT::UnsubclassWindow  
 分离从子类化的窗口`CContainedWindowT`对象，并还原原始窗口过程，以保存[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。  
  
```
HWND UnsubclassWindow(BOOL bForce = FALSE);
```  
  
### <a name="parameters"></a>参数  
 `bForce`  
 [in]设置为**TRUE**强制要还原的原始窗口过程即使其窗口过程如下`CContainedWindowT`对象不是当前处于活动状态。 如果`bForce`设置为**FALSE**和窗口过程`CContainedWindowT`对象不是当前处于活动状态，将不会还原原始窗口过程。  
  
### <a name="return-value"></a>返回值  
 先前子类化窗口的句柄。 如果`bForce`设置为**FALSE**和窗口过程`CContainedWindowT`对象未处于活动状态，则返回**NULL**。  
  
### <a name="remarks"></a>备注  
 仅当你想要还原的原始窗口过程窗口中被销毁之前，请使用此方法。 否则为[WindowProc](#windowproc)将自动执行此操作时窗口被破坏。  
  
##  <a name="a-namewindowproca--ccontainedwindowtwindowproc"></a><a name="windowproc"></a>CContainedWindowT::WindowProc  
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
 [in]窗口的句柄。  
  
 `uMsg`  
 [in]发送到窗口的消息。  
  
 `wParam`  
 [in]消息特定的附加信息。  
  
 `lParam`  
 [in]消息特定的附加信息。  
  
### <a name="return-value"></a>返回值  
 消息处理的结果。  
  
### <a name="remarks"></a>备注  
 `WindowProc`直接将消息传递到消息映射由标识[m_dwMsgMapID](#m_dwmsgmapid)。 如有必要，`WindowProc`调用[DefWindowProc](#defwindowproc)进行更多的消息处理。  
  
## <a name="see-also"></a>另请参阅  
 [CWindow 类](../../atl/reference/cwindow-class.md)   
 [CWindowImpl 类](../../atl/reference/cwindowimpl-class.md)   
 [CMessageMap 类](../../atl/reference/cmessagemap-class.md)   
 [BEGIN_MSG_MAP](http://msdn.microsoft.com/library/8bbb5af9-18b1-48c6-880e-166f599ee554)   
 [ALT_MSG_MAP](http://msdn.microsoft.com/library/2c8871bf-abc0-4d52-bcf7-6b2ab9eb5af8)   
 [类概述](../../atl/atl-class-overview.md)

