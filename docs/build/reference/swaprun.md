---
title: "/SWAPRUN | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/swaprun"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/SWAPRUN editbin 选项"
  - "SWAPRUN editbin 选项"
  - "-SWAPRUN editbin 选项"
ms.assetid: 6eefd7f3-ca47-48e3-8509-323d27cf4ae7
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /SWAPRUN
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/SWAPRUN:{[!]NET|[!]CD}  
```  
  
## 备注  
 此选项编辑图像以通知操作系统将图像复制到交换文件并从那里运行它。  此选项用于驻留在网络或可移动媒体上的图像。  
  
 可以添加或移除 NET 或 CD 限定符：  
  
-   NET 指示图像驻留在网络上。  
  
-   CD 指示图像驻留在光盘或类似的可移动媒体上。  
  
-   使用 \!NET 和 \!CD 可反转 NET 和 CD 的效果。  
  
## 请参阅  
 [EDITBIN 选项](../../build/reference/editbin-options.md)