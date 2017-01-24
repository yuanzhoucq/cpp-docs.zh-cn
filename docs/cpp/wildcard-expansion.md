---
title: "通配符扩展 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_setargv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_setargv 函数"
  - "星号通配符"
  - "命令行, 处理参数"
  - "命令行, 通配符"
  - "命令行通配符"
  - "问号, 通配符"
ms.assetid: 1a543398-607b-4404-93d1-45d290bde638
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 通配符扩展
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 可以使用通配符（问号 \(?\) 和星号 \(\*\)）在命令行上指定文件名和路径参数。  
  
 命令行参数由名为 **\_setargv** 的例程（或宽字节环境中的 **\_wsetargv**）处理，默认情况下，该例程不会将通配符扩展到 `argv` 字符串数组的单独字符串中。  有关启用通配符扩展的详细信息，请参阅[扩展通配符参数](../c-language/expanding-wildcard-arguments.md)。  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [main：程序启动](../cpp/main-program-startup.md)