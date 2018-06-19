---
title: CComSingleThreadModel 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComSingleThreadModel::CriticalSection
- ATLBASE/ATL::CComSingleThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComSingleThreadModel::Decrement
- ATLBASE/ATL::CComSingleThreadModel::Increment
dev_langs:
- C++
helpviewer_keywords:
- single-threaded applications
- CComSingleThreadModel class
- single-threaded applications, ATL
ms.assetid: e5dc30c7-405a-4ba4-8ae9-51937243fce8
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 175cc1b867356949ca861f7015dedb6d64c4282f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365095"
---
# <a name="ccomsinglethreadmodel-class"></a>CComSingleThreadModel 类
此类提供了方法递增和递减的变量的值。  
  
## <a name="syntax"></a>语法  
  
```
class CComSingleThreadModel
```  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|[CComSingleThreadModel::AutoCriticalSection](#autocriticalsection)|引用类[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。|  
|[CComSingleThreadModel::CriticalSection](#criticalsection)|引用类`CComFakeCriticalSection`。|  
|[CComSingleThreadModel::ThreadModelNoCS](#threadmodelnocs)|引用`CComSingleThreadModel`。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComSingleThreadModel::Decrement](#decrement)|递减指定变量的值。 此实现不是线程安全。|  
|[CComSingleThreadModel::Increment](#increment)|递增指定变量的值。 此实现不是线程安全。|  
  
## <a name="remarks"></a>备注  
 `CComSingleThreadModel` 提供用于递增和递减的变量的值的方法。 与不同[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)，这些方法不是线程安全。  

 通常情况下，使用`CComSingleThreadModel`通过两个类之一`typedef`名称，或者[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)或[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)。 每个所引用类`typedef`依赖于使用的线程处理模型下, 表中所示：  

  
|typedef|单线程模型|单元线程处理模型|自由线程处理模型|  
|-------------|----------------------------|-------------------------------|--------------------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S = `CComSingleThreadModel`;M = `CComMultiThreadModel`  
  
 `CComSingleThreadModel` 本身定义三个`typedef`名称。 `ThreadModelNoCS` 引用`CComSingleThreadModel`。 `AutoCriticalSection` 和`CriticalSection`引用类[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)，提供与获取和释放的关键部分所有权相关联的空方法。  
  
## <a name="requirements"></a>要求  
 **标头：** atlbase.h  
  
##  <a name="autocriticalsection"></a>  CComSingleThreadModel::AutoCriticalSection  
 使用时`CComSingleThreadModel`、`typedef`名称`AutoCriticalSection`引用类[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。  
  
```
typedef CComFakeCriticalSection AutoCriticalSection;
```  
  
### <a name="remarks"></a>备注  
 因为`CComFakeCriticalSection`不提供一个临界区，其方法不执行任何操作。  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)包含定义`AutoCriticalSection`。 下表显示的线程处理模型类和所引用的关键部分类之间的关系`AutoCriticalSection`:  
  
|在中定义的类|所引用类|  
|----------------------|----------------------|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComAutoCriticalSection`|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
  
 除了`AutoCriticalSection`，你可以使用`typedef`名称[CriticalSection](#criticalsection)。 不应指定`AutoCriticalSection`在全局对象或如果你想要消除 CRT 启动代码的静态类成员中。  
  
### <a name="example"></a>示例  
 请参阅[CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。  
  
##  <a name="criticalsection"></a>  CComSingleThreadModel::CriticalSection  
 使用时`CComSingleThreadModel`、`typedef`名称`CriticalSection`引用类[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。  
  
```
typedef CComFakeCriticalSection CriticalSection;
```  
  
### <a name="remarks"></a>备注  
 因为`CComFakeCriticalSection`不提供一个临界区，其方法不执行任何操作。  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)包含定义`CriticalSection`。 下表显示的线程处理模型类和所引用的关键部分类之间的关系`CriticalSection`:  
  
|在中定义的类|所引用类|  
|----------------------|----------------------|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
  
 除了`CriticalSection`，你可以使用`typedef`名称[AutoCriticalSection](#autocriticalsection)。 不应指定`AutoCriticalSection`在全局对象或如果你想要消除 CRT 启动代码的静态类成员中。  
  
### <a name="example"></a>示例  
 请参阅[CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。  
  
##  <a name="decrement"></a>  CComSingleThreadModel::Decrement  
 此静态函数递减的变量的值的指向`p`。  
  
```
static ULONG WINAPI Decrement(LPLONG p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 [in]指向要递减的变量的指针。  
  
### <a name="return-value"></a>返回值  
 减法的结果。  
  
##  <a name="increment"></a>  CComSingleThreadModel::Increment  
 此静态函数递减的变量的值的指向`p`。  
  
```
static ULONG WINAPI Increment(LPLONG p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 [in]指向要递增的变量的指针。  
  
### <a name="return-value"></a>返回值  
 增量结果。  
  
##  <a name="threadmodelnocs"></a>  CComSingleThreadModel::ThreadModelNoCS  
 使用时`CComSingleThreadModel`、`typedef`名称`ThreadModelNoCS`只引用`CComSingleThreadModel`。  
  
```
typedef CComSingleThreadModel ThreadModelNoCS;
```  
  
### <a name="remarks"></a>备注  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)包含定义`ThreadModelNoCS`。 下表显示的线程处理模型类和所引用的类之间的关系`ThreadModelNoCS`:  
  
|在中定义的类|所引用类|  
|----------------------|----------------------|  
|`CComSingleThreadModel`|`CComSingleThreadModel`|  
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|  
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|  
  
### <a name="example"></a>示例  
 请参阅[CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)
