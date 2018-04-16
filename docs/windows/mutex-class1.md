---
title: "互斥体 Class1 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex
dev_langs:
- C++
helpviewer_keywords:
- Mutex class
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c0e849d1fee7eca67f3b5765d31b54e0660eaa25
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mutex-class1"></a>互斥体 Class1
表示完全控制共享资源的同步对象。  
  
## <a name="syntax"></a>语法  
  
```  
class Mutex : public HandleT<HandleTraits::MutexTraits>  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|**SyncLock**|支持同步锁的类，同义词。|  
  
### <a name="public-constructor"></a>公共构造函数  
  
|name|描述|  
|----------|-----------------|  
|[Mutex::Mutex 构造函数](../windows/mutex-mutex-constructor.md)|初始化 Mutex 类的新实例。|  
  
### <a name="public-members"></a>公共成员  
  
|name|描述|  
|----------|-----------------|  
|[Mutex::Lock 方法](../windows/mutex-lock-method.md)|等到当前对象或与指定句柄，关联的互斥体对象释放互斥体，或指定的超时间隔已过去。|  
  
### <a name="public-operator"></a>公共运算符  
  
|name|描述|  
|----------|-----------------|  
|[Mutex::operator= 运算符](../windows/mutex-operator-assign-operator.md)|分配 （移动） 指定互斥体对象转换为当前的 Mutex 对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `Mutex`  
  
## <a name="requirements"></a>惠?  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)