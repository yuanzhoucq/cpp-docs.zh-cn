---
title: SyncLockT 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockT class
ms.assetid: a967f6f7-3555-43d1-b210-2bb65d63d15e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b1eb11480657d731a4667722572e921f405c0845
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012138"
---
# <a name="synclockt-class"></a>SyncLockT 类
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```cpp  
template <  
   typename SyncTraits  
>  
class SyncLockT;  
```  
  
### <a name="parameters"></a>参数  
 *SyncTraits*  
 可以获得资源的所有权类型。  
  
## <a name="remarks"></a>备注  
 表示可能需要排他的类型或共享资源的所有权。  
  
 **SyncLockT**类用于，例如，可以帮助实施[SRWLock](../windows/srwlock-class.md)类。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[SyncLockT::SyncLockT 构造函数](../windows/synclockt-synclockt-constructor.md)|初始化的新实例**SyncLockT**类。|  
|[SyncLockT::~SyncLockT 析构函数](../windows/synclockt-tilde-synclockt-destructor.md)|取消初始化的实例**SyncLockT**类。|  
  
### <a name="protected-constructors"></a>受保护的构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[SyncLockT::SyncLockT 构造函数](../windows/synclockt-synclockt-constructor.md)|初始化的新实例**SyncLockT**类。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[SyncLockT::IsLocked 方法](../windows/synclockt-islocked-method.md)|指示是否当前**SyncLockT**对象拥有一个资源; 也就是，则**SyncLockT**对象*锁定*。|  
|[SyncLockT::Unlock 方法](../windows/synclockt-unlock-method.md)|释放当前占用的资源的控制**SyncLockT**对象，如果有的话。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|name|描述|  
|----------|-----------------|  
|[SyncLockT::sync_ 数据成员](../windows/synclockt-sync-data-member.md)|保存由表示的基础资源**SyncLockT**类。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `SyncLockT`  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Wrappers::Details Namespace](../windows/microsoft-wrl-wrappers-details-namespace.md)   
 [SRWLock 类](../windows/srwlock-class.md)