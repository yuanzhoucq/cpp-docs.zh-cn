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
ms.openlocfilehash: e8db86f6214f95cd9bb08d3b5f6c6c1a38ca475c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327608"
---
# <a name="ccomobjectrootex-class"></a>CComObjectRootEx 类

此类提供了处理非聚合对象和聚合对象的对象引用计数管理的方法。

## <a name="syntax"></a>语法

```
template<class ThreadModel>
class CComObjectRootEx : public CComObjectRootBase
```

#### <a name="parameters"></a>参数

*螺纹模型*<br/>
其方法实现所需线程模型的类。 您可以通过将*线程模型*设置为[CCom 单线程模型](../../atl/reference/ccomsinglethreadmodel-class.md)[、CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)或[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)来显式选择线程模型。 通过将*ThreadModel*设置为[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)或[CComGlobalsThreadModel，](atl-typedefs.md#ccomglobalsthreadmodel)可以接受服务器的默认线程模型。

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[CComObjectRootEx](#ccomobjectrootex)|构造函数。|
|[内部添加参考](#internaladdref)|增加非聚合对象的引用计数。|
|[内部发布](#internalrelease)|取消非聚合对象的引用计数。|
|[Lock](#lock)|如果线程模型是多线程的，则获取关键部分对象的所有权。|
|[解 锁](#unlock)|如果线程模型是多线程的，则释放关键部分对象的所有权。|

### <a name="ccomobjectrootbase-methods"></a>CComObjectRootbase 方法

|||
|-|-|
|[最终构造](#finalconstruct)|在类中重写以执行对象所需的任何初始化。|
|[最终发布](#finalrelease)|在类中重写以执行对象所需的任何清理。|
|[外加参照](#outeraddref)|增加聚合对象的引用计数。|
|[外部查询接口](#outerqueryinterface)|表示到聚合对象的`IUnknown`外部。|
|[外部释放](#outerrelease)|取消聚合对象的引用计数。|

### <a name="static-functions"></a>静态函数

|||
|-|-|
|[内部查询接口](#internalqueryinterface)|委托给`IUnknown`非聚合对象的。|
|[对象主](#objectmain)|在模块初始化和对象映射中列出的派生类终止期间调用。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|[m_dwRef](#m_dwref)|与`m_pOuterUnknown`， 工会的一部分。 当对象未聚合以保存 和`AddRef``Release`的引用计数时使用。|
|[m_pOuterUnknown](#m_pouterunknown)|与`m_dwRef`， 工会的一部分。 当对象聚合以保存指向外部未知指针时使用。|

## <a name="remarks"></a>备注

`CComObjectRootEx`处理非聚合对象和聚合对象的对象引用计数管理。 如果对象未聚合，它将保存对象引用计数，并且保留指向外部未知对象的指针（如果对象正在聚合）。 对于聚合对象，`CComObjectRootEx`可以使用方法来处理内部对象构造的失败，并在释放内部接口或删除内部对象时保护外部对象不被删除。

实现 COM 服务器的类必须继承`CComObjectRootEx`或[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)。

如果类定义指定[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)宏，ATL 将创建调用时`CComPolyObject<CYourClass>``IClassFactory::CreateInstance`的实例。 在创建期间，将检查外部未知值。 如果为 NULL，`IUnknown`则为非聚合对象实现。 如果外部未知值不是 NULL，`IUnknown`则为聚合对象实现。

如果类未指定DECLARE_POLY_AGGREGATABLE宏，ATL`CAggComObject<CYourClass>`将创建聚合对象的实例或`CComObject<CYourClass>`非聚合对象的实例。

使用`CComPolyObject`的优点是，您避免在模块`CComAggObject``CComObject`中同时处理聚合和非聚合情况。 单个`CComPolyObject`对象处理这两种情况。 因此，模块中仅存在一个 vtable 副本和函数副本。 如果 vtable 很大，这可大幅减小模块大小。 但是，如果 vtable 很小，则`CComPolyObject`使用可能会导致模块大小稍大一些，因为它未针对聚合或非聚合对象进行优化，例如`CComAggObject`和`CComObject`。

如果对象是聚合的，[则 IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) `CComAggObject`由`CComPolyObject`或 实现。 这些类委托`QueryInterface``AddRef`和`Release`调用`CComObjectRootEx`的`OuterQueryInterface`，`OuterAddRef`并`OuterRelease`转发到外部未知。 通常，在类`CComObjectRootEx::FinalConstruct`中重写以创建任何聚合对象，并重写`CComObjectRootEx::FinalRelease`以释放任何聚合对象。

如果对象未聚合，`IUnknown`则由`CComObject`或`CComPolyObject`实现。 在这种情况下，`QueryInterface`对 的`AddRef``Release`调用 将委派给`CComObjectRootEx`的`InternalQueryInterface` `InternalAddRef`， 以及`InternalRelease`执行实际操作。

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="ccomobjectrootexccomobjectrootex"></a><a name="ccomobjectrootex"></a>CComObjectRootEx：CComObjectRootEx

构造函数将引用计数初始化为 0。

```
CComObjectRootEx();
```

## <a name="ccomobjectrootexfinalconstruct"></a><a name="finalconstruct"></a>CComObjectRootEx：最终构造

可以在派生类中重写此方法，以执行对象所需的任何初始化。

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>返回值

返回成功时S_OK或标准错误 HRESULT 值之一。

### <a name="remarks"></a>备注

默认情况下，`CComObjectRootEx::FinalConstruct`只需返回S_OK。

在 类中`FinalConstruct`执行初始化的优点，而不是类的构造函数：

- 您不能从构造函数返回状态代码，但可以通过`FinalConstruct`的返回值返回 HRESULT。 使用 ATL 提供的标准类工厂创建类的对象时，此返回值将传播回 COM 客户端，从而允许您向他们提供详细的错误信息。

- 不能通过类的构造函数调用虚拟函数机制。 从类的构造函数调用虚拟函数会导致对函数的静态解析调用，因为它在继承层次结构中定义。 对纯虚拟函数的调用会导致链接器错误。

   类不是继承层次结构中派生最多的类 - 它依赖于 ATL 提供的派生类来提供其某些功能。 初始化很可能需要使用该类提供的要素（当类的对象需要聚合其他对象时，情况确实如此），但类中的构造函数无法访问这些要素。 在完全构造最派生的类之前，将执行类的构造代码。

   但是，`FinalConstruct`在完全构造最派生的类后立即调用，允许您调用虚拟函数并使用 ATL 提供的引用计数实现。

### <a name="example"></a>示例

通常，在派生的`CComObjectRootEx`类中重写此方法以创建任何聚合对象。 例如：

[!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]

如果构造失败，您可以返回错误。 如果内部聚合对象在创建过程中增加引用计数，然后将计数化为 0，则可以使用宏[DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct)来保护外部对象不被删除。

以下是创建聚合的典型方法：

- 向类`IUnknown`对象添加指针，并将其初始化到构造函数中的 NULL。

- 重写`FinalConstruct`以创建聚合。

- 使用定义为`IUnknown`参数的指针[，COM_INTERFACE_ENTRY_AGGREGATE](com-interface-entry-macros.md#com_interface_entry_aggregate)宏。

- 重写`FinalRelease`以释放`IUnknown`指针。

## <a name="ccomobjectrootexfinalrelease"></a><a name="finalrelease"></a>CComObjectRootEx：最终发布

可以在派生类中重写此方法，以执行对象所需的任何清理。

```
void FinalRelease();
```

### <a name="remarks"></a>备注

默认情况下，`CComObjectRootEx::FinalRelease`不执行任何操作。

执行清理`FinalRelease`比向类的析构函数添加代码更可取，因为对象仍在调用的`FinalRelease`点完全构造。 这使您能够安全地访问最派生类提供的方法。 这对删除之前释放任何聚合对象尤其重要。

## <a name="ccomobjectrootexinternaladdref"></a><a name="internaladdref"></a>CComObjectRootEx：：内部AddRef

将非聚合对象的引用计数增加 1。

```
ULONG InternalAddRef();
```

### <a name="return-value"></a>返回值

可用于诊断和测试的值。

### <a name="remarks"></a>备注

如果线程模型是多线程的，`InterlockedIncrement`则用于防止多个线程同时更改引用计数。

## <a name="ccomobjectrootexinternalqueryinterface"></a><a name="internalqueryinterface"></a>CComObjectRootEx：内部查询接口

检索指向所请求的接口的指针。

```
static HRESULT InternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>参数

*p*<br/>
[在]指向对象的指针，其中包含向 公开的接口的 COM 映射`QueryInterface`。

*p条目*<br/>
[在]指向访问可用接口`_ATL_INTMAP_ENTRY`映射的结构的指针。

*Iid*<br/>
[在]请求的接口的 GUID。

*ppvObject*<br/>
[出]指向*iid*中指定的接口指针，如果找不到接口，则指向 NULL 中的指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="remarks"></a>备注

`InternalQueryInterface` 仅处理 COM 映射表中的接口。 如果对象是聚合的，`InternalQueryInterface`则不委托给外部未知对象。 您可以使用宏[COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry)或其变体之一在 COM 地图表中输入接口。

## <a name="ccomobjectrootexinternalrelease"></a><a name="internalrelease"></a>CComObjectRootEx：内部发布

将非聚合对象的引用计数减少 1。

```
ULONG InternalRelease();
```

### <a name="return-value"></a>返回值

在非调试和调试生成中，此函数返回一个可用于诊断或测试的值。 返回的确切值取决于许多因素，如使用的操作系统，并且可能是引用计数，也可能不是。

### <a name="remarks"></a>备注

如果线程模型是多线程的，`InterlockedDecrement`则用于防止多个线程同时更改引用计数。

## <a name="ccomobjectrootexlock"></a><a name="lock"></a>CComObjectRootEx：锁定

如果线程模型是多线程的，此方法将调用 Win32 API 函数[EnterDataSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection)，它等待线程可以取得通过私有数据成员获得的关键部分对象的所有权。

```
void Lock();
```

### <a name="remarks"></a>备注

当受保护的代码完成执行时，线程必须调用`Unlock`以释放关键部分的所有权。

如果线程模型是单线程的，则此方法不执行任何操作。

## <a name="ccomobjectrootexm_dwref"></a><a name="m_dwref"></a>CComObjectRootEx：m_dwRef

访问四个字节内存的联合的一部分。

```
long m_dwRef;
```

### <a name="remarks"></a>备注

使用`m_pOuterUnknown`，联合的一部分：

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

如果未聚合对象，则`AddRef``Release`和 访问的引用计数将存储在 中。 `m_dwRef` 如果对象是聚合的，则指向外部未知值的指针存储在[m_pOuterUnknown](#m_pouterunknown)中。

## <a name="ccomobjectrootexm_pouterunknown"></a><a name="m_pouterunknown"></a>CComObjectRootEx：：m_pOuterUnknown

访问四个字节内存的联合的一部分。

```
IUnknown*
    m_pOuterUnknown;
```

### <a name="remarks"></a>备注

使用`m_dwRef`，联合的一部分：

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

如果对象是聚合的，则指向外部未知值的指针存储在`m_pOuterUnknown`中。 如果未聚合对象，则 访问`AddRef`和`Release`的引用计数存储在[m_dwRef](#m_dwref)中。

## <a name="ccomobjectrootexobjectmain"></a><a name="objectmain"></a>CComObjectRootEx：对象Main

对于对象映射中列出的每个类，在初始化模块时调用此函数一次，在终止模块时再次调用该函数。

```
static void WINAPI ObjectMain(bool bStarting);
```

### <a name="parameters"></a>参数

*b 开始*<br/>
[出]如果要初始化类，则该值为 TRUE;如果正在初始化该类，则该值为 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

*bStarting*参数的值指示模块是初始化还是终止。 的`ObjectMain`默认实现不执行任何操作，但您可以重写类中的此函数，以初始化或清理要为类分配的资源。 请注意，`ObjectMain`在请求类的任何实例之前调用。

`ObjectMain`从 DLL 的入口点调用，因此入口点函数可以执行的操作类型受到限制。 有关这些限制的详细信息，请参阅[DLL 和 VisualC++运行时库行为](../../build/run-time-library-behavior.md)和[DllMain](/windows/win32/Dlls/dllmain)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]

## <a name="ccomobjectrootexouteraddref"></a><a name="outeraddref"></a>CComObjectRootEx：：外部AddRef

递增聚合的外部未知数。

```
ULONG OuterAddRef();
```

### <a name="return-value"></a>返回值

可用于诊断和测试的值。

## <a name="ccomobjectrootexouterqueryinterface"></a><a name="outerqueryinterface"></a>CComObjectRootEx：外部查询接口

检索指向请求的接口的间接指针。

```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>参数

*Iid*<br/>
[在]请求的接口的 GUID。

*ppvObject*<br/>
[出]指向*iid*中指定的接口指针，如果聚合不支持接口，则指向 NULL 中的指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

## <a name="ccomobjectrootexouterrelease"></a><a name="outerrelease"></a>CComObjectRootEx：外部释放

取消聚合外部未知项的引用计数。

```
ULONG OuterRelease();
```

### <a name="return-value"></a>返回值

在非调试生成中，始终返回 0。 在调试生成中，返回可用于诊断或测试的值。

## <a name="ccomobjectrootexunlock"></a><a name="unlock"></a>CComObjectRootEx：解锁

如果线程模型是多线程的，此方法调用 Win32 API 函数[Leave临界节](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection)，它释放通过私有数据成员获取的关键部分对象的所有权。

```
void Unlock();
```

### <a name="remarks"></a>备注

要获得所有权，线程必须调用`Lock`。 每个调用`Lock`都需要相应的调用以`Unlock`释放关键部分的所有权。

如果线程模型是单线程的，则此方法不执行任何操作。

## <a name="see-also"></a>另请参阅

[CComAggObject 类](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject 类](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject 类](../../atl/reference/ccompolyobject-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
