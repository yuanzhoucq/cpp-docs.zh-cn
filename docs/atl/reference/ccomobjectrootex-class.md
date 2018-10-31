---
title: CComObjectRootEx 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObjectRootEx
- ATLCOM/ATL::CComObjectRootEx
- ATLCOM/ATL::InternalAddRef
- ATLCOM/ATL::InternalRelease
- ATLCOM/ATL::Lock
- ATLCOM/ATL::Unlock
- ATLCOM/ATL::FinalConstruct
- ATLCOM/ATL::FinalRelease
- ATLCOM/ATL::OuterAddRef
- ATLCOM/ATL::OuterQueryInterface
- ATLCOM/ATL::OuterRelease
- ATLCOM/ATL::InternalQueryInterface
- ATLCOM/ATL::ObjectMain
- ATLCOM/ATL::m_dwRef
- ATLCOM/ATL::m_pOuterUnknown
dev_langs:
- C++
helpviewer_keywords:
- reference counting
ms.assetid: 894a3d7c-2daf-4fd0-8fa4-e6a05bcfb631
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 413485bc7675fbc68f2c224ceefdd0f552538eb9
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50076979"
---
# <a name="ccomobjectrootex-class"></a>CComObjectRootEx 类

此类提供方法以处理非聚合和聚合对象的对象引用计数管理。

## <a name="syntax"></a>语法

```
template<class ThreadModel>
class CComObjectRootEx : public CComObjectRootBase
```

#### <a name="parameters"></a>参数

*ThreadModel*<br/>
其方法实现所需的线程处理模型的类。 您可以通过设置显式选择的线程模型*ThreadModel*到[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)， [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)，或[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。 你可以通过设置接受服务器的默认线程模型*ThreadModel*到[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)或[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)。

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[CComObjectRootEx](#ccomobjectrootex)|构造函数。|
|[InternalAddRef](#internaladdref)|非聚合对象的引用计数会递增。|
|[InternalRelease](#internalrelease)|递减引用计数的非聚合的对象。|
|[锁](#lock)|如果线程模型为多线程，获取关键节对象的所有权。|
|[解锁](#unlock)|如果线程模型为多线程，将释放关键节对象的所有权。|

### <a name="ccomobjectrootbase-methods"></a>CComObjectRootBase 方法

|||
|-|-|
|[FinalConstruct](#finalconstruct)|在您执行任何所需的对象的初始化的类中重写。|
|[FinalRelease](#finalrelease)|在您执行所有清理操作所需的对象的类中重写。|
|[OuterAddRef](#outeraddref)|递增的聚合对象的引用计数。|
|[OuterQueryInterface](#outerqueryinterface)|委托给外部`IUnknown`的聚合对象。|
|[OuterRelease](#outerrelease)|递减引用计数的聚合对象。|

### <a name="static-functions"></a>静态函数

|||
|-|-|
|[InternalQueryInterface](#internalqueryinterface)|委托给`IUnknown`的非聚合对象。|
|[ObjectMain](#objectmain)|在模块初始化和终止的对象映射中所列的派生类期间调用。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|[m_dwRef](#m_dwref)|使用`m_pOuterUnknown`、 并集的一部分。 当对象不聚合来保存的引用计数时，使用`AddRef`和`Release`。|
|[m_pOuterUnknown](#m_pouterunknown)|使用`m_dwRef`、 并集的一部分。 聚合对象将保存到外部未知指针时使用。|

## <a name="remarks"></a>备注

`CComObjectRootEx` 处理非聚合和聚合对象的对象引用计数管理。 如果您的对象未被聚合，并且如果您的对象正在聚合包含指向未知的外部，它保留对象引用计数。 对于聚合对象，`CComObjectRootEx`方法可用于处理的内部对象失败，若要构造，并保护中删除发布内部接口时的外部对象或内部对象删除。

实现的 COM 服务器的类必须继承`CComObjectRootEx`或[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)。

如果类定义中指定[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)宏，ATL 创建的实例`CComPolyObject<CYourClass>`时`IClassFactory::CreateInstance`调用。 在创建期间，检查外部未知的值。 如果值为 NULL，`IUnknown`为非聚合对象实现。 如果未知的外部不为 NULL，`IUnknown`为聚合对象实现。

如果您的类没有指定 DECLARE_POLY_AGGREGATABLE 宏，ATL 创建的实例`CAggComObject<CYourClass>`用于聚合的对象或实例`CComObject<CYourClass>`的非聚合的对象。

使用的优点`CComPolyObject`避免同时`CComAggObject`和`CComObject`处理聚合和非聚合的情况下在模块中。 单个`CComPolyObject`对象将处理这两种情况。 因此，只有一份 vtable 和函数的一个副本存在于你的模块。 如果你 vtable 很大，这可以显著减少模块大小。 但是，如果你 vtable 很小，则使用`CComPolyObject`可能导致稍大模块大小，因为它不优化聚合或非聚合对象，因为`CComAggObject`和`CComObject`。

如果您的对象进行了聚合， [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)由实现`CComAggObject`或`CComPolyObject`。 这些类委托`QueryInterface`， `AddRef`，并`Release`调用`CComObjectRootEx`的`OuterQueryInterface`， `OuterAddRef`，和`OuterRelease`将转发到未知的外部。 通常情况下，重写`CComObjectRootEx::FinalConstruct`在您的类来创建聚合的任何对象，并重写`CComObjectRootEx::FinalRelease`以释放任何聚合对象。

如果您的对象不会聚合，`IUnknown`由实现`CComObject`或`CComPolyObject`。 在这种情况下，调用`QueryInterface`， `AddRef`，并`Release`委派给`CComObjectRootEx`的`InternalQueryInterface`， `InternalAddRef`，和`InternalRelease`执行实际操作。

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="ccomobjectrootex"></a>  CComObjectRootEx::CComObjectRootEx

构造函数将初始化为 0 的引用计数。

```
CComObjectRootEx();
```

##  <a name="finalconstruct"></a>  CComObjectRootEx::FinalConstruct

您可以执行任何所需的对象的初始化派生类中重写此方法。

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>返回值

成功，则其中一个标准错误的 HRESULT 值返回 S_OK。

### <a name="remarks"></a>备注

默认情况下，`CComObjectRootEx::FinalConstruct`只需返回 S_OK。

有一些执行中的初始化好处`FinalConstruct`而不是您的类的构造函数：

- 不能从构造函数，返回状态代码，但您可以返回一个 HRESULT 通过`FinalConstruct`的返回值。 当使用 ATL 提供的标准类工厂正在创建你的类的对象时，此返回值被传播回 COM 客户端，您可以向他们提供详细的错误信息。

- 不能通过类的构造函数中的虚函数机制调用虚函数。 从类的构造函数调用虚函数会导致对函数的静态解析调用继承层次结构中定义在该点。 对于纯虚函数的调用导致链接器错误。

   您的类不是继承层次结构中派生程度最高的类，它依赖于派生类提供由 ATL 提供其部分功能。 很可能你的初始化将需要使用的该类 （即是如此，当您的类的对象需要聚合的其他对象），提供的功能，但在您的类构造函数具有无法访问这些功能。 完全构造的派生程度最高的类之前，执行您的类的构造代码。

   但是，`FinalConstruct`称为立即派生程度最高之后完全构造类使您可以调用虚函数和使用引用计数的实现提供的 atl。

### <a name="example"></a>示例

通常情况下，重写此方法在派生类中的`CComObjectRootEx`创建任何聚合对象。 例如：

[!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]

如果在构造失败，可以返回错误。 此外可以使用该宏[DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct)来保护您的外部对象被删除如果在创建期间，内部聚合的对象递增引用计数则递减计数为 0。

下面是创建聚合的典型方式：

- 添加`IUnknown`指向您的类对象，并在构造函数中将其初始化为 NULL。

- 重写`FinalConstruct`创建聚合函数。

- 使用`IUnknown`定义为参数的指针[COM_INTERFACE_ENTRY_AGGREGATE](com-interface-entry-macros.md#com_interface_entry_aggregate)宏。

- 重写`FinalRelease`释放`IUnknown`指针。

##  <a name="finalrelease"></a>  CComObjectRootEx::FinalRelease

您可以执行所有清理操作所需的对象在派生类中重写此方法。

```
void FinalRelease();
```

### <a name="remarks"></a>备注

默认情况下，`CComObjectRootEx::FinalRelease`不执行任何操作。

执行中的清理`FinalRelease`优于将代码添加到您的类的析构函数，因为在此时点仍完全构造该对象`FinalRelease`调用。 这使您可以安全地访问由派生程度最高的类提供的方法。 这是对于释放之前删除任何聚合的对象尤为重要。

##  <a name="internaladdref"></a>  CComObjectRootEx::InternalAddRef

非聚合对象的引用计数递增 1。

```
ULONG InternalAddRef();
```

### <a name="return-value"></a>返回值

一个值，可能是有用的诊断和测试。

### <a name="remarks"></a>备注

如果线程模型为多线程，`InterlockedIncrement`用于防止多个线程同时更改引用计数。

##  <a name="internalqueryinterface"></a>  CComObjectRootEx::InternalQueryInterface

检索指向所请求的接口的指针。

```
static HRESULT InternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>参数

*pThis*<br/>
[in]指向包含向公开的接口的 COM 映射的对象的指针`QueryInterface`。

*pEntries*<br/>
[in]一个指向`_ATL_INTMAP_ENTRY`访问的可用接口映射的结构。

*iid*<br/>
[in]所请求的接口的 GUID。

*ppvObject*<br/>
[out]中指定的接口指针的指针*iid*，或如果找不到该接口，则为 NULL。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

### <a name="remarks"></a>备注

`InternalQueryInterface` 仅处理 COM 映射表中的接口。 如果您的对象进行了聚合，`InternalQueryInterface`不将委托给未知的外部。 接口可以输入到 COM 映射表与宏[COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry)或其一个变体。

##  <a name="internalrelease"></a>  CComObjectRootEx::InternalRelease

递减引用非聚合对象的计数按 1。

```
ULONG InternalRelease();
```

### <a name="return-value"></a>返回值

在这两非调试和调试版本，此函数返回一个值，该值可能是有用的诊断或测试。 取决于许多因素，例如操作系统使用，并可能，也可能不会返回的确切值，引用计数。

### <a name="remarks"></a>备注

如果线程模型为多线程，`InterlockedDecrement`用于防止多个线程同时更改引用计数。

##  <a name="lock"></a>  CComObjectRootEx::Lock

如果线程模型为多线程，此方法会调用 Win32 API 函数[EnterCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-entercriticalsection)，通过私有数据成员获取的等待线程可以获得关键部分对象的所有权。

```
void Lock();
```

### <a name="remarks"></a>备注

当受保护的代码执行完毕后时，必须调用线程`Unlock`释放关键节的所有权。

如果线程模型是单线程，则此方法没有任何影响。

##  <a name="m_dwref"></a>  CComObjectRootEx::m_dwRef

访问四个字节的内存的联合的一部分。

```
long m_dwRef;
```

### <a name="remarks"></a>备注

使用`m_pOuterUnknown`、 并集的一部分：

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

如果该对象不会聚合，引用计数的访问`AddRef`并`Release`存储在`m_dwRef`。 如果对象聚合，未知的外部指向存储在[m_pOuterUnknown](#m_pouterunknown)。

##  <a name="m_pouterunknown"></a>  CComObjectRootEx::m_pOuterUnknown

访问四个字节的内存的联合的一部分。

```
IUnknown*
    m_pOuterUnknown;
```

### <a name="remarks"></a>备注

使用`m_dwRef`、 并集的一部分：

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

如果对象聚合，未知的外部指向存储在`m_pOuterUnknown`。 如果该对象不会聚合，引用计数的访问`AddRef`并`Release`存储在[m_dwRef](#m_dwref)。

##  <a name="objectmain"></a>  CComObjectRootEx::ObjectMain

对于每个对象映射中列出的类后初始化模块时，调用此函数并再次时已终止。

```
static void WINAPI ObjectMain(bool bStarting);
```

### <a name="parameters"></a>参数

*bStarting*<br/>
[out]值为 TRUE，如果正在初始化类;否则为 FALSE。

### <a name="remarks"></a>备注

值*bStarting*参数指示是否将模块正在初始化或终止。 默认实现`ObjectMain`不执行任何操作，但可以在您的类初始化或清理资源，你想要分配的类中重写此函数。 请注意，`ObjectMain`类的任何实例都请求之前调用。

`ObjectMain` 从调用的 dll 的入口点的入口点函数可以执行的操作的类型是受限制。 有关这些限制的详细信息，请参阅[Dll 和 Visual c + + 运行时库行为](../../build/run-time-library-behavior.md)并[DllMain](/windows/desktop/Dlls/dllmain)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]

##  <a name="outeraddref"></a>  CComObjectRootEx::OuterAddRef

未知的外部聚合的引用计数递增。

```
ULONG OuterAddRef();
```

### <a name="return-value"></a>返回值

一个值，可能是有用的诊断和测试。

##  <a name="outerqueryinterface"></a>  CComObjectRootEx::OuterQueryInterface

检索指向所请求的接口的间接指针。

```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>参数

*iid*<br/>
[in]所请求的接口的 GUID。

*ppvObject*<br/>
[out]中指定的接口指针的指针*iid*，或如果聚合不支持该接口，则为 NULL。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

##  <a name="outerrelease"></a>  CComObjectRootEx::OuterRelease

递减引用计数的未知的外部聚合。

```
ULONG OuterRelease();
```

### <a name="return-value"></a>返回值

在非调试版本中，始终返回 0。 在调试版本中返回一个值，可能是有用的诊断或测试。

##  <a name="unlock"></a>  CComObjectRootEx::Unlock

如果线程模型为多线程，此方法会调用 Win32 API 函数[LeaveCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-leavecriticalsection)，通过私有数据成员获取关键节对象的哪些版本所有权。

```
void Unlock();
```

### <a name="remarks"></a>备注

若要获取所有权，线程必须调用`Lock`。 每次调用`Lock`需要相应地调用`Unlock`释放关键节的所有权。

如果线程模型是单线程，则此方法没有任何影响。

## <a name="see-also"></a>请参阅

[CComAggObject 类](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject 类](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject 类](../../atl/reference/ccompolyobject-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
