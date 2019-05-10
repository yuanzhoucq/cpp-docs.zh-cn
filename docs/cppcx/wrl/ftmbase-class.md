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
ms.openlocfilehash: fb7f103d8ea647f554d9bbf26c2e218d34f6b1ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398441"
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

| 名称                         | 描述                                        |
| ---------------------------- | -------------------------------------------------- |
| [FtmBase::FtmBase](#ftmbase) | 初始化 `FtmBase` 类的新实例。 |

### <a name="public-methods"></a>公共方法

| 名称                                                               | 描述                                                                                                                                                          |
| ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [FtmBase::CreateGlobalInterfaceTable](#createglobalinterfacetable) | 创建全局接口表 (GIT)。                                                                                                                              |
| [FtmBase::DisconnectObject](#disconnectobject)                     | 强制释放对象的所有外部连接。 对象的服务器将调用此方法在关机前对象的实现。                |
| [FtmBase::GetMarshalSizeMax](#getmarshalsizemax)                   | 获取有关封送指定的接口指针上指定的对象所需的字节数的上限。                                                |
| [FtmBase::GetUnmarshalClass](#getunmarshalclass)                   | 获取 COM 用来定位相应代理包含代码的 DLL 的 CLSID。 COM 加载此 DLL 才能创建代理的未初始化的实例。 |
| [FtmBase::MarshalInterface](#marshalinterface)                     | 初始化一些客户端进程中的代理对象所需的数据写入到流。                                                                          |
| [FtmBase::ReleaseMarshalData](#releasemarshaldata)                 | 销毁封送的数据包。                                                                                                                                    |
| [FtmBase::UnmarshalInterface](#unmarshalinterface)                 | 初始化新创建的代理，并对该代理返回的接口指针。                                                                                    |

### <a name="public-data-members"></a>公共数据成员

| 名称                                | 描述                                       |
| ----------------------------------- | ------------------------------------------------- |
| [FtmBase::marshaller_](#marshaller) | 保存对自由线程封送处理程序的引用。 |

## <a name="inheritance-hierarchy"></a>继承层次结构

`FtmBase`

## <a name="requirements"></a>要求

**标头：** ftm.h

**命名空间：** Microsoft:: wrl

## <a name="createglobalinterfacetable"></a>FtmBase::CreateGlobalInterfaceTable

创建全局接口表 (GIT)。

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

有关详细信息，请参阅`IGlobalInterfaceTable`中的主题`COM Interfaces`的子主题`COM Reference`MSDN Library 中的主题。

## <a name="disconnectobject"></a>FtmBase::DisconnectObject

强制释放对象的所有外部连接。 对象的服务器将调用此方法在关机前对象的实现。

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

## <a name="ftmbase"></a>FtmBase::FtmBase

初始化 `FtmBase` 类的新实例。

```cpp
FtmBase();
```

## <a name="getmarshalsizemax"></a>FtmBase::GetMarshalSizeMax

获取有关封送指定的接口指针上指定的对象所需的字节数的上限。

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
引用封送的接口标识符。

*pv*<br/>
接口指针进行封送;可以为 NULL。

*dwDestContext*<br/>
其中将被取消封送指定的接口的目标上下文。

指定一个或多个 MSHCTX 枚举值。

目前，取消封送可以发生在当前进程 (MSHCTX_INPROC) 的另一单元中或作为当前进程 (MSHCTX_LOCAL) 在同一台计算机上的另一个进程中。

*pvDestContext*<br/>
保留供将来使用;必须为 NULL。

*mshlflags*<br/>
标志，指示要封送处理的数据是否传输回客户端进程 — 典型用例，或写入到全局表，其中可以由多个客户端检索它。 指定一个或多个 MSHLFLAGS 枚举值。

*pSize*<br/>
此操作完成后，指向要写入到封送处理流的数据量上限。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为 E_FAIL 或 E_NOINTERFACE。

## <a name="getunmarshalclass"></a>FtmBase::GetUnmarshalClass

获取 COM 用来定位相应代理包含代码的 DLL 的 CLSID。 COM 加载此 DLL 才能创建代理的未初始化的实例。

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
引用封送的接口标识符。

*pv*<br/>
指向要封送处理; 的接口如果调用方不具有到所需的接口指针，则可以为 NULL。

*dwDestContext*<br/>
其中将被取消封送指定的接口的目标上下文。

指定一个或多个 MSHCTX 枚举值。

在当前进程 (MSHCTX_INPROC) 的另一单元中或作为当前进程 (MSHCTX_LOCAL) 在同一台计算机上的另一个进程中，可能发生取消封送。

*pvDestContext*<br/>
保留供将来使用;必须为 NULL。

*mshlflags*<br/>
此操作完成后，若要使用客户端进程中创建的代理的 CLSID 的指针。

*pCid*

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为 S_FALSE。

## <a name="marshalinterface"></a>FtmBase::MarshalInterface

初始化一些客户端进程中的代理对象所需的数据写入到流。

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
指向要封送处理期间使用的流。

*riid*<br/>
引用封送的接口标识符。 此接口必须派生自`IUnknown`接口。

*pv*<br/>
要封送处理; 的接口指针的指针如果调用方不具有到所需的接口指针，则可以为 NULL。

*dwDestContext*<br/>
其中将被取消封送指定的接口的目标上下文。

指定一个或多个 MSHCTX 枚举值。

在当前进程 (MSHCTX_INPROC) 的另一单元或者当前进程 (MSHCTX_LOCAL) 在同一台计算机上的另一个进程中，会发生取消封送。

*pvDestContext*<br/>
留待将来使用；必须为零。

*mshlflags*<br/>
指定要封送处理的数据是否传输回客户端进程 — 典型用例，或写入到全局表，其中可以由多个客户端检索它。

### <a name="return-value"></a>返回值

已成功地封送的接口指针，则为 S_OK。

E_NOINTERFACE 不支持指定的接口。

STG_E_MEDIUMFULL 流已满。

E_FAIL 操作失败。

## <a name="marshaller"></a>FtmBase::marshaller_

保存对自由线程封送处理程序的引用。

```cpp
Microsoft::WRL::ComPtr<IMarshal> marshaller_; ;
```

## <a name="releasemarshaldata"></a>FtmBase::ReleaseMarshalData

销毁封送的数据包。

```cpp
STDMETHODIMP ReleaseMarshalData(
   __in IStream *pStm
) override;
```

### <a name="parameters"></a>参数

*pStm*<br/>
指向包含要销毁的数据包的流。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="unmarshalinterface"></a>FtmBase::UnmarshalInterface

初始化新创建的代理，并对该代理返回的接口指针。

```cpp
STDMETHODIMP UnmarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __deref_out void **ppv
) override;
```

### <a name="parameters"></a>参数

*pStm*<br/>
指向要取消封送的接口指针的流。

*riid*<br/>
为要取消封送的接口的标识符的引用。

*ppv*<br/>
此操作完成后，接收中请求的接口指针的指针变量的地址*riid*。 如果此操作成功，**ppv*包含要取消封送的接口的请求的接口指针。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为 E_NOINTERFACE 和 e_fail 两者之一。
