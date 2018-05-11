---
title: scoped_d3d_access_lock 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- scoped_d3d_access_lock
- AMPRT/scoped_d3d_access_lock
- AMPRT/concurrency::direct3d::scoped_d3d_access_lock::scoped_d3d_access_lock
dev_langs:
- C++
ms.assetid: 0ad333e6-9839-4736-a722-16d95d70c4b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0053fa89139ac806a3d8ae0572cd053dd6bec72c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="scopedd3daccesslock-class"></a>scoped_d3d_access_lock 类
Accelerator_view 对象上 D3D 访问锁 RAII 包装器。  
  
### <a name="syntax"></a>语法  
  
```  
class scoped_d3d_access_lock;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[scoped_d3d_access_lock 构造函数](#ctor)|已重载。 构造 `scoped_d3d_access_lock` 对象。 当此对象超出范围时，该锁被释放。|  
|[~ scoped_d3d_access_lock 析构函数](#dtor)|释放上关联的 D3D 访问锁`accelerator_view`对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[operator=](#operator_eq)|负责从另一个锁`scoped_d3d_access_lock`。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `scoped_d3d_access_lock`  
  
## <a name="requirements"></a>要求  
 **标头：** amprt.h  
  
 **Namespace:** concurrency:: direct3d  

##  <a name="ctor"></a> scoped_d3d_access_lock 

 构造 `scoped_d3d_access_lock` 对象。 当此对象超出范围时，该锁被释放。  
 
```  
explicit scoped_d3d_access_lock(// [1] constructor  
    accelerator_view& _Av);

 
explicit scoped_d3d_access_lock(// [2] constructor  
    accelerator_view& _Av,  
    adopt_d3d_access_lock_t _T);

 
scoped_d3d_access_lock(// [3] move constructor  
    scoped_d3d_access_lock&& _Other);
```  
  
### <a name="parameters"></a>参数  
 `_Av`  
 `accelerator_view`要采用的锁。  
  
 `_T`  
 `adopt_d3d_access_lock_t` 对象。  
  
 `_Other`  
 `scoped_d3d_access_lock`从该处移动的现有锁的对象。  
  
## <a name="construction"></a>构造  
 [1] 构造函数  
 在获取 D3D 访问锁定给定[accelerator_view](accelerator-view-class.md)对象。 直到已获取锁的构造块。  
  
 [2] 构造函数  
 采用 D3D 访问锁从给定[accelerator_view](accelerator-view-class.md)对象。  
  
 [3] 移动构造函数  
 使用从另一个的现有 D3D 访问锁`scoped_d3d_access_lock`对象。 构造不会阻止。  

  
##  <a name="dtor"></a> ~scoped_d3d_access_lock 

 释放上关联的 D3D 访问锁`accelerator_view`对象。  
  
```  
~scoped_d3d_access_lock();
```  
## <a name="operator_eq"></a> 运算符 = 

从另一个 D3D 访问锁定的所有权并装入`scoped_d3d_access_lock`对象，释放以前的锁。  
 
```  
scoped_d3d_access_lock& operator= (scoped_d3d_access_lock&& _Other);
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 从该处移动 D3D 访问锁 accelerator_view。  
  
### <a name="return-value"></a>返回值  
 对此引用`scoped_accelerator_view_lock`。  

## <a name="see-also"></a>请参阅  
 [Concurrency::direct3d 命名空间](concurrency-direct3d-namespace.md)
