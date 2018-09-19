---
title: CAtlExeModuleT 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT::CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT::InitializeCom
- ATLBASE/ATL::CAtlExeModuleT::ParseCommandLine
- ATLBASE/ATL::CAtlExeModuleT::PostMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::PreMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::RegisterClassObjects
- ATLBASE/ATL::CAtlExeModuleT::RevokeClassObjects
- ATLBASE/ATL::CAtlExeModuleT::Run
- ATLBASE/ATL::CAtlExeModuleT::RunMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::UninitializeCom
- ATLBASE/ATL::CAtlExeModuleT::Unlock
- ATLBASE/ATL::CAtlExeModuleT::WinMain
- ATLBASE/ATL::CAtlExeModuleT::m_bDelayShutdown
- ATLBASE/ATL::CAtlExeModuleT::m_dwPause
- ATLBASE/ATL::CAtlExeModuleT::m_dwTimeOut
dev_langs:
- C++
helpviewer_keywords:
- CAtlExeModuleT class
ms.assetid: 82245f3d-91d4-44fa-aa86-7cc7fbd758d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b9b19888f6eae3efe7baf4429ec1174432f99a10
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118552"
---
# <a name="catlexemodulet-class"></a>CAtlExeModuleT 类

此类表示应用程序的模块。

## <a name="syntax"></a>语法

```
template <class T>
class ATL_NO_VTABLE CAtlExeModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类派生自`CAtlExeModuleT`。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAtlExeModuleT::CAtlExeModuleT](#catlexemodulet)|构造函数。|
|[CAtlExeModuleT:: ~ CAtlExeModuleT](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CAtlExeModuleT::InitializeCom](#initializecom)|初始化 com。|
|[CAtlExeModuleT::ParseCommandLine](#parsecommandline)|分析命令行，并根据需要执行注册。|
|[CAtlExeModuleT::PostMessageLoop](#postmessageloop)|消息循环退出后立即调用此方法。|
|[CAtlExeModuleT::PreMessageLoop](#premessageloop)|输入消息循环之前调用此方法。|
|[CAtlExeModuleT::RegisterClassObjects](#registerclassobjects)|注册类对象。|
|[CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects)|撤消类对象。|
|[CAtlExeModuleT::Run](#run)|此方法在初始化、 运行消息循环，该 EXE 模块中执行代码和清理。|
|[CAtlExeModuleT::RunMessageLoop](#runmessageloop)|此方法执行消息循环。|
|[CAtlExeModuleT::UninitializeCom](#uninitializecom)|取消初始化 com。|
|[CAtlExeModuleT::Unlock](#unlock)|模块的锁计数递减。|
|[CAtlExeModuleT::WinMain](#winmain)|此方法实现运行 EXE 所需的代码。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown)|指示应为延迟关闭该模块的标志。|
|[CAtlExeModuleT::m_dwPause](#m_dwpause)|暂停值，用于确保在关闭前发布所有对象。|
|[CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout)|使用要延迟模块卸载的超时值。|

## <a name="remarks"></a>备注

`CAtlExeModuleT` 表示应用程序 (EXE) 模块，并包含在退出支持创建 EXE、 处理命令行、 注册类对象、 运行消息循环和清理代码。

此类旨在不断地创建和销毁 EXE 服务器中的 COM 对象时提高性能。 该 EXE 释放最后一个的 COM 对象后，等待指定的持续时间[CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout)数据成员。 如果在此期间没有任何活动 （即，创建 COM 对象），启动关机进程。

[CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown)数据成员是标志，用于确定该 exe 文件应使用上面定义的机制。 如果设置为 false，该模块将立即终止。

在 ATL 中的模块的详细信息，请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlExeModuleT`

## <a name="requirements"></a>要求

**标头：** atlbase.h

##  <a name="catlexemodulet"></a>  CAtlExeModuleT::CAtlExeModuleT

构造函数。

```
CAtlExeModuleT() throw();
```

### <a name="remarks"></a>备注

如果无法初始化 EXE 模块，WinMain 将立即返回而不会进一步处理。

##  <a name="dtor"></a>  CAtlExeModuleT:: ~ CAtlExeModuleT

析构函数。

```
~CAtlExeModuleT() throw();
```

### <a name="remarks"></a>备注

释放所有已分配的资源。

##  <a name="initializecom"></a>  CAtlExeModuleT::InitializeCom

初始化 com。

```
static HRESULT InitializeCom() throw();
```

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

此方法从构造函数调用，并且可重写以不同于默认实现方式初始化 COM。 默认实现可以调用`CoInitializeEx(NULL, COINIT_MULTITHREADED)`或`CoInitialize(NULL)`具体取决于项目配置。

重写此方法通常需要重写[CAtlExeModuleT::UninitializeCom](#uninitializecom)。

##  <a name="m_bdelayshutdown"></a>  CAtlExeModuleT::m_bDelayShutdown

指示应为延迟关闭该模块的标志。

```
bool m_bDelayShutdown;
```

### <a name="remarks"></a>备注

请参阅[CAtlExeModuleT 概述](../../atl/reference/catlexemodulet-class.md)有关详细信息。

##  <a name="m_dwpause"></a>  CAtlExeModuleT::m_dwPause

用来确保所有对象都已关闭之前的暂停值。

```
DWORD m_dwPause;
```

### <a name="remarks"></a>备注

将此值更改之后调用[CAtlExeModuleT::InitializeCom](#initializecom)设置为关闭服务器用作暂停值的毫秒数。 默认值为 1000年毫秒。

##  <a name="m_dwtimeout"></a>  CAtlExeModuleT::m_dwTimeOut

使用要延迟模块卸载的超时值。

```
DWORD m_dwTimeOut;
```

### <a name="remarks"></a>备注

将此值更改之后调用[CAtlExeModuleT::InitializeCom](#initializecom)定义用作关闭服务器的超时值的毫秒数。 默认值为 5000 毫秒。 请参阅[CAtlExeModuleT 概述](../../atl/reference/catlexemodulet-class.md)的更多详细信息。

##  <a name="parsecommandline"></a>  CAtlExeModuleT::ParseCommandLine

分析命令行，并根据需要执行注册。

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>参数

*lpCmdLine*<br/>
命令行传递给应用程序。

*pnRetCode*<br/>
（如果发生） 与注册相对应的 HRESULT。

### <a name="return-value"></a>返回值

如果应用程序应继续运行，否则为 false 则返回 true。

### <a name="remarks"></a>备注

从中调用此方法[CAtlExeModuleT::WinMain](#winmain) ，可以重写以处理命令行开关。 默认实现可检查 **/RegServer**并 **/UnRegServer**命令行参数，并执行注册或注销。

##  <a name="postmessageloop"></a>  CAtlExeModuleT::PostMessageLoop

消息循环退出后立即调用此方法。

```
HRESULT PostMessageLoop() throw();
```

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

重写此方法以执行自定义应用程序的清理操作。 默认实现调用[CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects)。

##  <a name="premessageloop"></a>  CAtlExeModuleT::PreMessageLoop

输入消息循环之前调用此方法。

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>参数

*nShowCmd*<br/>
作为传递的值*nShowCmd* WinMain 中的参数。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

重写此方法以添加该应用程序的自定义初始化代码。 默认实现注册类对象。

##  <a name="registerclassobjects"></a>  CAtlExeModuleT::RegisterClassObjects

向 OLE 注册类对象，以便其他应用程序可以连接到它。

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>参数

*dwClsContext*<br/>
指定在其中运行的类对象的上下文。 可能的值为 CLSCTX_INPROC_SERVER、 CLSCTX_INPROC_HANDLER 或 CLSCTX_LOCAL_SERVER。

*dwFlags*<br/>
确定指向类对象的连接类型。 可能的值为 REGCLS_SINGLEUSE、 REGCLS_MULTIPLEUSE 或 REGCLS_MULTI_SEPARATE。

### <a name="return-value"></a>返回值

成功、 S_FALSE 没有任何类注册，则在失败的错误 HRESULT 返回 S_OK。

##  <a name="revokeclassobjects"></a>  CAtlExeModuleT::RevokeClassObjects

删除类的对象。

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>返回值

成功、 S_FALSE 没有任何类注册，则在失败的错误 HRESULT 返回 S_OK。

##  <a name="run"></a>  CAtlExeModuleT::Run

此方法在初始化、 运行消息循环，该 EXE 模块中执行代码和清理。

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>参数

*nShowCmd*<br/>
指定窗口的显示方式。 此参数可以是讨论中的值之一[WinMain](https://msdn.microsoft.com/library/windows/desktop/ms633559)部分。 默认值为 SW_HIDE。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

可以重写此方法。 但是，在实践中是它更好地重写[CAtlExeModuleT::PreMessageLoop](#premessageloop)， [CAtlExeModuleT::RunMessageLoop](#runmessageloop)，或[CAtlExeModuleT::PostMessageLoop](#postmessageloop)改为。

##  <a name="runmessageloop"></a>  CAtlExeModuleT::RunMessageLoop

此方法执行消息循环。

```
void RunMessageLoop() throw();
```

### <a name="remarks"></a>备注

可以重写此方法，若要更改的消息循环行为。

##  <a name="uninitializecom"></a>  CAtlExeModuleT::UninitializeCom

取消初始化 com。

```
static void UninitializeCom() throw();
```

### <a name="remarks"></a>备注

默认情况下此方法只是调用[CoUninitialize](/windows/desktop/api/combaseapi/nf-combaseapi-couninitialize)和从析构函数调用。 重写此方法，如果重写[CAtlExeModuleT::InitializeCom](#initializecom)。

##  <a name="unlock"></a>  CAtlExeModuleT::Unlock

模块的锁计数递减。

```
LONG Unlock() throw();
```

### <a name="return-value"></a>返回值

返回一个值，该值可能是有用的诊断或测试。

##  <a name="winmain"></a>  CAtlExeModuleT::WinMain

此方法实现运行 EXE 所需的代码。

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>参数

*nShowCmd*<br/>
指定窗口的显示方式。 此参数可以是讨论中的值之一[WinMain](https://msdn.microsoft.com/library/windows/desktop/ms633559)部分。

### <a name="return-value"></a>返回值

返回可执行文件的返回值。

### <a name="remarks"></a>备注

可以重写此方法。 如果重写[CAtlExeModuleT::PreMessageLoop](#premessageloop)， [CAtlExeModuleT::PostMessageLoop](#postmessageloop)，或[CAtlExeModuleT::RunMessageLoop](#runmessageloop)不具有足够的灵活性它是可以重写`WinMain`函数使用此方法。

## <a name="see-also"></a>请参阅

[ATLDuck 示例](../../visual-cpp-samples.md)<br/>
[CAtlModuleT 类](../../atl/reference/catlmodulet-class.md)<br/>
[CAtlDllModuleT 类](../../atl/reference/catldllmodulet-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
