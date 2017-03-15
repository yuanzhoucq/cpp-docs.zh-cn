---
title: "CManualAccessor::CreateParameterAccessor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CManualAccessor::CreateParameterAccessor"
  - "ATL.CManualAccessor.CreateParameterAccessor"
  - "CManualAccessor.CreateParameterAccessor"
  - "CreateParameterAccessor"
  - "CManualAccessor::CreateParameterAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateParameterAccessor 方法"
ms.assetid: d0a2095b-b37c-4472-accc-45ef365a18c8
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CManualAccessor::CreateParameterAccessor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

分配内存并绑定参数的构造初始化参数数据成员。  
  
## 语法  
  
```  
  
      HRESULT CreateParameterAccessor(   
   int nBindEntries,   
   void* pBuffer,   
   DBLENGTH nBufferSize    
) throw( );  
```  
  
#### 参数  
 `nBindEntries`  
 \[in\] 列数。  
  
 `pBuffer`  
 \[in\] 与输入列存储的缓冲区的指针。  
  
 `nBufferSize`  
 \[in\] 缓冲区的大小 \(以字节为单位\)。  
  
## 返回值  
 标准的 `HRESULT` 值。  
  
## 备注  
 必须在调用 [AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md)之前调用此函数。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)   
 [CManualAccessor::CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md)   
 [CManualAccessor::AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md)