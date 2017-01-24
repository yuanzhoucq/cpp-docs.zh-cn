---
title: "AsyncResultType 枚举 | Microsoft Docs"
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
  - "async/Microsoft::WRL::AsyncResultType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AsyncResultType 枚举"
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncResultType 枚举
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定 GetResults\(\) 方法返回的结果类型。  
  
## 语法  
  
```  
enum AsyncResultType;  
```  
  
## 成员  
  
### 值  
  
|名称|说明|  
|--------|--------|  
|`MultipleResults`|一个多个结果现在，运行时在启动条件，并且，在 Close\(\) 调用之前。|  
|`SingleResult`|唯一，结果存在，在完全事件发生之后。|  
  
## 要求  
 **页眉：**async.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Microsoft::WRL 命名空间](../windows/microsoft-wrl-namespace.md)