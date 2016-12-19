---
title: "CBookmark::CBookmark | Microsoft Docs"
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
  - "CBookmark<0>.CBookmark<0>"
  - "CBookmark::CBookmark"
  - "ATL.CBookmark.CBookmark"
  - "CBookmark.CBookmark"
  - "CBookmark"
  - "ATL::CBookmark<0>::CBookmark<0>"
  - "ATL.CBookmark<0>.CBookmark<0>"
  - "CBookmark<0>::CBookmark<0>"
  - "ATL::CBookmark::CBookmark"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBookmark 类, 构造函数"
ms.assetid: 84f4ad2b-67d4-4ba3-8b2b-656a66fb6298
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBookmark::CBookmark
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

构造函数。  
  
## 语法  
  
```  
  
      CBookmark( );   
CBookmark(  
   DBLENGTH nSize   
);  
```  
  
#### 参数  
 `nSize`  
 \[in\] 大小以字节为单位的书签缓冲区。  
  
## 备注  
 第一个函数设置缓冲区对 **NULL** 和缓冲区大小设置为 0。  第二个函数将缓冲区大小设置为 `nSize`和缓冲区为字节数组 `nSize` 字节。  
  
> [!NOTE]
>  此函数只能用于 **CBookmark\<0\>**。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CBookmark 类](../../data/oledb/cbookmark-class.md)