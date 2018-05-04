---
title: CComMultiThreadModelNoCS 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::CriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::Decrement
- ATLBASE/ATL::CComMultiThreadModelNoCS::Increment
dev_langs:
- C++
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModelNoCS class
- threading [ATL]
ms.assetid: 2b3f7a45-fd72-452c-aaf3-ccdaa621c821
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 758811b10757cd7903b4f1d6218a5f34f8a98462
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="ccommultithreadmodelnocs-class"></a>CComMultiThreadModelNoCS 类
`CComMultiThreadModelNoCS` 提供线程安全的方法的递增和递减值的变量中，而无需临界区锁定或解锁功能。  
  
## <a name="syntax"></a>语法  
  
```
class CComMultiThreadModelNoCS
```  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|[CComMultiThreadModelNoCS::AutoCriticalSection](#autocriticalsection)|引用类[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。|  
|[CComMultiThreadModelNoCS::CriticalSection](#criticalsection)|引用类`CComFakeCriticalSection`。|  
|[CComMultiThreadModelNoCS::ThreadModelNoCS](#threadmodelnocs)|引用类`CComMultiThreadModelNoCS`。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComMultiThreadModelNoCS::Decrement](#decrement)|（静态）递减指定变量以线程安全的方式的值。|  
|[CComMultiThreadModelNoCS::Increment](#increment)|（静态）线程安全的方式递增指定变量的值。|  
  
## <a name="remarks"></a>备注  
 `CComMultiThreadModelNoCS` 类似于[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)在于它提供线程安全方法递增和递减的变量。 但是，当引用的关键部分类通过`CComMultiThreadModelNoCS`，等方法`Lock`和`Unlock`将不执行任何操作。  
  
 通常情况下，使用`CComMultiThreadModelNoCS`通过`ThreadModelNoCS``typedef`名称。 这`typedef`中定义`CComMultiThreadModelNoCS`， `CComMultiThreadModel`，和[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)。  
  
> [!NOTE]
>  全局`typedef`名称[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)和[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)不引用`CComMultiThreadModelNoCS`。  
  
 除了`ThreadModelNoCS`，`CComMultiThreadModelNoCS`定义`AutoCriticalSection`和`CriticalSection`。 这些后的两个`typedef`名称引用[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)，提供与获取和释放临界区关联的空方法。  
  
## <a name="requirements"></a>要求  
 **标头：** atlbase.h  
  
##  <a name="autocriticalsection"></a>  CComMultiThreadModelNoCS::AutoCriticalSection  
 使用时`CComMultiThreadModelNoCS`、`typedef`名称`AutoCriticalSection`引用类[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。  
  
```
typedef CComFakeCriticalSection AutoCriticalSection;
```  
  
### <a name="remarks"></a>备注  
 因为`CComFakeCriticalSection`不提供一个临界区，其方法不执行任何操作。  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)还包含定义`AutoCriticalSection`。 下表显示的线程处理模型类和所引用的关键部分类之间的关系`AutoCriticalSection`:  
  
|在中定义的类|所引用类|  
|----------------------|----------------------|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComAutoCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
  
 除了`AutoCriticalSection`，你可以使用`typedef`名称[CriticalSection](#criticalsection)。 不应指定`AutoCriticalSection`在全局对象或如果你想要消除 CRT 启动代码的静态类成员中。  
  
### <a name="example"></a>示例  
 请参阅[CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。  
  
##  <a name="criticalsection"></a>  CComMultiThreadModelNoCS::CriticalSection  
 使用时`CComMultiThreadModelNoCS`、`typedef`名称`CriticalSection`引用类[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。  
  
```
typedef CComFakeCriticalSection CriticalSection;
```  
  
### <a name="remarks"></a>备注  
 因为`CComFakeCriticalSection`不提供一个临界区，其方法不执行任何操作。  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)还包含定义`CriticalSection`。 下表显示的线程处理模型类和所引用的关键部分类之间的关系`CriticalSection`:  
  
|在中定义的类|所引用类|  
|----------------------|----------------------|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
  
 除了`CriticalSection`，你可以使用`typedef`名称`AutoCriticalSection`。 不应指定`AutoCriticalSection`在全局对象或如果你想要消除 CRT 启动代码的静态类成员中。  
  
### <a name="example"></a>示例  
 请参阅[CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。  
  
##  <a name="decrement"></a>  CComMultiThreadModelNoCS::Decrement  
 此静态函数将调用 Win32 函数[InterlockedDecrement](http://msdn.microsoft.com/library/windows/desktop/ms683580)，指向变量的值的递减`p`。  
  
```
static ULONG WINAPI Decrement(LPLONG p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 [in]指向要递减的变量的指针。  
  
### <a name="return-value"></a>返回值  
 如果递减的结果为 0，则`Decrement`返回 0。 减法的结果不为零，如果返回值也为非零值，但可能不是递减的结果。  
  
### <a name="remarks"></a>备注  
 **InterlockedDecrement**防止多个线程同时使用此变量。  
  
##  <a name="increment"></a>  CComMultiThreadModelNoCS::Increment  
 此静态函数将调用 Win32 函数[InterlockedIncrement](http://msdn.microsoft.com/library/windows/desktop/ms683614)，指向的变量的值时都会增加`p`。  
  
```
static ULONG WINAPI Increment(LPLONG p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 [in]指向要递增的变量的指针。  
  
### <a name="return-value"></a>返回值  
 如果增量的结果为 0，则**递增**返回 0。 如果增量的结果不为零，返回值也为非零值，但可能抵不上的增量结果。  
  
### <a name="remarks"></a>备注  
 **InterlockedIncrement**防止多个线程同时使用此变量。  
  
##  <a name="threadmodelnocs"></a>  CComMultiThreadModelNoCS::ThreadModelNoCS  
 使用时`CComMultiThreadModelNoCS`、`typedef`名称`ThreadModelNoCS`只引用`CComMultiThreadModelNoCS`。  
  
```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```  
  
### <a name="remarks"></a>备注  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)还包含定义`ThreadModelNoCS`。 下表显示的线程处理模型类和所引用的类之间的关系`ThreadModelNoCS`:  
  
|在中定义的类|所引用类|  
|----------------------|----------------------|  
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|  
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|  
|`CComSingleThreadModel`|`CComSingleThreadModel`|  
  
 请注意，定义`ThreadModelNoCS`中`CComMultiThreadModelNoCS`提供与对称性`CComMultiThreadModel`和`CComSingleThreadModel`。 例如，假设中的示例代码`CComMultiThreadModel::AutoCriticalSection`声明以下`typedef`:  
  
 [!code-cpp[NVC_ATL_COM#37](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]  
  
 无论为指定的类`ThreadModel`(如`CComMultiThreadModelNoCS`)，`_ThreadModel`相应地解析。  
  
### <a name="example"></a>示例  
 请参阅[CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)