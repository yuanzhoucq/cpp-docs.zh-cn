---
title: "CBookmark::SetBookmark | Microsoft Docs"
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
  - "CBookmark<0>::SetBookmark"
  - "ATL.CBookmark<0>.SetBookmark"
  - "CBookmark<0>.SetBookmark"
  - "SetBookmark"
  - "ATL::CBookmark::SetBookmark"
  - "ATL::CBookmark<0>::SetBookmark"
  - "CBookmark.SetBookmark"
  - "ATL.CBookmark.SetBookmark"
  - "CBookmark::SetBookmark"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetBookmark 方法"
ms.assetid: bcd26831-6045-4e69-96d6-abf8037fc18d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBookmark::SetBookmark
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

复制引用 `pBuffer` 的书签值到 `CBookmark` 缓冲区将缓冲区大小设置为 `nSize`。  
  
## 语法  
  
```  
  
      HRESULT SetBookmark(  
   DBLENGTH nSize,  
   BYTE* pBuffer   
) throw( );  
```  
  
#### 参数  
 *nSize*  
 \[in\] 书签缓冲区的大小。  
  
 `pBuffer`  
 \[in\] 向书签包含值的字节数组的指针。  
  
## 返回值  
 标准 `HRESULT`。  
  
## 备注  
 此函数只能用于 **CBookmark\<0\>**。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CBookmark 类](../../data/oledb/cbookmark-class.md)