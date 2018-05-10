---
title: SyncLockWithStatusT 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockWithStatusT class
ms.assetid: 4832fd93-0ac8-4168-9404-b43fefea7476
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 51e5a66358890fc20731fb5cb657616484e19db4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT 类
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
template <  
   typename SyncTraits  
>  
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;  
```  
  
#### <a name="parameters"></a>参数  
 `SyncTraits`  
 可能需要独占的类型或共享资源的所有权。  
  
## <a name="remarks"></a>备注  
 表示可能需要独占的类型或共享资源的所有权。  
  
 SyncLockWithStatusT 类用于实现[互斥体](../windows/mutex-class1.md)和[信号量](../windows/semaphore-class.md)类。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[SyncLockWithStatusT::SyncLockWithStatusT 构造函数](../windows/synclockwithstatust-synclockwithstatust-constructor.md)|初始化 SyncLockWithStatusT 类的新实例。|  
  
### <a name="protected-constructors"></a>受保护的构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[SyncLockWithStatusT::SyncLockWithStatusT 构造函数](../windows/synclockwithstatust-synclockwithstatust-constructor.md)|初始化 SyncLockWithStatusT 类的新实例。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[SyncLockWithStatusT::GetStatus 方法](../windows/synclockwithstatust-getstatus-method.md)|检索当前 SyncLockWithStatusT 对象的等待状态。|  
|[SyncLockWithStatusT::IsLocked 方法](../windows/synclockwithstatust-islocked-method.md)|指示当前的 SyncLockWithStatusT 对象是否拥有资源;SyncLockWithStatusT 对象也是*锁定*。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[SyncLockWithStatusT::status_ 数据成员](../windows/synclockwithstatust-status-data-member.md)|根据当前的 SyncLockWithStatusT 对象保留的结果的基础等待锁操作完成后的操作对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `SyncLockT`  
  
 `SyncLockWithStatusT`  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Wrappers::Details 命名空间](../windows/microsoft-wrl-wrappers-details-namespace.md)