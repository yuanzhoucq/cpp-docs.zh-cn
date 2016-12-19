---
title: "RuntimeClass::AddRef 方法 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::RuntimeClass::AddRef"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddRef 方法"
ms.assetid: 9c705749-680b-4308-bbec-5b601e8e7dbd
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RuntimeClass::AddRef 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

递增RuntimeClass当前对象的引用计数。  
  
## 语法  
  
```  
STDMETHOD_(  
   ULONG,  
   AddRef  
)();  
```  
  
## 返回值  
 S\_OK，如果成功；否则，一错误的 HRESULT。  
  
## 要求  
 **头文件：**implements.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [RuntimeClass 类](../windows/runtimeclass-class.md)