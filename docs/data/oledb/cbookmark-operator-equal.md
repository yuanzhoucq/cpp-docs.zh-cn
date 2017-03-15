---
title: "CBookmark::operator = | Microsoft Docs"
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
  - "CBookmark<0>::operator="
  - "CBookmark<0>.operator="
  - "ATL.CBookmark.operator="
  - "CBookmark::operator="
  - "ATL.CBookmark<0>.operator="
  - "ATL::CBookmark<0>::operator="
  - "CBookmark.operator="
  - "ATL::CBookmark::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "= 运算符, 使用 OLE DB 模板"
  - "运算符 =, 书签"
  - "operator=, 书签"
ms.assetid: 23805af4-aedd-47ad-bef4-21d902463797
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBookmark::operator =
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

分配一个 `CBookmark` 对象给其他。  
  
## 语法  
  
```  
  
      CBookmark& operator =(   
   const CBookmark& bookmark    
) throw( );  
```  
  
## 备注  
 此运算符只在 **CBookmark\<0\>** 需要。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CBookmark 类](../../data/oledb/cbookmark-class.md)