---
title: "CComMultiThreadModel 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModel::CriticalSection
- ATLBASE/ATL::CComMultiThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModel::Decrement
- ATLBASE/ATL::CComMultiThreadModel::Increment
dev_langs:
- C++
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModel class
- threading [ATL]
ms.assetid: db8f1662-2f7a-44b3-b341-ffbfb6e422a3
caps.latest.revision: 21
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 6dbfb33a717b23e8252c9bcb2fc11b4a6e420280
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="ccommultithreadmodel-class"></a>CComMultiThreadModel 类
`CComMultiThreadModel`提供用于递增和递减的变量值的线程安全的方法。  
  
## <a name="syntax"></a>语法  
  
```
class CComMultiThreadModel
```  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|说明|  
|----------|-----------------|  
|[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)|引用类[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)。|  
|[CComMultiThreadModel::CriticalSection](#criticalsection)|引用类[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)。|  
|[CComMultiThreadModel::ThreadModelNoCS](#threadmodelnocs)|引用类[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComMultiThreadModel::Decrement](#decrement)|（静态）递减指定变量以线程安全的方式的值。|  
|[CComMultiThreadModel::Increment](#increment)|（静态）指定变量的值递增以线程安全的方式。|  
  
## <a name="remarks"></a>备注  
 通常，您可以使用`CComMultiThreadModel`通过两种`typedef`名称、 任一 [CComObjectThreadModel] (atl typedefs.md #ccomobjectthreadmodel 或 [CComGlobalsThreadModel] (atl typedefs.md #ccomglobalsthreadmodel。 由每个引用的类`typedef`，所使用的线程模型取决于下表中所示︰  
  
|typedef|单线程|单元线程处理|自由线程处理|  
|-------------|----------------------|-------------------------|--------------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S= `CComSingleThreadModel`;M =`CComMultiThreadModel`  
  
 `CComMultiThreadModel`本身定义三个`typedef`名称。 `AutoCriticalSection`和`CriticalSection`引用用于获取和释放关键节的所有权提供方法的类。 `ThreadModelNoCS`引用类 [CComMultiThreadModelNoCS(ccommultithreadmodelnocs-class.md)。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlbase.h  
  
##  <a name="autocriticalsection"></a>CComMultiThreadModel::AutoCriticalSection  
 当使用`CComMultiThreadModel`、`typedef`名称`AutoCriticalSection`引用类[CComAutoCriticalSection](ccomautocriticalsection-class.md)，它提供用于获取和释放关键节对象的所有权的方法。  
  
```
typedef CComAutoCriticalSection AutoCriticalSection;
```  
  
### <a name="remarks"></a>备注  
 [CComSingleThreadModel](ccomsinglethreadmodel-class.md)和[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)还包含定义`AutoCriticalSection`。 下表显示的线程模型类与所引用的关键部分类之间的关系`AutoCriticalSection`:  
  
|中定义的类|引用类|  
|----------------------|----------------------|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
  
 除了`AutoCriticalSection`，您可以使用`typedef`名称[CriticalSection](#criticalsection)。 不应指定`AutoCriticalSection`全局对象或如果您想要消除 CRT 启动代码的静态类成员中。  
  
### <a name="example"></a>示例  
 下面的代码建模后[CComObjectRootEx](ccomobjectrootex-class.md)，并演示`AutoCriticalSection`线程环境中正在使用。  
  

```cpp  
template<class ThreadModel>
class CMyAutoCritClass
{
public:
   typedef ThreadModel _ThreadModel;
   typedef typename _ThreadModel::AutoCriticalSection _CritSec;

   CMyAutoCritClass() : m_dwRef(0) {}

   ULONG InternalAddRef()
   {
      return _ThreadModel::Increment(&m_dwRef);
   }
   ULONG InternalRelease()
   {
      return _ThreadModel::Decrement(&m_dwRef);   
   }
   void Lock() { m_critsec.Lock( ); }
   void Unlock() { m_critsec.Unlock(); }

private:
   _CritSec m_critsec;
   LONG m_dwRef;
```  
  
 下表显示的结果`InternalAddRef`和`Lock`方法，具体取决于**ThreadModel**模板参数和应用程序所使用的线程模型︰  
  
### <a name="threadmodel--ccomobjectthreadmodel"></a>ThreadModel = CComObjectThreadModel  
  
|方法|单个或单元线程处理|自由线程处理|  
|------------|-----------------------------------|--------------------|  
|`InternalAddRef`|增量不是线程安全的。|增量是线程安全的。|  
|`Lock`|未执行任何操作;没有要锁定关键节。|锁定关键节。|  
  
### <a name="threadmodel--ccomobjectthreadmodelthreadmodelnocs"></a>ThreadModel = CComObjectThreadModel::ThreadModelNoCS  
  
|方法|单个或单元线程处理|自由线程处理|  
|------------|-----------------------------------|--------------------|  
|`InternalAddRef`|增量不是线程安全的。|增量是线程安全的。|  
|`Lock`|未执行任何操作;没有要锁定关键节。|未执行任何操作;没有要锁定关键节。|  
  
##  <a name="criticalsection"></a>CComMultiThreadModel::CriticalSection  
 当使用`CComMultiThreadModel`、`typedef`名称`CriticalSection`引用类[CComCriticalSection](ccomcriticalsection-class.md)，它提供用于获取和释放关键节对象的所有权的方法。  
  
```
typedef CComCriticalSection CriticalSection;
```  
  
### <a name="remarks"></a>备注  
 [CComSingleThreadModel](ccomsinglethreadmodel-class.md)和[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)还包含定义`CriticalSection`。 下表显示的线程模型类与所引用的关键部分类之间的关系`CriticalSection`:  
  
|中定义的类|引用类|  
|----------------------|----------------------|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
  
 除了`CriticalSection`，您可以使用`typedef`名称[AutoCriticalSection](#autocriticalsection)。 不应指定`AutoCriticalSection`全局对象或如果您想要消除 CRT 启动代码的静态类成员中。  
  
### <a name="example"></a>示例  
 请参阅[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)。  
  
##  <a name="decrement"></a>CComMultiThreadModel::Decrement  
 此静态函数将调用 Win32 函数[InterlockedDecrement](http://msdn.microsoft.com/library/windows/desktop/ms683580)，这由指向变量的值将减少`p`。  
  
```
static ULONG WINAPI Decrement(LPLONG p) throw ();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 [in]指向要递减的变量的指针。  
  
### <a name="return-value"></a>返回值  
 如果减法的结果为 0，则`Decrement`，则返回 0。 如果减法的结果不为零，则返回值也为非零值，但可能不等于减法的结果。  
  
### <a name="remarks"></a>备注  
 **InterlockedDecrement**防止多个线程同时使用此变量。  
  
##  <a name="increment"></a>CComMultiThreadModel::Increment  
 此静态函数将调用 Win32 函数[InterlockedIncrement](http://msdn.microsoft.com/library/windows/desktop/ms683614)，变量所指向的值时都会增加`p`。  
  
```
static ULONG WINAPI Increment(LPLONG p) throw ();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 [in]指向要递增的变量的指针。  
  
### <a name="return-value"></a>返回值  
 如果增量结果为 0，则**增量**，则返回 0。 如果增量结果不为零，则返回值也为非零值，但可能抵不上的增量结果。  
  
### <a name="remarks"></a>备注  
 **InterlockedIncrement**防止多个线程同时使用此变量。  
  
##  <a name="threadmodelnocs"></a>CComMultiThreadModel::ThreadModelNoCS  
 当使用`CComMultiThreadModel`、`typedef`名称`ThreadModelNoCS`引用类[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)。  
  
```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```  
  
### <a name="remarks"></a>备注  
 `CComMultiThreadModelNoCS`提供用于递增和递减变量，例如︰ 线程安全的方法但是，它不提供关键部分。  
  
 [CComSingleThreadModel](ccomsinglethreadmodel-class.md)和`CComMultiThreadModelNoCS`还包含定义`ThreadModelNoCS`。 下表显示的线程模型类与所引用的类之间的关系`ThreadModelNoCS`:  
  
|中定义的类|引用类|  
|----------------------|----------------------|  
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|  
|`CComSingleThreadModel`|`CComSingleThreadModel`|  
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|  
  
### <a name="example"></a>示例  
 请参阅[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)。  
  
## <a name="see-also"></a>另请参阅  
 [CComSingleThreadModel 类](ccomsinglethreadmodel-class.md)   
 [CComAutoCriticalSection 类](ccomautocriticalsection-class.md)   
 [CComCriticalSection 类](ccomcriticalsection-class.md)   
 [类概述](../atl-class-overview.md)

