---
title: "VCPROFILE_ALLOC_SCALE | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VCPROFILE_ALLOC_SCALE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VCPROFILE_ALLOC_SCALE 环境变量"
ms.assetid: 5cb5ce27-f9b8-489b-b46c-d6e9bcab2d34
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# VCPROFILE_ALLOC_SCALE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

修改分配的内存量以容纳配置文件数据。  
  
## 语法  
  
```  
VCPROFILE_ALLOC_SCALE=scale_value  
```  
  
#### 参数  
 `scale_value`  
 运行测试方案所需的内存量的范围值。默认值为 1。  
  
## 备注  
 在极少数情况下，当运行测试方案时，没有足够的可用内存来支持收集配置文件数据。在这些情况下，可使用 `VCPROFILE_ALLOC_SCALE` 增加内存量。  
  
 如果在测试运行期间收到一条错误信息，指示内存不足，请对 `VCPROFILE_ALLOC_SCALE` 分配一个较大的值，直到测试运行完成时不再出现任何内存不足错误。  
  
## 示例  
  
```  
set VCPROFILE_ALLOC_SCALE=2  
```  
  
## 请参阅  
 [用于按配置文件优化的环境变量](../../build/reference/environment-variables-for-profile-guided-optimizations.md)