---
title: "Semaphore 类 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Semaphore"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Semaphore 类"
ms.assetid: ded53526-17b4-4381-9c60-ea5e77363db6
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Semaphore 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

同步对象表示控件可以支持用户的有限的共享资源。  
  
## 语法  
  
```  
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>  
```  
  
## 成员  
  
### 公共 Typedef  
  
|名称|说明|  
|--------|--------|  
|`SyncLock`|支持的同步锁类的同义词。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[Semaphore::Semaphore 构造函数](../windows/semaphore-semaphore-constructor.md)|初始化 Semaphore 类的新实例。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[InvokeHelper::Invoke 方法](../windows/invokehelper-invoke-method.md)|调用签名包含参数的指定的事件处理程序。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[Semaphore::Lock 方法](../windows/semaphore-lock-method.md)|等待直到当前对象，或与指定句柄关联的对象，是在信号的状态或指定的超时间隔已过。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[Semaphore::operator\= 运算符](../windows/semaphore-operator-assign-operator.md)|将从一个信号量对象的指定处理到当前信号量对象。|  
  
## 继承层次结构  
 `Semaphore`  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)