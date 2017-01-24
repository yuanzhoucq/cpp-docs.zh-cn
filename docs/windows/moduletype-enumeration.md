---
title: "ModuleType 枚举 | Microsoft Docs"
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
  - "module/Microsoft::WRL::ModuleType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ModuleType 枚举"
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ModuleType 枚举
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定模块是否应支持进程内服务器或进程外服务器。  
  
## 语法  
  
```  
enum ModuleType;  
```  
  
## 成员  
  
### 值  
  
|名称|说明|  
|--------|--------|  
|`InProc`|进程内服务器 DLL|  
|`OutOfProc`|进程外服务器。|  
|`DisableCaching`|禁用在模块上的缓存机制。|  
|`InProcDisableCaching`|`InProc` 和 `DisableCaching` 的组合。|  
|`OutOfProcDisableCaching`|`OutOfProc` 和 `DisableCaching` 的组合。|  
  
## 要求  
 **标头:** module.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Microsoft::WRL 命名空间](../windows/microsoft-wrl-namespace.md)