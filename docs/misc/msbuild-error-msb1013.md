---
title: "MSBuild 错误 MSB1013 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.RepeatedResponseFileError"
helpviewer_keywords: 
  - "MSB1013"
ms.assetid: 3e85c710-99e6-4141-b058-63a144a06454
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB1013
**该响应文件被指定了两次。  每个响应文件只能指定一次。**  
  
 命令行含有对多个响应文件的引用。  如 `msbuild @response.rsp @response.rsp`。  
  
 此错误还会在以下情况下发生：指定的响应文件包含对另一个响应文件的引用，而那个响应文件又包含对原始响应文件的引用。  一个响应文件在每个编译中只能指定一次。  
  
### 更正此错误  
  
-   移除对响应文件的重复引用。  例如，使用 `msbuild @response.rsp`，而不要使用 `msbuild @response.rsp @response.rsp`。  
  
-   从它引用的响应文件中移除对原始响应文件的引用。  
  
## 请参阅  
 [命令行参考](../Topic/MSBuild%20Command-Line%20Reference.md)