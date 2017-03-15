---
title: "CComSingleThreadModel 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CComSingleThreadModel
- CComSingleThreadModel
- ATL::CComSingleThreadModel
dev_langs:
- C++
helpviewer_keywords:
- single-threaded applications
- CComSingleThreadModel class
- single-threaded applications, ATL
ms.assetid: e5dc30c7-405a-4ba4-8ae9-51937243fce8
caps.latest.revision: 19
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
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: ff5d8d2ced1d6fe0196888d8c746844ace8307f8
ms.lasthandoff: 02/24/2017

---
# <a name="ccomsinglethreadmodel-class"></a>CComSingleThreadModel 类
此类提供方法递增和递减的变量的值。  
  
## <a name="syntax"></a>语法  
  
```
class CComSingleThreadModel
```  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|说明|  
|----------|-----------------|  
|[CComSingleThreadModel::AutoCriticalSection](#autocriticalsection)|引用类[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。|  
|[CComSingleThreadModel::CriticalSection](#criticalsection)|引用类`CComFakeCriticalSection`。|  
|[CComSingleThreadModel::ThreadModelNoCS](#threadmodelnocs)|引用`CComSingleThreadModel`。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CComSingleThreadModel::Decrement](#decrement)|递减指定变量的值。 此实现不是线程安全的。|  
|[CComSingleThreadModel::Increment](#increment)|递增指定变量的值。 此实现不是线程安全的。|  
  
## <a name="remarks"></a>备注  
 `CComSingleThreadModel`提供用于递增和递减的变量值的方法。 与不同[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)，这些方法不是线程安全。  

 通常，您可以使用`CComSingleThreadModel`通过两种`typedef`名称，或者[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)或[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)。 由每个引用的类`typedef`，所使用的线程模型取决于下表中所示︰  

  
|typedef|单线程模型|单元线程模型|自由线程处理模型|  
|-------------|----------------------------|-------------------------------|--------------------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S= `CComSingleThreadModel`;M =`CComMultiThreadModel`  
  
 `CComSingleThreadModel`本身定义三个`typedef`名称。 `ThreadModelNoCS`引用`CComSingleThreadModel`。 `AutoCriticalSection`和`CriticalSection`引用类[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)，该属性提供与获得和释放关键节的所有权相关的空方法。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlbase.h  
  
##  <a name="a-nameautocriticalsectiona--ccomsinglethreadmodelautocriticalsection"></a><a name="autocriticalsection"></a>CComSingleThreadModel::AutoCriticalSection  
 当使用`CComSingleThreadModel`、`typedef`名称`AutoCriticalSection`引用类[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。  
  
```
typedef CComFakeCriticalSection AutoCriticalSection;
```  
  
### <a name="remarks"></a>备注  
 因为`CComFakeCriticalSection`不提供一个临界区，其方法不执行任何操作。  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)包含定义`AutoCriticalSection`。 下表显示的线程模型类与所引用的关键部分类之间的关系`AutoCriticalSection`:  
  
|中定义的类|引用类|  
|----------------------|----------------------|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComAutoCriticalSection`|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
  
 除了`AutoCriticalSection`，您可以使用`typedef`名称[CriticalSection](#criticalsection)。 不应指定`AutoCriticalSection`全局对象或如果您想要消除 CRT 启动代码的静态类成员中。  
  
### <a name="example"></a>示例  
 请参阅[CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。  
  
##  <a name="a-namecriticalsectiona--ccomsinglethreadmodelcriticalsection"></a><a name="criticalsection"></a>CComSingleThreadModel::CriticalSection  
 当使用`CComSingleThreadModel`、`typedef`名称`CriticalSection`引用类[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。  
  
```
typedef CComFakeCriticalSection CriticalSection;
```  
  
### <a name="remarks"></a>备注  
 因为`CComFakeCriticalSection`不提供一个临界区，其方法不执行任何操作。  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)包含定义`CriticalSection`。 下表显示的线程模型类与所引用的关键部分类之间的关系`CriticalSection`:  
  
|中定义的类|引用类|  
|----------------------|----------------------|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
  
 除了`CriticalSection`，您可以使用`typedef`名称[AutoCriticalSection](#autocriticalsection)。 不应指定`AutoCriticalSection`全局对象或如果您想要消除 CRT 启动代码的静态类成员中。  
  
### <a name="example"></a>示例  
 请参阅[CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。  
  
##  <a name="a-namedecrementa--ccomsinglethreadmodeldecrement"></a><a name="decrement"></a>CComSingleThreadModel::Decrement  
 此静态函数递减该变量的值由指向`p`。  
  
```
static ULONG WINAPI Decrement(LPLONG p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 [in]指向要递减的变量的指针。  
  
### <a name="return-value"></a>返回值  
 减法的结果。  
  
##  <a name="a-nameincrementa--ccomsinglethreadmodelincrement"></a><a name="increment"></a>CComSingleThreadModel::Increment  
 此静态函数递减该变量的值由指向`p`。  
  
```
static ULONG WINAPI Increment(LPLONG p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 [in]指向要递增的变量的指针。  
  
### <a name="return-value"></a>返回值  
 增量结果。  
  
##  <a name="a-namethreadmodelnocsa--ccomsinglethreadmodelthreadmodelnocs"></a><a name="threadmodelnocs"></a>CComSingleThreadModel::ThreadModelNoCS  
 当使用`CComSingleThreadModel`、`typedef`名称`ThreadModelNoCS`只引用`CComSingleThreadModel`。  
  
```
typedef CComSingleThreadModel ThreadModelNoCS;
```  
  
### <a name="remarks"></a>备注  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)包含定义`ThreadModelNoCS`。 下表显示的线程模型类与所引用的类之间的关系`ThreadModelNoCS`:  
  
|中定义的类|引用类|  
|----------------------|----------------------|  
|`CComSingleThreadModel`|`CComSingleThreadModel`|  
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|  
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|  
  
### <a name="example"></a>示例  
 请参阅[CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)

