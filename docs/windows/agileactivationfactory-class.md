---
title: "AgileActivationFactory 类 | Microsoft Docs"
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
  - "module/Microsoft::WRL::AgileActivationFactory"
dev_langs: 
  - "C++"
ms.assetid: fab98f32-bb93-4c0f-badb-49fbddb194b0
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AgileActivationFactory 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示一个单元友好激活的工厂实现 [FtmBase](../windows/ftmbase-class.md)。  
  
## 语法  
  
```cpp  
template <  
   typename I0 = Details::Nil,   
   typename I1 = Details::Nil,   
   typename I2 = Details::Nil,   
FactoryCacheFlags cacheFlagValue = FactoryCacheDefault>  
class AgileActivationFactory :   
   public ActivationFactory<Implements<FtmBase, I0>, I1, I2, cacheFlagValue>  
{};  
```  
  
## 要求  
 **标头:** module.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Microsoft::WRL 命名空间](../windows/microsoft-wrl-namespace.md)   
 [ActivationFactory 类](../windows/activationfactory-class.md)