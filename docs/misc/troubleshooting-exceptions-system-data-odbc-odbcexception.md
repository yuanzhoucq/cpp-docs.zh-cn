---
title: "关于异常的疑难解答：System.Data.Odbc.OdbcException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHOdbc"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "异常, ODBC"
  - "ODBC, 异常"
  - "OdbcException 类"
ms.assetid: 5f2c2167-cf7b-4634-af86-44dc71eff02d
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Data.Odbc.OdbcException
如果 ODBC 数据源返回警告或错误，则会生成 <xref:System.Data.Odbc.OdbcException> 异常。  
  
## 相关提示  
 **验证您是否在使用有效的凭据进行连接。**  
 检查凭据以确保它们是有效的。  
  
 **验证服务器名称是否正确，服务器是否正在运行。**  
 确保使用了正确的服务器名称，且该服务器可达。  
  
## 备注  
 每当 <xref:System.Data.Odbc.OdbcDataAdapter> 遇到服务器生成的错误时，都将引发此异常。  
  
 如果错误的严重程度太高，服务器可能会关闭 <xref:System.Data.Odbc.OdbcConnection>。 但是，用户可以重新打开连接并继续操作。  
  
## 请参阅  
 <xref:System.Data.Odbc.OdbcException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)