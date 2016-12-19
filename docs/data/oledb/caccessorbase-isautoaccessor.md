---
title: "CAccessorBase::IsAutoAccessor | Microsoft Docs"
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
  - "IsAutoAccessor"
  - "CAccessorBase.IsAutoAccessor"
  - "CAccessorBase::IsAutoAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsAutoAccessor 方法"
ms.assetid: c330da15-2947-4050-ad00-8f776adc58fb
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAccessorBase::IsAutoAccessor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果数据为自动访问器检索在移动操作，则返回 true。  
  
## 语法  
  
```  
  
      bool IsAutoAccessor(  
   ULONG nAccessor   
) const;  
```  
  
#### 参数  
 `nAccessor`  
 \[in\] 访问器的零数字的偏移量。  
  
## 返回值  
 如果访问器是否为自动访问，返回 **true**。  否则，返回 **false**。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CAccessorBase 类](../../data/oledb/caccessorbase-class.md)