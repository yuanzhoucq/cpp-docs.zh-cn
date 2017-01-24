---
title: "CDBErrorInfo 类 | Microsoft Docs"
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
  - "CDBErrorInfo"
  - "ATL::CDBErrorInfo"
  - "ATL.CDBErrorInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDBErrorInfo 类"
ms.assetid: 9a5c18a2-ee3e-40f5-ab4c-581288d7f737
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDBErrorInfo 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为处理 [IErrorRecords](https://msdn.microsoft.com/en-us/library/ms718112.aspx) 使用 OLE DB 接口的 OLE DB 提供错误支持。  
  
## 语法  
  
```  
class CDBErrorInfo  
```  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[GetAllErrorInfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md)|返回在错误记录任何包含错误信息。|  
|[GetBasicErrorInfo](../../data/oledb/cdberrorinfo-getbasicerrorinfo.md)|调用 [IErrorRecords::GetBasicErrorInfo](https://msdn.microsoft.com/en-us/library/ms723907.aspx) 指定返回有关错误的基本信息。|  
|[GetCustomErrorObject](../../data/oledb/cdberrorinfo-getcustomerrorobject.md)|调用[IErrorRecords::GetCustomErrorObject](https://msdn.microsoft.com/en-us/library/ms725417.aspx)返回自定义错误对接口的指针。|  
|[GetErrorInfo](../../data/oledb/cdberrorinfo-geterrorinfo.md)|调用 [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx) 返回一个 **IErrorInfo** 接口指向指定记录的指针。|  
|[GetErrorParameters](../../data/oledb/cdberrorinfo-geterrorparameters.md)|调用 [IErrorRecords::GetErrorParameters](https://msdn.microsoft.com/en-us/library/ms715793.aspx) 返回错误参数。|  
|[GetErrorRecords](../../data/oledb/cdberrorinfo-geterrorrecords.md)|获取指定的对象的错误的记录。|  
  
## 备注  
 此接口返回一个或多个错误记录给用户。  调用 [CDBErrorInfo::GetErrorRecords](../../data/oledb/cdberrorinfo-geterrorrecords.md) 首先，需要获取计数错误的记录。  然后调用一个访问功能，如 [CDBErrorInfo::GetAllErrorInfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md)，检索每个记录的错误信息。  
  
## 要求  
 **Header:** atldbcli.h  
  
## 请参阅  
 [DBViewer](../../top/visual-cpp-samples.md)   
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)