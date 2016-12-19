---
title: "FtmBase::DisconnectObject 方法 | Microsoft Docs"
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
  - "ftm/Microsoft::WRL::FtmBase::DisconnectObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DisconnectObject 方法"
ms.assetid: 33253eec-3a65-4e72-8525-0249245a4790
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# FtmBase::DisconnectObject 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

优秀释放对对象的任何外部连接。  对象的服务器在关闭之前调用该方法的对象的实现。  
  
## 语法  
  
```  
STDMETHODIMP DisconnectObject(  
   __in DWORD dwReserved  
) override;  
```  
  
#### 参数  
 `dwReserved`  
 留待将来使用；必须为零。  
  
## 返回值  
 S\_OK，如果成功；否则，一错误的 HRESULT。  
  
## 要求  
 **页眉：**ftm.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [FtmBase 类](../windows/ftmbase-class.md)