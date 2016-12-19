---
title: "HandleT::Close 方法 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HandleT::Close"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Close 方法"
ms.assetid: 1b9d597c-abcf-4028-a068-0344560009f6
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HandleT::Close 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

关闭当前的 HandleT对象。  
  
## 语法  
  
```  
void Close();  
```  
  
## 备注  
 在当前 HandleT 的句柄关闭并 HandleT 设置为无效状态。  
  
 如果处理不正确关闭，异常在调用线程中引发。  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [HandleT 类](../windows/handlet-class.md)