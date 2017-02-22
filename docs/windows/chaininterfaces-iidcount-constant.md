---
title: "ChainInterfaces::IidCount 常量 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::ChainInterfaces::IidCount"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IidCount 常量"
ms.assetid: d4a90aa0-513c-4e99-b978-e12149734936
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# ChainInterfaces::IidCount 常量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

接口 ID 的总数。包含接口的模板通过指定的参数 `I0` `I9`。  
  
## 语法  
  
```  
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;  
```  
  
## 返回值  
 接口 ID 的总数。  
  
## 备注  
 需要模板 `I0` 和 `I1` 参数，然后通过 `I2` 参数，`I9` 是可选的。IID 计数个接口通常是 1。  
  
## 要求  
 **头文件：**implements.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [ChainInterfaces 结构](../windows/chaininterfaces-structure.md)