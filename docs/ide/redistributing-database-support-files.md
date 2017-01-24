---
title: "重新分发数据库支持文件 | Microsoft Docs"
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
  - "数据库支持文件 [C++], 重新分发"
  - "重新分发数据库支持文件"
ms.assetid: d80cffe0-177c-4515-9de7-fbf0517eb8d6
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 重新分发数据库支持文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以重新发布用于数据访问对象 \(DAO\) 以及 Microsoft 数据访问 SDK 中的数据库技术的支持文件。  
  
## 安装 DAO 支持文件  
 若要获取最新版本的 DAO，请参见 Microsoft 支持网站上的 [文章 239114：如何获取 Microsoft Jet 4.0 数据库引擎的最新服务包](http://go.microsoft.com/fwlink/?LinkId=198014) 。  
  
## 安装 Microsoft 数据访问 SDK 支持文件  
 使用 Mdac\_typ.exe 来安装对 ODBC、OLE DB、ActiveX 数据对象 \(ADO\) 和远程数据服务 \(RDS\) 的支持。  Mdac\_typ.exe 位于Visual Studio 安装媒体上的..\\WCU\\MDAC28\\文件夹中。  你也可以从[微软下载中心](http://go.microsoft.com/fwlink/?LinkId=198015)下载Mdac\_typ.exe 。  
  
 有关更多信息，请在[MSDN](http://go.microsoft.com/fwlink/?LinkId=198016) 网站上，搜索“Redistributing MDAC 2.8 SP1”。  如果使用 Visual Studio 安装项目来部署应用程序，请参见[Deployment and Dependencies](http://msdn.microsoft.com/zh-cn/49e9b84d-bd6a-4388-b9ac-46ea79cf0733)。  
  
## 请参阅  
 [重新分发 Visual C\+\+ 文件](../ide/redistributing-visual-cpp-files.md)