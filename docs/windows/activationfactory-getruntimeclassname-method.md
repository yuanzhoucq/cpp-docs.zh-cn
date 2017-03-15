---
title: "ActivationFactory::GetRuntimeClassName 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::ActivationFactory::GetRuntimeClassName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetRuntimeClassName 方法"
ms.assetid: 74e34f0a-9c51-4b40-89f5-45c6c5886ece
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# ActivationFactory::GetRuntimeClassName 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

获取当前 ActivationFactory 实例化对象的运行时类名。  
  
## 语法  
  
```  
STDMETHOD(  
   GetRuntimeClassName  
)(_Out_ HSTRING* runtimeName);  
```  
  
#### 参数  
 `runtimeName`  
 当完成此操作，对象包含对运行时 ActivationFactory 当前实例化类名的字符串的句柄。  
  
## 返回值  
 S\_OK，如果成功；描述，否则失败的 HRESULT。  
  
## 要求  
 **标头:** module.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [ActivationFactory 类](../windows/activationfactory-class.md)