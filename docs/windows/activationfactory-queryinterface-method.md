---
title: "ActivationFactory::QueryInterface 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::ActivationFactory::QueryInterface"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "QueryInterface 方法"
ms.assetid: 2a9b71aa-61c0-43f7-aa35-00f0ee0af031
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# ActivationFactory::QueryInterface 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

检索特定接口的指针。  
  
## 语法  
  
```  
STDMETHOD(  
   QueryInterface  
)(REFIID riid, _Deref_out_ void **ppvObject);  
```  
  
#### 参数  
 `riid`  
 是一个ID接口。  
  
 `ppvObject`  
 当此操作完成时，指向接口的指针由 `riid`参数指定。  
  
## 返回值  
 S\_OK，如果成功；描述，否则失败的 HRESULT。  
  
## 要求  
 **标头:** module.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [ActivationFactory 类](../windows/activationfactory-class.md)