---
title: "CManualAccessor::CreateAccessor | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CManualAccessor::CreateAccessor"
  - "CreateAccessor"
  - "ATL.CManualAccessor.CreateAccessor"
  - "CManualAccessor.CreateAccessor"
  - "CManualAccessor::CreateAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateAccessor 方法"
ms.assetid: 594c8d6d-b49a-4818-a9a5-81c8115d4e42
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CManualAccessor::CreateAccessor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

分配列绑定结构的内存并初始化列数据成员。  
  
## 语法  
  
```  
  
      HRESULT CreateAccessor(   
   int nBindEntries,   
   void* pBuffer,   
   DBLENGTH nBufferSize    
) throw( );  
```  
  
#### 参数  
 `nBindEntries`  
 \[in\] 列数。  此数字应与调用数。[CManualAccessor::AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md) 函数。  
  
 `pBuffer`  
 \[in\] 对输出列存储的缓冲区的指针。  
  
 `nBufferSize`  
 \[in\] 字节缓冲区的大小。  
  
## 返回值  
 `HRESULT` 标准的值之一。  
  
## 备注  
 在调用函数 `CManualAccessor::AddBindEntry` 之前，调用此函数。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)   
 [DBViewer 示例](../../top/visual-cpp-samples.md)