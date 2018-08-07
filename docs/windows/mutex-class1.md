---
title: Mutex 类 1 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex
dev_langs:
- C++
helpviewer_keywords:
- Mutex class
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cd9c3dbbcbffff32f7c1611b6b49ee19ada7e52c
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606769"
---
# <a name="mutex-class1"></a>Mutex 类 1
表示完全控制共享资源的同步对象。  
  
## <a name="syntax"></a>语法  
  
```  
class Mutex : public HandleT<HandleTraits::MutexTraits>  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`SyncLock`|类支持同步锁的同义词。|  
  
### <a name="public-constructor"></a>公共构造函数  
  
|name|描述|  
|----------|-----------------|  
|[Mutex::Mutex 构造函数](../windows/mutex-mutex-constructor.md)|初始化的新实例**互斥体**类。|  
  
### <a name="public-members"></a>公共成员  
  
|name|描述|  
|----------|-----------------|  
|[Mutex::Lock 方法](../windows/mutex-lock-method.md)|等到当前对象或**互斥体**与指定句柄，互斥体或指定的超时间隔已过的版本关联的对象。|  
  
### <a name="public-operator"></a>公共运算符  
  
|name|描述|  
|----------|-----------------|  
|[Mutex::operator= 运算符](../windows/mutex-operator-assign-operator.md)|分配 （移动） 指定**Mutex**对象与当前**互斥体**对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `Mutex`  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)