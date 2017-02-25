---
title: "CCommand::GetParameterInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetParameterInfo"
  - "CCommand.GetParameterInfo"
  - "CCommand::GetParameterInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetParameterInfo 方法"
ms.assetid: 9cd9277f-0161-4bd8-ad24-58e5e90b92a7
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CCommand::GetParameterInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取命令、其名称及其类型的列表。  
  
## 语法  
  
```  
  
      HRESULT CCommandBase::GetParameterInfo(  
   DB_UPARAMS* pParams,  
   DBPARAMINFO** ppParamInfo,  
   OLECHAR** ppNamesBuffer   
) throw ( );  
```  
  
#### 参数  
 参阅《*OLE DB 程序员参考》\) 中的*[ICommandWithParameters::GetParameterInfo](https://msdn.microsoft.com/en-us/library/ms714917.aspx)。  
  
## 返回值  
 标准版`HRESULT`。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CCommand 类](../../data/oledb/ccommand-class.md)