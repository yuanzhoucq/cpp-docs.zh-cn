---
title: "CriticalSection 类 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::CriticalSection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CriticalSection 类"
ms.assetid: f2e0a024-71a3-4f6b-99ea-d93a4a608ac4
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CriticalSection 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示一个临界区对象。  
  
## 语法  
  
```  
class CriticalSection;  
```  
  
## 成员  
  
### 构造函数  
  
|名称|说明|  
|--------|--------|  
|[CriticalSection::CriticalSection 构造函数](../windows/criticalsection-criticalsection-constructor.md)|初始化类似 Mutex 对象的同步对象，但是，可以由单个进程中只使用线程。|  
|[CriticalSection::~CriticalSection 析构函数](../windows/criticalsection-tilde-criticalsection-destructor.md)|Deinitializes 和销毁当前 CriticalSection 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CriticalSection::TryLock 方法](../windows/criticalsection-trylock-method.md)|尝试输入临界区，但不阻塞。  如果调用成功，调用线程获取临界区的所有权。|  
|[CriticalSection::Lock 方法](../windows/criticalsection-lock-method.md)|等待指定的临界区对象的所有权。  在授予调用线程所属权时，函数会返回。|  
|[CriticalSection::IsValid 方法](../windows/criticalsection-isvalid-method.md)|指示当前的临界是否有效。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CriticalSection::cs\_ 数据成员](../windows/criticalsection-cs-data-member.md)|声明关键部分数据成员。|  
  
## 继承层次结构  
 `CriticalSection`  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)