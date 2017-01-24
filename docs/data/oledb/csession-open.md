---
title: "CSession::Open | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CSession::Open"
  - "CSession::Open"
  - "CSession.Open"
  - "ATL.CSession.Open"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Open 方法"
ms.assetid: c2050c2c-9817-4857-be49-189f346968f6
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSession::Open
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

启动数据源对象的新会话。  
  
## 语法  
  
```  
  
      HRESULT Open(  
   const CDataSource& ds,  
   DBPROPSET *pPropSet = NULL,  
   ULONG ulPropSets = 0  
) throw( );  
```  
  
#### 参数  
 `ds`  
 \[in\] 会话将举行的数据源。  
  
 *pPropSet*  
 \[in\] 对数组的指针包含属性和值的结构将 [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)。  参阅《*OLE DB 程序员参考》\) 中的*[属性设置和属性组](https://msdn.microsoft.com/en-us/library/ms713696.aspx)[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]中。  
  
 `ulPropSets`  
 \[in\] [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) 结构数。*pPropSet* 参数传递的。  
  
## 返回值  
 标准 `HRESULT`。  
  
## 备注  
 必须打开数据源对象。[CDataSource::Open](../../data/oledb/cdatasource-open.md) 前请为 `CSession::Open`。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CSession 类](../../data/oledb/csession-class.md)