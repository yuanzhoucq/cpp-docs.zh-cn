---
title: "CArrayRowset::operator | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CArrayRowset::operator[]"
  - "CArrayRowset.operator[]"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "运算符 []，数组"
  - "[] 运算符"
  - "运算符 []，数组"
ms.assetid: 3bb8c310-cc1e-46e8-9711-9b565488acaa
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CArrayRowset::operator
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为访问行集合中的行所提供类似数组的语法。  
  
## 语法  
  
```  
  
      TAccessor  
      & operator[](int nRow);  
```  
  
#### 参数  
 `TAccessor`  
 指定访问器类型中的模板参数。行集合中。  
  
 `nRow`  
 \[in\] 数组行 \(元素\) 的次数要访问。  
  
## 返回值  
 请求行的内容。  
  
## 备注  
 如果 `nRow` 超过所在行集合中，将引发异常。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CArrayRowset 类](../../data/oledb/carrayrowset-class.md)