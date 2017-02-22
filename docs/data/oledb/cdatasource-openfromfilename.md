---
title: "CDataSource::OpenFromFileName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDataSource::OpenFromFileName"
  - "ATL::CDataSource::OpenFromFileName"
  - "OpenFromFileName"
  - "CDataSource.OpenFromFileName"
  - "ATL.CDataSource.OpenFromFileName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OpenFromFileName 方法"
ms.assetid: c4226de6-59da-4368-9c15-c5afab86f68b
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# CDataSource::OpenFromFileName
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从由用户提供的文件名指定的文件打开数据源。  
  
## 语法  
  
```  
  
        HRESULT OpenFromFileName(   
   LPCOLESTR szFileName    
) throw( );  
```  
  
#### 参数  
 `szFileName`  
 \[in\] 文件的名称，通常是数据源连接 \(.UDL\) 文件。  
  
 有关数据链接文件（.udl 文件）的详细信息，请参阅 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] 中的[数据链接 API 概述](https://msdn.microsoft.com/en-us/library/ms718102.aspx)。  
  
## 返回值  
 一个标准 `HRESULT`。  
  
## 备注  
 此方法使用 oledb32.dll 中的服务组件打开数据源对象；此 DLL 包含资源池、自动事务登记等服务组件功能的实现。  有关详细信息，请访问 [http:\/\/msdn.microsoft.com\/library\/default.asp?url\=\/library\/oledb\/htm\/oledbole\_db\_services.asp?frame\=true](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true)，参阅“OLE DB 程序员参考”中的“OLE DB 服务”。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDataSource 类](../../data/oledb/cdatasource-class.md)