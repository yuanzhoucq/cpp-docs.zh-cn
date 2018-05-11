---
title: SyncLockT 类 |Microsoft 文档
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
ms.openlocfilehash: e05a1be5d84db52573d3c3235936ecf82dde5894
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="synclockt-class"></a>SyncLockT 类
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
template <  
   typename SyncTraits  
>  
class SyncLockT;  
```  
  
#### <a name="parameters"></a>参数  
 `SyncTraits`  
 可以获得资源的所有权类型。  
  
## <a name="remarks"></a>备注  
 表示可能需要独占的类型或共享资源的所有权。  
  
 SyncLockT 类使用，例如，来帮助实施[SRWLock](../windows/srwlock-class.md)类。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[SyncLockT::SyncLockT 构造函数](../windows/synclockt-synclockt-constructor.md)|初始化 SyncLockT 类的新实例。|  
|[SyncLockT::~SyncLockT 析构函数](../windows/synclockt-tilde-synclockt-destructor.md)|取消初始化 SyncLockT 类的实例。|  
  
### <a name="protected-constructors"></a>受保护的构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[SyncLockT::SyncLockT 构造函数](../windows/synclockt-synclockt-constructor.md)|初始化 SyncLockT 类的新实例。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[SyncLockT::IsLocked 方法](../windows/synclockt-islocked-method.md)|指示当前的 SyncLockT 对象是否拥有资源;SyncLockT 对象也是*锁定*。|  
|[SyncLockT::Unlock 方法](../windows/synclockt-unlock-method.md)|释放由当前 SyncLockT 对象占用的资源的控制，如果有的话。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[SyncLockT::sync_ 数据成员](../windows/synclockt-sync-data-member.md)|包含表示 SyncLockT 类的基础资源。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `SyncLockT`  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Wrappers::Details Namespace](../windows/microsoft-wrl-wrappers-details-namespace.md)   
 [SRWLock 类](../windows/srwlock-class.md)