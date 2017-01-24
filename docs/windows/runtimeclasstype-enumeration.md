---
title: "RuntimeClassType 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::RuntimeClassType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RuntimeClassType 枚举"
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RuntimeClassType 枚举
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定[RuntimeClass](../windows/runtimeclass-class.md) 支持的实例类型。  
  
## 语法  
  
```  
enum RuntimeClassType;  
```  
  
## 成员  
  
### 值  
  
|名称|说明|  
|--------|--------|  
|`ClassicCom`|创建运行时COM类|  
|`Delegate`|等效于 **ClassicCom**。|  
|`InhibitFtmBase`|禁用 `FtmBase` 支持，而 `__WRL_CONFIGURATION_LEGACY__` 没有定义。|  
|`InhibitWeakReference`|禁用弱引用支持。|  
|`WinRt`|[!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 类。|  
|`WinRtClassicComMix`|`WinRt` 和 `ClassicCom` 的组合。|  
  
## 要求  
 **头文件：**implements.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Microsoft::WRL 命名空间](../windows/microsoft-wrl-namespace.md)