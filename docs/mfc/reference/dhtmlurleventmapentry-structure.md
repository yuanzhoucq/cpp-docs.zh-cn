---
title: "DHtmlUrlEventMapEntry 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DHtmlUrlEventMapEntry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DHtmlUrlEventMapEntry 结构"
ms.assetid: 43117c1f-1a51-406c-aa2f-fea647080049
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# DHtmlUrlEventMapEntry 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`DHtmlUrlEventMapEntry` 结构提供多 URL 事件映射支持。  
  
## 语法  
  
```  
  
      struct DHtmlUrlEventMapEntry  
{  
   LPCTSTR szUrl;  
   const DHtmlEventMapEntry *pEventMap;  
};  
```  
  
#### 参数  
 `szUrl`  
 URL。  
  
 *pEventMap*  
 与 URL 关联的事件映射。  
  
## 要求  
 **头文件：** afxdhtml.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)