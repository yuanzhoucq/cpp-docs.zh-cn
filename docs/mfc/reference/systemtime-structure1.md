---
title: "SYSTEMTIME 结构&amp;1; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SYSTEMTIME"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SYSTEMTIME 结构"
ms.assetid: 9aaef4d6-de79-4fa1-8158-86b245ef5bff
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# SYSTEMTIME 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`SYSTEMTIME` 结构使用单个成员的年、月、日、星期、小时、分钟、秒和毫秒表示日期和时间。  
  
## 语法  
  
```  
  
      typedef struct _SYSTEMTIME {  
   WORD wYear;  
   WORD wMonth;  
   WORD wDayOfWeek;  
   WORD wDay;  
   WORD wHour;  
   WORD wMinute;  
   WORD wSecond;  
   WORD wMilliseconds;  
} SYSTEMTIME;  
```  
  
#### 参数  
 *wYear*  
 当前年。  
  
 *wMonth*  
 当前月份；一月即表示为 1。  
  
 *wDayOfWeek*  
 周的当前日；星期天为 0，星期一为 1，依此类推。  
  
 *wDay*  
 月的当前天。  
  
 *wHour*  
 当前时。  
  
 *wMinute*  
 当前分钟。  
  
 *wSecond*  
 当前秒。  
  
 *wMilliseconds*  
 当前毫秒。  
  
## 示例  
 [!code-cpp[NVC_MFC_Utilities#39](../../mfc/codesnippet/CPP/systemtime-structure1_1.cpp)]  
  
## 要求  
 **标头：**winbase.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CTime::CTime](../Topic/CTime::CTime.md)