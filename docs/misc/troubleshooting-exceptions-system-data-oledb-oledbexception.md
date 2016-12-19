---
title: "关于异常的疑难解答：System.Data.OleDb.OleDbException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "OLEDB"
  - "OleDbException 类"
  - "异常，OLEDB"
ms.assetid: f50077cf-e411-41f0-b73e-19eef83036c1
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Data.OleDb.OleDbException
当 OLE DB 数据源返回警告或错误时，会生成 <xref:System.Data.OleDb.OleDbException> 异常。  
  
## 相关提示  
 **验证您是否在使用有效的凭据进行连接。**  
 确保您提供的凭据有效。 有关详细信息，请参阅<xref:System.Data.OleDb.OleDbErrorCollection>。  
  
 **验证服务器名称是否正确，服务器是否正在运行。**  
 确保使用了正确的服务器名称，且该服务器可达。 有关详细信息，请参阅<xref:System.Data.OleDb.OleDbErrorCollection>。  
  
### 备注  
 当用于 OLE DB 的 .NET Framework 数据提供程序遇到服务器生成的错误时，将引发此异常。  
  
 如果错误的严重程度太高，服务器可能会关闭 <xref:System.Data.OleDb.OleDbConnection>。 但是，用户可以重新打开连接并继续操作。  
  
## 请参阅  
 <xref:System.Data.OleDb.OleDbException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)