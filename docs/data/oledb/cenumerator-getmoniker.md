---
title: "CEnumerator::GetMoniker | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetMoniker"
  - "CEnumerator.GetMoniker"
  - "CEnumerator::GetMoniker"
  - "ATL.CEnumerator.GetMoniker"
  - "ATL::CEnumerator::GetMoniker"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetMoniker 方法"
ms.assetid: 69a5cf2d-4a94-41dc-812d-bc1661d516d2
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CEnumerator::GetMoniker
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

分析显示名称提取可转换为字符串对象命名的组件。  
  
## 语法  
  
```  
  
      HRESULT GetMoniker(   
   LPMONIKER* ppMoniker    
) const throw( );  
HRESULT GetMoniker(   
   LPMONIKER* ppMoniker,   
   LPCTSTR lpszDisplayName    
) const throw( );  
```  
  
#### 参数  
 *ppMoniker*  
 \[out\] 从显示名称分析的名字对象 \([CEnumeratorAccessor::m\_szParseName](../../data/oledb/cenumeratoraccessor-m-szparsename.md)\) 当前行。  
  
 *lpszDisplayName*  
 \[in\] 分析的显示名称。  
  
## 返回值  
 标准版`HRESULT`。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CEnumerator 类](../../data/oledb/cenumerator-class.md)