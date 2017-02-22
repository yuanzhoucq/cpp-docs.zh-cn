---
title: "CCommand::SetParameterInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SetParameterInfo"
  - "CCommand.SetParameterInfo"
  - "CCommand::SetParameterInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetParameterInfo 方法"
ms.assetid: a70e92f4-1e73-41d7-a5b7-c6ebb45a6477
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CCommand::SetParameterInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定每个命令的本机类型。  
  
## 语法  
  
```  
  
      HRESULT CCommandBase::SetParameterInfo(  
   DB_UPARAMS ulParams,  
   const DBORDINAL* pOrdinals,  
   const DBPARAMBINDINFO* pParamInfo   
) throw( );  
```  
  
#### 参数  
 参阅《*OLE DB 程序员参考》\) 中的*[ICommandWithParameters::SetParameterInfo](https://msdn.microsoft.com/en-us/library/ms725393.aspx)。  
  
## 返回值  
 标准版`HRESULT`。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CCommand 类](../../data/oledb/ccommand-class.md)