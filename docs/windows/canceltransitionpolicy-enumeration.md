---
title: "CancelTransitionPolicy 枚举 | Microsoft Docs"
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
  - "module/Microsoft::WRL::CancelTransitionPolicy::TransitionFromCanceled"
  - "module/Microsoft::WRL::CancelTransitionPolicy::RemainCanceled"
  - "module/Microsoft::WRL::CancelTransitionPolicy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CancelTransitionPolicy 枚举"
ms.assetid: 5de49f7d-e5e3-43e9-bbca-666caf226cef
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CancelTransitionPolicy 枚举
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示切换的异步操作的完成。尝试或错误的最终状态如何。应行为一个客户端已请求取消的状态。  
  
## 语法  
  
```  
enum CancelTransitionPolicy;  
```  
  
## 成员  
  
### 值  
  
|名称|说明|  
|--------|--------|  
|`RemainCanceled`|如果异步操作当前处于一个客户端已请求取消的状态，这表示它。已取消状态将保持与相对转换到终端完成或错误状态。|  
|`TransitionFromCanceled`|如果异步操作当前处于一个客户端已请求取消的状态，这指示状态如果已取消状态到已完成或 false 的最终状态。使用此标志的调用依赖于该转换。|  
  
## 要求  
 **页眉：**async.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Microsoft::WRL 命名空间](../windows/microsoft-wrl-namespace.md)