---
title: "Mutex 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::Mutex"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Mutex 类"
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# Mutex 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示完全控制一共享资源的同步对象。  
  
## 语法  
  
```  
class Mutex : public HandleT<HandleTraits::MutexTraits>  
  
```  
  
## 成员  
  
### 公共 Typedef  
  
|名称|说明|  
|--------|--------|  
|**SyncLock**|支持的同步锁类的同义词。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[Mutex::Mutex 构造函数](../windows/mutex-mutex-constructor.md)|初始化 Mutex 类的新实例。|  
  
### 公共成员  
  
|名称|说明|  
|--------|--------|  
|[Mutex::Lock 方法](../windows/mutex-lock-method.md)|等待，直至当前对象或互斥对象与指定的句柄、释放 Mutex 或指定的超时间隔结束。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[Mutex::operator\= 运算符](../windows/mutex-operator-assign-operator.md)|分配 \(移动\) 为当前 Mutex 对象的指定互斥对象。|  
  
## 继承层次结构  
 `Mutex`  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)