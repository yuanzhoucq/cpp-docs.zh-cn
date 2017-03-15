---
title: "CDynamicAccessor::Close | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CDynamicAccessor::Close"
  - "ATL.CDynamicAccessor.Close"
  - "CDynamicAccessor.Close"
  - "CDynamicAccessor::Close"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Close 方法"
ms.assetid: 2a28ded2-d7ed-4e80-90bf-143133c93feb
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDynamicAccessor::Close
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

断开所有列，释放分配的内存，然后释放类中[IAccessor](https://msdn.microsoft.com/en-us/library/ms719672.aspx)的接口指针。  
  
## 语法  
  
```  
  
void Close( ) throw( );  
  
```  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)