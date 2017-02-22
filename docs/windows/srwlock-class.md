---
title: "SRWLock 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::SRWLock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SRWLock 类"
ms.assetid: 4fa250e3-5f29-4b06-ac24-61b6c04ade93
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# SRWLock 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示一亭亭玉立的读取器\/编写器锁。  
  
## 语法  
  
```  
class SRWLock;  
```  
  
## 备注  
 一个小的读取器\/编写器锁用于在中同步线程访问对象或资源。  有关详细信息，请参阅《运行时库参考》中的 [Synchronization Functions](http://msdn.microsoft.com/zh-cn/9b6359c2-0113-49b6-83d0-316ad95aba1b) 。  
  
## 成员  
  
### 公共 Typedef  
  
|||  
|-|-|  
|**SyncLockExclusive**|以独占模式访问的对象 SRWLock 的同义词。|  
|**SyncLockShared**|以共享模式访问的对象 SRWLock 的同义词。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[SRWLock::SRWLock 构造函数](../windows/srwlock-srwlock-constructor.md)|初始化 SRWLock 类的新实例。|  
|[SRWLock::~SRWLock 析构函数](../windows/srwlock-tilde-srwlock-destructor.md)|初始化SRWLock类的实例。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[SRWLock::LockExclusive 方法](../windows/srwlock-lockexclusive-method.md)|获取以独占模式的一 SRWLock 对象。|  
|[SRWLock::LockShared 方法](../windows/srwlock-lockshared-method.md)|获取以共享模式的一 SRWLock 对象。|  
|[SRWLock::TryLockExclusive 方法](../windows/srwlock-trylockexclusive-method.md)|尝试获取在独占的图案 SRWLock 对象当前或指定的 SRWLock 对象。|  
|[SRWLock::TryLockShared 方法](../windows/srwlock-trylockshared-method.md)|尝试获取在共享的图案 SRWLock 对象当前或指定的 SRWLock 对象。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[SRWLock::SRWLock\_ 数据成员](../windows/srwlock-srwlock-data-member.md)|包含当前 SRWLock 对象的锁基础变量。|  
  
## 继承层次结构  
 `SRWLock`  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)