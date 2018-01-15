---
title: "CComMultiThreadModel 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModel class
- threading [ATL]
ms.assetid: db8f1662-2f7a-44b3-b341-ffbfb6e422a3
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 96f8c24736309ef1030664ee0fd466537d739496
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ccommultithreadmodel-class"></a>CComMultiThreadModel 类
`CComMultiThreadModel`提供用于递增和递减的变量的值的线程安全的方法。  
  
## <a name="syntax"></a>语法  
  
```
class CComMultiThreadModel
```  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)|引用类[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)。|  
|[CComMultiThreadModel::CriticalSection](#criticalsection)|引用类[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)。|  
|[CComMultiThreadModel::ThreadModelNoCS](#threadmodelnocs)|引用类[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComMultiThreadModel::Decrement](#decrement)|（静态）递减指定变量以线程安全的方式的值。|  
|[CComMultiThreadModel::Increment](#increment)|（静态）线程安全的方式递增指定变量的值。|  
  
## <a name="remarks"></a>备注  
 通常情况下，使用`CComMultiThreadModel`通过两个类之一`typedef`名称、 任一 [CComObjectThreadModel] (atl typedefs.md #ccomobjectthreadmodel 或 [CComGlobalsThreadModel] (atl typedefs.md #ccomglobalsthreadmodel。 每个所引用类`typedef`依赖于使用的线程处理模型下, 表中所示：  
  
|typedef|单个线程处理|单元线程处理|自由线程处理|  
|-------------|----------------------|-------------------------|--------------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S = `CComSingleThreadModel`;M =`CComMultiThreadModel`  
  
 `CComMultiThreadModel`本身定义三个`typedef`名称。 `AutoCriticalSection`和`CriticalSection`引用用于获取和释放临界区的所有权提供的方法的类。 `ThreadModelNoCS`引用类 [CComMultiThreadModelNoCS(ccommultithreadmodelnocs-class.md)。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlbase.h  
  
##  <a name="autocriticalsection"></a>CComMultiThreadModel::AutoCriticalSection  
 使用时`CComMultiThreadModel`、`typedef`名称`AutoCriticalSection`引用类[CComAutoCriticalSection](ccomautocriticalsection-class.md)，用于获取和释放的关键部分对象的所有权提供方法。  
  
```
typedef CComAutoCriticalSection AutoCriticalSection;
```  
  
### <a name="remarks"></a>备注  
 [CComSingleThreadModel](ccomsinglethreadmodel-class.md)和[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)还包含定义`AutoCriticalSection`。 下表显示的线程处理模型类和所引用的关键部分类之间的关系`AutoCriticalSection`:  
  
|在中定义的类|所引用类|  
|----------------------|----------------------|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
  
 除了`AutoCriticalSection`，你可以使用`typedef`名称[CriticalSection](#criticalsection)。 不应指定`AutoCriticalSection`在全局对象或如果你想要消除 CRT 启动代码的静态类成员中。  
  
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
  
 下表显示的结果`InternalAddRef`和`Lock`方法，具体取决于**ThreadModel**模板参数和应用程序使用的线程模型：  
  
### <a name="threadmodel--ccomobjectthreadmodel"></a>ThreadModel = CComObjectThreadModel  
  
|方法|单或单元线程处理|自由线程处理|  
|------------|-----------------------------------|--------------------|  
|`InternalAddRef`|增量不是线程安全。|增量是线程安全。|  
|`Lock`|未执行任何操作;没有任何锁定的关键部分。|关键节被锁定。|  
  
### <a name="threadmodel--ccomobjectthreadmodelthreadmodelnocs"></a>ThreadModel = CComObjectThreadModel::ThreadModelNoCS  
  
|方法|单或单元线程处理|自由线程处理|  
|------------|-----------------------------------|--------------------|  
|`InternalAddRef`|增量不是线程安全。|增量是线程安全。|  
|`Lock`|未执行任何操作;没有任何锁定的关键部分。|未执行任何操作;没有任何锁定的关键部分。|  
  
##  <a name="criticalsection"></a>CComMultiThreadModel::CriticalSection  
 使用时`CComMultiThreadModel`、`typedef`名称`CriticalSection`引用类[CComCriticalSection](ccomcriticalsection-class.md)，用于获取和释放的关键部分对象的所有权提供方法。  
  
```
typedef CComCriticalSection CriticalSection;
```  
  
### <a name="remarks"></a>备注  
 [CComSingleThreadModel](ccomsinglethreadmodel-class.md)和[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)还包含定义`CriticalSection`。 下表显示的线程处理模型类和所引用的关键部分类之间的关系`CriticalSection`:  
  
|在中定义的类|所引用类|  
|----------------------|----------------------|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
  
 除了`CriticalSection`，你可以使用`typedef`名称[AutoCriticalSection](#autocriticalsection)。 不应指定`AutoCriticalSection`在全局对象或如果你想要消除 CRT 启动代码的静态类成员中。  
  
### <a name="example"></a>示例  
 请参阅[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)。  
  
##  <a name="decrement"></a>CComMultiThreadModel::Decrement  
 此静态函数将调用 Win32 函数[InterlockedDecrement](http://msdn.microsoft.com/library/windows/desktop/ms683580)，指向变量的值的递减`p`。  
  
```
static ULONG WINAPI Decrement(LPLONG p) throw ();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 [in]指向要递减的变量的指针。  
  
### <a name="return-value"></a>返回值  
 如果递减的结果为 0，则`Decrement`返回 0。 减法的结果不为零，如果返回值也为非零值，但可能不是递减的结果。  
  
### <a name="remarks"></a>备注  
 **InterlockedDecrement**防止多个线程同时使用此变量。  
  
##  <a name="increment"></a>CComMultiThreadModel::Increment  
 此静态函数将调用 Win32 函数[InterlockedIncrement](http://msdn.microsoft.com/library/windows/desktop/ms683614)，指向的变量的值时都会增加`p`。  
  
```
static ULONG WINAPI Increment(LPLONG p) throw ();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 [in]指向要递增的变量的指针。  
  
### <a name="return-value"></a>返回值  
 如果增量的结果为 0，则**递增**返回 0。 如果增量的结果不为零，返回值也为非零值，但可能抵不上的增量结果。  
  
### <a name="remarks"></a>备注  
 **InterlockedIncrement**防止多个线程同时使用此变量。  
  
##  <a name="threadmodelnocs"></a>CComMultiThreadModel::ThreadModelNoCS  
 使用时`CComMultiThreadModel`、`typedef`名称`ThreadModelNoCS`引用类[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)。  
  
```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```  
  
### <a name="remarks"></a>备注  
 `CComMultiThreadModelNoCS`提供用于递增和递减变量，例如： 的线程安全的方法但是，它不提供关键部分。  
  
 [CComSingleThreadModel](ccomsinglethreadmodel-class.md)和`CComMultiThreadModelNoCS`还包含定义`ThreadModelNoCS`。 下表显示的线程处理模型类和所引用的类之间的关系`ThreadModelNoCS`:  
  
|在中定义的类|所引用类|  
|----------------------|----------------------|  
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|  
|`CComSingleThreadModel`|`CComSingleThreadModel`|  
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|  
  
### <a name="example"></a>示例  
 请参阅[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)。  
  
## <a name="see-also"></a>请参阅  
 [CComSingleThreadModel 类](ccomsinglethreadmodel-class.md)   
 [CComAutoCriticalSection 类](ccomautocriticalsection-class.md)   
 [CComCriticalSection 类](ccomcriticalsection-class.md)   
 [类概述](../atl-class-overview.md)
