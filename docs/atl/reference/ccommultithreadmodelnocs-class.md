---
title: "CComMultiThreadModelNoCS 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CComMultiThreadModelNoCS
- CComMultiThreadModelNoCS
- ATL.CComMultiThreadModelNoCS
dev_langs:
- C++
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModelNoCS class
- threading [ATL]
ms.assetid: 2b3f7a45-fd72-452c-aaf3-ccdaa621c821
caps.latest.revision: 18
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 718aac826916b977eec4fb8400da81b5e32d4afa
ms.lasthandoff: 02/24/2017

---
# <a name="ccommultithreadmodelnocs-class"></a>CComMultiThreadModelNoCS 类
`CComMultiThreadModelNoCS`提供线程安全的方法为递增和递减值的变量中，无需临界区锁定或解锁功能。  
  
## <a name="syntax"></a>语法  
  
```
class CComMultiThreadModelNoCS
```  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|说明|  
|----------|-----------------|  
|[CComMultiThreadModelNoCS::AutoCriticalSection](#autocriticalsection)|引用类[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。|  
|[CComMultiThreadModelNoCS::CriticalSection](#criticalsection)|引用类`CComFakeCriticalSection`。|  
|[CComMultiThreadModelNoCS::ThreadModelNoCS](#threadmodelnocs)|引用类`CComMultiThreadModelNoCS`。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CComMultiThreadModelNoCS::Decrement](#decrement)|（静态）递减指定变量以线程安全的方式的值。|  
|[CComMultiThreadModelNoCS::Increment](#increment)|（静态）指定变量的值递增以线程安全的方式。|  
  
## <a name="remarks"></a>备注  
 `CComMultiThreadModelNoCS`类似于[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) ，因为它提供了线程安全方式递增和递减的变量。 但是，当引用的关键部分类通过`CComMultiThreadModelNoCS`，等方法`Lock`和`Unlock`将不执行任何操作。  
  
 通常，您可以使用`CComMultiThreadModelNoCS`通过`ThreadModelNoCS``typedef`名称。 这`typedef`中定义`CComMultiThreadModelNoCS`， `CComMultiThreadModel`，和[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)。  
  
> [!NOTE]
>  全局`typedef`名称[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)和[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)不引用`CComMultiThreadModelNoCS`。  
  
 除了`ThreadModelNoCS`，`CComMultiThreadModelNoCS`定义`AutoCriticalSection`和`CriticalSection`。 这后一种两个`typedef`名称引用[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)，该属性提供与获取和释放关键节相关联的空方法。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlbase.h  
  
##  <a name="a-nameautocriticalsectiona--ccommultithreadmodelnocsautocriticalsection"></a><a name="autocriticalsection"></a>CComMultiThreadModelNoCS::AutoCriticalSection  
 当使用`CComMultiThreadModelNoCS`、`typedef`名称`AutoCriticalSection`引用类[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。  
  
```
typedef CComFakeCriticalSection AutoCriticalSection;
```  
  
### <a name="remarks"></a>备注  
 因为`CComFakeCriticalSection`不提供一个临界区，其方法不执行任何操作。  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)还包含定义`AutoCriticalSection`。 下表显示的线程模型类与所引用的关键部分类之间的关系`AutoCriticalSection`:  
  
|中定义的类|引用类|  
|----------------------|----------------------|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComAutoCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
  
 除了`AutoCriticalSection`，您可以使用`typedef`名称[CriticalSection](#criticalsection)。 不应指定`AutoCriticalSection`全局对象或如果您想要消除 CRT 启动代码的静态类成员中。  
  
### <a name="example"></a>示例  
 请参阅[CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。  
  
##  <a name="a-namecriticalsectiona--ccommultithreadmodelnocscriticalsection"></a><a name="criticalsection"></a>CComMultiThreadModelNoCS::CriticalSection  
 当使用`CComMultiThreadModelNoCS`、`typedef`名称`CriticalSection`引用类[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。  
  
```
typedef CComFakeCriticalSection CriticalSection;
```  
  
### <a name="remarks"></a>备注  
 因为`CComFakeCriticalSection`不提供一个临界区，其方法不执行任何操作。  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)还包含定义`CriticalSection`。 下表显示的线程模型类与所引用的关键部分类之间的关系`CriticalSection`:  
  
|中定义的类|引用类|  
|----------------------|----------------------|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
  
 除了`CriticalSection`，您可以使用`typedef`名称`AutoCriticalSection`。 不应指定`AutoCriticalSection`全局对象或如果您想要消除 CRT 启动代码的静态类成员中。  
  
### <a name="example"></a>示例  
 请参阅[CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。  
  
##  <a name="a-namedecrementa--ccommultithreadmodelnocsdecrement"></a><a name="decrement"></a>CComMultiThreadModelNoCS::Decrement  
 此静态函数将调用 Win32 函数[InterlockedDecrement](http://msdn.microsoft.com/library/windows/desktop/ms683580)，这由指向变量的值将减少`p`。  
  
```
static ULONG WINAPI Decrement(LPLONG p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 [in]指向要递减的变量的指针。  
  
### <a name="return-value"></a>返回值  
 如果减法的结果为 0，则`Decrement`，则返回 0。 如果减法的结果不为零，则返回值也为非零值，但可能不等于减法的结果。  
  
### <a name="remarks"></a>备注  
 **InterlockedDecrement**防止多个线程同时使用此变量。  
  
##  <a name="a-nameincrementa--ccommultithreadmodelnocsincrement"></a><a name="increment"></a>CComMultiThreadModelNoCS::Increment  
 此静态函数将调用 Win32 函数[InterlockedIncrement](http://msdn.microsoft.com/library/windows/desktop/ms683614)，变量所指向的值时都会增加`p`。  
  
```
static ULONG WINAPI Increment(LPLONG p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 [in]指向要递增的变量的指针。  
  
### <a name="return-value"></a>返回值  
 如果增量结果为 0，则**增量**，则返回 0。 如果增量结果不为零，则返回值也为非零值，但可能抵不上的增量结果。  
  
### <a name="remarks"></a>备注  
 **InterlockedIncrement**防止多个线程同时使用此变量。  
  
##  <a name="a-namethreadmodelnocsa--ccommultithreadmodelnocsthreadmodelnocs"></a><a name="threadmodelnocs"></a>CComMultiThreadModelNoCS::ThreadModelNoCS  
 当使用`CComMultiThreadModelNoCS`、`typedef`名称`ThreadModelNoCS`只引用`CComMultiThreadModelNoCS`。  
  
```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```  
  
### <a name="remarks"></a>备注  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)还包含定义`ThreadModelNoCS`。 下表显示的线程模型类与所引用的类之间的关系`ThreadModelNoCS`:  
  
|中定义的类|引用类|  
|----------------------|----------------------|  
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|  
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|  
|`CComSingleThreadModel`|`CComSingleThreadModel`|  
  
 请注意，定义`ThreadModelNoCS`中`CComMultiThreadModelNoCS`提供与对称性`CComMultiThreadModel`和`CComSingleThreadModel`。 例如，假设中的示例代码`CComMultiThreadModel::AutoCriticalSection`声明以下`typedef`:  
  
 [!code-cpp[NVC_ATL_COM&#37;](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]  
  
 无论为指定的类`ThreadModel`(如`CComMultiThreadModelNoCS`)，`_ThreadModel`相应地进行解析。  
  
### <a name="example"></a>示例  
 请参阅[CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)
