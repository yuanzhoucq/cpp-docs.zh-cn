---
title: "FtmBase::ReleaseMarshalData 方法 | Microsoft Docs"
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
  - "ftm/Microsoft::WRL::FtmBase::ReleaseMarshalData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ReleaseMarshalData 方法"
ms.assetid: a94f9940-183a-4fde-8504-d223f346a0a9
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# FtmBase::ReleaseMarshalData 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

销毁一个封送的数据包。  
  
## 语法  
  
```  
STDMETHODIMP ReleaseMarshalData(  
   __in IStream *pStm  
) override;  
```  
  
#### 参数  
 `pStm`  
 对包含要销毁的数据包与流的指针。  
  
## 返回值  
 S\_OK，如果成功；否则，一错误的 HRESULT。  
  
## 要求  
 **页眉：**ftm.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [FtmBase 类](../windows/ftmbase-class.md)