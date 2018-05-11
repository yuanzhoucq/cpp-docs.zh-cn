---
title: 信号类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore
dev_langs:
- C++
helpviewer_keywords:
- Semaphore class
ms.assetid: ded53526-17b4-4381-9c60-ea5e77363db6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1219c2118f9cde18fe1909a2edd02d58a4be2341
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="semaphore-class"></a>Semaphore 类
表示控制可支持有限数量用户的共享资源的同步对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`SyncLock`|支持同步锁的类，同义词。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[Semaphore::Semaphore 构造函数](../windows/semaphore-semaphore-constructor.md)|初始化 Semaphore 类的新实例。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[InvokeHelper::Invoke 方法](../windows/invokehelper-invoke-method.md)|调用签名包含参数的指定的数目的事件处理程序。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[Semaphore::Lock 方法](../windows/semaphore-lock-method.md)|等到当前对象或与指定句柄关联的对象处于终止状态，或者指定的超时间隔已过去。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[Semaphore::operator= 运算符](../windows/semaphore-operator-assign-operator.md)|将指定的句柄从信号量对象移动到当前的信号量对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `Semaphore`  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)