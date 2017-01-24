---
title: "HString::IsValid 方法 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HString::IsValid"
dev_langs: 
  - "C++"
ms.assetid: 540e222a-0eee-4764-bd6c-8e3d12c877a2
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HString::IsValid 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示当前 HString 对象是否为空。  
  
## 语法  
  
```  
bool IsValid() const throw()  
```  
  
#### 参数  
 `true`，如果当前对象 HString 不为空；否则，返回 `false`。  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [HString 类](../windows/hstring-class.md)