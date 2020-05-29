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
ms.openlocfilehash: b678c8a46f56337d76ec192869449797a4f66fb3
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168783"
---
# <a name="catlexemodulet-class"></a>CAtlExeModuleT 类

此类表示应用程序的模块。

## <a name="syntax"></a>语法

```cpp
template <class T>
class ATL_NO_VTABLE CAtlExeModuleT : public CAtlModuleT<T>
```

### <a name="parameters"></a>参数

*T*<br/>
派生自`CAtlExeModuleT`的类。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[Catlexemodulet 用作：： Catlexemodulet 用作](#catlexemodulet)|构造函数。|
|[Catlexemodulet 用作：： ~ Catlexemodulet 用作](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[Catlexemodulet 用作：： InitializeCom](#initializecom)|初始化 COM。|
|[Catlexemodulet 用作：:P arseCommandLine](#parsecommandline)|分析命令行并在必要时执行注册。|
|[Catlexemodulet 用作：:P ostMessageLoop](#postmessageloop)|消息循环退出后，立即调用此方法。|
|[Catlexemodulet 用作：:P reMessageLoop](#premessageloop)|此方法将在进入消息循环前立即调用。|
|[Catlexemodulet 用作：： RegisterClassObjects](#registerclassobjects)|注册类对象。|
|[Catlexemodulet 用作：： RevokeClassObjects](#revokeclassobjects)|撤消类对象。|
|[Catlexemodulet 用作：： Run](#run)|此方法执行 EXE 模块中的代码以初始化、运行消息循环，并进行清理。|
|[Catlexemodulet 用作：： RunMessageLoop](#runmessageloop)|此方法执行消息循环。|
|[Catlexemodulet 用作：： UninitializeCom](#uninitializecom)|取消 COM。|
|[Catlexemodulet 用作：： Unlock](#unlock)|减小模块的锁计数。|
|[Catlexemodulet 用作：： WinMain](#winmain)|此方法实现运行 EXE 所需的代码。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[Catlexemodulet 用作：： m_bDelayShutdown](#m_bdelayshutdown)|一个标志，该标志指示应延迟关闭模块。|
|[Catlexemodulet 用作：： m_dwPause](#m_dwpause)|用于确保在关闭前释放所有对象的暂停值。|
|[Catlexemodulet 用作：： m_dwTimeOut](#m_dwtimeout)|用于延迟模块卸载的超时值。|

## <a name="remarks"></a>备注

`CAtlExeModuleT`表示应用程序的模块（EXE），其中包含支持创建 EXE、处理命令行、注册类对象、运行消息循环和在退出时清除的代码。

此类旨在提高 EXE 服务器中的 COM 对象不断创建和销毁时的性能。 在最后一个 COM 对象发布后，EXE 等待[catlexemodulet 用作：： m_dwTimeOut](#m_dwtimeout)数据成员指定的持续时间。 如果在此期间没有活动（即，未创建 COM 对象），则启动关闭进程。

[Catlexemodulet 用作：： m_bDelayShutdown](#m_bdelayshutdown)数据成员是一个标志，用于确定 EXE 是否应使用上面定义的机制。 如果将其设置为 false，则该模块将立即终止。

有关 ATL 中的模块的详细信息，请参阅[Atl Module 类](../../atl/atl-module-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlExeModuleT`

## <a name="requirements"></a>要求

**标头:** atlbase.h

## <a name="catlexemoduletcatlexemodulet"></a><a name="catlexemodulet"></a>Catlexemodulet 用作：： Catlexemodulet 用作

构造函数。

```cpp
CAtlExeModuleT() throw();
```

### <a name="remarks"></a>备注

如果无法初始化 EXE 模块，WinMain 将立即返回，无需进一步处理。

## <a name="catlexemoduletcatlexemodulet"></a><a name="dtor"></a>Catlexemodulet 用作：： ~ Catlexemodulet 用作

析构函数。

```cpp
~CAtlExeModuleT() throw();
```

### <a name="remarks"></a>备注

释放所有已分配的资源。

## <a name="catlexemoduletinitializecom"></a><a name="initializecom"></a>Catlexemodulet 用作：： InitializeCom

初始化 COM。

```cpp
static HRESULT InitializeCom() throw();
```

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

此方法是从构造函数调用的，可以重写，以不同于默认实现的方式初始化 COM。 默认实现将调用`CoInitializeEx(NULL, COINIT_MULTITHREADED)`或`CoInitialize(NULL)` ，具体取决于项目配置。

重写此方法通常需要重写[catlexemodulet 用作：： UninitializeCom](#uninitializecom)。

## <a name="catlexemoduletm_bdelayshutdown"></a><a name="m_bdelayshutdown"></a>Catlexemodulet 用作：： m_bDelayShutdown

一个标志，该标志指示应延迟关闭模块。

```cpp
bool m_bDelayShutdown;
```

### <a name="remarks"></a>备注

有关详细信息，请参阅[Catlexemodulet 用作概述](../../atl/reference/catlexemodulet-class.md)。

## <a name="catlexemoduletm_dwpause"></a><a name="m_dwpause"></a>Catlexemodulet 用作：： m_dwPause

用于确保所有对象在关闭之前都已消失的暂停值。

```cpp
DWORD m_dwPause;
```

### <a name="remarks"></a>备注

请在调用[catlexemodulet 用作：： InitializeCom](#initializecom)后更改此值，以设置用作关闭服务器的暂停值的毫秒数。 默认值为1000毫秒。

## <a name="catlexemoduletm_dwtimeout"></a><a name="m_dwtimeout"></a>Catlexemodulet 用作：： m_dwTimeOut

用于延迟模块卸载的超时值。

```cpp
DWORD m_dwTimeOut;
```

### <a name="remarks"></a>备注

请在调用[catlexemodulet 用作：： InitializeCom](#initializecom)后更改此值，以定义用作关闭服务器的超时值的毫秒数。 默认值为 5000 毫秒。 有关更多详细信息，请参阅[Catlexemodulet 用作概述](../../atl/reference/catlexemodulet-class.md)。

## <a name="catlexemoduletparsecommandline"></a><a name="parsecommandline"></a>Catlexemodulet 用作：:P arseCommandLine

分析命令行并在必要时执行注册。

```cpp
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>参数

*lpCmdLine*<br/>
传递给应用程序的命令行。

*pnRetCode*<br/>
与注册相对应的 HRESULT （如果已发生）。

### <a name="return-value"></a>返回值

如果应用程序应继续运行，则返回 true; 否则返回 false。

### <a name="remarks"></a>备注

此方法是从[catlexemodulet 用作：： WinMain](#winmain)调用的，可以重写此方法以处理命令行开关。 默认实现检查 **/RegServer**和 **/UnRegServer**命令行参数，并执行注册或注销。

## <a name="catlexemoduletpostmessageloop"></a><a name="postmessageloop"></a>Catlexemodulet 用作：:P ostMessageLoop

消息循环退出后，立即调用此方法。

```cpp
HRESULT PostMessageLoop() throw();
```

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

重写此方法以执行自定义应用程序清理。 默认实现将调用[catlexemodulet 用作：： RevokeClassObjects](#revokeclassobjects)。

## <a name="catlexemoduletpremessageloop"></a><a name="premessageloop"></a>Catlexemodulet 用作：:P reMessageLoop

此方法将在进入消息循环前立即调用。

```cpp
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>参数

*nShowCmd*<br/>
作为 WinMain 中的*nShowCmd*参数传递的值。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

重写此方法以添加应用程序的自定义初始化代码。 默认实现注册类对象。

## <a name="catlexemoduletregisterclassobjects"></a><a name="registerclassobjects"></a>Catlexemodulet 用作：： RegisterClassObjects

向 OLE 注册类对象，以便其他应用程序可以连接到它。

```cpp
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>参数

*dwClsContext*<br/>
指定要在其中运行类对象的上下文。 可能的值为 CLSCTX_INPROC_SERVER、CLSCTX_INPROC_HANDLER 或 CLSCTX_LOCAL_SERVER。

dwFlags**<br/>
确定类对象的连接类型。 可能的值为 REGCLS_SINGLEUSE、REGCLS_MULTIPLEUSE 或 REGCLS_MULTI_SEPARATE。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK，如果没有要注册的类，则返回 S_FALSE; 否则返回错误 HRESULT。

## <a name="catlexemoduletrevokeclassobjects"></a><a name="revokeclassobjects"></a>Catlexemodulet 用作：： RevokeClassObjects

删除类对象。

```cpp
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK，如果没有要注册的类，则返回 S_FALSE; 否则返回错误 HRESULT。

## <a name="catlexemoduletrun"></a><a name="run"></a>Catlexemodulet 用作：： Run

此方法执行 EXE 模块中的代码以初始化、运行消息循环，并进行清理。

```cpp
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>参数

*nShowCmd*<br/>
指定窗口的显示方式。 此参数可以是[WinMain](/windows/win32/api/winbase/nf-winbase-winmain)节中讨论的值之一。 默认为 SW_HIDE。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

可以重写此方法。 但实际上，更好的做法是替代[catlexemodulet 用作：:P remessageloop](#premessageloop)、 [Catlexemodulet 用作：： RunMessageLoop](#runmessageloop)或[catlexemodulet 用作：:P ostmessageloop](#postmessageloop) 。

## <a name="catlexemoduletrunmessageloop"></a><a name="runmessageloop"></a>Catlexemodulet 用作：： RunMessageLoop

此方法执行消息循环。

```cpp
void RunMessageLoop() throw();
```

### <a name="remarks"></a>备注

可以重写此方法以更改消息循环的行为。

## <a name="catlexemoduletuninitializecom"></a><a name="uninitializecom"></a>Catlexemodulet 用作：： UninitializeCom

取消 COM。

```cpp
static void UninitializeCom() throw();
```

### <a name="remarks"></a>备注

默认情况下，此方法只调用[CoUninitialize](/windows/win32/api/combaseapi/nf-combaseapi-couninitialize)并从析构函数调用。 如果重写[catlexemodulet 用作：： InitializeCom](#initializecom)，则重写此方法。

## <a name="catlexemoduletunlock"></a><a name="unlock"></a>Catlexemodulet 用作：： Unlock

减小模块的锁计数。

```cpp
LONG Unlock() throw();
```

### <a name="return-value"></a>返回值

返回一个值，该值对于诊断或测试可能很有用。

## <a name="catlexemoduletwinmain"></a><a name="winmain"></a>Catlexemodulet 用作：： WinMain

此方法实现运行 EXE 所需的代码。

```cpp
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>参数

*nShowCmd*<br/>
指定窗口的显示方式。 此参数可以是[WinMain](/windows/win32/api/winbase/nf-winbase-winmain)节中讨论的值之一。

### <a name="return-value"></a>返回值

返回可执行文件的返回值。

### <a name="remarks"></a>备注

可以重写此方法。 如果重写[catlexemodulet 用作：:P remessageloop](#premessageloop)， [Catlexemodulet 用作：:P ostmessageloop](#postmessageloop)或[catlexemodulet 用作：： RunMessageLoop](#runmessageloop)无法提供足够的灵活性，则可以使用此方法`WinMain`重写该函数。

## <a name="see-also"></a>另请参阅

[ATLDuck 示例](../../overview/visual-cpp-samples.md)<br/>
[CAtlModuleT 类](../../atl/reference/catlmodulet-class.md)<br/>
[CAtlDllModuleT 类](../../atl/reference/catldllmodulet-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
