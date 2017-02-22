---
title: "ActivationFactory::GetTrustLevel 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::ActivationFactory::GetTrustLevel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetTrustLevel 方法"
ms.assetid: 31547ae6-d2ab-4039-923c-154d53fb1a8b
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# ActivationFactory::GetTrustLevel 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

获取当前 ActivationFactory 实例化对象的信任级别。  
  
## 语法  
  
```  
STDMETHOD(  
   GetTrustLevel  
)(_Out_ TrustLevel* trustLvl);  
```  
  
#### 参数  
 `trustLvl`  
 当完成此操作，ActivationFactory 实例化运行时类的信任级别。  
  
## 返回值  
 S\_OK，如果成功；否则，断言错误发出，并且 `trustLvl` 设置为 FullTrust。  
  
## 要求  
 **标头:** module.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [ActivationFactory 类](../windows/activationfactory-class.md)