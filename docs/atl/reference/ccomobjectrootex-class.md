---
title: CComObjectRootEx 类 |Microsoft 文档
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
ms.openlocfilehash: b147f0ad3f1a54c2ae640b6bf2426bcddf060b35
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="ccomobjectrootex-class"></a>CComObjectRootEx 类
此类提供方法以处理对象的非聚合和聚合对象的引用计数管理。  
  
## <a name="syntax"></a>语法  
  
```
template<class ThreadModel>  
class CComObjectRootEx : public CComObjectRootBase
```  
  
#### <a name="parameters"></a>参数  
 `ThreadModel`  
 类，其方法实现所需的线程处理模型。 你可以通过设置显式选择的线程模型`ThreadModel`到[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)， [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)，或[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。 你可以通过设置接受服务器的默认线程模型`ThreadModel`到[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)或[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)。  

  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CComObjectRootEx](#ccomobjectrootex)|构造函数。|  
|[InternalAddRef](#internaladdref)|递增非聚合对象的引用的计数。|  
|[InternalRelease](#internalrelease)|递减引用计数的非聚合对象。|  
|[锁](#lock)|如果线程模型为多线程，将获取关键部分对象的所有权。|  
|[解锁](#unlock)|如果线程模型为多线程，将释放的关键部分对象的所有权。|  
  
### <a name="ccomobjectrootbase-methods"></a>CComObjectRootBase 方法  
  
|||  
|-|-|  
|[FinalConstruct](#finalconstruct)|在您执行任何所需的对象的初始化的类中重写。|  
|[FinalRelease](#finalrelease)|在执行任何所需的对象的清理您的类中重写。|  
|[OuterAddRef](#outeraddref)|递增聚合对象的引用的计数。|  
|[OuterQueryInterface](#outerqueryinterface)|委托给外部**IUnknown**的聚合对象。|  
|[OuterRelease](#outerrelease)|递减引用计数的聚合对象。|  
  
### <a name="static-functions"></a>静态函数  
  
|||  
|-|-|  
|[InternalQueryInterface](#internalqueryinterface)|委托给**IUnknown**的非聚合对象。|  
|[ObjectMain](#objectmain)|在初始化模块和派生类对象图中列出的终止期间调用。|  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|[m_dwRef](#m_dwref)|与`m_pOuterUnknown`、 并集的一部分。 使用时不会聚合该对象来保存的引用计数`AddRef`和**版本**。|  
|[m_pOuterUnknown](#m_pouterunknown)|与`m_dwRef`、 并集的一部分。 聚合对象以容纳到未知的外部对象的指针时使用。|  
  
## <a name="remarks"></a>备注  
 `CComObjectRootEx` 处理非聚合和聚合对象的对象引用计数管理。 如果你的对象不正在聚合，并且如果你的对象进行了正在聚合包含指向未知的外部对象，它包含的对象引用计数。 对于聚合对象，`CComObjectRootEx`方法可以用于处理失败的内部对象构造，并保护中删除在发布内部接口的外部对象或内部对象删除。  
  
 实现的 COM 服务器的类必须继承自`CComObjectRootEx`或[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)。  
  
 如果你的类定义指定[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)宏，ATL 创建的实例**CComPolyObject\<CYourClass >** 时**IClassFactory::CreateInstance**调用。 在创建期间，会检查未知的外部对象的值。 如果它是**NULL**， **IUnknown**为非聚合对象实现。 如果不是未知的外部对象**NULL**， **IUnknown**为聚合对象实现。  
  
 如果你的类并不指定`DECLARE_POLY_AGGREGATABLE`宏，ATL 创建的实例**CAggComObject\<CYourClass >** 聚合的对象或实例的**CComObject\<CYourClass>** 非聚合对象。  
  
 使用的优点`CComPolyObject`是，你可以避免同时`CComAggObject`和`CComObject`处理聚合和非聚合情况你模块中。 单个`CComPolyObject`对象处理这两种情况。 因此，只有一份 vtable 和函数的一个副本存在于你的模块。 如果你 vtable 很大，这会显著降低模块大小。 但是，如果你 vtable 很小，则使用`CComPolyObject`由于未经过优化聚合或非聚合对象，可能会导致稍大一些的模块大小允许进行`CComAggObject`和`CComObject`。  
  
 如果你的对象进行了聚合， [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)由实现`CComAggObject`或`CComPolyObject`。 这些类委托`QueryInterface`， `AddRef`，和**版本**调用`CComObjectRootEx`的`OuterQueryInterface`， `OuterAddRef`，和`OuterRelease`将转发到未知的外部对象。 通常情况下，重写`CComObjectRootEx::FinalConstruct`在类中创建任何聚合的对象，并重写`CComObjectRootEx::FinalRelease`以释放任何聚合对象。  
  
 如果你的对象未聚合， **IUnknown**由实现`CComObject`或`CComPolyObject`。 在这种情况下，调用`QueryInterface`， `AddRef`，和**版本**委派给`CComObjectRootEx`的`InternalQueryInterface`， `InternalAddRef`，和`InternalRelease`执行实际的操作。  
  
## <a name="requirements"></a>要求  
 **标头：** atlcom.h  
  
##  <a name="ccomobjectrootex"></a>  CComObjectRootEx::CComObjectRootEx  
 构造函数初始化为 0 的引用计数。  
  
```
CComObjectRootEx();
```  
  
##  <a name="finalconstruct"></a>  CComObjectRootEx::FinalConstruct  
 你可以执行任何所需的对象的初始化派生类中重写此方法。  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>返回值  
 返回`S_OK`成功则标准错误之一`HRESULT`值。  
  
### <a name="remarks"></a>备注  
 默认情况下，`CComObjectRootEx::FinalConstruct`只返回`S_OK`。  
  
 有个执行中的初始化优点`FinalConstruct`而不是你的类的构造函数：  
  
-   无法从构造函数，返回状态代码，但你可以返回`HRESULT`通过`FinalConstruct`的返回值。 当使用 ATL 提供的标准类工厂在创建你的类的对象时，此返回值将传播回 COM 客户端可以向他们提供详细的错误信息。  
  
-   不能通过从类的构造函数的虚函数机制调用虚函数。 从一个类的构造函数调用虚函数导致于静态解析函数调用在该点在继承层次结构中定义它。 对于纯虚函数的调用导致链接器错误。  
  
     你的类不是继承层次结构中的派生程度最高的类 — 它依赖于 ATL 提供其部分功能所提供的派生类。 很可能会你初始化将需要使用的该类 （即是如此，当你的类的对象需要聚合其他对象），提供的功能，但你的类中的构造函数还没有方法来访问这些功能。 为您的类的构造代码将执行之前完全构造的派生程度最高的类。  
  
     但是，`FinalConstruct`立即派生程度最后类完全构造，使你可以调用虚函数，并使用 atl 提供的引用计数实现称为  
  
### <a name="example"></a>示例  
 通常情况下，重写此方法在派生自类`CComObjectRootEx`创建任何聚合对象。 例如：  
  
 [!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]  
  
 如果构造失败，你可以返回错误。 你还可以使用宏[DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct)从正在保护你的外部对象删除如果在创建期间，内部聚合的对象递增引用计数然后递减的计数为 0。  
  
 下面是创建聚合的典型方式：  
  
-   添加**IUnknown**指向您的类对象，并将其初始化为**NULL**构造函数中。  
  
-   重写`FinalConstruct`创建聚合。  
  
-   使用**IUnknown**定义为的参数的指针[COM_INTERFACE_ENTRY_AGGREGATE](com-interface-entry-macros.md#com_interface_entry_aggregate)宏。  
  
-   重写`FinalRelease`释放**IUnknown**指针。  
  
##  <a name="finalrelease"></a>  CComObjectRootEx::FinalRelease  
 在派生类来执行你对象所需的任何清理中，可以重写此方法。  
  
```
void FinalRelease();
```  
  
### <a name="remarks"></a>备注  
 默认情况下，`CComObjectRootEx::FinalRelease`不执行任何操作。  
  
 执行在清理`FinalRelease`优于将代码添加到你的类的析构函数，因为在该处的点仍然能够完全构造对象`FinalRelease`调用。 这使您可以安全地访问最多衍生的类提供的方法。 这是对于释放之前删除任何聚合的对象尤为重要。  
  
##  <a name="internaladdref"></a>  CComObjectRootEx::InternalAddRef  
 非聚合对象的引用计数递增 1。  
  
```
ULONG InternalAddRef();
```  
  
### <a name="return-value"></a>返回值  
 一个值，可能是用于诊断和测试。  
  
### <a name="remarks"></a>备注  
 如果线程模型为多线程， **InterlockedIncrement**用于防止多个线程同时更改引用计数。  
  
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
 `pThis`  
 [in]指向包含向公开的接口的 COM 映射的对象的指针`QueryInterface`。  
  
 `pEntries`  
 [in]指向的指针 **_ATL_INTMAP_ENTRY**访问可用接口映射的结构。  
  
 `iid`  
 [in]所请求接口的 GUID。  
  
 `ppvObject`  
 [out]指向中指定的接口指针的指针`iid`，或**NULL**如果找不到该接口。  
  
### <a name="return-value"></a>返回值  
 一个标准`HRESULT`值。  
  
### <a name="remarks"></a>备注  
 `InternalQueryInterface` 仅处理 COM 映射表中的接口。 如果你的对象进行了聚合，`InternalQueryInterface`不未将委托给未知的外部对象。 可以接口输入到 COM 映射表与宏[COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry)或其变化版本之一。  
  
##  <a name="internalrelease"></a>  CComObjectRootEx::InternalRelease  
 递减引用非聚合对象的计数加 1。  
  
```
ULONG InternalRelease();
```  
  
### <a name="return-value"></a>返回值  
 在同时非调试和调试版本，此函数将返回一个值，该值可能是用于诊断或测试。 取决于许多因素，例如操作系统使用，并可能，或可能不返回的确切的值，请引用计数。  
  
### <a name="remarks"></a>备注  
 如果线程模型为多线程， **InterlockedDecrement**用于防止多个线程同时更改引用计数。  
  
##  <a name="lock"></a>  CComObjectRootEx::Lock  
 如果线程模型为多线程，此方法调用 Win32 API 函数[EnterCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682608)，通过的私有数据成员获取哪些等待线程可以获得的关键部分对象的所有权。  
  
```
void Lock();
```  
  
### <a name="remarks"></a>备注  
 当受保护的代码执行完毕后时，必须调用线程`Unlock`可释放的关键部分的所有权。  
  
 如果线程模型是单线程方式，则此方法没有任何影响。  
  
##  <a name="m_dwref"></a>  CComObjectRootEx::m_dwRef  
 访问的内存的四个字节的联合的一部分。  
  
```
long m_dwRef;
```  
  
### <a name="remarks"></a>备注  
 与`m_pOuterUnknown`、 并集的一部分：  
  
 `union`  
  
 `{`  
  
 `long m_dwRef;`  
  
 `IUnknown* m_pOuterUnknown;`  
  
 `};`  
  
 如果对象不会聚合，访问引用计数`AddRef`和**版本**存储在`m_dwRef`。 如果对象进行了聚合，指向未知的外部对象的指针存储在[m_pOuterUnknown](#m_pouterunknown)。  
  
##  <a name="m_pouterunknown"></a>  CComObjectRootEx::m_pOuterUnknown  
 访问的内存的四个字节的联合的一部分。  
  
```
IUnknown*
    m_pOuterUnknown;
```     
  
### <a name="remarks"></a>备注  
 与`m_dwRef`、 并集的一部分：  
  
 `union`  
  
 `{`  
  
 `long m_dwRef;`  
  
 `IUnknown* m_pOuterUnknown;`  
  
 `};`  
  
 如果对象进行了聚合，指向未知的外部对象的指针存储在`m_pOuterUnknown`。 如果对象不会聚合，访问引用计数`AddRef`和**版本**存储在[m_dwRef](#m_dwref)。  
  
##  <a name="objectmain"></a>  CComObjectRootEx::ObjectMain  
 中列出每个类[对象映射](http://msdn.microsoft.com/en-us/b57619cc-534f-4b8f-bfd4-0c12f937202f)，一旦初始化模块时，调用此函数并且再次时它已被终止。  
  
```
static void WINAPI ObjectMain(bool bStarting);
```  
  
### <a name="parameters"></a>参数  
 `bStarting`  
 [out]值是**true**对类进行初始化; 否则为如果**false**。  
  
### <a name="remarks"></a>备注  
 值`bStarting`参数指示是否模块正在初始化或终止。 默认实现`ObjectMain`不执行任何操作，但可以在您初始化或清理你想要为该类分配的资源的类中重写此函数。 请注意，`ObjectMain`在请求的类的任何实例之前调用。  
  
 `ObjectMain` 从调用 DLL 的入口点的入口点函数可以执行的操作的类型而受限制。 有关这些限制的详细信息，请参阅[Dll 和 Visual c + + 运行库行为](../../build/run-time-library-behavior.md)和[DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]  
  
##  <a name="outeraddref"></a>  CComObjectRootEx::OuterAddRef  
 递增未知聚合的外部对象的引用计数。  
  
```
ULONG OuterAddRef();
```  
  
### <a name="return-value"></a>返回值  
 一个值，可能是用于诊断和测试。  
  
##  <a name="outerqueryinterface"></a>  CComObjectRootEx::OuterQueryInterface  
 检索指向所请求的接口的间接指针。  
  
```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]所请求接口的 GUID。  
  
 `ppvObject`  
 [out]指向中指定的接口指针的指针`iid`，或**NULL**如果聚合不支持该接口。  
  
### <a name="return-value"></a>返回值  
 一个标准`HRESULT`值。  
  
##  <a name="outerrelease"></a>  CComObjectRootEx::OuterRelease  
 递减引用计数的聚合的未知的外部对象。  
  
```
ULONG OuterRelease();
```  
  
### <a name="return-value"></a>返回值  
 在非调试版本中，始终返回 0。 在调试版本中，返回一个值，可能是用于诊断或测试。  
  
##  <a name="unlock"></a>  CComObjectRootEx::Unlock  
 如果线程模型为多线程，此方法调用 Win32 API 函数[LeaveCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms684169)，通过的私有数据成员获取关键部分对象的哪些版本所有权。  
  
```
void Unlock();
```  
  
### <a name="remarks"></a>备注  
 若要获取所有权，线程必须调用`Lock`。 每次调用`Lock`需要相应地调用`Unlock`可释放的关键部分的所有权。  
  
 如果线程模型是单线程方式，则此方法没有任何影响。  
  
## <a name="see-also"></a>请参阅  
 [CComAggObject 类](../../atl/reference/ccomaggobject-class.md)   
 [CComObject 类](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject 类](../../atl/reference/ccompolyobject-class.md)   
 [类概述](../../atl/atl-class-overview.md)
