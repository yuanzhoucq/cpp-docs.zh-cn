---
title: CComObjectRootEx 类
ms.date: 11/04/2016
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
helpviewer_keywords:
- reference counting
ms.assetid: 894a3d7c-2daf-4fd0-8fa4-e6a05bcfb631
ms.openlocfilehash: 8fa4e7a035ded2e1a20dd278a5d54d40252e1958
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423320"
---
# <a name="ccomobjectrootex-class"></a>CComObjectRootEx 类

此类提供方法来处理非聚合对象和聚合对象的对象引用计数管理。

## <a name="syntax"></a>语法

```
template<class ThreadModel>
class CComObjectRootEx : public CComObjectRootBase
```

#### <a name="parameters"></a>parameters

*ThreadModel*<br/>
类，该类的方法实现所需的线程模型。 可以通过将*ThreadModel*设置为[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)、 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)或[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)来显式选择线程模型。 可以通过将*ThreadModel*设置为[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)或[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)，来接受服务器的默认线程模型。

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[CComObjectRootEx](#ccomobjectrootex)|构造函数。|
|[InternalAddRef](#internaladdref)|递增非聚合对象的引用计数。|
|[InternalRelease](#internalrelease)|减少非聚合对象的引用计数。|
|[住](#lock)|如果线程模型为多线程模型，则获取临界区对象的所有权。|
|[解锁](#unlock)|如果线程模型为多线程模型，则释放临界区对象的所有权。|

### <a name="ccomobjectrootbase-methods"></a>CComObjectRootBase 方法

|||
|-|-|
|[FinalConstruct](#finalconstruct)|在您的类中重写，以执行您的对象所需的任何初始化。|
|[FinalRelease](#finalrelease)|在您的类中重写，以执行您的对象所需的任何清理。|
|[OuterAddRef](#outeraddref)|递增聚合对象的引用计数。|
|[OuterQueryInterface](#outerqueryinterface)|委托到聚合对象的外部 `IUnknown`。|
|[OuterRelease](#outerrelease)|递减聚合对象的引用计数。|

### <a name="static-functions"></a>静态函数

|||
|-|-|
|[InternalQueryInterface](#internalqueryinterface)|委托给非聚合对象的 `IUnknown`。|
|[ObjectMain](#objectmain)|在模块初始化和终止对象映射中列出的派生类的过程中调用。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|[m_dwRef](#m_dwref)|在 `m_pOuterUnknown`中，联合的一部分。 在未聚合对象以容纳 `AddRef` 和 `Release`的引用计数时使用。|
|[m_pOuterUnknown](#m_pouterunknown)|在 `m_dwRef`中，联合的一部分。 当聚合对象以保存指向外部未知的指针时使用。|

## <a name="remarks"></a>备注

`CComObjectRootEx` 处理非聚合对象和聚合对象的对象引用计数管理。 如果未对对象进行聚合，则它保存对象引用计数，如果对象正在聚合，则保存指向外部未知的指针。 对于聚合对象，可以使用 `CComObjectRootEx` 方法来处理要构造的内部对象的故障，以及在释放内部接口或删除内部对象时防止删除外部对象。

实现 COM 服务器的类必须从 `CComObjectRootEx` 或[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)继承。

如果类定义指定[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)宏，则在调用 `IClassFactory::CreateInstance` 时 ATL 将创建 `CComPolyObject<CYourClass>` 的实例。 在创建过程中，将检查外部 "未知" 的值。 如果为 NULL，则为非聚合对象实现 `IUnknown`。 如果外部未知不为 NULL，则为聚合的对象实现 `IUnknown`。

如果类未指定 DECLARE_POLY_AGGREGATABLE 宏，ATL 将为聚合对象创建 `CAggComObject<CYourClass>` 的实例，或为非聚合对象创建 `CComObject<CYourClass>` 的实例。

使用 `CComPolyObject` 的优点在于，您可以避免在模块中同时使用 `CComAggObject` 和 `CComObject` 来处理聚合和非聚合情况。 单个 `CComPolyObject` 对象处理两种情况。 因此，您的模块中只存在一个 vtable 副本和一个函数副本。 如果 vtable 很大，这可能会显著降低模块大小。 但是，如果你的 vtable 较小，则使用 `CComPolyObject` 会导致模块大小稍微大一些，因为它未针对聚合对象或非聚合对象进行优化，因为 `CComAggObject` 和 `CComObject`。

如果对象已聚合，则会通过 `CComAggObject` 或 `CComPolyObject`来实现[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 。 这些类将 `QueryInterface`、`AddRef`和 `Release` 调用委托给 `CComObjectRootEx`的 `OuterQueryInterface`、`OuterAddRef`和 `OuterRelease`，以便转发到外部未知。 通常，重写类中的 `CComObjectRootEx::FinalConstruct` 以创建任何聚合对象，并重写 `CComObjectRootEx::FinalRelease` 以释放任何聚合对象。

如果对象未聚合，则 `IUnknown` 由 `CComObject` 或 `CComPolyObject`实现。 在这种情况下，对 `QueryInterface`、`AddRef`和 `Release` 的调用将被委派给 `CComObjectRootEx`的 `InternalQueryInterface`、`InternalAddRef`和 `InternalRelease`，以执行实际的操作。

## <a name="requirements"></a>要求

**标头：** atlcom。h

##  <a name="ccomobjectrootex"></a>CComObjectRootEx：： CComObjectRootEx

构造函数将引用计数初始化为0。

```
CComObjectRootEx();
```

##  <a name="finalconstruct"></a>CComObjectRootEx：： FinalConstruct

您可以在派生类中重写此方法，以执行您的对象所需的任何初始化。

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>返回值

返回 S_OK 成功或某个标准错误 HRESULT 值。

### <a name="remarks"></a>备注

默认情况下，`CComObjectRootEx::FinalConstruct` 只返回 S_OK。

在 `FinalConstruct` 而不是类的构造函数中执行初始化有一些优点：

- 不能从构造函数返回状态代码，但可以通过 `FinalConstruct`的返回值返回 HRESULT。 当使用 ATL 提供的标准类工厂创建类的对象时，会将此返回值传播回 COM 客户端，以便您向其提供详细的错误信息。

- 不能通过类的构造函数中的虚函数机制调用虚拟函数。 从类的构造函数调用虚函数将导致静态解析的对函数的调用，因为它是在继承层次结构中的该点定义的。 调用纯虚函数会导致链接器错误。

   你的类不是继承层次结构中派生程度最高的类，它依赖于 ATL 提供的派生类来提供其某些功能。 你的初始化可能需要使用该类提供的功能（当类的对象需要聚合其他对象时，这无疑是如此），但你的类中的构造函数无法访问这些功能。 在完全构造派生程度最高的类之前，将执行类的构造代码。

   但是，在完全构造派生的类后，立即调用 `FinalConstruct`，这样你就可以调用虚拟函数并使用 ATL 提供的引用计数实现。

### <a name="example"></a>示例

通常，在从 `CComObjectRootEx` 派生的类中重写此方法以创建任何聚合对象。 例如：

[!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]

如果构造失败，你可以返回一个错误。 你还可以使用宏[DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct)来保护外部对象，前提是在创建过程中，内部聚合对象递增引用计数，然后将计数递减为0。

下面是创建聚合的典型方法：

- 向类对象添加一个 `IUnknown` 指针，并在构造函数中将其初始化为 NULL。

- 重写 `FinalConstruct` 以创建聚合。

- 使用你定义为[COM_INTERFACE_ENTRY_AGGREGATE](com-interface-entry-macros.md#com_interface_entry_aggregate)宏的参数的 `IUnknown` 指针。

- 重写 `FinalRelease` 以释放 `IUnknown` 指针。

##  <a name="finalrelease"></a>CComObjectRootEx：： FinalRelease

您可以在派生类中重写此方法，以执行您的对象所需的任何清理。

```
void FinalRelease();
```

### <a name="remarks"></a>备注

默认情况下，`CComObjectRootEx::FinalRelease` 不执行任何操作。

执行 `FinalRelease` 中的清理优于向类的析构函数中添加代码，因为该对象仍在调用 `FinalRelease` 的位置完全构造。 这使您可以安全地访问由最派生的类提供的方法。 这对于在删除之前释放任何聚合对象尤其重要。

##  <a name="internaladdref"></a>CComObjectRootEx：： InternalAddRef

将非聚合对象的引用计数递增1。

```
ULONG InternalAddRef();
```

### <a name="return-value"></a>返回值

可能对诊断和测试有用的值。

### <a name="remarks"></a>备注

如果线程模型为多线程模型，则使用 `InterlockedIncrement` 来防止多个线程同时更改引用计数。

##  <a name="internalqueryinterface"></a>CComObjectRootEx：： InternalQueryInterface

检索指向所请求的接口的指针。

```
static HRESULT InternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>parameters

*pThis*<br/>
中指向对象的指针，该对象包含向 `QueryInterface`公开的接口的 COM 映射。

*pEntries*<br/>
中指向 `_ATL_INTMAP_ENTRY` 结构的指针，该结构访问可用接口的映射。

*iid*<br/>
中所请求的接口的 GUID。

*ppvObject*<br/>
弄指向在*iid*中指定的接口指针的指针; 如果找不到接口，则为 NULL。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

`InternalQueryInterface` 仅处理 COM 映射表中的接口。 如果对象已聚合，则 `InternalQueryInterface` 不会委托给外部未知。 您可以将接口输入到 COM 映射表中，其中的宏[COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry)或其变量之一。

##  <a name="internalrelease"></a>CComObjectRootEx：： InternalRelease

将非聚合对象的引用计数递减1。

```
ULONG InternalRelease();
```

### <a name="return-value"></a>返回值

在非调试和调试生成中，此函数将返回一个值，该值对于诊断或测试可能很有用。 返回的确切值取决于许多因素，如使用的操作系统、可能的和不是引用计数。

### <a name="remarks"></a>备注

如果线程模型为多线程模型，则使用 `InterlockedDecrement` 来防止多个线程同时更改引用计数。

##  <a name="lock"></a>CComObjectRootEx：： Lock

如果线程模型为多线程模型，此方法将调用 Win32 API 函数[EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection)，该函数将等待，直到线程可以获得通过私有数据成员获取的临界区对象的所有权。

```
void Lock();
```

### <a name="remarks"></a>备注

当受保护的代码执行完毕后，线程必须调用 `Unlock` 才能释放关键部分的所有权。

如果线程模型是单线程的，则此方法不执行任何操作。

##  <a name="m_dwref"></a>CComObjectRootEx：： m_dwRef

访问4个字节内存的联合的一部分。

```
long m_dwRef;
```

### <a name="remarks"></a>备注

在 `m_pOuterUnknown`中，联合的一部分：

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

如果对象未聚合，则 `AddRef` 和 `Release` 访问的引用计数存储在 `m_dwRef`中。 如果对象已聚合，则指向外部 "未知" 的指针将存储在[m_pOuterUnknown](#m_pouterunknown)中。

##  <a name="m_pouterunknown"></a>CComObjectRootEx：： m_pOuterUnknown

访问4个字节内存的联合的一部分。

```
IUnknown*
    m_pOuterUnknown;
```

### <a name="remarks"></a>备注

在 `m_dwRef`中，联合的一部分：

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

如果对象已聚合，则指向外部 "未知" 的指针将存储在 `m_pOuterUnknown`中。 如果对象未聚合，则 `AddRef` 和 `Release` 访问的引用计数存储在[m_dwRef](#m_dwref)中。

##  <a name="objectmain"></a>CComObjectRootEx：： ObjectMain

对于对象映射中列出的每个类，将在初始化模块时调用此函数一次，并在终止时再次调用。

```
static void WINAPI ObjectMain(bool bStarting);
```

### <a name="parameters"></a>parameters

*bStarting*<br/>
弄如果正在初始化该类，则该值为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

*BStarting*参数的值指示是否正在初始化或终止模块。 `ObjectMain` 的默认实现不执行任何操作，但你可以在你的类中重写此函数，以初始化或清理你要为类分配的资源。 请注意，在请求类的任何实例之前，将调用 `ObjectMain`。

从 DLL 的入口点调用 `ObjectMain`，因此入口点函数可以执行的操作类型受到限制。 有关这些限制的详细信息，请参阅[dll 和C++ Visual 运行时库行为](../../build/run-time-library-behavior.md)和[DllMain](/windows/win32/Dlls/dllmain)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]

##  <a name="outeraddref"></a>CComObjectRootEx：： OuterAddRef

递增聚合的外部未知的引用计数。

```
ULONG OuterAddRef();
```

### <a name="return-value"></a>返回值

可能对诊断和测试有用的值。

##  <a name="outerqueryinterface"></a>CComObjectRootEx：： OuterQueryInterface

检索指向所请求接口的间接指针。

```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>parameters

*iid*<br/>
中所请求的接口的 GUID。

*ppvObject*<br/>
弄指向在*iid*中指定的接口指针的指针; 如果聚合不支持接口，则为 NULL。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

##  <a name="outerrelease"></a>CComObjectRootEx：： OuterRelease

递减聚合的外部未知的引用计数。

```
ULONG OuterRelease();
```

### <a name="return-value"></a>返回值

在非调试版本中，始终返回0。 在调试版本中，将返回一个值，该值对于诊断或测试可能很有用。

##  <a name="unlock"></a>CComObjectRootEx：： Unlock

如果线程模型为多线程模型，此方法将调用 Win32 API 函数[LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection)，该函数将释放通过私有数据成员获取的关键节对象的所有权。

```
void Unlock();
```

### <a name="remarks"></a>备注

若要获取所有权，线程必须调用 `Lock`。 对 `Lock` 的每个调用都需要对 `Unlock` 进行相应的调用，以释放关键部分的所有权。

如果线程模型是单线程的，则此方法不执行任何操作。

## <a name="see-also"></a>另请参阅

[CComAggObject 类](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject 类](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject 类](../../atl/reference/ccompolyobject-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
