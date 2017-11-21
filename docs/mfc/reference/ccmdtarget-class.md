---
title: "CCmdTarget 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCmdTarget
- AFXWIN/CCmdTarget
- AFXWIN/CCmdTarget::CCmdTarget
- AFXWIN/CCmdTarget::BeginWaitCursor
- AFXWIN/CCmdTarget::DoOleVerb
- AFXWIN/CCmdTarget::EnableAutomation
- AFXWIN/CCmdTarget::EnableConnections
- AFXWIN/CCmdTarget::EnableTypeLib
- AFXWIN/CCmdTarget::EndWaitCursor
- AFXWIN/CCmdTarget::EnumOleVerbs
- AFXWIN/CCmdTarget::FromIDispatch
- AFXWIN/CCmdTarget::GetDispatchIID
- AFXWIN/CCmdTarget::GetIDispatch
- AFXWIN/CCmdTarget::GetTypeInfoCount
- AFXWIN/CCmdTarget::GetTypeInfoOfGuid
- AFXWIN/CCmdTarget::GetTypeLib
- AFXWIN/CCmdTarget::GetTypeLibCache
- AFXWIN/CCmdTarget::IsInvokeAllowed
- AFXWIN/CCmdTarget::IsResultExpected
- AFXWIN/CCmdTarget::OnCmdMsg
- AFXWIN/CCmdTarget::OnFinalRelease
- AFXWIN/CCmdTarget::RestoreWaitCursor
dev_langs: C++
helpviewer_keywords:
- CCmdTarget [MFC], CCmdTarget
- CCmdTarget [MFC], BeginWaitCursor
- CCmdTarget [MFC], DoOleVerb
- CCmdTarget [MFC], EnableAutomation
- CCmdTarget [MFC], EnableConnections
- CCmdTarget [MFC], EnableTypeLib
- CCmdTarget [MFC], EndWaitCursor
- CCmdTarget [MFC], EnumOleVerbs
- CCmdTarget [MFC], FromIDispatch
- CCmdTarget [MFC], GetDispatchIID
- CCmdTarget [MFC], GetIDispatch
- CCmdTarget [MFC], GetTypeInfoCount
- CCmdTarget [MFC], GetTypeInfoOfGuid
- CCmdTarget [MFC], GetTypeLib
- CCmdTarget [MFC], GetTypeLibCache
- CCmdTarget [MFC], IsInvokeAllowed
- CCmdTarget [MFC], IsResultExpected
- CCmdTarget [MFC], OnCmdMsg
- CCmdTarget [MFC], OnFinalRelease
- CCmdTarget [MFC], RestoreWaitCursor
ms.assetid: 8883b132-2057-4ce0-a5f2-88979f8f2b13
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: aaae01c2e63c152139694c9d723b6bde7febf9c6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="ccmdtarget-class"></a>CCmdTarget 类
Microsoft 基础类库消息映射体系结构的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class CCmdTarget : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CCmdTarget::CCmdTarget](#ccmdtarget)|构造 `CCmdTarget` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CCmdTarget::BeginWaitCursor](#beginwaitcursor)|显示为沙漏光标的光标。|  
|[CCmdTarget::DoOleVerb](#dooleverb)|导致要执行的 OLE 谓词所指定的操作。|  
|[CCmdTarget::EnableAutomation](#enableautomation)|允许的 OLE 自动化`CCmdTarget`对象。|  
|[CCmdTarget::EnableConnections](#enableconnections)|在连接点上实现事件激发。|  
|[CCmdTarget::EnableTypeLib](#enabletypelib)|启用对象的类型库。|  
|[CCmdTarget::EndWaitCursor](#endwaitcursor)|返回到以前的光标。|  
|[CCmdTarget::EnumOleVerbs](#enumoleverbs)|枚举的对象的 OLE 谓词。|  
|[CCmdTarget::FromIDispatch](#fromidispatch)|返回一个指向`CCmdTarget`与关联的对象`IDispatch`指针。|  
|[CCmdTarget::GetDispatchIID](#getdispatchiid)|获取主要的调度接口 id。|  
|[CCmdTarget::GetIDispatch](#getidispatch)|返回一个指向`IDispatch`与关联的对象`CCmdTarget`对象。|  
|[CCmdTarget::GetTypeInfoCount](#gettypeinfocount)|检索对象提供的类型信息接口的数量。|  
|[CCmdTarget::GetTypeInfoOfGuid](#gettypeinfoofguid)|检索与指定的 GUID 相对应的类型说明。|  
|[CCmdTarget::GetTypeLib](#gettypelib)|获取一个指针指向类型库。|  
|[CCmdTarget::GetTypeLibCache](#gettypelibcache)|获取类型库缓存。|  
|[CCmdTarget::IsInvokeAllowed](#isinvokeallowed)|启用自动化方法调用。|  
|[CCmdTarget::IsResultExpected](#isresultexpected)|返回非零，如果自动化函数应返回值。|  
|[CCmdTarget::OnCmdMsg](#oncmdmsg)|路由和调度命令消息。|  
|[Ccmdtarget:: Onfinalrelease](#onfinalrelease)|发布的最后一个 OLE 引用后清理。|  
|[CCmdTarget::RestoreWaitCursor](#restorewaitcursor)|还原沙漏光标。|  
  
## <a name="remarks"></a>备注  
 消息映射将命令或消息路由到你编写来处理它们的成员函数。 （命令是从菜单项、 命令按钮或快捷键一条消息。）  
  
 密钥 framework 类派生自`CCmdTarget`包括[CView](../../mfc/reference/cview-class.md)， [CWinApp](../../mfc/reference/cwinapp-class.md)， [CDocument](../../mfc/reference/cdocument-class.md)， [CWnd](../../mfc/reference/cwnd-class.md)，和[CFrameWnd](../../mfc/reference/cframewnd-class.md)。 如果你想为新类来处理消息，请从以下方法之一派生类`CCmdTarget`-派生类。 极少数情况下将派生的类从`CCmdTarget`直接。  
  
 有关命令目标的概述和`OnCmdMsg`路由，请参阅[命令目标](../../mfc/command-targets.md)，[命令路由](../../mfc/command-routing.md)，和[消息映射](../../mfc/mapping-messages.md)。  
  
 `CCmdTarget`包括处理沙漏光标的显示的成员函数。 当你需要的命令，以获得明显的时间间隔内执行，则显示沙漏光标。  
  
 调度映射，类似于消息映射，用于公开 OLE 自动化`IDispatch`功能。 通过公开此接口，你的应用程序可以调用其他应用程序 （如 Visual Basic 中)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CCmdTarget`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="beginwaitcursor"></a>CCmdTarget::BeginWaitCursor  
 调用此函数可显示为一个沙漏光标，当你需要的命令，以获得明显的时间间隔内执行。  
  
```  
void BeginWaitCursor();
```  
  
### <a name="remarks"></a>备注  
 框架调用此函数可向用户显示这是忙，例如，当**CDocument**对象加载或保存到文件本身。  
  
 操作`BeginWaitCursor`并不总是有效外部单个消息处理程序与其他操作，如`OnSetCursor`处理，无法更改的光标。  
  
 调用`EndWaitCursor`还原以前的光标。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
##  <a name="ccmdtarget"></a>CCmdTarget::CCmdTarget  
 构造 `CCmdTarget` 对象。  
  
```  
CCmdTarget();
```  
  
##  <a name="dooleverb"></a>CCmdTarget::DoOleVerb  
 导致要执行的 OLE 谓词所指定的操作。  
  
```  
BOOL DoOleVerb(
    LONG iVerb,  
    LPMSG lpMsg,  
    HWND hWndParent,  
    LPCRECT lpRect);
```  
  
### <a name="parameters"></a>参数  
 `iVerb`  
 该谓词的数字标识符。  
  
 `lpMsg`  
 指向[消息](http://msdn.microsoft.com/library/windows/desktop/ms644958)结构描述调用谓词 （如双击） 的事件。  
  
 `hWndParent`  
 包含该对象的文档窗口的句柄。  
  
 `lpRect`  
 指向[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它包含的坐标，以像素为单位，用于定义对象的边框中*hwndParent*。  
  
### <a name="return-value"></a>返回值  
 如果成功，否则为 FALSE，则为 TRUE。  
  
### <a name="remarks"></a>备注  
 此成员函数基本上是实现[IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508)。 可能的操作都用枚举[CCmdTarget::EnumOleVerbs](#enumoleverbs)。  
  
##  <a name="enableautomation"></a>CCmdTarget::EnableAutomation  
 调用此函数可启用 OLE 自动化对象。  
  
```  
void EnableAutomation();
```  
  
### <a name="remarks"></a>备注  
 此函数通常称为从你的对象的构造函数，并应只有当调度映射已声明的类调用。 自动化的详细信息请参阅文章[自动化客户端](../../mfc/automation-clients.md)和[自动化服务器](../../mfc/automation-servers.md)。  
  
##  <a name="enableconnections"></a>CCmdTarget::EnableConnections  
 在连接点上实现事件激发。  
  
```  
void EnableConnections();
```  
  
### <a name="remarks"></a>备注  
 若要启用连接点，请在派生类的构造函数中调用此成员函数。  
  
##  <a name="enabletypelib"></a>CCmdTarget::EnableTypeLib  
 启用对象的类型库。  
  
```  
void EnableTypeLib();
```  
  
### <a name="remarks"></a>备注  
 此成员函数调用的构造函数中你`CCmdTarget`-派生对象，如果它提供了类型信息。 有关详细信息，请参阅知识库文章 Q185720，"如何： 从 MFC 自动化服务器提供类型信息。" 知识库文章位于[http://support.microsoft.com](http://support.microsoft.com/)。  
  
##  <a name="endwaitcursor"></a>CCmdTarget::EndWaitCursor  
 调用此函数后你调用了`BeginWaitCursor`成员函数以将来自沙漏光标返回到以前的光标。  
  
```  
void EndWaitCursor();
```  
  
### <a name="remarks"></a>备注  
 该维度被称为沙漏光标后，框架还会调用此成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
##  <a name="enumoleverbs"></a>CCmdTarget::EnumOleVerbs  
 枚举的对象的 OLE 谓词。  
  
```  
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```  
  
### <a name="parameters"></a>参数  
 `ppenumOleVerb`  
 指针到指向[IEnumOLEVERB](http://msdn.microsoft.com/library/windows/desktop/ms695084)接口。  
  
### <a name="return-value"></a>返回值  
 如果对象支持 OLE 的至少一个谓词，则返回 TRUE (在这种情况下\*`ppenumOleVerb`指向**IEnumOLEVERB**枚举器接口)，否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 此成员函数基本上是实现[ioleobject:: Enumverbs](http://msdn.microsoft.com/library/windows/desktop/ms692781)。  
  
##  <a name="fromidispatch"></a>CCmdTarget::FromIDispatch  
 调用此函数可映射`IDispatch`指针，从自动化成员函数的类，接收到进入`CCmdTarget`实现的接口的对象`IDispatch`对象。  
  
```  
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```  
  
### <a name="parameters"></a>参数  
 `lpDispatch`  
 指向 `IDispatch` 对象的指针。  
  
### <a name="return-value"></a>返回值  
 指向的指针`CCmdTarget`与关联的对象`lpDispatch`。 此函数将返回**NULL**如果`IDispatch`对象不被识别为 Microsoft 基础类`IDispatch`对象。  
  
### <a name="remarks"></a>备注  
 此函数的结果是指向成员函数的调用的反向`GetIDispatch`。  
  
##  <a name="getdispatchiid"></a>CCmdTarget::GetDispatchIID  
 获取主要的调度接口 id。  
  
```  
virtual BOOL GetDispatchIID(IID* pIID);
```  
  
### <a name="parameters"></a>参数  
 *pIID*  
 指向接口 ID 的指针 ( [GUID](http://msdn.microsoft.com/library/windows/desktop/aa373931))。  
  
### <a name="return-value"></a>返回值  
 如果成功，否则为 FALSE，则为 TRUE。 如果成功， \* *pIID*设置为主要的调度接口 id。  
  
### <a name="remarks"></a>备注  
 派生的类应重写该成员函数 (如果未重写，`GetDispatchIID`返回 FALSE)。 请参阅[COleControl](../../mfc/reference/colecontrol-class.md)。  
  
 有关详细信息，请参阅知识库文章 Q185720，"如何： 从 MFC 自动化服务器提供类型信息。" 知识库文章位于[http://support.microsoft.com](http://support.microsoft.com/)。  
  
##  <a name="getidispatch"></a>CCmdTarget::GetIDispatch  
 调用此成员函数可检索`IDispatch`指针从自动化方法的其中一个返回`IDispatch`指针或采用`IDispatch`通过引用的指针。  
  
```  
LPDISPATCH GetIDispatch(BOOL bAddRef);
```  
  
### <a name="parameters"></a>参数  
 *bAddRef*  
 指定是否递增的对象的引用计数。  
  
### <a name="return-value"></a>返回值  
 `IDispatch`与对象关联的指针。  
  
### <a name="remarks"></a>备注  
 有关对象该调用`EnableAutomation`在其构造函数，使其自动化启用，此函数返回一个指向的基础类实现`IDispatch`由客户端都通过通信`IDispatch`接口。 自动调用此函数将引用添加到指针，因此不需要调用[iunknown:: Addref](http://msdn.microsoft.com/library/windows/desktop/ms691379)。  
  
##  <a name="gettypeinfocount"></a>CCmdTarget::GetTypeInfoCount  
 检索对象提供的类型信息接口的数量。  
  
```  
virtual UINT GetTypeInfoCount();
```  
  
### <a name="return-value"></a>返回值  
 类型信息接口的数量。  
  
### <a name="remarks"></a>备注  
 此成员函数基本上实现[IDispatch::GetTypeInfoCount](http://msdn.microsoft.com/en-us/da876d53-cb8a-465c-a43e-c0eb272e2a12)。  
  
 派生的类应重写此函数可返回的类型信息接口提供 （0 或 1） 的数量。 如果未重写， **GetTypeInfoCount**返回 0。 若要重写，使用[IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)宏，还实现`GetTypeLib`和`GetTypeLibCache`。  
  
##  <a name="gettypeinfoofguid"></a>CCmdTarget::GetTypeInfoOfGuid  
 检索与指定的 GUID 相对应的类型说明。  
  
```  
HRESULT GetTypeInfoOfGuid(
    LCID lcid,  
    const GUID& guid,  
    LPTYPEINFO* ppTypeInfo);
```  
  
### <a name="parameters"></a>参数  
 `lcid`  
 区域设置标识符 ( `LCID`)。  
  
 `guid`  
 [GUID](http://msdn.microsoft.com/library/windows/desktop/aa373931)的类型说明。  
  
 `ppTypeInfo`  
 指针到指向`ITypeInfo`接口。  
  
### <a name="return-value"></a>返回值  
 HRESULT，指示调用成功与否。 如果成功，*`ppTypeInfo`指向类型信息接口。  
  
##  <a name="gettypelib"></a>CCmdTarget::GetTypeLib  
 获取一个指针指向类型库。  
  
```  
virtual HRESULT GetTypeLib(
    LCID lcid,  
    LPTYPELIB* ppTypeLib);
```  
  
### <a name="parameters"></a>参数  
 `lcid`  
 区域设置标识符 ( `LCID`)。  
  
 `ppTypeLib`  
 指针到指向`ITypeLib`接口。  
  
### <a name="return-value"></a>返回值  
 HRESULT，指示调用成功与否。 如果成功，*`ppTypeLib`指向类型库接口。  
  
### <a name="remarks"></a>备注  
 派生的类应重写该成员函数 (如果未重写，`GetTypeLib`返回 TYPE_E_CANTLOADLIBRARY)。 使用[IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)宏，还实现`GetTypeInfoCount`和`GetTypeLibCache`。  
  
##  <a name="gettypelibcache"></a>CCmdTarget::GetTypeLibCache  
 获取类型库缓存。  
  
```  
virtual CTypeLibCache* GetTypeLibCache();
```  
  
### <a name="return-value"></a>返回值  
 指向的指针**CTypeLibCache**对象。  
  
### <a name="remarks"></a>备注  
 派生的类应重写该成员函数 (如果未重写， **GetTypeLibCache**返回 NULL)。 使用[IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)宏，还实现`GetTypeInfoCount`和`GetTypeLib`。  
  
##  <a name="isinvokeallowed"></a>CCmdTarget::IsInvokeAllowed  
 MFC 的实现调用此函数**idispatch:: Invoke**以确定给定的自动化方法 (由标识`dispid`) 可以调用。  
  
```  
virtual BOOL IsInvokeAllowed(DISPID dispid);
```  
  
### <a name="parameters"></a>参数  
 `dispid`  
 调度 id。  
  
### <a name="return-value"></a>返回值  
 如果该方法可以调用，否则为 FALSE，则为 TRUE。  
  
### <a name="remarks"></a>备注  
 如果`IsInvokeAllowed`，则返回 TRUE， **Invoke**继续调用该方法中; 否则为`Invoke`将失败，返回 E_UNEXPECTED。  
  
 派生的类可以重写此函数可返回适当的值 (如果未重写， `IsInvokeAllowed` ，则返回 TRUE)。 请参阅尤其[COleControl::IsInvokeAllowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed)。  
  
##  <a name="isresultexpected"></a>CCmdTarget::IsResultExpected  
 使用`IsResultExpected`来确定客户端是否接受来自其调用自动化函数的返回值。  
  
```  
BOOL IsResultExpected();
```  
  
### <a name="return-value"></a>返回值  
 如果自动化函数应返回一个值; 如果非零否则为 0。  
  
### <a name="remarks"></a>备注  
 OLE 接口提供有关客户端是否使用或忽略的函数调用，结果到 MFC 的信息和 MFC 反过来使用此信息来确定对的调用结果`IsResultExpected`。 如果返回值的生产时间-或-占用大量资源，你可以通过计算返回的值之前调用此函数来提高效率。  
  
 仅在客户端，以便将与其他自动化函数获取有效的返回值，如果你从调用它们自动化函数，已调用后，此函数将返回 0。  
  
 `IsResultExpected`如果不进行的自动化函数调用时调用，则返回非零值。  
  
##  <a name="oncmdmsg"></a>CCmdTarget::OnCmdMsg  
 由框架调用以路由和调度命令消息并处理的命令用户界面对象的更新。  
  
```  
virtual BOOL OnCmdMsg(
    UINT nID,  
    int nCode,  
    void* pExtra,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 包含命令 id。  
  
 `nCode`  
 命令通知代码都标识。 请参阅**备注**值有关的详细信息`nCode`。  
  
 `pExtra`  
 使用的值根据`nCode`。 请参阅**备注**有关详细信息`pExtra`。  
  
 `pHandlerInfo`  
 如果不是**NULL**，`OnCmdMsg`填入**pTarget**和**pmf**的成员`pHandlerInfo`结构而不调度该命令。 通常情况下，此参数应**NULL**。  
  
### <a name="return-value"></a>返回值  
 处理此消息; 如果非零否则为 0。  
  
### <a name="remarks"></a>备注  
 这是框架命令体系结构的主要实现例程。  
  
 在运行时，`OnCmdMsg`调度对其他对象的命令或通过调用根类处理命令本身`CCmdTarget::OnCmdMsg`，后者执行实际的消息映射查找。 默认命令路由的完整说明，请参阅[消息处理和映射主题](../../mfc/message-handling-and-mapping.md)。  
  
 在少数情况下，你可能想要重写该成员函数以扩展框架的标准命令路由。 请参阅[技术说明 21](../../mfc/tn021-command-and-message-routing.md)命令路由体系结构的高级详细信息。  
  
 如果你重写`OnCmdMsg`，你必须提供的相应值`nCode`，命令通知代码，和`pExtra`，取决于值`nCode`。 下表列出其对应的值：  
  
|`nCode` 值|`pExtra` 值|  
|-------------------|--------------------|  
|CN_COMMAND|[CCmdUI](../../mfc/reference/ccmdui-class.md)*|  
|CN_EVENT|AFX_EVENT *|  
|CN_UPDATE_COMMAND_UI|CCmdUI *|  
|CN_OLECOMMAND|[COleCmdUI](../../mfc/reference/colecmdui-class.md)*|  
|CN_OLE_UNREGISTER|NULL|  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#44](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#45](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]  
  
##  <a name="onfinalrelease"></a>Ccmdtarget:: Onfinalrelease  
 发布到或从对象的最后一个 OLE 引用时，由框架调用。  
  
```  
virtual void OnFinalRelease();
```  
  
### <a name="remarks"></a>备注  
 重写此函数以这种情况下提供特殊处理。 默认实现将删除对象。  
  
##  <a name="restorewaitcursor"></a>CCmdTarget::RestoreWaitCursor  
 调用此函数可将相应的沙漏光标还原系统光标位置后已更改 （例如，在消息框中具有打开和关闭中间较长的操作后）。  
  
```  
void RestoreWaitCursor();
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 ACDUAL](../../visual-cpp-samples.md)   
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CCmdUI 类](../../mfc/reference/ccmdui-class.md)   
 [CDocument 类](../../mfc/reference/cdocument-class.md)   
 [CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)   
 [CWinApp 类](../../mfc/reference/cwinapp-class.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CView 类](../../mfc/reference/cview-class.md)   
 [CFrameWnd 类](../../mfc/reference/cframewnd-class.md)   
 [COleDispatchDriver 类](../../mfc/reference/coledispatchdriver-class.md)
