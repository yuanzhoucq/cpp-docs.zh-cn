---
title: FtmBase 类
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase
- ftm/Microsoft::WRL::FtmBaseCreateGlobalInterfaceTable
- ftm/Microsoft::WRL::FtmBase::DisconnectObject
- ftm/Microsoft::WRL::FtmBase::FtmBase
- ftm/Microsoft::WRL::FtmBase::GetMarshalSizeMax
- ftm/Microsoft::WRL::FtmBase::GetUnmarshalClass
- ftm/Microsoft::WRL::FtmBase::MarshalInterface
- ftm/Microsoft::WRL::FtmBase::marshaller_
- ftm/Microsoft::WRL::FtmBase::ReleaseMarshalData
- ftm/Microsoft::WRL::FtmBase::UnmarshalInterface
helpviewer_keywords:
- Microsoft::WRL::FtmBase class
- Microsoft::WRL::FtmBase::CreateGlobalInterfaceTable method
- Microsoft::WRL::FtmBase::DisconnectObject method
- Microsoft::WRL::FtmBase::FtmBase, constructor
- Microsoft::WRL::FtmBase::GetMarshalSizeMax method
- Microsoft::WRL::FtmBase::GetUnmarshalClass method
- Microsoft::WRL::FtmBase::MarshalInterface method
- Microsoft::WRL::FtmBase::marshaller_ data member
- Microsoft::WRL::FtmBase::ReleaseMarshalData method
- Microsoft::WRL::FtmBase::UnmarshalInterface method
ms.assetid: 275f3b71-2975-4f92-89e7-d351e96496df
ms.openlocfilehash: f28a850c365bc9a75d8e5b100e5e5cc0a1c5dc10
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404559"
---
# <a name="ftmbase-class"></a>FtmBase 类

表示自由线程封送拆收器对象。

## <a name="syntax"></a>语法

```cpp
class FtmBase :
    public Microsoft::WRL::Implements<
        Microsoft::WRL::RuntimeClassFlags<WinRtClassicComMix>,
        Microsoft::WRL::CloakedIid<IMarshal>
    >;
```

## <a name="remarks"></a>备注

有关详细信息，请参阅[RuntimeClass 类](runtimeclass-class.md)。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

| 名称                         | 说明                                        |
| ---------------------------- | -------------------------------------------------- |
| [FtmBase：： FtmBase](#ftmbase) | 初始化 `FtmBase` 类的新实例。 |

### <a name="public-methods"></a>公共方法

| “属性”                                                               | 说明                                                                                                                                                          |
| ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [FtmBase：： CreateGlobalInterfaceTable](#createglobalinterfacetable) | 创建全局接口表（GIT）。                                                                                                                              |
| [FtmBase：:D isconnectObject](#disconnectobject)                     | 强制释放到对象的所有外部连接。 对象的服务器在关闭之前调用此方法的对象实现。                |
| [FtmBase：： GetMarshalSizeMax](#getmarshalsizemax)                   | 获取在指定的对象上封送指定接口指针所需的字节数的上限。                                                |
| [FtmBase：： GetUnmarshalClass](#getunmarshalclass)                   | 获取 COM 用于查找包含相应代理的代码的 DLL 的 CLSID。 COM 加载此 DLL 以创建代理的未初始化的实例。 |
| [FtmBase：： MarshalInterface](#marshalinterface)                     | 将在某个客户端进程中初始化代理对象所需的数据写入到流中。                                                                          |
| [FtmBase：： ReleaseMarshalData](#releasemarshaldata)                 | 销毁已封送的数据包。                                                                                                                                    |
| [FtmBase：： UnmarshalInterface](#unmarshalinterface)                 | 初始化新创建的代理并返回指向该代理的接口指针。                                                                                    |

### <a name="public-data-members"></a>公共数据成员

| 名称                                | 说明                                       |
| ----------------------------------- | ------------------------------------------------- |
| [FtmBase：： marshaller_](#marshaller) | 保留对自由线程封送拆收器的引用。 |

## <a name="inheritance-hierarchy"></a>继承层次结构

`FtmBase`

## <a name="requirements"></a>要求

**标头：** internal。h

**命名空间：** Microsoft::WRL

## <a name="ftmbasecreateglobalinterfacetable"></a><a name="createglobalinterfacetable"></a>FtmBase：： CreateGlobalInterfaceTable

创建全局接口表（GIT）。

```cpp
static HRESULT CreateGlobalInterfaceTable(
   __out IGlobalInterfaceTable **git
);
```

### <a name="parameters"></a>参数

*git*<br/>
此操作完成后，指向全局接口表的指针。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [`IGlobalInterfaceTable`](https://docs.microsoft.com/windows/win32/api/objidl/nn-objidl-iglobalinterfacetable)。

## <a name="ftmbasedisconnectobject"></a><a name="disconnectobject"></a>FtmBase：:D isconnectObject

强制释放到对象的所有外部连接。 对象的服务器在关闭之前调用此方法的对象实现。

```cpp
STDMETHODIMP DisconnectObject(
   __in DWORD dwReserved
) override;
```

### <a name="parameters"></a>参数

*dwReserved*<br/>
留待将来使用；必须为零。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="ftmbaseftmbase"></a><a name="ftmbase"></a>FtmBase：： FtmBase

初始化 `FtmBase` 类的新实例。

```cpp
FtmBase();
```

## <a name="ftmbasegetmarshalsizemax"></a><a name="getmarshalsizemax"></a>FtmBase：： GetMarshalSizeMax

获取在指定的对象上封送指定接口指针所需的字节数的上限。

```cpp
STDMETHODIMP GetMarshalSizeMax(
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags,
   __out DWORD *pSize
) override;
```

### <a name="parameters"></a>参数

*riid*<br/>
对要封送处理的接口的标识符的引用。

*函数*<br/>
要封送的接口指针;可以为 NULL。

*dwDestContext*<br/>
要取消封送的指定接口的目标上下文。

指定一个或多个 MSHCTX 枚举值。

目前，取消封送可能出现在当前进程的另一个单元中（MSHCTX_INPROC），或在与当前进程相同的计算机上的另一个进程中（MSHCTX_LOCAL）。

*pvDestContext*<br/>
保留以供将来使用;必须为 NULL。

*mshlflags*<br/>
一个标志，用于指示要封送的数据是否要传输回客户端进程（通常是典型情况）或写入到全局表中，这些数据可由多个客户端进行检索。 指定一个或多个 MSHLFLAGS 枚举值。

*pSize*<br/>
此操作完成后，指向要写入封送处理流的数据量的上限。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK;否则，E_FAIL 或 E_NOINTERFACE。

## <a name="ftmbasegetunmarshalclass"></a><a name="getunmarshalclass"></a>FtmBase：： GetUnmarshalClass

获取 COM 用于查找包含相应代理的代码的 DLL 的 CLSID。 COM 加载此 DLL 以创建代理的未初始化的实例。

```cpp
STDMETHODIMP GetUnmarshalClass(
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags,
   __out CLSID *pCid
) override;
```

### <a name="parameters"></a>参数

*riid*<br/>
对要封送处理的接口的标识符的引用。

*函数*<br/>
指向要封送的接口的指针;如果调用方没有指向所需接口的指针，则可以为 NULL。

*dwDestContext*<br/>
要取消封送的指定接口的目标上下文。

指定一个或多个 MSHCTX 枚举值。

在当前进程中的另一个单元（MSHCTX_INPROC）或在与当前进程相同的计算机上的另一个进程（MSHCTX_LOCAL）中，取消封送可能发生。

*pvDestContext*<br/>
保留以供将来使用;必须为 NULL。

*mshlflags*<br/>
此操作完成后，指向用于在客户端进程中创建代理的 CLSID 的指针。

*pCid*

### <a name="return-value"></a>返回值

如果成功，则为 S_OK;否则，S_FALSE。

## <a name="ftmbasemarshalinterface"></a><a name="marshalinterface"></a>FtmBase：： MarshalInterface

将在某个客户端进程中初始化代理对象所需的数据写入到流中。

```cpp
STDMETHODIMP MarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags
) override;
```

### <a name="parameters"></a>参数

*pStm*<br/>
一个指针，指向要在封送处理期间使用的流。

*riid*<br/>
对要封送处理的接口的标识符的引用。 此接口必须派生自 `IUnknown` 接口。

*函数*<br/>
指向要封送的接口指针的指针;如果调用方没有指向所需接口的指针，则可以为 NULL。

*dwDestContext*<br/>
要取消封送的指定接口的目标上下文。

指定一个或多个 MSHCTX 枚举值。

在当前进程中的另一个单元（MSHCTX_INPROC）或与当前进程（MSHCTX_LOCAL）相同的计算机上的另一个进程中，取消封送处理。

*pvDestContext*<br/>
留待将来使用；必须为零。

*mshlflags*<br/>
指定要封送处理的数据是否要传输回客户端进程（通常是典型情况），或写入到全局表中，这些数据可通过多个客户端进行检索。

### <a name="return-value"></a>返回值

已成功封送 S_OK 接口指针。

E_NOINTERFACE 不支持指定的接口。

STG_E_MEDIUMFULL 流已满。

E_FAIL 操作失败。

## <a name="ftmbasemarshaller_"></a><a name="marshaller"></a>FtmBase：： marshaller_

保留对自由线程封送拆收器的引用。

```cpp
Microsoft::WRL::ComPtr<IMarshal> marshaller_; ;
```

## <a name="ftmbasereleasemarshaldata"></a><a name="releasemarshaldata"></a>FtmBase：： ReleaseMarshalData

销毁已封送的数据包。

```cpp
STDMETHODIMP ReleaseMarshalData(
   __in IStream *pStm
) override;
```

### <a name="parameters"></a>参数

*pStm*<br/>
指向包含要销毁的数据包的流的指针。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="ftmbaseunmarshalinterface"></a><a name="unmarshalinterface"></a>FtmBase：： UnmarshalInterface

初始化新创建的代理并返回指向该代理的接口指针。

```cpp
STDMETHODIMP UnmarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __deref_out void **ppv
) override;
```

### <a name="parameters"></a>参数

*pStm*<br/>
指向要从中取消封送接口指针的流的指针。

*riid*<br/>
引用要取消封送的接口的标识符。

*ppv*<br/>
此操作完成后，将接收在*riid*中请求的接口指针的指针变量的地址。 如果此操作成功，则 **ppv*包含要取消封送的接口所请求的接口指针。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK;否则，E_NOINTERFACE 或 E_FAIL。
