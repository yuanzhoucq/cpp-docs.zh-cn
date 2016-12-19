---
title: "ChainInterfaces::FillArrayWithIid 方法 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::ChainInterfaces::FillArrayWithIid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FillArrayWithIid 方法"
ms.assetid: f1ce699c-dfb6-40a9-9ea0-e6703d3cf971
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ChainInterfaces::FillArrayWithIid 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

存储 `I0` 模板参数定义的接口 ID 到指定的数组中的指定位置设置接口 ID。  
  
## 语法  
  
```  
__forceinline static void FillArrayWithIid(  
   _Inout_ unsigned long &index,  
   _In_ IID* iids  
);  
```  
  
#### 参数  
 `index`  
 为索引的指针到 `iids` 数组中。  
  
 `iids`  
 测试用例 ID 的数组。  
  
## 要求  
 **头文件：**implements.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [ChainInterfaces 结构](../windows/chaininterfaces-structure.md)