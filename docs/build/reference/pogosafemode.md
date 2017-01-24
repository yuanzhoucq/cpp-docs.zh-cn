---
title: "PogoSafeMode | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PogoSafeMode"
ms.assetid: 2daeeff7-44cb-417f-90eb-6b9edf658533
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# PogoSafeMode
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定是否为应用程序分析使用快速模式或安全模式。  
  
## 语法  
  
```  
PogoSafeMode  
```  
  
## 备注  
 按配置优化 \(PGO\) 在分析阶段有两个可能的模式：快速模式和安全模式。  分析在快速模式下时，它会使用 **INC** 指令来增加数据计数器。  **INC** 指令速度更快，但不是线程安全的。  分析在安全模式下时，它会使用 **LOCK INC** 指令来增加数据计数器。  **LOCK INC** 指令具有和 **INC** 指令相同的功能，并且是线程安全的，但它是比 **INC** 指令慢。  
  
 默认情况下，PGO 分析以快速模式操作。  仅当使用安全模式时才需要 `PogoSafeMode`。  
  
 若要在安全模式下运行 PGO 分析，您必须使用环境变量 `PogoSafeMode` 或链接器开关 **\-PogoSafeMode**，依系统而定。  如果您正在 x64 计算机上执行分析，则必须使用链接器开关。  如果您正在 x86 计算机上执行分析，则必须在开始优化过程之前将环境变量定义为任何值。  
  
## 示例  
  
```  
set PogoSafeMode=1  
```  
  
## 请参阅  
 [用于按配置文件优化的环境变量](../../build/reference/environment-variables-for-profile-guided-optimizations.md)   
 [按配置文件优化](../../build/reference/profile-guided-optimizations.md)