---
title: "导入到应用程序中 | Microsoft Docs"
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
  - "应用程序 [C++], 导入到"
  - "DLL [C++], 导入"
  - "导入 DLL [C++], 应用程序"
ms.assetid: 9d646466-e12e-4710-8ad9-c819c0375fcc
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 导入到应用程序中
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用两种方法将函数导入到应用程序中：  
  
-   在主应用程序的函数定义中使用 **\_\_declspec\(dllimport\)** 关键字。  
  
-   将模块定义 \(.def\) 文件与 **\_\_declspec\(dllimport\)** 一起使用。  
  
## 你希望做什么？  
  
-   [使用 \_\_declspec\(dllimport\) 导入到应用程序中](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [使用 \_\_declspec\(dllimport\) 导入函数调用](../build/importing-function-calls-using-declspec-dllimport.md)  
  
-   [使用 \_\_declspec\(dllimport\) 导入数据](../build/importing-data-using-declspec-dllimport.md)  
  
-   [使用 DEF 文件导入](../build/importing-using-def-files.md)  
  
## 请参阅  
 [导入和导出](../build/importing-and-exporting.md)