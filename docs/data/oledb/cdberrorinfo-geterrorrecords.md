---
title: "CDBErrorInfo::GetErrorRecords | Microsoft Docs"
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
  - "CDBErrorInfo.GetErrorRecords"
  - "ATL.CDBErrorInfo.GetErrorRecords"
  - "ATL::CDBErrorInfo::GetErrorRecords"
  - "GetErrorRecords"
  - "CDBErrorInfo::GetErrorRecords"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetErrorRecords 方法"
ms.assetid: 07746774-bcca-4833-8f55-a619e9777c17
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDBErrorInfo::GetErrorRecords
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取指定的对象的错误的记录。  
  
## 语法  
  
```  
  
      HRESULT GetErrorRecords(   
   IUnknown* pUnk,   
   const IID& iid,   
   ULONG* pcRecords    
) throw( );  
HRESULT GetErrorRecords(   
   ULONG* pcRecords    
) throw( );  
```  
  
#### 参数  
 *pUnk*  
 \[in\] 连接到来获得错误记录的对象。  
  
 `iid`  
 \[in\] 接口的 IID 与错误。  
  
 *pcRecords*  
 \[out\] 对 \(基于\) 计数的指针错误的记录。  
  
## 返回值  
 标准版`HRESULT`。  
  
## 备注  
 使用函数的第一个形式您是否希望签请连接获取错误信息。  否则，使用第二种形式。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDBErrorInfo 类](../../data/oledb/cdberrorinfo-class.md)