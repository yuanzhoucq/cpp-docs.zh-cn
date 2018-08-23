---
title: CCmdTarget 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b6630ad9721b7a58e7da2660337660cc7916db01
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/16/2018
ms.locfileid: "42539211"
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
|[CCmdTarget::DoOleVerb](#dooleverb)|使指定的 OLE 谓词，要执行的操作。|  
|[CCmdTarget::EnableAutomation](#enableautomation)|允许的 OLE 自动化`CCmdTarget`对象。|  
|[CCmdTarget::EnableConnections](#enableconnections)|支持通过连接点事件触发。|  
|[CCmdTarget::EnableTypeLib](#enabletypelib)|启用对象的类型库。|  
|[CCmdTarget::EndWaitCursor](#endwaitcursor)|返回到上一个游标。|  
|[CCmdTarget::EnumOleVerbs](#enumoleverbs)|枚举对象的 OLE 谓词。|  
|[CCmdTarget::FromIDispatch](#fromidispatch)|返回一个指向`CCmdTarget`对象与关联`IDispatch`指针。|  
|[CCmdTarget::GetDispatchIID](#getdispatchiid)|获取主调度接口 id。|  
|[CCmdTarget::GetIDispatch](#getidispatch)|返回一个指向`IDispatch`对象与关联`CCmdTarget`对象。|  
|[CCmdTarget::GetTypeInfoCount](#gettypeinfocount)|检索对象提供的类型信息接口的数量。|  
|[CCmdTarget::GetTypeInfoOfGuid](#gettypeinfoofguid)|检索与指定的 GUID 相对应的类型说明。|  
|[CCmdTarget::GetTypeLib](#gettypelib)|获取一个指针指向的类型库。|  
|[CCmdTarget::GetTypeLibCache](#gettypelibcache)|获取类型库缓存。|  
|[CCmdTarget::IsInvokeAllowed](#isinvokeallowed)|启用自动化方法调用。|  
|[CCmdTarget::IsResultExpected](#isresultexpected)|返回非零，如果自动化函数应返回一个值。|  
|[CCmdTarget::OnCmdMsg](#oncmdmsg)|路由和调度命令消息。|  
|[Ccmdtarget:: Onfinalrelease](#onfinalrelease)|发布的最后一个 OLE 引用后清理。|  
|[CCmdTarget::RestoreWaitCursor](#restorewaitcursor)|还原沙漏光标。|  
  
## <a name="remarks"></a>备注  
 消息映射将命令或消息路由到您编写来处理它们的成员函数。 （一个命令是来自菜单项、 命令按钮或加速键的消息。）  
  
 密钥框架类派生自`CCmdTarget`包括[CView](../../mfc/reference/cview-class.md)， [CWinApp](../../mfc/reference/cwinapp-class.md)， [CDocument](../../mfc/reference/cdocument-class.md)， [CWnd](../../mfc/reference/cwnd-class.md)，和[CFrameWnd](../../mfc/reference/cframewnd-class.md)。 如果你想要处理的消息为新类，其中一种从派生类`CCmdTarget`-派生的类。 你将很少从派生类`CCmdTarget`直接。  
  
 有关命令目标的概述和`OnCmdMsg`路由，请参阅[命令目标](../../mfc/command-targets.md)，[命令路由](../../mfc/command-routing.md)，并且[消息映射](../../mfc/mapping-messages.md)。  
  
 `CCmdTarget` 包括处理的沙漏光标显示的成员函数。 预期采用一个明显的时间间隔来执行的命令时，将显示沙漏光标。  
  
 调度映射，类似于消息映射，用于公开 OLE 自动化`IDispatch`功能。 通过公开此接口，您的应用程序可以调用其他应用程序 （如 Visual Basic 中)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CCmdTarget`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="beginwaitcursor"></a>  CCmdTarget::BeginWaitCursor  
 调用此函数可显示为一个沙漏光标，要得到命令，以获得一个明显的时间间隔来执行。  
  
```  
void BeginWaitCursor();
```  
  
### <a name="remarks"></a>备注  
 框架调用此函数可向用户显示它处于繁忙状态，例如何时`CDocument`对象加载或保存到文件本身。  
  
 操作`BeginWaitCursor`并不总是有效之外的单个消息处理程序与其他操作，如`OnSetCursor`处理时，可能会更改游标。  
  
 调用`EndWaitCursor`还原上一个游标。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
##  <a name="ccmdtarget"></a>  CCmdTarget::CCmdTarget  
 构造 `CCmdTarget` 对象。  
  
```  
CCmdTarget();
```  
  
##  <a name="dooleverb"></a>  CCmdTarget::DoOleVerb  
 使指定的 OLE 谓词，要执行的操作。  
  
```  
BOOL DoOleVerb(
    LONG iVerb,  
    LPMSG lpMsg,  
    HWND hWndParent,  
    LPCRECT lpRect);
```  
  
### <a name="parameters"></a>参数  
 *iVerb*  
 该谓词的数字标识符。  
  
 *lpMsg*  
 指向[MSG](http://msdn.microsoft.com/library/windows/desktop/ms644958)结构描述调用此谓词的事件 （如双击）。  
  
 *hWndParent*  
 包含该对象的文档窗口的句柄。  
  
 *lpRect*  
 指向[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它包含的坐标，以像素为单位，用于定义对象的边界中的矩形*hwndParent*。  
  
### <a name="return-value"></a>返回值  
 如果成功，否则为 FALSE，则为 TRUE。  
  
### <a name="remarks"></a>备注  
 此成员函数基本上是实现[IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508)。 通过枚举可能的操作[CCmdTarget::EnumOleVerbs](#enumoleverbs)。  
  
##  <a name="enableautomation"></a>  CCmdTarget::EnableAutomation  
 调用此函数可启用 OLE 自动化对象。  
  
```  
void EnableAutomation();
```  
  
### <a name="remarks"></a>备注  
 此函数通常称为从您的对象的构造函数，如果已为类声明调度映射只应调用。 自动化的详细信息，请参阅文章[自动化客户端](../../mfc/automation-clients.md)并[自动化服务器](../../mfc/automation-servers.md)。  
  
##  <a name="enableconnections"></a>  CCmdTarget::EnableConnections  
 支持通过连接点事件触发。  
  
```  
void EnableConnections();
```  
  
### <a name="remarks"></a>备注  
 若要启用连接点，请在派生类的构造函数中调用此成员函数。  
  
##  <a name="enabletypelib"></a>  CCmdTarget::EnableTypeLib  
 启用对象的类型库。  
  
```  
void EnableTypeLib();
```  
  
### <a name="remarks"></a>备注  
 调用此成员函数的构造函数中你`CCmdTarget`-如果提供了类型信息派生的对象。 有关详细信息，请参阅知识库文章 Q185720，"如何： 从 MFC 自动化服务器提供类型信息。" 知识库文章位于[ http://support.microsoft.com ](http://support.microsoft.com/)。  
  
##  <a name="endwaitcursor"></a>  CCmdTarget::EndWaitCursor  
 已调用后调用此函数`BeginWaitCursor`成员函数以从沙漏光标返回到上一个游标。  
  
```  
void EndWaitCursor();
```  
  
### <a name="remarks"></a>备注  
 框架还调用此成员函数后它具有名为沙漏光标。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
##  <a name="enumoleverbs"></a>  CCmdTarget::EnumOleVerbs  
 枚举对象的 OLE 谓词。  
  
```  
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```  
  
### <a name="parameters"></a>参数  
 *ppenumOleVerb*  
 指针到指向[IEnumOLEVERB](http://msdn.microsoft.com/library/windows/desktop/ms695084)接口。  
  
### <a name="return-value"></a>返回值  
 如果对象支持至少一个 OLE 谓词，则返回 TRUE (在这种情况下\* *ppenumOleVerb*指向`IEnumOLEVERB`枚举数接口)，否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 此成员函数基本上是实现[ioleobject:: Enumverbs](http://msdn.microsoft.com/library/windows/desktop/ms692781)。  
  
##  <a name="fromidispatch"></a>  CCmdTarget::FromIDispatch  
 调用此函数可将映射`IDispatch`指针，从自动化成员函数的类，接收到`CCmdTarget`实现的接口的对象`IDispatch`对象。  
  
```  
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```  
  
### <a name="parameters"></a>参数  
 *lpDispatch*  
 指向 `IDispatch` 对象的指针。  
  
### <a name="return-value"></a>返回值  
 一个指向`CCmdTarget`对象与关联*lpDispatch*。 如果此函数将返回 NULL`IDispatch`对象未被识别为 Microsoft 基础类`IDispatch`对象。  
  
### <a name="remarks"></a>备注  
 此函数的结果就是对成员函数的调用`GetIDispatch`。  
  
##  <a name="getdispatchiid"></a>  CCmdTarget::GetDispatchIID  
 获取主调度接口 id。  
  
```  
virtual BOOL GetDispatchIID(IID* pIID);
```  
  
### <a name="parameters"></a>参数  
 *pIID*  
 一个指向接口 ID ( [GUID](http://msdn.microsoft.com/library/windows/desktop/aa373931))。  
  
### <a name="return-value"></a>返回值  
 如果成功，否则为 FALSE，则为 TRUE。 如果成功， \* *pIID*设置为主调度接口 id。  
  
### <a name="remarks"></a>备注  
 派生的类应重写此成员函数 (如果未重写，`GetDispatchIID`返回 FALSE)。 请参阅[COleControl](../../mfc/reference/colecontrol-class.md)。  
  
 有关详细信息，请参阅知识库文章 Q185720，"如何： 从 MFC 自动化服务器提供类型信息。" 知识库文章位于[ http://support.microsoft.com ](http://support.microsoft.com/)。  
  
##  <a name="getidispatch"></a>  CCmdTarget::GetIDispatch  
 调用此成员函数以检索`IDispatch`指针从自动化方法，或者返回`IDispatch`指针或采用`IDispatch`通过引用的指针。  
  
```  
LPDISPATCH GetIDispatch(BOOL bAddRef);
```  
  
### <a name="parameters"></a>参数  
 *bAddRef*  
 指定是否递增该对象的引用计数。  
  
### <a name="return-value"></a>返回值  
 `IDispatch`与对象关联的指针。  
  
### <a name="remarks"></a>备注  
 为对象调用`EnableAutomation`在其构造函数，使其自动化已启用，此函数返回一个指向的基础类实现`IDispatch`通过进行通信的客户端使用`IDispatch`接口。 自动调用此函数添加到指针的引用，因此不需要调用[iunknown:: Addref](http://msdn.microsoft.com/library/windows/desktop/ms691379)。  
  
##  <a name="gettypeinfocount"></a>  CCmdTarget::GetTypeInfoCount  
 检索对象提供的类型信息接口的数量。  
  
```  
virtual UINT GetTypeInfoCount();
```  
  
### <a name="return-value"></a>返回值  
 类型信息接口的数量。  
  
### <a name="remarks"></a>备注  
 此成员函数基本上可实现[IDispatch::GetTypeInfoCount](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfocount)。  
  
 派生的类应重写此函数可返回提供 （0 或 1） 的类型信息接口的数量。 如果未重写，`GetTypeInfoCount`返回 0。 若要重写，请使用[IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)宏，还可实现`GetTypeLib`和`GetTypeLibCache`。  
  
##  <a name="gettypeinfoofguid"></a>  CCmdTarget::GetTypeInfoOfGuid  
 检索与指定的 GUID 相对应的类型说明。  
  
```  
HRESULT GetTypeInfoOfGuid(
    LCID lcid,  
    const GUID& guid,  
    LPTYPEINFO* ppTypeInfo);
```  
  
### <a name="parameters"></a>参数  
 *lcid*  
 区域设置标识符 ( `LCID`)。  
  
 *guid*  
 [GUID](http://msdn.microsoft.com/library/windows/desktop/aa373931)的类型说明。  
  
 *ppTypeInfo*  
 指针到指向`ITypeInfo`接口。  
  
### <a name="return-value"></a>返回值  
 一个 HRESULT，指示调用成功与否。 如果成功， \* *ppTypeInfo*指向类型信息接口。  
  
##  <a name="gettypelib"></a>  CCmdTarget::GetTypeLib  
 获取一个指针指向的类型库。  
  
```  
virtual HRESULT GetTypeLib(
    LCID lcid,  
    LPTYPELIB* ppTypeLib);
```  
  
### <a name="parameters"></a>参数  
 *lcid*  
 区域设置标识符 (LCID)。  
  
 *ppTypeLib*  
 指针到指向`ITypeLib`接口。  
  
### <a name="return-value"></a>返回值  
 一个 HRESULT，指示调用成功与否。 如果成功， \* *ppTypeLib*指向类型库接口。  
  
### <a name="remarks"></a>备注  
 派生的类应重写此成员函数 (如果未重写，`GetTypeLib`返回 TYPE_E_CANTLOADLIBRARY)。 使用[IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)宏，还可实现`GetTypeInfoCount`和`GetTypeLibCache`。  
  
##  <a name="gettypelibcache"></a>  CCmdTarget::GetTypeLibCache  
 获取类型库缓存。  
  
```  
virtual CTypeLibCache* GetTypeLibCache();
```  
  
### <a name="return-value"></a>返回值  
 一个指向`CTypeLibCache`对象。  
  
### <a name="remarks"></a>备注  
 派生的类应重写此成员函数 (如果未重写，`GetTypeLibCache`返回 NULL)。 使用[IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)宏，还可实现`GetTypeInfoCount`和`GetTypeLib`。  
  
##  <a name="isinvokeallowed"></a>  CCmdTarget::IsInvokeAllowed  
 MFC 的实现调用此函数`IDispatch::Invoke`若要确定给定的自动化方法 (由标识*dispid*) 可以调用。  
  
```  
virtual BOOL IsInvokeAllowed(DISPID dispid);
```  
  
### <a name="parameters"></a>参数  
 *dispid*  
 调度 id。  
  
### <a name="return-value"></a>返回值  
 如果该方法可以调用，否则为 FALSE，则为 TRUE。  
  
### <a name="remarks"></a>备注  
 如果`IsInvokeAllowed`，则返回 TRUE，`Invoke`继续调用该方法; 否则为`Invoke`将失败并返回 E_UNEXPECTED。  
  
 派生的类可以重写此函数可返回适当的值 (如果未重写， `IsInvokeAllowed` ，则返回 TRUE)。 请参阅特别[COleControl::IsInvokeAllowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed)。  
  
##  <a name="isresultexpected"></a>  CCmdTarget::IsResultExpected  
 使用`IsResultExpected`来确定客户端是否期望来自其调用自动化函数的返回值。  
  
```  
BOOL IsResultExpected();
```  
  
### <a name="return-value"></a>返回值  
 如果自动化函数应返回一个值; 如果非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 OLE 接口提供有关客户端是否使用或忽略的函数调用结果信息到 MFC 和 MFC 又使用此信息以确定对的调用结果`IsResultExpected`。 如果返回值的生产时间-或-需要消耗大量资源，可以通过计算返回值之前调用此函数来提高效率。  
  
 仅在客户端，以便将从其他自动化函数获取有效的返回值，它们从调用自动化函数，如果已调用后，此函数将返回 0。  
  
 `IsResultExpected` 如果不进行自动化函数调用时调用，返回非零值。  
  
##  <a name="oncmdmsg"></a>  CCmdTarget::OnCmdMsg  
 由框架调用以路由和调度命令消息和处理命令用户界面对象的更新。  
  
```  
virtual BOOL OnCmdMsg(
    UINT nID,  
    int nCode,  
    void* pExtra,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>参数  
 *nID*  
 包含命令 id。  
  
 *nCode*  
 标识命令通知代码。 请参阅**备注**的值有关的详细信息*nCode*。  
  
 *pExtra*  
 使用的值根据*nCode*。 请参阅**备注**有关详细信息*pExtra*。  
  
 *pHandlerInfo*  
 如果不为 NULL，`OnCmdMsg`填入*pTarget*并*pmf*的成员*pHandlerInfo*而不是调度该命令的结构。 通常情况下，此参数应为 NULL。  
  
### <a name="return-value"></a>返回值  
 处理此消息; 如果非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 这是框架命令体系结构的主要实施例程。  
  
 在运行时，`OnCmdMsg`调度对其他对象的命令或通过调用根类来处理命令本身`CCmdTarget::OnCmdMsg`，它执行实际的消息映射查找。 默认命令路由的完整说明，请参阅[消息处理和映射主题](../../mfc/message-handling-and-mapping.md)。  
  
 在少数情况下，你可能想要重写此成员函数来扩展框架的标准命令路由。 请参阅[技术说明 21](../../mfc/tn021-command-and-message-routing.md)命令路由体系结构的高级详细信息。  
  
 如果重写`OnCmdMsg`，必须提供适当的值*nCode*，命令通知代码，并*pExtra*，这取决于值*nCode*. 下表列出了其对应的值：  
  
|*nCode*值|*pExtra*值|  
|-------------------|--------------------|  
|CN_COMMAND|[CCmdUI](../../mfc/reference/ccmdui-class.md)\*|  
|CN_EVENT|AFX_EVENT\*|  
|CN_UPDATE_COMMAND_UI|CCmdUI\*|  
|CN_OLECOMMAND|[COleCmdUI](../../mfc/reference/colecmdui-class.md)\*|  
|CN_OLE_UNREGISTER|NULL|  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#44](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#45](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]  
  
##  <a name="onfinalrelease"></a>  Ccmdtarget:: Onfinalrelease  
 发布到或从该对象的最后一个 OLE 引用时，由框架调用。  
  
```  
virtual void OnFinalRelease();
```  
  
### <a name="remarks"></a>备注  
 重写此函数以这种情况下提供特殊处理。 默认实现将删除对象。  
  
##  <a name="restorewaitcursor"></a>  CCmdTarget::RestoreWaitCursor  
 调用此函数可适当沙漏光标还原系统光标位置后已更改 （例如后一个消息框已打开并关闭中间较长的操作）。  
  
```  
void RestoreWaitCursor();
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 ACDUAL](../../visual-cpp-samples.md)   
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [CCmdUI 类](../../mfc/reference/ccmdui-class.md)   
 [CDocument 类](../../mfc/reference/cdocument-class.md)   
 [CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)   
 [CWinApp 类](../../mfc/reference/cwinapp-class.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CView 类](../../mfc/reference/cview-class.md)   
 [CFrameWnd 类](../../mfc/reference/cframewnd-class.md)   
 [COleDispatchDriver 类](../../mfc/reference/coledispatchdriver-class.md)
