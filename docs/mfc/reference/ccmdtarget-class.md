---
title: CCmdTarget 类
ms.date: 11/04/2016
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
ms.openlocfilehash: 5ee4101302322a5212a80b32f095cdd13d9769e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352290"
---
# <a name="ccmdtarget-class"></a>CCmdTarget 类

微软基础类库消息映射体系结构的基类。

## <a name="syntax"></a>语法

```
class CCmdTarget : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CmD目标：：CMD目标](#ccmdtarget)|构造 `CCmdTarget` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMD目标：：开始等待光标](#beginwaitcursor)|将光标显示为沙漏光标。|
|[CmdTarget：:DoOleVerb](#dooleverb)|导致执行由 OLE 谓词指定的操作。|
|[CmD目标：：启用自动化](#enableautomation)|允许`CCmdTarget`对象进行 OLE 自动化。|
|[CmD目标：：启用连接](#enableconnections)|启用在连接点上触发事件。|
|[CmD目标：：启用类型Lib](#enabletypelib)|启用对象的类型库。|
|[CmD目标：：结束等待光标](#endwaitcursor)|返回到上一个游标。|
|[Cmd目标：：枚举](#enumoleverbs)|枚举对象的 OLE 谓词。|
|[Cmd目标：：从I调度](#fromidispatch)|返回指向与`IDispatch`指针关联的`CCmdTarget`对象的指针。|
|[CmD目标：：获取调度IID](#getdispatchiid)|获取主调度接口 ID。|
|[CmD目标：：获取I调度](#getidispatch)|返回指向与`IDispatch``CCmdTarget`对象关联的对象的指针。|
|[CmD目标：：获取类型信息计数](#gettypeinfocount)|检索对象提供的类型信息接口的数量。|
|[Cmd目标：：获取信息](#gettypeinfoofguid)|检索与指定的 GUID 相对应的类型说明。|
|[CmD目标：：获取类型Lib](#gettypelib)|获取指向类型库的指针。|
|[CmD目标：：获取类型LibCache](#gettypelibcache)|获取类型库缓存。|
|[Cmd目标：：已调用](#isinvokeallowed)|启用自动化方法调用。|
|[Cmd目标：：预期结果](#isresultexpected)|如果自动化函数应返回值，则返回非零。|
|[CmD目标：：OnCmdMsg](#oncmdmsg)|路由和调度命令消息。|
|[Cmd目标：：最终发布](#onfinalrelease)|释放最后一个 OLE 参考后进行清理。|
|[Cmd目标：：恢复等待光标](#restorewaitcursor)|恢复沙漏光标。|

## <a name="remarks"></a>备注

消息映射将命令或消息路由到您编写处理这些命令或消息的成员函数。 （命令是来自菜单项、命令按钮或快捷键的消息。

`CCmdTarget`来自的关键框架类包括CView、CWinApp、CDocument、CWnd和[CFrameWnd。](../../mfc/reference/cframewnd-class.md) [CView](../../mfc/reference/cview-class.md) [CWinApp](../../mfc/reference/cwinapp-class.md) [CDocument](../../mfc/reference/cdocument-class.md) [CWnd](../../mfc/reference/cwnd-class.md) 如果希望新类处理消息，则从这些`CCmdTarget`派生类之一派生类。 您很少直接从`CCmdTarget`派生类。

有关`OnCmdMsg`命令目标和路由的概述，请参阅[命令目标](../../mfc/command-targets.md)、[命令路由](../../mfc/command-routing.md)和[映射消息](../../mfc/mapping-messages.md)。

`CCmdTarget`包括处理沙漏光标显示的成员函数。 当您希望命令需要一个明显的时间间隔执行时，显示沙漏光标。

调度映射类似于消息映射，用于公开 OLE 自动化`IDispatch`功能。 通过公开此接口，其他应用程序（如 Visual Basic）可以调用到应用程序中。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CCmdTarget`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="ccmdtargetbeginwaitcursor"></a><a name="beginwaitcursor"></a>CMD目标：：开始等待光标

调用此函数，当希望命令需要一个明显的时间间隔执行时，将光标显示为沙漏。

```
void BeginWaitCursor();
```

### <a name="remarks"></a>备注

框架调用此函数是为了向用户显示它正忙，例如当`CDocument`对象加载或保存到文件中时。

的操作`BeginWaitCursor`并不总是在单个消息处理程序之外有效，因为其他操作（如`OnSetCursor`处理）可能会更改游标。

调用`EndWaitCursor`以还原上一个游标。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="ccmdtargetccmdtarget"></a><a name="ccmdtarget"></a>CmD目标：：CMD目标

构造 `CCmdTarget` 对象。

```
CCmdTarget();
```

## <a name="ccmdtargetdooleverb"></a><a name="dooleverb"></a>CmdTarget：:DoOleVerb

导致执行由 OLE 谓词指定的操作。

```
BOOL DoOleVerb(
    LONG iVerb,
    LPMSG lpMsg,
    HWND hWndParent,
    LPCRECT lpRect);
```

### <a name="parameters"></a>参数

*iVerb*<br/>
动词的数值标识符。

*lpMsg*<br/>
指向描述调用谓词的事件（如双击）的[MSG](/windows/win32/api/winuser/ns-winuser-msg)结构的指针。

*hWnd 父母*<br/>
包含该对象的文档窗口的句柄。

*lpRect*<br/>
指向[RECT](/previous-versions/dd162897\(v=vs.85\))结构的指针，该结构以像素为单位定义对象的边界矩形，以*hwndParent*。

### <a name="return-value"></a>返回值

如果成功，则为 TRUE，否则为 FALSE。

### <a name="remarks"></a>备注

此成员函数基本上是[IOleObject：:DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb)） 的实现。 可能的操作由[CCmdTarget：：枚举EmeOleVerbs](#enumoleverbs)枚举。

## <a name="ccmdtargetenableautomation"></a><a name="enableautomation"></a>CmD目标：：启用自动化

调用此函数以启用对象的 OLE 自动化。

```
void EnableAutomation();
```

### <a name="remarks"></a>备注

此函数通常从对象的构造函数调用，并且仅当已声明类调度映射时才应调用。 有关自动化的详细信息，请参阅[文章"自动化客户端](../../mfc/automation-clients.md)"和["自动化服务器](../../mfc/automation-servers.md)"。

## <a name="ccmdtargetenableconnections"></a><a name="enableconnections"></a>CmD目标：：启用连接

启用在连接点上触发事件。

```
void EnableConnections();
```

### <a name="remarks"></a>备注

要启用连接点，请调用派生类的构造函数中的此成员函数。

## <a name="ccmdtargetenabletypelib"></a><a name="enabletypelib"></a>CmD目标：：启用类型Lib

启用对象的类型库。

```
void EnableTypeLib();
```

### <a name="remarks"></a>备注

如果`CCmdTarget`派生对象的构造函数提供类型信息，则调用此成员函数。

## <a name="ccmdtargetendwaitcursor"></a><a name="endwaitcursor"></a>CmD目标：：结束等待光标

调用`BeginWaitCursor`成员函数后调用此函数，以便从沙漏光标返回到上一个游标。

```
void EndWaitCursor();
```

### <a name="remarks"></a>备注

框架在调用沙漏光标后还会调用此成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="ccmdtargetenumoleverbs"></a><a name="enumoleverbs"></a>Cmd目标：：枚举

枚举对象的 OLE 谓词。

```
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```

### <a name="parameters"></a>参数

*佩纳姆奥勒Verb*<br/>
指向[IEnumOLEVERB 接口](/windows/win32/api/oleidl/nn-oleidl-ienumoleverb)的指针。

### <a name="return-value"></a>返回值

如果对象支持至少一个 OLE 谓词（在这种情况下\**，ppenOleVerb*指向`IEnumOLEVERB`枚举器接口），则为 TRUE，否则为 FALSE。

### <a name="remarks"></a>备注

此成员函数基本上是[IOleObject：：enumVerbs 的](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs)实现。

## <a name="ccmdtargetfromidispatch"></a><a name="fromidispatch"></a>Cmd目标：：从I调度

调用此函数将从类`IDispatch`的自动化成员函数接收的指针映射到实现`CCmdTarget``IDispatch`对象接口的对象中。

```
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```

### <a name="parameters"></a>参数

*lpDispatch*<br/>
指向 `IDispatch` 对象的指针。

### <a name="return-value"></a>返回值

指向与`CCmdTarget`*lpDispatch*关联的对象的指针。 如果对象未识别为`IDispatch`Microsoft 基础类`IDispatch`对象，则此功能将返回 NULL。

### <a name="remarks"></a>备注

此函数的结果是对成员函数的调用的相反。 `GetIDispatch`

## <a name="ccmdtargetgetdispatchiid"></a><a name="getdispatchiid"></a>CmD目标：：获取调度IID

获取主调度接口 ID。

```
virtual BOOL GetDispatchIID(IID* pIID);
```

### <a name="parameters"></a>参数

*pIID*<br/>
指向接口 ID [（GUID](/previous-versions/cc317743(v%3dmsdn.10))） 的指针。

### <a name="return-value"></a>返回值

如果成功，则为 TRUE，否则为 FALSE。 如果成功\**，pIID*将设置为主调度接口 ID。

### <a name="remarks"></a>备注

派生类应覆盖此成员函数（如果不重写，`GetDispatchIID`则返回 FALSE）。 请参阅[COleControl](../../mfc/reference/colecontrol-class.md)。

## <a name="ccmdtargetgetidispatch"></a><a name="getidispatch"></a>CmD目标：：获取I调度

调用此成员函数从返回`IDispatch``IDispatch`指针或通过引用获取`IDispatch`指针的自动化方法检索指针。

```
LPDISPATCH GetIDispatch(BOOL bAddRef);
```

### <a name="parameters"></a>参数

*bAddRef*<br/>
指定是否增加对象的引用计数。

### <a name="return-value"></a>返回值

与`IDispatch`对象关联的指针。

### <a name="remarks"></a>备注

对于在其构造函数`EnableAutomation`中调用的对象，使其启用自动化，此函数返回一个指针，指向通过`IDispatch``IDispatch`接口通信的客户端使用的基类实现。 调用此函数会自动添加对指针的引用，因此不必调用[IUnknown：：：AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)。

## <a name="ccmdtargetgettypeinfocount"></a><a name="gettypeinfocount"></a>CmD目标：：获取类型信息计数

检索对象提供的类型信息接口的数量。

```
virtual UINT GetTypeInfoCount();
```

### <a name="return-value"></a>返回值

类型信息接口的数量。

### <a name="remarks"></a>备注

此成员函数基本上实现了[IDispatch：getTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount)。

派生类应重写此函数以返回提供的类型信息接口数（0 或 1）。 如果未重写，`GetTypeInfoCount`则返回 0。 要重写，请使用[IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)宏，该宏还实现`GetTypeLib``GetTypeLibCache`和 。

## <a name="ccmdtargetgettypeinfoofguid"></a><a name="gettypeinfoofguid"></a>Cmd目标：：获取信息

检索与指定的 GUID 相对应的类型说明。

```
HRESULT GetTypeInfoOfGuid(
    LCID lcid,
    const GUID& guid,
    LPTYPEINFO* ppTypeInfo);
```

### <a name="parameters"></a>参数

*Lcid*<br/>
区域设置标识符 （ `LCID`。

*Guid*<br/>
类型描述的[GUID。](/previous-versions/cc317743(v%3dmsdn.10))

*ppTypeInfo*<br/>
指向接口的`ITypeInfo`指针。

### <a name="return-value"></a>返回值

指示呼叫成功或失败的 HRESULT。 如果成功\**，ppTypeInfo*将指向类型信息界面。

## <a name="ccmdtargetgettypelib"></a><a name="gettypelib"></a>CmD目标：：获取类型Lib

获取指向类型库的指针。

```
virtual HRESULT GetTypeLib(
    LCID lcid,
    LPTYPELIB* ppTypeLib);
```

### <a name="parameters"></a>参数

*Lcid*<br/>
区域设置标识符 (LCID)。

*ppTypeLib*<br/>
指向接口的`ITypeLib`指针。

### <a name="return-value"></a>返回值

指示呼叫成功或失败的 HRESULT。 如果成功\**，ppTypeLib*将指向类型库接口。

### <a name="remarks"></a>备注

派生类应覆盖此成员函数（如果不重写，`GetTypeLib`则返回TYPE_E_CANTLOADLIBRARY）。 使用[IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)宏，该宏还实现`GetTypeInfoCount``GetTypeLibCache`和 。

## <a name="ccmdtargetgettypelibcache"></a><a name="gettypelibcache"></a>CmD目标：：获取类型LibCache

获取类型库缓存。

```
virtual CTypeLibCache* GetTypeLibCache();
```

### <a name="return-value"></a>返回值

一个指向 `CTypeLibCache` 对象的指针。

### <a name="remarks"></a>备注

派生类应覆盖此成员函数（如果不重写，`GetTypeLibCache`则返回 NULL）。 使用[IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)宏，该宏还实现`GetTypeInfoCount``GetTypeLib`和 。

## <a name="ccmdtargetisinvokeallowed"></a><a name="isinvokeallowed"></a>Cmd目标：：已调用

MFC 的实现调用此函数`IDispatch::Invoke`，以确定是否可以调用给定的自动化方法（由*dispid*标识）。

```
virtual BOOL IsInvokeAllowed(DISPID dispid);
```

### <a name="parameters"></a>参数

*不一部分*<br/>
调度 ID。

### <a name="return-value"></a>返回值

如果可以调用该方法，则为 TRUE，否则为 FALSE。

### <a name="remarks"></a>备注

如果`IsInvokeAllowed`返回 TRUE，`Invoke`则继续调用 方法;如果返回 TRUE，则继续调用 方法。否则，`Invoke`将失败，返回E_UNEXPECTED。

派生类可以重写此函数以返回适当的值（如果不重写，`IsInvokeAllowed`则返回 TRUE）。 请特别参见[COleControl：是调用允许](../../mfc/reference/colecontrol-class.md#isinvokeallowed)的 。

## <a name="ccmdtargetisresultexpected"></a><a name="isresultexpected"></a>Cmd目标：：预期结果

用于`IsResultExpected`确定客户端是否期望从调用自动化函数返回值。

```
BOOL IsResultExpected();
```

### <a name="return-value"></a>返回值

如果自动化函数应返回值，则非零;否则 0。

### <a name="remarks"></a>备注

OLE 接口向 MFC 提供有关客户端是否正在使用或忽略函数调用结果的信息，而 MFC 则使用此信息来确定调用`IsResultExpected`的结果。 如果返回值的生产是时间或资源密集型，则可以在计算返回值之前调用此函数来提高效率。

此函数仅返回 0 一次，以便从客户端调用的自动化函数中调用它们，则从其他自动化函数中获取有效返回值。

`IsResultExpected`如果在自动化函数调用未进行时调用，则返回非零值。

## <a name="ccmdtargetoncmdmsg"></a><a name="oncmdmsg"></a>CmD目标：：OnCmdMsg

由框架调用以路由和调度命令消息，并处理命令用户界面对象的更新。

```
virtual BOOL OnCmdMsg(
    UINT nID,
    int nCode,
    void* pExtra,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>参数

*nID*<br/>
包含命令 ID。

*n代码*<br/>
标识命令通知代码。 有关*nCode*的值的详细信息，请参阅**备注**。

*pExtra*<br/>
根据*nCode*的值使用。 有关*pExtra*的更多信息，请参阅**备注**。

*pHandlerInfo*<br/>
如果不是 NULL，`OnCmdMsg`请填写*pHandlerInfo*结构的*pTarget*和*pmf*成员，而不是调度命令。 通常，此参数应为 NULL。

### <a name="return-value"></a>返回值

处理消息时非零;否则 0。

### <a name="remarks"></a>备注

这是框架命令体系结构的主要实现例程。

在运行时，`OnCmdMsg`将命令调度到其他对象，或者通过调用 root 类来处理命令本身，`CCmdTarget::OnCmdMsg`该类执行实际的消息映射查找。 有关默认命令路由的完整说明，请参阅[消息处理和映射主题](../../mfc/message-handling-and-mapping.md)。

在极少数情况下，您可能希望重写此成员函数以扩展框架的标准命令路由。 有关命令路由体系结构的高级详细信息，请参阅[技术说明 21。](../../mfc/tn021-command-and-message-routing.md)

`OnCmdMsg`如果重写 ，则必须提供*nCode、* 命令通知代码和*pExtra*的相应值，具体取决于*nCode*的值。 下表列出了其相应的值：

|*n代码*值|*p额外*值|
|-------------------|--------------------|
|CN_COMMAND|[CmDUI](../../mfc/reference/ccmdui-class.md)\*|
|CN_EVENT|AFX_EVENT\*|
|CN_UPDATE_COMMAND_UI|CCmdUI\*|
|CN_OLECOMMAND|[COleCmdUI](../../mfc/reference/colecmdui-class.md)\*|
|CN_OLE_UNREGISTER|Null|

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#44](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#45](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]

## <a name="ccmdtargetonfinalrelease"></a><a name="onfinalrelease"></a>Cmd目标：：最终发布

释放对象或对象的最后一个 OLE 引用时，由框架调用。

```
virtual void OnFinalRelease();
```

### <a name="remarks"></a>备注

重写此函数以为此情况提供特殊处理。 默认实现将删除该对象。

## <a name="ccmdtargetrestorewaitcursor"></a><a name="restorewaitcursor"></a>Cmd目标：：恢复等待光标

调用此函数以在系统光标更改后（例如，在长时间操作期间打开消息框然后关闭后）还原相应的沙漏光标。

```
void RestoreWaitCursor();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 样品 ACDUAL](../../overview/visual-cpp-samples.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CmDUI 类](../../mfc/reference/ccmdui-class.md)<br/>
[CDocument 类](../../mfc/reference/cdocument-class.md)<br/>
[CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)<br/>
[CWinApp 类](../../mfc/reference/cwinapp-class.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[CView 类](../../mfc/reference/cview-class.md)<br/>
[CFrameWnd 类](../../mfc/reference/cframewnd-class.md)<br/>
[COleDispatchDriver 类](../../mfc/reference/coledispatchdriver-class.md)
