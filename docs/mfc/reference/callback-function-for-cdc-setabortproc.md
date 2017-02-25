---
title: "Callback Function for CDC::SetAbortProc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Callback Function for CDC::SetAbortProc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "回调函数, 对于 CDC::SetAbortProc"
ms.assetid: daa36d5d-15de-40fc-8d37-a865d06c4710
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# Callback Function for CDC::SetAbortProc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

名称 *AbortFunc* 是应用程序所提供的函数名称的占位符。  
  
## 语法  
  
```  
  
      BOOL CALLBACK EXPORT AbortFunc(   
   HDC hPr,   
   int code    
);  
```  
  
#### 参数  
 *hPr*  
 标识设备上下文。  
  
 `code`  
 指定发生了错误。  如果未发生任何错误，它是 0。  为 **SP\_OUTOFDISK**，如果管理当前打印用完磁盘空间，并且更多磁盘空间将变为可用，则应用程序等待。  如果 `code` 为 **SP\_OUTOFDISK**，应用程序不必中止打印作业。  如果不使用，则必须对版式监督通过调用 **PeekMessage** 或 **GetMessage**。Windows 函数  
  
## 返回值  
 中止处理程序函数的返回值不为零，如果打印作业。延续和 0，则将其移除。  
  
## 备注  
 必须导出实际名称 \(如 [CDC::SetAbortProc](../Topic/CDC::SetAbortProc.md)的"备注"节所述。  
  
## 要求  
 **标头:** afxwin.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::SetAbortProc](../Topic/CDC::SetAbortProc.md)