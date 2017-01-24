---
title: "CCommand::GetNextResult | Microsoft Docs"
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
  - "ATL::CCommand::GetNextResult"
  - "CCommand::GetNextResult"
  - "GetNextResult"
  - "CCommand.GetNextResult"
  - "ATL.CCommand.GetNextResult"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetNextResult 方法"
ms.assetid: 63df9b55-9490-45c4-934a-879c5c2725d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCommand::GetNextResult
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果一种可用，将取下一个结果集。  
  
## 语法  
  
```  
  
      HRESULT GetNextResult(  
   DBROWCOUNT* pulRowsAffected,  
   bool bBind = true   
) throw( );  
```  
  
#### 参数  
 *pulRowsAffected*  
 \[in\/out\] 指向受返回命令影响的行计数的内存的指针。  
  
 `bBind`  
 \[in\] 指定是否在执行后自动绑定命令。  默认是 **true**，导致命令自动绑定。  设置 `bBind` 为 **false** 以阻止命令的自动绑定，以便手动绑定。\(OLAP 用户对手动绑定特别感兴趣。\)  
  
## 返回值  
 标准版`HRESULT`。  
  
## 备注  
 如果结果集以前提取，此函数释放以前的结果集和未绑定列。  如果 `bBind` 为 **true**，则绑定新列。  
  
 应调用此函数时，如果通过设置 `CCommand` 模板参数 *TMultiple*\=`CMultipleResults`指定多个结果。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CCommand 类](../../data/oledb/ccommand-class.md)