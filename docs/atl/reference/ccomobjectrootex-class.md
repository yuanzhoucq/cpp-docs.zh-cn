---
title: "CComObjectRootEx 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComObjectRootEx
- ATLCOM/ATL::CComObjectRootEx
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
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: f3a6d26ddb4f612824f959ca3046531dc3bbf2a9
ms.lasthandoff: 02/24/2017

---
# <a name="ccomobjectrootex-class"></a>CComObjectRootEx 类
此类提供方法来处理非聚合和聚合对象的对象引用计数管理。  
  
## <a name="syntax"></a>语法  
  
```
template<class ThreadModel>  
class CComObjectRootEx : public CComObjectRootBase
```  
  
#### <a name="parameters"></a>参数  
 `ThreadModel`  
 类的方法实现所需的线程模型。 您可以显式选择的线程模型，通过设置`ThreadModel`到[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)， [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)，或[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。 您可以通过设置接受服务器的默认线程模型`ThreadModel`到[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)或[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)。  

  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CComObjectRootEx](#ccomobjectrootex)|构造函数。|  
|[InternalAddRef](#internaladdref)|递增非聚合对象的引用的计数。|  
|[InternalRelease](#internalrelease)|递减引用计数的非聚合的对象。|  
|[锁](#lock)|如果线程模型为多线程，会获得关键部分对象的所有权。|  
|[解除锁定](#unlock)|如果线程模型为多线程，将释放关键节对象的所有权。|  
  
### <a name="ccomobjectrootbase-methods"></a>CComObjectRootBase 方法  
  
|||  
|-|-|  
|[FinalConstruct](#finalconstruct)|在您执行任何所需的对象的初始化的类中重写。|  
|[FinalRelease](#finalrelease)|在执行任何所需的对象的清理您的类中重写。|  
|[OuterAddRef](#outeraddref)|递增的聚合对象的引用计数。|  
|[OuterQueryInterface](#outerqueryinterface)|委托给外部**IUnknown**的聚合的对象。|  
|[OuterRelease](#outerrelease)|递减引用计数的聚合对象。|  
  
### <a name="static-functions"></a>静态函数  
  
|||  
|-|-|  
|[InternalQueryInterface](#internalqueryinterface)|委托给**IUnknown**的非聚合对象。|  
|[ObjectMain](#objectmain)|在模块初始化和终止时为在对象映射中列出的派生类调用。|  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|[m_dwRef](#m_dwref)|与`m_pOuterUnknown`、 并集的一部分。 当对象不聚合来保存的引用计数时，使用`AddRef`和**版本**。|  
|[m_pOuterUnknown](#m_pouterunknown)|与`m_dwRef`、 并集的一部分。 聚合对象以容纳到未知的外部对象的指针时使用。|  
  
## <a name="remarks"></a>备注  
 `CComObjectRootEx`处理非聚合和聚合对象的对象引用计数管理。 如果您的对象未正在聚合，并且如果您的对象进行了正在聚合包含指向未知的外部对象，它保留对象引用计数。 对于聚合的对象，`CComObjectRootEx`方法可以用于处理在内部对象的错误，若要构造，并以保护中删除，如果发布的内部接口的外部对象或内部对象被删除。  
  
 COM 服务器实现的类必须继承自`CComObjectRootEx`或[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)。  
  
 如果您的类定义指定[DECLARE_POLY_AGGREGATABLE](http://msdn.microsoft.com/library/7569e738-cfbc-4404-ba1d-78dcefa3bdb3)宏，ATL 创建的一个实例**CComPolyObject\<CYourClass&1;>**时**IClassFactory::CreateInstance**调用。 在创建过程中，将检查未知的外部对象的值。 如果它是**NULL**， **IUnknown**对于非聚合对象的实现。 如果不是未知的外部对象**NULL**， **IUnknown**聚合对象实现。  
  
 如果您的类没有指定`DECLARE_POLY_AGGREGATABLE`宏，ATL 创建的一个实例**CAggComObject\<CYourClass&1;>**聚合的对象或实例的**CComObject\<CYourClass&1;>**的非聚合对象。  
  
 使用的优点`CComPolyObject`是避免同时`CComAggObject`和`CComObject`模块来处理聚合的和非聚合情况中。 单个`CComPolyObject`对象处理这两种情况。 因此，只有一份 vtable 和函数的一个副本存在在模块中。 如果您 vtable 很大，这可以显著减少模块大小。 但是，如果您 vtable 很小，则使用`CComPolyObject`可能会导致稍大一些的模块的大小，因为它不优化聚合或非聚合对象，允许进行`CComAggObject`和`CComObject`。  
  
 如果您的对象进行了聚合， [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)由实现`CComAggObject`或`CComPolyObject`。 这些类委派`QueryInterface`， `AddRef`，和**版本**调用`CComObjectRootEx`的`OuterQueryInterface`， `OuterAddRef`，和`OuterRelease`将转发到未知的外部对象。 通常情况下，重写`CComObjectRootEx::FinalConstruct`在类中创建任何聚合的对象，并重写`CComObjectRootEx::FinalRelease`以释放任何聚合对象。  
  
 如果您的对象不会累计， **IUnknown**由实现`CComObject`或`CComPolyObject`。 在这种情况下，调用`QueryInterface`， `AddRef`，和**版本**委派给`CComObjectRootEx`的`InternalQueryInterface`， `InternalAddRef`，和`InternalRelease`来执行实际操作。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="ccomobjectrootex"></a>CComObjectRootEx::CComObjectRootEx  
 构造函数将初始化为 0 的引用计数。  
  
```
CComObjectRootEx();
```  
  
##  <a name="finalconstruct"></a>CComObjectRootEx::FinalConstruct  
 您可以执行任何所需的对象的初始化派生类中重写此方法。  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>返回值  
 返回`S_OK`成功，则其中一个标准错误`HRESULT`值。  
  
### <a name="remarks"></a>备注  
 默认情况下，`CComObjectRootEx::FinalConstruct`只是返回`S_OK`。  
  
 有一些好处执行中的初始化`FinalConstruct`而不是您的类的构造函数︰  
  
-   您不能从一个构造函数，返回状态代码，但可以返回`HRESULT`通过`FinalConstruct`的返回值。 当正在使用由 ATL 提供的标准类工厂创建您的类的对象时，该返回值被传播回 COM 客户端，从而可以向他们提供详细的错误信息。  
  
-   不能通过从某个类的构造函数的虚函数机制调用虚函数。 从类的构造函数调用虚函数会导致对函数的静态解析调用继承层次结构中定义在该点。 对于纯虚函数的调用导致链接器错误。  
  
     您的类不是继承层次结构中的派生程度最大的类 — — 它依赖于 ATL 提供其部分功能所提供的派生类。 很可能您初始化将需要使用的该类 （即是如此，当您的类的对象需要聚合的其他对象），提供的功能，但在您的类构造函数具有无法访问这些功能。 您的类的构造代码完全构造的派生程度最高的类之前执行。  
  
     但是，`FinalConstruct`立即派生程度最之后完全构造类使您可以调用虚函数和使用 atl 提供的引用计数实现称为  
  
### <a name="example"></a>示例  
 通常情况下，重写此方法在派生类中的`CComObjectRootEx`创建任何聚合对象。 例如:   
  
 [!code-cpp[NVC_ATL_COM&#40;](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]  
  
 如果构建出现故障，可以返回错误。 您还可以使用该宏[DECLARE_PROTECT_FINAL_CONSTRUCT](http://msdn.microsoft.com/library/2d2e5ddc-057a-43ca-87c8-d3477a8193a0)阻碍保护您的外部对象删除如果创建过程中，内部聚合的对象递增引用计数则递减计数为 0。  
  
 下面是创建聚合的典型方式︰  
  
-   添加**IUnknown**指针，指向您的类对象，并将其初始化为**NULL**构造函数中。  
  
-   重写`FinalConstruct`若要创建的聚合。  
  
-   使用**IUnknown**指针作为参数定义[COM_INTERFACE_ENTRY_AGGREGATE](http://msdn.microsoft.com/library/c671fa40-a57b-4797-ae88-c9762dabd4dc)宏。  
  
-   重写`FinalRelease`释放**IUnknown**指针。  
  
##  <a name="finalrelease"></a>CComObjectRootEx::FinalRelease  
 在派生类来执行您的对象所需的任何清理操作中，可以重写此方法。  
  
```
void FinalRelease();
```  
  
### <a name="remarks"></a>备注  
 默认情况下，`CComObjectRootEx::FinalRelease`不执行任何操作。  
  
 执行清理在`FinalRelease`优于将代码添加到您的类的析构函数，因为在该处的点仍完全构造的对象`FinalRelease`调用。 这使您可以安全地访问提供的派生程度最高的类的方法。 这一点特别重要释放之前删除任何聚合的对象。  
  
##  <a name="internaladdref"></a>CComObjectRootEx::InternalAddRef  
 非聚合对象的引用计数递增 1。  
  
```
ULONG InternalAddRef();
```  
  
### <a name="return-value"></a>返回值  
 一个值，可能会有助于诊断和测试。  
  
### <a name="remarks"></a>备注  
 如果线程模型为多线程、 **InterlockedIncrement**用于防止多个线程同时更改引用计数。  
  
##  <a name="internalqueryinterface"></a>CComObjectRootEx::InternalQueryInterface  
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
 [in]一个指向**_ATL_INTMAP_ENTRY**访问可用的接口映射的结构。  
  
 `iid`  
 [in]正在请求的接口的 GUID。  
  
 `ppvObject`  
 [out]中指定的接口指针指向的指针`iid`，或**NULL**如果找不到该接口。  
  
### <a name="return-value"></a>返回值  
 其中一个标准`HRESULT`值。  
  
### <a name="remarks"></a>备注  
 `InternalQueryInterface` 仅处理 COM 映射表中的接口。 如果您的对象进行了聚合，`InternalQueryInterface`不将委派给未知的外部对象。 接口输入到 COM 映射表与宏[COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)或其变化版本之一。  
  
##  <a name="internalrelease"></a>CComObjectRootEx::InternalRelease  
 递减引用非聚合对象的计数加 1。  
  
```
ULONG InternalRelease();
```  
  
### <a name="return-value"></a>返回值  
 在这两非调试和 debug，此函数将返回一个值，这可能是有用的诊断或测试。 取决于许多因素，例如操作系统使用，并可能，或可能没有返回的确切值，请引用计数。  
  
### <a name="remarks"></a>备注  
 如果线程模型为多线程、 **InterlockedDecrement**用于防止多个线程同时更改引用计数。  
  
##  <a name="lock"></a>CComObjectRootEx::Lock  
 如果线程模型为多线程，则此方法将调用 Win32 API 函数[EnterCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682608)，通过私有数据成员获取的等待线程可以获得关键部分对象的所有权。  
  
```
void Lock();
```  
  
### <a name="remarks"></a>备注  
 当受保护的代码执行完毕后时，必须调用该线程`Unlock`释放关键节的所有权。  
  
 如果线程模型是单线程，则此方法将没有任何效果。  
  
##  <a name="m_dwref"></a>CComObjectRootEx::m_dwRef  
 访问四个字节的内存的联合的一部分。  
  
```
long m_dwRef;
```  
  
### <a name="remarks"></a>备注  
 与`m_pOuterUnknown`、 并集的一部分︰  
  
 `union`  
  
 `{`  
  
 `long m_dwRef;`  
  
 `IUnknown* m_pOuterUnknown;`  
  
 `};`  
  
 如果该对象不会累计，引用计数的访问`AddRef`和**版本**存储在`m_dwRef`。 如果该对象进行了聚合，未知的外部对象的指针存储在[m_pOuterUnknown](#m_pouterunknown)。  
  
##  <a name="m_pouterunknown"></a>CComObjectRootEx::m_pOuterUnknown  
 访问四个字节的内存的联合的一部分。  
  
```
IUnknown*
    m_pOuterUnknown;
```     
  
### <a name="remarks"></a>备注  
 与`m_dwRef`、 并集的一部分︰  
  
 `union`  
  
 `{`  
  
 `long m_dwRef;`  
  
 `IUnknown* m_pOuterUnknown;`  
  
 `};`  
  
 如果该对象进行了聚合，未知的外部对象的指针存储在`m_pOuterUnknown`。 如果该对象不会累计，引用计数的访问`AddRef`和**版本**存储在[m_dwRef](#m_dwref)。  
  
##  <a name="objectmain"></a>CComObjectRootEx::ObjectMain  
 对于每个类中列出[对象映射](http://msdn.microsoft.com/en-us/b57619cc-534f-4b8f-bfd4-0c12f937202f)，一旦初始化模块时，调用此函数并且再次时它已被终止。  
  
```
static void WINAPI ObjectMain(bool bStarting);
```  
  
### <a name="parameters"></a>参数  
 `bStarting`  
 [out]值是**true**对类进行初始化; 否则为如果**false**。  
  
### <a name="remarks"></a>备注  
 值`bStarting`参数指示是否将模块正在初始化或终止。 默认实现`ObjectMain`不起作用，但可以在您初始化或清理你想要为该类分配的资源的类中重写此函数。 请注意，`ObjectMain`请求类的任何实例之前调用。  
  
 `ObjectMain`从调用的 dll 的入口点是受限制的入口点函数可以执行的操作的类型。 有关这些限制的详细信息，请参阅[实时运行库行为](../../build/run-time-library-behavior.md)和[DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM&#41;](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]  
  
##  <a name="outeraddref"></a>CComObjectRootEx::OuterAddRef  
 未知聚合的外部对象的引用计数递增。  
  
```
ULONG OuterAddRef();
```  
  
### <a name="return-value"></a>返回值  
 一个值，可能会有助于诊断和测试。  
  
##  <a name="outerqueryinterface"></a>CComObjectRootEx::OuterQueryInterface  
 检索指向所请求的接口的间接指针。  
  
```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]正在请求的接口的 GUID。  
  
 `ppvObject`  
 [out]中指定的接口指针指向的指针`iid`，或**NULL**如果聚合不支持该接口。  
  
### <a name="return-value"></a>返回值  
 其中一个标准`HRESULT`值。  
  
##  <a name="outerrelease"></a>CComObjectRootEx::OuterRelease  
 递减引用计数的未知聚合的外部对象。  
  
```
ULONG OuterRelease();
```  
  
### <a name="return-value"></a>返回值  
 在非调试版本中，始终返回 0。 在调试版本中，返回一个值，可能是有用的诊断或测试。  
  
##  <a name="unlock"></a>CComObjectRootEx::Unlock  
 如果线程模型为多线程，则此方法将调用 Win32 API 函数[LeaveCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms684169)，通过私有数据成员获取关键部分对象的哪些版本所有权。  
  
```
void Unlock();
```  
  
### <a name="remarks"></a>备注  
 尝试获得所有权，线程必须调用`Lock`。 每次调用`Lock`需要相应地调用`Unlock`释放关键节的所有权。  
  
 如果线程模型是单线程，则此方法将没有任何效果。  
  
## <a name="see-also"></a>另请参阅  
 [CComAggObject 类](../../atl/reference/ccomaggobject-class.md)   
 [CComObject 类](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject 类](../../atl/reference/ccompolyobject-class.md)   
 [类概述](../../atl/atl-class-overview.md)

