---
title: "SimpleActivationFactory::GetTrustLevel 方法 | Microsoft Docs"
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
  - "module/Microsoft::WRL::SimpleActivationFactory::GetTrustLevel"
dev_langs: 
  - "C++"
ms.assetid: 99aa9bc9-d954-4a6f-902b-4abe00e43039
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SimpleActivationFactory::GetTrustLevel 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

类获取实例的信任级别。`Base` 类模板参数指定的。  
  
## 语法  
  
```  
STDMETHOD(  
   GetTrustLevel  
)(_Out_ TrustLevel* trustLvl);  
```  
  
#### 参数  
 `trustLvl`  
 该操作完成，当前类对象的信任级别。  
  
## 返回值  
 始终是 S\_OK。  
  
## 要求  
 **标头:** module.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [SimpleActivationFactory 类](../windows/simpleactivationfactory-class.md)