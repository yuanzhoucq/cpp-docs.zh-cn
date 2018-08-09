---
title: SyncLockWithStatusT 类 |Microsoft Docs
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
ms.openlocfilehash: 66fd02ff9af4f7a5c1cb85b58e966622bed0060a
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648686"
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
  
### <a name="parameters"></a>参数  
 *SyncTraits*  
 可能需要排他的类型或共享资源的所有权。  
  
## <a name="remarks"></a>备注  
 表示可能需要排他的类型或共享资源的所有权。  
  
 **SyncLockWithStatusT**类用于实现[互斥体](../windows/mutex-class1.md)并[信号量](../windows/semaphore-class.md)类。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[SyncLockWithStatusT::SyncLockWithStatusT 构造函数](../windows/synclockwithstatust-synclockwithstatust-constructor.md)|初始化的新实例**SyncLockWithStatusT**类。|  
  
### <a name="protected-constructors"></a>受保护的构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[SyncLockWithStatusT::SyncLockWithStatusT 构造函数](../windows/synclockwithstatust-synclockwithstatust-constructor.md)|初始化的新实例**SyncLockWithStatusT**类。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[SyncLockWithStatusT::GetStatus 方法](../windows/synclockwithstatust-getstatus-method.md)|检索当前的等待状态**SyncLockWithStatusT**对象。|  
|[SyncLockWithStatusT::IsLocked 方法](../windows/synclockwithstatust-islocked-method.md)|指示是否当前**SyncLockWithStatusT**对象拥有一个资源; 也就是，则**SyncLockWithStatusT**对象*锁定*。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|name|描述|  
|----------|-----------------|  
|[SyncLockWithStatusT::status_ 数据成员](../windows/synclockwithstatust-status-data-member.md)|保存后对象的锁操作取决于当前的基础的等待操作结果**SyncLockWithStatusT**对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `SyncLockT`  
  
 `SyncLockWithStatusT`  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Wrappers::Details 命名空间](../windows/microsoft-wrl-wrappers-details-namespace.md)