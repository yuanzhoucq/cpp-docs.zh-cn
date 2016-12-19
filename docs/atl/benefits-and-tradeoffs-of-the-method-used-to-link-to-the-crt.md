---
title: "Benefits and Tradeoffs of the Method Used to Link to the CRT | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ATL_MIN_CRT 宏"
ms.assetid: 49b485f7-9487-49e4-b12a-0f710b620e2b
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Benefits and Tradeoffs of the Method Used to Link to the CRT
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您的项目可以使用CRT动态或静态链接。  在分层下表显示优点和权衡在使用的方法选择参与。  
  
|方法|优点|权衡|  
|--------|--------|--------|  
|静态链接到CRT<br /><br /> （**Runtime Library** 设置为 **Single\-threaded**\)|CRT DLL在图像上运行的系统不需要。|有关启动代码25K添加到您的图像，完全增加其大小。|  
|动态链接到CRT<br /><br /> （**Runtime Library** 设置为 **Multi\-threaded**\)|将图像不需要CRT启动代码，因此，较小。|CRT DLL必须在运行该图像的系统。|  
  
 [链接到在您的ATL项目的CRT](../atl/linking-to-the-crt-in-your-atl-project.md) 主题讨论如何选择为了CRT链接的方式使用。  
  
## 请参阅  
 [使用 ATL 和 C 运行时代码进行编程](../atl/programming-with-atl-and-c-run-time-code.md)   
 [运行库行为](../build/run-time-library-behavior.md)   
 [CRT 库功能](../c-runtime-library/crt-library-features.md)