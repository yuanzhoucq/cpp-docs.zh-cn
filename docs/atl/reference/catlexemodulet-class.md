---
title: CAtlExeModuleT 类
ms.date: 11/04/2016
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
helpviewer_keywords:
- CAtlExeModuleT class
ms.assetid: 82245f3d-91d4-44fa-aa86-7cc7fbd758d9
ms.openlocfilehash: a20a02a467d74a89e3cda176a6a15961be4ffd61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318986"
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
来自 的类`CAtlExeModuleT`派生自 。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CAtlExeModuleT：CAtlExeModuleT](#catlexemodulet)|构造函数。|
|[CAtlExeModuleT：_CAtlExeModuleT](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAtlExeModuleT：初始化Com](#initializecom)|初始化 COM。|
|[CAtlExeModuleT：:P](#parsecommandline)|分析命令行并在必要时执行注册。|
|[CAtlExeModuleT：:PostMessageLoop](#postmessageloop)|此方法在消息循环退出后立即调用。|
|[CAtlExeModuleT：:P重新消息循环](#premessageloop)|在输入消息循环之前立即调用此方法。|
|[CAtlExeModuleT：：注册类对象](#registerclassobjects)|注册类对象。|
|[CAtlExeModuleT：：撤销类对象](#revokeclassobjects)|撤消类对象。|
|[CAtlExeModuleT：：运行](#run)|此方法在 EXE 模块中执行代码以初始化、运行消息循环和清理。|
|[CAtlExeModuleT：：运行消息循环](#runmessageloop)|此方法执行消息循环。|
|[CAtlExeModuleT：取消初始化Com](#uninitializecom)|取消初始化 COM。|
|[CAtlExeModuleT：解锁](#unlock)|撤销模块的锁计数。|
|[CAtlExeModuleT：：赢主](#winmain)|此方法实现运行 EXE 所需的代码。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CAtlExeModuleT：m_bDelayShutdown](#m_bdelayshutdown)|指示关闭模块时应出现延迟的标志。|
|[CAtlExeModuleT：m_dwPause](#m_dwpause)|用于确保所有对象的暂停值在关机之前释放。|
|[CAtlExeModuleT：m_dwTimeOut](#m_dwtimeout)|用于延迟模块卸载的超时值。|

## <a name="remarks"></a>备注

`CAtlExeModuleT`表示应用程序 （EXE） 的模块，并包含支持创建 EXE、处理命令行、注册类对象、运行消息循环和在退出时清理的代码。

当不断创建和销毁 EXE 服务器中的 COM 对象时，此类旨在提高性能。 释放最后一个 COM 对象后，EXE 将等待[由 CAtlExeModuleT：：m_dwTimeOut](#m_dwtimeout)数据成员指定的持续时间。 如果在此期间没有活动（即未创建 COM 对象），则启动关闭过程。

[CAtlExeModuleT：：m_bDelayShutdown](#m_bdelayshutdown)数据成员是一个标志，用于确定 EXE 是否应使用上面定义的机制。 如果设置为 false，则模块将立即终止。

有关 ATL 中的模块的详细信息，请参阅[ATL 模块类](../../atl/atl-module-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlExeModuleT`

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="catlexemoduletcatlexemodulet"></a><a name="catlexemodulet"></a>CAtlExeModuleT：CAtlExeModuleT

构造函数。

```
CAtlExeModuleT() throw();
```

### <a name="remarks"></a>备注

如果 EXE 模块无法初始化，WinMain 将立即返回，无需进一步处理。

## <a name="catlexemoduletcatlexemodulet"></a><a name="dtor"></a>CAtlExeModuleT：_CAtlExeModuleT

析构函数。

```
~CAtlExeModuleT() throw();
```

### <a name="remarks"></a>备注

释放所有分配的资源。

## <a name="catlexemoduletinitializecom"></a><a name="initializecom"></a>CAtlExeModuleT：初始化Com

初始化 COM。

```
static HRESULT InitializeCom() throw();
```

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

此方法是从构造函数调用的，可以重写以不同于默认实现的方式初始化 COM。 默认实现调用`CoInitializeEx(NULL, COINIT_MULTITHREADED)`或`CoInitialize(NULL)`取决于项目配置。

重写此方法通常需要重写[CAtlExeModuleT：：取消初始化Com](#uninitializecom)。

## <a name="catlexemoduletm_bdelayshutdown"></a><a name="m_bdelayshutdown"></a>CAtlExeModuleT：m_bDelayShutdown

指示关闭模块时应出现延迟的标志。

```
bool m_bDelayShutdown;
```

### <a name="remarks"></a>备注

有关详细信息，请参阅[CAtlExeModuleT 概述](../../atl/reference/catlexemodulet-class.md)。

## <a name="catlexemoduletm_dwpause"></a><a name="m_dwpause"></a>CAtlExeModuleT：m_dwPause

用于确保所有对象在关机前消失的暂停值。

```
DWORD m_dwPause;
```

### <a name="remarks"></a>备注

在调用[CAtlExeModuleT：：初始化Com](#initializecom)后更改此值，以设置用作关闭服务器的暂停值的毫秒数。 默认值为 1000 毫秒。

## <a name="catlexemoduletm_dwtimeout"></a><a name="m_dwtimeout"></a>CAtlExeModuleT：m_dwTimeOut

用于延迟模块卸载的超时值。

```
DWORD m_dwTimeOut;
```

### <a name="remarks"></a>备注

在调用[CAtlExeModuleT：：初始化Com](#initializecom)后更改此值，以定义用作关闭服务器超时值的毫秒数。 默认值为 5000 毫秒。 有关详细信息，请参阅[CAtlExeModuleT 概述](../../atl/reference/catlexemodulet-class.md)。

## <a name="catlexemoduletparsecommandline"></a><a name="parsecommandline"></a>CAtlExeModuleT：:P

分析命令行并在必要时执行注册。

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>参数

*lpCmdline*<br/>
传递给应用程序的命令行。

*pnRet代码*<br/>
与注册对应的 HRESULT（如果发生）。

### <a name="return-value"></a>返回值

如果应用程序应继续运行，则返回 true，否则为 false。

### <a name="remarks"></a>备注

此方法从[CAtlExeModuleT 调用：winMain，](#winmain)可以重写以处理命令行交换机。 默认实现检查 **/RegServer**和 **/unRegServer**命令行参数，并执行注册或取消注册。

## <a name="catlexemoduletpostmessageloop"></a><a name="postmessageloop"></a>CAtlExeModuleT：:PostMessageLoop

此方法在消息循环退出后立即调用。

```
HRESULT PostMessageLoop() throw();
```

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

重写此方法以执行自定义应用程序清理。 默认实现调用[CAtlExemoduleT：：撤销类对象](#revokeclassobjects)。

## <a name="catlexemoduletpremessageloop"></a><a name="premessageloop"></a>CAtlExeModuleT：:P重新消息循环

在输入消息循环之前立即调用此方法。

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>参数

*nShowCmd*<br/>
在 WinMain 中作为*nShowCmd*参数传递的值。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

重写此方法以添加应用程序的自定义初始化代码。 默认实现注册类对象。

## <a name="catlexemoduletregisterclassobjects"></a><a name="registerclassobjects"></a>CAtlExeModuleT：：注册类对象

将类对象注册到 OLE，以便其他应用程序可以连接到它。

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>参数

*dwCls上下文*<br/>
指定要在其中运行类对象的上下文。 可能的值是CLSCTX_INPROC_SERVER、CLSCTX_INPROC_HANDLER或CLSCTX_LOCAL_SERVER。

dwFlags**<br/>
确定与类对象的连接类型。 可能的值是REGCLS_SINGLEUSE、REGCLS_MULTIPLEUSE 或REGCLS_MULTI_SEPARATE。

### <a name="return-value"></a>返回值

返回成功S_OK，S_FALSE如果没有要注册的类，或者失败时出现错误 HRESULT。

## <a name="catlexemoduletrevokeclassobjects"></a><a name="revokeclassobjects"></a>CAtlExeModuleT：：撤销类对象

删除类对象。

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>返回值

返回成功S_OK，S_FALSE如果没有要注册的类，或者失败时出现错误 HRESULT。

## <a name="catlexemoduletrun"></a><a name="run"></a>CAtlExeModuleT：：运行

此方法在 EXE 模块中执行代码以初始化、运行消息循环和清理。

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>参数

*nShowCmd*<br/>
指定窗口的显示方式。 此参数可以是[WinMain](/windows/win32/api/winbase/nf-winbase-winmain)部分中讨论的值之一。 默认值为SW_HIDE。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

可以重写此方法。 然而，在实践中，最好重写[CAtlExeModuleT：:P重新消息环](#premessageloop)[，CAtlExeModuleT：：RunMessageLoop，](#runmessageloop)或[CAtlExmoduleT：:PostMessageLoop。](#postmessageloop)

## <a name="catlexemoduletrunmessageloop"></a><a name="runmessageloop"></a>CAtlExeModuleT：：运行消息循环

此方法执行消息循环。

```
void RunMessageLoop() throw();
```

### <a name="remarks"></a>备注

可以重写此方法来更改消息循环的行为。

## <a name="catlexemoduletuninitializecom"></a><a name="uninitializecom"></a>CAtlExeModuleT：取消初始化Com

取消初始化 COM。

```
static void UninitializeCom() throw();
```

### <a name="remarks"></a>备注

默认情况下，此方法只需调用[CoUn初始化](/windows/win32/api/combaseapi/nf-combaseapi-couninitialize)，并从析构函数调用。 如果重写[CAtlExeModuleT：：初始化Com，](#initializecom)则重写此方法。

## <a name="catlexemoduletunlock"></a><a name="unlock"></a>CAtlExeModuleT：解锁

撤销模块的锁计数。

```
LONG Unlock() throw();
```

### <a name="return-value"></a>返回值

返回可用于诊断或测试的值。

## <a name="catlexemoduletwinmain"></a><a name="winmain"></a>CAtlExeModuleT：：赢主

此方法实现运行 EXE 所需的代码。

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>参数

*nShowCmd*<br/>
指定窗口的显示方式。 此参数可以是[WinMain](/windows/win32/api/winbase/nf-winbase-winmain)部分中讨论的值之一。

### <a name="return-value"></a>返回值

返回可执行文件的返回值。

### <a name="remarks"></a>备注

可以重写此方法。 如果重写[CAtlExeModuleT：:PreMessageLoop、CAtlExeModuleT：:PostMessageLoop）](#premessageloop)或[CAtlExeModuleT：：RunMessageLoop](#runmessageloop)不能提供足够的灵活性，则可以使用此方法重写`WinMain`函数。 [CAtlExeModuleT::PostMessageLoop](#postmessageloop)

## <a name="see-also"></a>另请参阅

[ATLDuck 样品](../../overview/visual-cpp-samples.md)<br/>
[CAtlModuleT 类](../../atl/reference/catlmodulet-class.md)<br/>
[CAtlDllModuleT 类](../../atl/reference/catldllmodulet-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
