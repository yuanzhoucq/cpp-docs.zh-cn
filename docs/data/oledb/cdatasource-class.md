---
title: "CDataSource 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CDataSource"
  - "ATL::CDataSource"
  - "CDataSource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDataSource 类"
ms.assetid: 99bf862c-9d5c-4117-9501-aa0e2672085c
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataSource 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

对应于 OLE DB 数据源对象，通过提供程序表示连接到数据源。  
  
## 语法  
  
```  
class CDataSource  
```  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[关闭](../../data/oledb/cdatasource-close.md)|关闭 UDP 连接。|  
|[GetInitializationString](../../data/oledb/cdatasource-getinitializationstring.md)|检索当前打开数据源的初始化字符串。|  
|[获得属性](../../data/oledb/cdatasource-getproperties.md)|获取用于连接数据源的当前设置的属性值。|  
|[GetProperty](../../data/oledb/cdatasource-getproperty.md)|获取用于连接数据源的当前设置的单个属性的值。|  
|[打开](../../data/oledb/cdatasource-open.md)|创建到提供程序 \(数据源\) 的连接使用 **CLSID**， **ProgID**或调用方提供的 `CEnumerator` 的对象。|  
|[OpenFromFileName](../../data/oledb/cdatasource-openfromfilename.md)|打开一数据源从用户提供的文件名指定的文件。|  
|[OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md)|初始化字符串打开指定的数据源。|  
|[OpenWithPromptFileName](../../data/oledb/cdatasource-openwithpromptfilename.md)|允许用户选择以前创建的数据链接文件打开对应的数据源。|  
|[OpenWithServiceComponents](../../data/oledb/cdatasource-openwithservicecomponents.md)|使用数据链接打开对话框，数据源对象。|  
  
## 备注  
 一个或多个数据库会话可以为单个串联创建。  这些会话由 `CSession`表示。  必须调用 [CDataSource::Open](../../data/oledb/cdatasource-open.md) 在创建具有 `CSession::Open`的会话之前打开连接。  
  
 有关如何使用 `CDataSource` 控件的示例，请参见[](../../top/visual-cpp-samples.md "Visual C++ Samples")  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)