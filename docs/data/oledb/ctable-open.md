---
title: "CTable::Open | Microsoft Docs"
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
  - "ATL.CTable.Open"
  - "ATL::CTable::Open"
  - "CTable::Open"
  - "CTable.Open"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Open 方法"
ms.assetid: 5d006d95-74d7-4e2b-b243-a33bc53b5455
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTable::Open
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

打开表。  
  
## 语法  
  
```  
  
      HRESULT Open(  
   const CSession& session,  
   LPCWSTR wszTableName,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0  
) throw ( );  
HRESULT Open(  
   const CSession& session,  
   LPCSTR szTableName,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0  
) throw ( );  
HRESULT Open(  
   const CSession& session,  
   DBID& dbid,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0  
) throw ( );  
```  
  
#### 参数  
 `session`  
 \[in\] 表中打开的会话。  
  
 *wszTableName*  
 \[in\] 打开表的名称，通过为 Unicode 字符串。  
  
 *szTableName*  
 \[in\] 打开表的名称，通过为 ANSI 字符串。  
  
 *dbid*  
 \[in\] 打开表的 **DBID**。  
  
 *pPropSet*  
 \[in\] 对数组的指针包含属性和值的结构将 [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)。  见[属性集和属性组](https://msdn.microsoft.com/en-us/library/ms713696.aspx)在 *OLE DB程序员参考*在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  NULL的默认值指定没有属性。  
  
 `ulPropSets`  
 \[in\] [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) 结构数。*pPropSet* 参数传递的。  
  
## 返回值  
 标准版`HRESULT`。  
  
## 备注  
 有关更多信息，请参见 [IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx)（在 *OLE DB 程序员参考* 中）。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CTable 类](../../data/oledb/ctable-class.md)