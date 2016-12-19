---
title: "FtmBase::CreateGlobalInterfaceTable 方法 | Microsoft Docs"
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
  - "ftm/Microsoft::WRL::FtmBase::CreateGlobalInterfaceTable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateGlobalInterfaceTable 方法"
ms.assetid: bb82a0c5-22b9-4844-9204-7922033d8b07
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# FtmBase::CreateGlobalInterfaceTable 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

创建全局表 \(GIT\) 接口。  
  
## 语法  
  
```  
static HRESULT CreateGlobalInterfaceTable(  
   __out IGlobalInterfaceTable **git  
);  
```  
  
#### 参数  
 `git`  
 该操作完成，对全局表接口的指针。  
  
## 返回值  
 S\_OK，如果成功；否则，一错误的 HRESULT。  
  
## 备注  
 有关更多信息，请参见“COM 连接”COM 引用”主题的副主题中的“IGlobalInterfaceTable”主题 MSDN Library。  
  
## 要求  
 **页眉：**ftm.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [FtmBase 类](../windows/ftmbase-class.md)