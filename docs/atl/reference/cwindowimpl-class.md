---
title: "CWindowImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CWindowImpl
- ATL.CWindowImpl
- CWindowImpl
dev_langs:
- C++
helpviewer_keywords:
- CWindowImpl class
- subclassing windows, ATL
ms.assetid: 02eefd45-a0a6-4d1b-99f6-dbf627e2cc2f
caps.latest.revision: 22
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 76827682e96d2aea80880fa7d70c267abe02ee1c
ms.lasthandoff: 02/24/2017

---
# <a name="cwindowimpl-class"></a>CWindowImpl 类
提供创建或子类化窗口的方法。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
## <a name="syntax"></a>语法  
  
```
template <class T, class TBase = CWindow, class TWinTraits = CControlWinTraits>  
class ATL_NO_VTABLE CWindowImpl : public CWindowImplBaseT<TBase, TWinTraits>
```    
  
#### <a name="parameters"></a>参数  
 `T`  
 您的新类，派生自 `CWindowImpl`。  
  
 *TBase*  
 您的类的基类。 默认情况下，基类是[CWindow](../../atl/reference/cwindow-class.md)。  
  
 `TWinTraits`  
 一个[特征类](../../atl/understanding-window-traits.md)定义为您的窗口样式。 默认值为 `CControlWinTraits`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CWindowImpl::Create](#create)|创建一个窗口。|  
  
### <a name="cwindowimplbaset-methods"></a>CWindowImplBaseT 方法  
  
|||  
|-|-|  
|[DefWindowProc](#defwindowproc)|提供默认消息处理。|  
|[GetCurrentMessage](#getcurrentmessage)|返回当前消息。|  
|[GetWindowProc](#getwindowproc)|返回当前窗口过程。|  
|[OnFinalMessage](#onfinalmessage)|接收最后一条消息后调用（通常为 `WM_NCDESTROY`）。|  
|[SubclassWindow](#subclasswindow)|对窗口子类化。|  
|[UnsubclassWindow](#unsubclasswindow)|还原先前子类化的窗口。|  
  
### <a name="static-methods"></a>静态方法  
  
|||  
|-|-|  
|[GetWndClassInfo](#getwndclassinfo)|返回的静态实例[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)，后者管理窗口类信息。|  
|[WindowProc](#windowproc)|处理发送到窗口的消息。|  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|指向窗口类的原始窗口过程。|  
  
## <a name="remarks"></a>备注  
 您可以使用`CWindowImpl`以现有的窗口，创建一个窗口或子类。 `CWindowImpl`窗口过程使用消息映射来将消息定向到相应的处理程序。  
  
 `CWindowImpl::Create`创建一个基于由管理的窗口类信息的窗口[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)。 `CWindowImpl`包含[DECLARE_WND_CLASS](http://msdn.microsoft.com/library/55247a72-fb9e-4bde-87f3-747c08076971)宏，这意味着`CWndClassInfo`注册新的窗口类。 如果希望超类现有窗口类，派生您的类从`CWindowImpl`并且包括[DECLARE_WND_SUPERCLASS](http://msdn.microsoft.com/library/650337b6-4973-41e5-8c36-55f90327bdcd)宏。 在这种情况下，`CWndClassInfo` 将注册基于现有类的窗口类，但使用 `CWindowImpl::WindowProc`。 例如:   
  
 [!code-cpp[NVC_ATL_Windowing #&43;](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]  
  
> [!NOTE]
>  由于 `CWndClassInfo` 只管理一个窗口类的信息，所以通过 `CWindowImpl` 实例创建的每个窗口都基于同一个窗口类。  
  
 `CWindowImpl` 还支持窗口子类化。 `SubclassWindow` 方法将现有的窗口附加到 `CWindowImpl` 对象并将窗口过程更改为 `CWindowImpl::WindowProc`。 `CWindowImpl` 的每个实例可以子类化其他窗口。  
  
> [!NOTE]
>  对于任何给定`CWindowImpl`对象，请调用**创建**或`SubclassWindow`。 不要对同一对象调用两种方法。  
  
 除了`CWindowImpl`，ATL 还提供[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)若要创建一个窗口，其中包含在另一个对象。  
  
 基类析构函数 (~ **CWindowImplRoot**) 可确保窗口消失之前该对象被销毁。  
  
 `CWindowImpl`派生自**CWindowImplBaseT**，它派生自**CWindowImplRoot**，它派生自**TBase**和[CMessageMap](../../atl/reference/cmessagemap-class.md)。  
  
|有关以下内容的详细信息|请参阅|  
|--------------------------------|---------|  
|创建控件|[ATL 教程](../../atl/active-template-library-atl-tutorial.md)|  
|使用 ATL 中的窗口|[ATL 窗口类](../../atl/atl-window-classes.md)|  
|ATL 项目向导|[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CMessageMap](../../atl/reference/cmessagemap-class.md)  
  
 `TBase`  
  
 `CWindowImplRoot`  
  
 `CWindowImplBaseT`  
  
 `CWindowImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlwin.h  
  
##  <a name="a-namecreatea--cwindowimplcreate"></a><a name="create"></a>CWindowImpl::Create  
 创建基于新的窗口类的窗口。  
  
```
HWND Create(
    HWND hWndParent,
    _U_RECT rect = NULL,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```  
  
### <a name="parameters"></a>参数  
 `hWndParent`  
 [in]父或所有者窗口的句柄。  
  
 `rect`  
 [in]一个[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它指定窗口的位置。 `RECT`可以通过指针还是通过引用传递。  
  
 `szWindowName`  
 [in]指定的窗口的名称。 默认值是**NULL**。  
  
 `dwStyle`  
 [in]窗口的样式。 此值结合所提供的特征类的窗口样式。 默认值为特征提供了类样式的完全控制。 有关可能的值的列表，请参阅[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwExStyle`  
 [in]扩展的窗口样式。 此值结合所提供的特征类的窗口样式。 默认值为特征提供了类样式的完全控制。 有关可能的值的列表，请参阅[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `MenuOrID`  
 [in]子窗口，窗口标识符。 对于顶级窗口，窗口的菜单句柄。 默认值是**0U**。  
  
 `lpCreateParam`  
 [in]指向窗口创建数据的指针。 完整说明，请参见到最后一个参数的说明[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)。  
  
### <a name="return-value"></a>返回值  
 如果成功，新创建的窗口的句柄。 否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 **创建**第一次注册窗口类，如果尚未注册。 新创建的窗口会自动附加到`CWindowImpl`对象。  
  
> [!NOTE]
>  不要调用**创建**如果您调用了[SubclassWindow](#subclasswindow)。  
  
 若要使用的窗口类，基于现有窗口类，派生您的类从`CWindowImpl`并且包括[DECLARE_WND_SUPERCLASS](http://msdn.microsoft.com/library/650337b6-4973-41e5-8c36-55f90327bdcd)宏。 现有窗口类的窗口过程将保存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。 有关详细信息，请参阅[CWindowImpl](../../atl/reference/cwindowimpl-class.md)概述。  
  
> [!NOTE]
>  如果为的值使用 0`MenuOrID`参数，则必须指定为 0U （默认值） 以避免编译器错误。  
  
##  <a name="a-namedefwindowproca--cwindowimpldefwindowproc"></a><a name="defwindowproc"></a>CWindowImpl::DefWindowProc  
 由调用[WindowProc](#windowproc)未处理的消息映射处理这些消息。  
  
```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
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
  
 不带参数的函数会自动从当前消息检索所需的参数。  
  
##  <a name="a-namegetcurrentmessagea--cwindowimplgetcurrentmessage"></a><a name="getcurrentmessage"></a>CWindowImpl::GetCurrentMessage  
 返回当前消息，打包在`MSG`结构。  
  
```
const MSG* GetCurrentMessage();
```  
  
### <a name="return-value"></a>返回值  
 当前消息。  
  
##  <a name="a-namegetwindowproca--cwindowimplgetwindowproc"></a><a name="getwindowproc"></a>CWindowImpl::GetWindowProc  
 返回`WindowProc`，当前窗口过程。  
  
```
virtual WNDPROC GetWindowProc();
```  
  
### <a name="return-value"></a>返回值  
 当前的窗口过程。  
  
### <a name="remarks"></a>备注  
 重写此方法，以替换为您自己的窗口过程。  
  
##  <a name="a-namegetwndclassinfoa--cwindowimplgetwndclassinfo"></a><a name="getwndclassinfo"></a>CWindowImpl::GetWndClassInfo  
 由调用[创建](#create)若要访问的窗口类信息。  
  
```
static CWndClassInfo& GetWndClassInfo();
```  
  
### <a name="return-value"></a>返回值  
 一个静态实例[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)。  
  
### <a name="remarks"></a>备注  
 默认情况下，`CWindowImpl`将获取通过此方法[DECLARE_WND_CLASS](http://msdn.microsoft.com/library/55247a72-fb9e-4bde-87f3-747c08076971)宏，它指定新的窗口类。  
  
 为现有窗口类创建超类，派生您的类从`CWindowImpl`并且包括[DECLARE_WND_SUPERCLASS](http://msdn.microsoft.com/library/650337b6-4973-41e5-8c36-55f90327bdcd)宏来重写`GetWndClassInfo`。 有关详细信息，请参阅[CWindowImpl](../../atl/reference/cwindowimpl-class.md)概述。  
  
 除了使用`DECLARE_WND_CLASS`和`DECLARE_WND_SUPERCLASS`宏，可以重写`GetWndClassInfo`使用您自己的实现。  
  
##  <a name="a-namempfnsuperwindowproca--cwindowimplmpfnsuperwindowproc"></a><a name="m_pfnsuperwindowproc"></a>CWindowImpl::m_pfnSuperWindowProc  
 具体取决于窗口中，指向以下窗口过程之一。  
  
```
WNDPROC m_pfnSuperWindowProc;
```  
  
### <a name="remarks"></a>备注  
  
|窗口类型|窗口过程|  
|--------------------|----------------------|  
|一个窗口根据新的窗口类，可以通过指定[DECLARE_WND_CLASS](http://msdn.microsoft.com/library/55247a72-fb9e-4bde-87f3-747c08076971)宏。|[DefWindowProc](http://msdn.microsoft.com/library/windows/desktop/ms633572) Win32 函数。|  
|一个窗口根据的窗口类，还将修改现有的类，可以通过指定[DECLARE_WND_SUPERCLASS](http://msdn.microsoft.com/library/650337b6-4973-41e5-8c36-55f90327bdcd)宏。|现有窗口类的窗口过程。|  
|子类化的窗口。|子类化的窗口的原始窗口过程。|  
  
 [CWindowImpl::DefWindowProc](#defwindowproc)发送消息到窗口过程中保存的信息`m_pfnSuperWindowProc`。  
  
##  <a name="a-nameonfinalmessagea--cwindowimplonfinalmessage"></a><a name="onfinalmessage"></a>CWindowImpl::OnFinalMessage  
 接收最后一条消息后调用 (通常`WM_NCDESTROY`)。  
  
```
virtual void OnFinalMessage(HWND hWnd);
```  
  
### <a name="parameters"></a>参数  
 `hWnd`  
 [in]销毁窗口的句柄。  
  
### <a name="remarks"></a>备注  
 默认实现`OnFinalMessage`不起作用，但您可以覆盖此函数来销毁窗口之前处理清理。 如果您想要自动删除您的对象在窗口析构时，您可以调用`delete this;`在此函数。  
  
##  <a name="a-namesubclasswindowa--cwindowimplsubclasswindow"></a><a name="subclasswindow"></a>CWindowImpl::SubclassWindow  
 由窗口中标识的子类`hWnd`并将其附加到`CWindowImpl`对象。  
  
```
BOOL SubclassWindow(HWND hWnd);
```  
  
### <a name="parameters"></a>参数  
 `hWnd`  
 [in]正在子类化窗口的句柄。  
  
### <a name="return-value"></a>返回值  
 **TRUE**成功子类化; 否则为此窗口是否**FALSE**。  
  
### <a name="remarks"></a>备注  
 子类化的窗口现在使用[CWindowImpl::WindowProc](#windowproc)。 在中保存的原始窗口过程[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。  
  
> [!NOTE]
>  不要调用`SubclassWindow`如果您调用了[创建](#create)。  
  
##  <a name="a-nameunsubclasswindowa--cwindowimplunsubclasswindow"></a><a name="unsubclasswindow"></a>CWindowImpl::UnsubclassWindow  
 分离从子类化的窗口`CWindowImpl`对象，并还原原始窗口过程，以保存[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。  
  
```
HWND UnsubclassWindow();
```  
  
### <a name="return-value"></a>返回值  
 先前子类化窗口的句柄。  
  
##  <a name="a-namewindowproca--cwindowimplwindowproc"></a><a name="windowproc"></a>CWindowImpl::WindowProc  
 此静态函数实现的窗口过程。  
  
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
 `WindowProc`使用默认消息映射 (使用声明[BEGIN_MSG_MAP](http://msdn.microsoft.com/library/8bbb5af9-18b1-48c6-880e-166f599ee554)) 将消息定向到相应的处理程序。 如有必要，`WindowProc`调用[DefWindowProc](#defwindowproc)进行更多的消息处理。 如果未处理最后一条消息，`WindowProc`执行下列任务︰  
  
-   执行 unsubclassing unsubclassed 窗口中时。  
  
-   清除`m_hWnd`。  
  
-   调用[OnFinalMessage](#onfinalmessage)窗口被破坏之前。  
  
 您可以重写`WindowProc`提供另一种机制来处理消息。  
  
## <a name="see-also"></a>另请参阅  
 [BEGIN_MSG_MAP](http://msdn.microsoft.com/library/8bbb5af9-18b1-48c6-880e-166f599ee554)   
 [CComControl 类](../../atl/reference/ccomcontrol-class.md)   
 [类概述](../../atl/atl-class-overview.md)

