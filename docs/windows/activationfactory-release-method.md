---
title: "ActivationFactory::Release 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::ActivationFactory::Release"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Release 方法"
ms.assetid: 5bc25ff0-ee3c-4a2d-a9b6-2d8f158033ad
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# ActivationFactory::Release 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

递减 ActivationFactory 当前对象的引用计数。  
  
## 语法  
  
```  
STDMETHOD_(  
   ULONG,  
   Release  
)();  
```  
  
## 返回值  
 S\_OK，如果成功；描述，否则失败的 HRESULT。  
  
## 要求  
 **标头:** module.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [ActivationFactory 类](../windows/activationfactory-class.md)