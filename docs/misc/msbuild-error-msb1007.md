---
title: "MSBuild 错误 MSB1007 | Microsoft Docs"
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
  - "MSBuild.MissingLoggerError"
helpviewer_keywords: 
  - "MSB1007"
ms.assetid: bf45dbc3-50cd-488a-87df-9e647cd71f10
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB1007
**指定记录器。**  
  
 必须为 **\/logger** 开关指定记录器。  
  
### 更正此错误  
  
1.  使用记录器类和记录器程序集两者指定记录器。  `<logger>` 语法为：  
  
     `<logger class>,<logger assembly>[;<logger parameters>]`  
  
     `<logger class>` 语法为：  
  
    ```  
    [<partial or full namespace>.]<logger class name>  
    ```  
  
     `<logger assembly>` 语法为：  
  
    ```  
    {<assembly name>[,<strong name>] | <assembly file>}  
    ```  
  
     `<logger parameters>` 是可选的，它们完全按您所键入的样子传递给记录器。  
  
     **\/logger** 开关的一些示例包括：  
  
     `/logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`  
  
     `/logger:XMLLogger,C:\Loggers\MyLogger.dll`  
  
     `/logger:XMLLogger,..  \Loggers\MyLogger.dll;OutputAsHTML`  
  
## 请参阅  
 [命令行参考](../Topic/MSBuild%20Command-Line%20Reference.md)