---
title: "SyncLockT 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SyncLockT 类"
ms.assetid: a967f6f7-3555-43d1-b210-2bb65d63d15e
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SyncLockT 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
template <  
   typename SyncTraits  
>  
class SyncLockT;  
```  
  
#### 参数  
 `SyncTraits`  
 可以采用资源的所有权的类型。  
  
## 备注  
 呈现可以排除或采用资源的共享所有权的类型。  
  
 类用于 SyncLockT，例如，为了帮助实现 [SRWLock](../windows/srwlock-class.md) 类。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[SyncLockT::SyncLockT 构造函数](../windows/synclockt-synclockt-constructor.md)|初始化 SyncLockT 类的新实例。|  
|[SyncLockT::~SyncLockT 析构函数](../windows/synclockt-tilde-synclockt-destructor.md)|初始化SyncLockT类的实例。|  
  
### 受保护的构造函数  
  
|名称|说明|  
|--------|--------|  
|[SyncLockT::SyncLockT 构造函数](../windows/synclockt-synclockt-constructor.md)|初始化 SyncLockT 类的新实例。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[SyncLockT::IsLocked 方法](../windows/synclockt-islocked-method.md)|指示当前 SyncLockT 对象是否拥有一资源；即 SyncLockT 对象已被 *锁定*。|  
|[SyncLockT::Unlock 方法](../windows/synclockt-unlock-method.md)|当前 SyncLockT 对象持有的资源的发布控制，因此，如果有\)。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[SyncLockT::sync\_ 数据成员](../windows/synclockt-sync-data-member.md)|容纳基础资源由 SyncLockT 类。|  
  
## 继承层次结构  
 `SyncLockT`  
  
## 要求  
 **标头：**corewrappers.h  
  
 Microsoft::WRL::Wrappers::Details**命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Wrappers::Details 命名空间](../windows/microsoft-wrl-wrappers-details-namespace.md)   
 [SRWLock 类](../windows/srwlock-class.md)