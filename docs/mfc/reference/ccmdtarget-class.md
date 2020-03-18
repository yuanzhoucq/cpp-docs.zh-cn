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
ms.openlocfilehash: 583b685295bf77910ef134776c1c4fa39baf93ad
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425999"
---
# <a name="ccmdtarget-class"></a>CCmdTarget 类

Microsoft 基础类库消息映射体系结构的基类。

## <a name="syntax"></a>语法

```
class CCmdTarget : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CCmdTarget：： CCmdTarget](#ccmdtarget)|构造 `CCmdTarget` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CCmdTarget：： BeginWaitCursor](#beginwaitcursor)|将光标显示为沙漏光标。|
|[CCmdTarget：:D oOleVerb](#dooleverb)|导致执行 OLE 谓词指定的操作。|
|[CCmdTarget：： EnableAutomation](#enableautomation)|允许 `CCmdTarget` 对象的 OLE 自动化。|
|[CCmdTarget：： EnableConnections](#enableconnections)|允许通过连接点触发事件。|
|[CCmdTarget：： EnableTypeLib](#enabletypelib)|启用对象的类型库。|
|[CCmdTarget：： EndWaitCursor](#endwaitcursor)|返回到上一个游标。|
|[CCmdTarget：： EnumOleVerbs](#enumoleverbs)|枚举对象的 OLE 谓词。|
|[CCmdTarget：： FromIDispatch](#fromidispatch)|返回一个指向与 `IDispatch` 指针关联的 `CCmdTarget` 对象的指针。|
|[CCmdTarget：： GetDispatchIID](#getdispatchiid)|获取主调度接口 ID。|
|[CCmdTarget：： GetIDispatch](#getidispatch)|返回一个指向与 `CCmdTarget` 对象关联的 `IDispatch` 对象的指针。|
|[CCmdTarget：： GetTypeInfoCount](#gettypeinfocount)|检索对象提供的类型信息接口的数量。|
|[CCmdTarget：： GetTypeInfoOfGuid](#gettypeinfoofguid)|检索与指定的 GUID 相对应的类型说明。|
|[CCmdTarget：： GetTypeLib](#gettypelib)|获取指向类型库的指针。|
|[CCmdTarget：： GetTypeLibCache](#gettypelibcache)|获取类型库缓存。|
|[CCmdTarget：： IsInvokeAllowed](#isinvokeallowed)|启用自动化方法调用。|
|[CCmdTarget：： IsResultExpected](#isresultexpected)|如果自动化函数应返回值，则返回非零值。|
|[CCmdTarget：： OnCmdMsg](#oncmdmsg)|路由和调度命令消息。|
|[CCmdTarget：： OnFinalRelease](#onfinalrelease)|在最后一次 OLE 引用发布后进行清理。|
|[CCmdTarget：： RestoreWaitCursor](#restorewaitcursor)|还原沙漏光标。|

## <a name="remarks"></a>备注

消息映射将命令或消息路由到你编写的用于处理它们的成员函数。 （命令是来自菜单项、命令按钮或快捷键的消息。）

派生自 `CCmdTarget` 的关键框架类包括[CView](../../mfc/reference/cview-class.md)、 [CWinApp](../../mfc/reference/cwinapp-class.md)、 [CDocument](../../mfc/reference/cdocument-class.md)、 [CWnd](../../mfc/reference/cwnd-class.md)和[CFrameWnd](../../mfc/reference/cframewnd-class.md)。 如果打算使用新类来处理消息，请从这些 `CCmdTarget`派生类之一派生类。 很少会直接从 `CCmdTarget` 派生类。

有关命令目标和 `OnCmdMsg` 路由的概述，请参阅[命令目标](../../mfc/command-targets.md)、[命令路由](../../mfc/command-routing.md)和[映射消息](../../mfc/mapping-messages.md)。

`CCmdTarget` 包含处理沙漏光标显示的成员函数。 如果希望命令采取明显的时间间隔来执行，则显示沙漏光标。

调度映射与消息映射类似，用于公开 OLE 自动化 `IDispatch` 功能。 通过公开此接口，其他应用程序（如 Visual Basic）可以调入您的应用程序。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CCmdTarget`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="beginwaitcursor"></a>CCmdTarget：： BeginWaitCursor

调用此函数可在希望命令采取明显时间间隔时将光标显示为沙漏。

```
void BeginWaitCursor();
```

### <a name="remarks"></a>备注

框架调用此函数以显示用户处于繁忙状态，例如，当 `CDocument` 对象将自身加载或保存到文件时。

`BeginWaitCursor` 的操作并非始终在单个消息处理程序的外部有效，因为其他操作（如 `OnSetCursor` 处理）可能会更改游标。

调用 `EndWaitCursor` 以还原上一个游标。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

##  <a name="ccmdtarget"></a>CCmdTarget：： CCmdTarget

构造 `CCmdTarget` 对象。

```
CCmdTarget();
```

##  <a name="dooleverb"></a>CCmdTarget：:D oOleVerb

导致执行 OLE 谓词指定的操作。

```
BOOL DoOleVerb(
    LONG iVerb,
    LPMSG lpMsg,
    HWND hWndParent,
    LPCRECT lpRect);
```

### <a name="parameters"></a>parameters

*iVerb*<br/>
谓词的数值标识符。

*lpMsg*<br/>
一个指针，它指向说明调用谓词的事件（如双击）的[消息](/windows/win32/api/winuser/ns-winuser-msg)结构。

*hWndParent*<br/>
包含该对象的文档窗口的句柄。

*lpRect*<br/>
指向[矩形](/previous-versions/dd162897\(v=vs.85\))结构的指针，该结构包含在*hwndParent*中定义对象的边框的坐标（以像素为单位）。

### <a name="return-value"></a>返回值

如果成功，则为 TRUE; 否则为 FALSE。

### <a name="remarks"></a>备注

此成员函数基本上是 IOleObject 的一个实现[：:D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb)。 可能的操作由[CCmdTarget：： EnumOleVerbs](#enumoleverbs)枚举。

##  <a name="enableautomation"></a>CCmdTarget：： EnableAutomation

调用此函数可为对象启用 OLE 自动化。

```
void EnableAutomation();
```

### <a name="remarks"></a>备注

此函数通常从对象的构造函数调用，只应在为类声明了调度映射的情况下才调用。 有关自动化的详细信息，请参阅文章[自动化客户端](../../mfc/automation-clients.md)和[自动化服务器](../../mfc/automation-servers.md)。

##  <a name="enableconnections"></a>CCmdTarget：： EnableConnections

允许通过连接点触发事件。

```
void EnableConnections();
```

### <a name="remarks"></a>备注

若要启用连接点，请在派生类的构造函数中调用此成员函数。

##  <a name="enabletypelib"></a>CCmdTarget：： EnableTypeLib

启用对象的类型库。

```
void EnableTypeLib();
```

### <a name="remarks"></a>备注

如果此成员函数提供类型信息，则在 `CCmdTarget`派生对象的构造函数中调用此成员函数。

##  <a name="endwaitcursor"></a>CCmdTarget：： EndWaitCursor

在调用了从沙漏光标返回到上一个游标的 `BeginWaitCursor` 成员函数后，调用此函数。

```
void EndWaitCursor();
```

### <a name="remarks"></a>备注

框架还在调用沙漏光标后调用此成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

##  <a name="enumoleverbs"></a>CCmdTarget：： EnumOleVerbs

枚举对象的 OLE 谓词。

```
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```

### <a name="parameters"></a>parameters

*ppenumOleVerb*<br/>
指向指向[IEnumOLEVERB](/windows/win32/api/oleidl/nn-oleidl-ienumoleverb)接口的指针的指针。

### <a name="return-value"></a>返回值

如果对象至少支持一个 OLE 谓词（在这种情况下 \* *ppenumOleVerb*指向 `IEnumOLEVERB` 枚举器接口），则为 TRUE; 否则为 FALSE。

### <a name="remarks"></a>备注

此成员函数基本上是[IOleObject：： EnumVerbs](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs)的实现。

##  <a name="fromidispatch"></a>CCmdTarget：： FromIDispatch

调用此函数可将从类的 automation 成员函数接收的 `IDispatch` 指针映射到实现 `IDispatch` 对象接口的 `CCmdTarget` 对象中。

```
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```

### <a name="parameters"></a>parameters

*lpDispatch*<br/>
指向 `IDispatch` 对象的指针。

### <a name="return-value"></a>返回值

指向与*lpDispatch*关联的 `CCmdTarget` 对象的指针。 如果 `IDispatch` 对象未被识别为 Microsoft 基础类 `IDispatch` 对象，则此函数将返回 NULL。

### <a name="remarks"></a>备注

此函数的结果是对成员函数的调用的反向 `GetIDispatch`。

##  <a name="getdispatchiid"></a>CCmdTarget：： GetDispatchIID

获取主调度接口 ID。

```
virtual BOOL GetDispatchIID(IID* pIID);
```

### <a name="parameters"></a>parameters

*pIID*<br/>
指向接口 ID 的指针（ [GUID](/previous-versions/cc317743(v%3dmsdn.10))。

### <a name="return-value"></a>返回值

如果成功，则为 TRUE; 否则为 FALSE。 如果成功，则将 \* *pIID*设置为主调度接口 ID。

### <a name="remarks"></a>备注

派生类应重写此成员函数（如果未重写，`GetDispatchIID` 返回 FALSE）。 请参阅[COleControl](../../mfc/reference/colecontrol-class.md)。

##  <a name="getidispatch"></a>CCmdTarget：： GetIDispatch

调用此成员函数以从自动化方法检索 `IDispatch` 指针，该方法返回 `IDispatch` 指针或按引用使用 `IDispatch` 指针。

```
LPDISPATCH GetIDispatch(BOOL bAddRef);
```

### <a name="parameters"></a>parameters

*bAddRef*<br/>
指定是否递增对象的引用计数。

### <a name="return-value"></a>返回值

与对象关联的 `IDispatch` 指针。

### <a name="remarks"></a>备注

对于在其构造函数中调用 `EnableAutomation` 的对象，使其实现自动化，此函数返回一个指针，该指针指向通过 `IDispatch` 接口进行通信的客户端使用的 `IDispatch` 的基础类实现。 调用此函数会自动添加对指针的引用，因此不需要调用[IUnknown：： AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)。

##  <a name="gettypeinfocount"></a>CCmdTarget：： GetTypeInfoCount

检索对象提供的类型信息接口的数量。

```
virtual UINT GetTypeInfoCount();
```

### <a name="return-value"></a>返回值

类型信息接口的数量。

### <a name="remarks"></a>备注

此成员函数主要实现[IDispatch：： GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount)。

派生类应重写此函数以返回提供的类型信息接口的数量（0或1）。 如果未重写，`GetTypeInfoCount` 将返回0。 若要重写，请使用[IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)宏，该宏也实现 `GetTypeLib` 和 `GetTypeLibCache`。

##  <a name="gettypeinfoofguid"></a>CCmdTarget：： GetTypeInfoOfGuid

检索与指定的 GUID 相对应的类型说明。

```
HRESULT GetTypeInfoOfGuid(
    LCID lcid,
    const GUID& guid,
    LPTYPEINFO* ppTypeInfo);
```

### <a name="parameters"></a>parameters

*lcid*<br/>
区域设置标识符（`LCID`）。

*guid*<br/>
类型说明的[GUID](/previous-versions/cc317743(v%3dmsdn.10)) 。

*ppTypeInfo*<br/>
指向 `ITypeInfo` 接口的指针的指针。

### <a name="return-value"></a>返回值

一个 HRESULT，指示调用是成功还是失败。 如果成功，\* *ppTypeInfo*将指向类型信息接口。

##  <a name="gettypelib"></a>CCmdTarget：： GetTypeLib

获取指向类型库的指针。

```
virtual HRESULT GetTypeLib(
    LCID lcid,
    LPTYPELIB* ppTypeLib);
```

### <a name="parameters"></a>parameters

*lcid*<br/>
区域设置标识符 (LCID)。

*ppTypeLib*<br/>
指向指向 `ITypeLib` 接口的指针的指针。

### <a name="return-value"></a>返回值

一个 HRESULT，指示调用是成功还是失败。 如果成功，\* *ppTypeLib*指向类型库接口。

### <a name="remarks"></a>备注

派生类应重写此成员函数（如果未重写，`GetTypeLib` 返回 TYPE_E_CANTLOADLIBRARY）。 使用[IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)宏，该宏还实现 `GetTypeInfoCount` 和 `GetTypeLibCache`。

##  <a name="gettypelibcache"></a>CCmdTarget：： GetTypeLibCache

获取类型库缓存。

```
virtual CTypeLibCache* GetTypeLibCache();
```

### <a name="return-value"></a>返回值

一个指向 `CTypeLibCache` 对象的指针。

### <a name="remarks"></a>备注

派生类应重写此成员函数（如果未重写，`GetTypeLibCache` 返回 NULL）。 使用[IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)宏，该宏还实现 `GetTypeInfoCount` 和 `GetTypeLib`。

##  <a name="isinvokeallowed"></a>CCmdTarget：： IsInvokeAllowed

此函数由 MFC 的 `IDispatch::Invoke` 实现调用，以确定是否可以调用给定的自动化方法（由*dispid*标识）。

```
virtual BOOL IsInvokeAllowed(DISPID dispid);
```

### <a name="parameters"></a>parameters

*dispid*<br/>
调度 ID。

### <a name="return-value"></a>返回值

如果可以调用方法，则为 TRUE; 否则为 FALSE。

### <a name="remarks"></a>备注

如果 `IsInvokeAllowed` 返回 TRUE，`Invoke` 继续调用方法;否则，`Invoke` 将失败，并返回 E_UNEXPECTED。

派生类可以重写此函数以返回适当的值（如果未重写，`IsInvokeAllowed` 返回 TRUE）。 请参阅特定[COleControl：： IsInvokeAllowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed)。

##  <a name="isresultexpected"></a>CCmdTarget：： IsResultExpected

使用 `IsResultExpected` 来确定客户端是否需要从其调用自动化函数的返回值。

```
BOOL IsResultExpected();
```

### <a name="return-value"></a>返回值

如果自动化函数应返回值，则为非零值;否则为0。

### <a name="remarks"></a>备注

OLE 接口向 MFC 提供有关客户端是使用还是忽略函数调用结果的信息，而 MFC 又会使用此信息来确定调用 `IsResultExpected`的结果。 如果生产返回值是需要耗费时间或消耗资源的，则可以在计算返回值之前调用此函数，从而提高效率。

此函数只返回一次0次，这样，如果从客户端调用的自动化函数调用它们，将从其他自动化函数获取有效的返回值。

如果未在自动化函数调用的过程中调用，`IsResultExpected` 将返回一个非零值。

##  <a name="oncmdmsg"></a>CCmdTarget：： OnCmdMsg

由框架调用以路由和调度命令消息，并处理命令用户界面对象的更新。

```
virtual BOOL OnCmdMsg(
    UINT nID,
    int nCode,
    void* pExtra,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>parameters

*nID*<br/>
包含命令 ID。

*nCode*<br/>
标识命令通知代码。 有关*nCode*的值的详细信息，请参阅**备注**。

*pExtra*<br/>
根据*nCode*的值使用。 有关*pExtra*的详细信息，请参阅 "**备注**"。

*pHandlerInfo*<br/>
如果不为 NULL，`OnCmdMsg` 将填充*pHandlerInfo*结构的*pTarget*和*pmf*成员，而不是分派命令。 通常，此参数应为 NULL。

### <a name="return-value"></a>返回值

如果处理消息，则为非零值;否则为0。

### <a name="remarks"></a>备注

这是框架命令体系结构的主要实现例程。

在运行时，`OnCmdMsg` 向其他对象调度一个命令，或通过调用根类 `CCmdTarget::OnCmdMsg`来处理命令本身，此类将执行实际的消息映射查找。 有关默认命令路由的完整说明，请参阅[消息处理和映射主题](../../mfc/message-handling-and-mapping.md)。

在极少数情况下，您可能希望重写此成员函数以扩展框架的标准命令路由。 有关命令路由体系结构的高级详细信息，请参阅[技术说明 21](../../mfc/tn021-command-and-message-routing.md) 。

如果重写 `OnCmdMsg`，则必须为*nCode*、命令通知代码和*pExtra*提供适当的值，具体取决于*nCode*的值。 下表列出了相应的值：

|*nCode*值|*pExtra*值|
|-------------------|--------------------|
|CN_COMMAND|[CCmdUI](../../mfc/reference/ccmdui-class.md)\*|
|CN_EVENT|AFX_EVENT\*|
|CN_UPDATE_COMMAND_UI|CCmdUI\*|
|CN_OLECOMMAND|[COleCmdUI](../../mfc/reference/colecmdui-class.md)\*|
|CN_OLE_UNREGISTER|Null|

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#44](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#45](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]

##  <a name="onfinalrelease"></a>CCmdTarget：： OnFinalRelease

当释放从对象到或的最后一个 OLE 引用时由框架调用。

```
virtual void OnFinalRelease();
```

### <a name="remarks"></a>备注

重写此函数以提供此情况的特殊处理。 默认实现将删除该对象。

##  <a name="restorewaitcursor"></a>CCmdTarget：： RestoreWaitCursor

调用此函数可在系统游标发生更改后（例如，在某一消息框打开后关闭，并在漫长的操作过程中关闭）时还原适当的沙漏光标。

```
void RestoreWaitCursor();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 示例 ACDUAL](../../overview/visual-cpp-samples.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CCmdUI 类](../../mfc/reference/ccmdui-class.md)<br/>
[CDocument 类](../../mfc/reference/cdocument-class.md)<br/>
[CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)<br/>
[CWinApp 类](../../mfc/reference/cwinapp-class.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[CView 类](../../mfc/reference/cview-class.md)<br/>
[CFrameWnd 类](../../mfc/reference/cframewnd-class.md)<br/>
[COleDispatchDriver 类](../../mfc/reference/coledispatchdriver-class.md)
