---
title: "CVTRES 错误 CVT1100 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "CVT1100"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CVT1100"
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# CVTRES 错误 CVT1100
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

重复的资源 \-\- type:type、name:name、language:language、flags:flags、size:size  
  
 给定资源被指定一次以上。  
  
 如果链接器正在创建类型库而您未指定 [\/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md)，并且您的项目中的某一资源已经使用 1，则可产生该错误。  在这种情况下，请指定 \/TLBID 并指定 65535 以内的另一个数字。