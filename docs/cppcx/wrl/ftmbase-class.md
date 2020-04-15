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
ms.openlocfilehash: d37cdddda8cf8894016ed80b9055fe106b1600f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371518"
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

有关详细信息，请参阅[运行时类](runtimeclass-class.md)。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

| 名称                         | 说明                                        |
| ---------------------------- | -------------------------------------------------- |
| [FtmBase：：FtmBase](#ftmbase) | 初始化 `FtmBase` 类的新实例。 |

### <a name="public-methods"></a>公共方法

| 名称                                                               | 说明                                                                                                                                                          |
| ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [FtmBase：：创建全局接口表](#createglobalinterfacetable) | 创建全局接口表 （GIT）。                                                                                                                              |
| [FtmBase：:D连接对象](#disconnectobject)                     | 强制释放到对象的所有外部连接。 在关闭之前，对象的服务器调用该对象的此方法的实现。                |
| [FtmBase：获取元帅SizeMax](#getmarshalsizemax)                   | 获取在指定对象上封送指定接口指针所需的字节数的上限。                                                |
| [FtmBase：获取 Unmarshal 类](#getunmarshalclass)                   | 获取 COM 用于查找包含相应代理代码的 DLL 的 CLSID。 COM 加载此 DLL 以创建代理的未初始化实例。 |
| [FtmBase：：MarshalInterface](#marshalinterface)                     | 将在某些客户端进程中初始化代理对象所需的数据写入流中。                                                                          |
| [FtmBase：：释放元帅数据](#releasemarshaldata)                 | 销毁封送的数据包。                                                                                                                                    |
| [FtmBase：取消封送接口](#unmarshalinterface)                 | 初始化新创建的代理并返回指向该代理的接口指针。                                                                                    |

### <a name="public-data-members"></a>公共数据成员

| 名称                                | 说明                                       |
| ----------------------------------- | ------------------------------------------------- |
| [FtmBase：marshaller_](#marshaller) | 保存对自由线程封送器的引用。 |

## <a name="inheritance-hierarchy"></a>继承层次结构

`FtmBase`

## <a name="requirements"></a>要求

**标题：** ftm.h

**命名空间：** Microsoft::WRL

## <a name="ftmbasecreateglobalinterfacetable"></a><a name="createglobalinterfacetable"></a>FtmBase：：创建全局接口表

创建全局接口表 （GIT）。

```cpp
static HRESULT CreateGlobalInterfaceTable(
   __out IGlobalInterfaceTable **git
);
```

### <a name="parameters"></a>参数

*Git*<br/>
此操作完成后，将指针指向全局接口表。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

### <a name="remarks"></a>备注

有关详细信息，请参阅 MSDN`IGlobalInterfaceTable`库中`COM Reference`主题`COM Interfaces`子主题中的主题。

## <a name="ftmbasedisconnectobject"></a><a name="disconnectobject"></a>FtmBase：:D连接对象

强制释放到对象的所有外部连接。 在关闭之前，对象的服务器调用该对象的此方法的实现。

```cpp
STDMETHODIMP DisconnectObject(
   __in DWORD dwReserved
) override;
```

### <a name="parameters"></a>参数

*dw保留*<br/>
留待将来使用；必须为零。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="ftmbaseftmbase"></a><a name="ftmbase"></a>FtmBase：：FtmBase

初始化 `FtmBase` 类的新实例。

```cpp
FtmBase();
```

## <a name="ftmbasegetmarshalsizemax"></a><a name="getmarshalsizemax"></a>FtmBase：获取元帅SizeMax

获取在指定对象上封送指定接口指针所需的字节数的上限。

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
对要封送的接口的标识符的引用。

*光伏*<br/>
要封送的接口指针;可以是 NULL。

*dwDest上下文*<br/>
要取消封送指定接口的目标上下文。

指定一个或多个 MSHCTX 枚举值。

目前，取消封送可能发生在当前进程的另一个单元（MSHCTX_INPROC），也可以与当前进程 （MSHCTX_LOCAL） 在同一台计算机上的另一个进程中发生。

*pvDest上下文*<br/>
保留供将来使用;必须为 NULL。

*毫秒标志*<br/>
指示要封送的数据是传输回客户端进程（典型情况）还是写入全局表（多个客户端可以检索）的标志。 指定一个或多个 MSHLFLAGS 枚举值。

*pSize*<br/>
此操作完成后，指针指向要写入封送流的数据量上的上限。

### <a name="return-value"></a>返回值

S_OK如果成功;否则，E_FAIL或E_NOINTERFACE。

## <a name="ftmbasegetunmarshalclass"></a><a name="getunmarshalclass"></a>FtmBase：获取 Unmarshal 类

获取 COM 用于查找包含相应代理代码的 DLL 的 CLSID。 COM 加载此 DLL 以创建代理的未初始化实例。

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
对要封送的接口的标识符的引用。

*光伏*<br/>
指向要封送的接口的指针;如果调用方没有指向所需接口的指针，则可以为 NULL。

*dwDest上下文*<br/>
要取消封送指定接口的目标上下文。

指定一个或多个 MSHCTX 枚举值。

取消封送可以在当前进程的另一个单元（MSHCTX_INPROC）中，也可以与当前进程 （MSHCTX_LOCAL） 在同一台计算机上的另一个进程中发生解封送。

*pvDest上下文*<br/>
保留供将来使用;必须为 NULL。

*毫秒标志*<br/>
此操作完成后，指向 CLSID 的指针将用于在客户端进程中创建代理。

*pCid*

### <a name="return-value"></a>返回值

S_OK如果成功;否则，S_FALSE。

## <a name="ftmbasemarshalinterface"></a><a name="marshalinterface"></a>FtmBase：：MarshalInterface

将在某些客户端进程中初始化代理对象所需的数据写入流中。

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
指向在封送过程中使用的流的指针。

*riid*<br/>
对要封送的接口的标识符的引用。 此接口必须派生自 `IUnknown` 接口。

*光伏*<br/>
指向要封送的接口指针;如果调用方没有指向所需接口的指针，则可以为 NULL。

*dwDest上下文*<br/>
要取消封送指定接口的目标上下文。

指定一个或多个 MSHCTX 枚举值。

取消封送可以发生在当前进程的另一个单元（MSHCTX_INPROC），也可以与当前进程 （MSHCTX_LOCAL） 在同一台计算机上的另一个进程中发生。

*pvDest上下文*<br/>
留待将来使用；必须为零。

*毫秒标志*<br/>
指定要封送的数据是要传输回客户端进程（典型情况），还是写入全局表，由多个客户端检索这些数据。

### <a name="return-value"></a>返回值

S_OK接口指针已成功封送。

E_NOINTERFACE不支持指定的接口。

STG_E_MEDIUMFULL 流已满。

E_FAIL 操作失败。

## <a name="ftmbasemarshaller_"></a><a name="marshaller"></a>FtmBase：marshaller_

保存对自由线程封送器的引用。

```cpp
Microsoft::WRL::ComPtr<IMarshal> marshaller_; ;
```

## <a name="ftmbasereleasemarshaldata"></a><a name="releasemarshaldata"></a>FtmBase：：释放元帅数据

销毁封送的数据包。

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

## <a name="ftmbaseunmarshalinterface"></a><a name="unmarshalinterface"></a>FtmBase：取消封送接口

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
指向要取消封送接口指针的流。

*riid*<br/>
引用要取消封送的接口的标识符。

*Ppv*<br/>
此操作完成后，接收*riid*中请求的接口指针的指针变量的地址。 如果此操作成功，**ppv*包含要取消封解的接口的请求接口指针。

### <a name="return-value"></a>返回值

S_OK如果成功;否则，E_NOINTERFACE或E_FAIL。
