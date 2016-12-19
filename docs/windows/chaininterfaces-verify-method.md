---
title: "ChainInterfaces::Verify 方法 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::ChainInterfaces::Verify"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Verify 方法"
ms.assetid: c591e130-8686-4130-ba69-1aaedc250038
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ChainInterfaces::Verify 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

验证模板参数定义的每个接口 `I0` 通过 `I9` 和 IInspectable 由从继承，因此，通过 `I0` 从 `I1` 继承 `I9`。  
  
## 语法  
  
```  
WRL_NOTHROW __forceinline static void Verify();  
```  
  
## 备注  
 如果验证操作失败，`static_assert` 发出描述失败的错误消息。  
  
## 备注  
 需要模板 `I0` 和 `I1` 参数，然后通过 `I2` 参数，`I9` 是可选的。  
  
## 要求  
 **头文件：**implements.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [ChainInterfaces 结构](../windows/chaininterfaces-structure.md)