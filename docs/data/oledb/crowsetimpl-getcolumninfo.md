---
title: "CRowsetImpl::GetColumnInfo | Microsoft Docs"
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
  - "GetColumnInfo"
  - "CRowsetImpl.GetColumnInfo"
  - "CRowsetImpl::GetColumnInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetColumnInfo 方法"
ms.assetid: 9ef76525-f996-4c6f-81b9-68eb260350ef
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowsetImpl::GetColumnInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索特定客户端请求的列信息。  
  
## 语法  
  
```  
  
      static ATLCOLUMNINFO* CRowsetBaseImpl::GetColumnInfo(  
   T* pv,  
   ULONG* pcCols   
);  
```  
  
#### 参数  
 `pv`  
 \[in\] 给用户的 `CRowsetImpl` 派生类的指针。  
  
 `pcCols`  
 \[in\] 指针 \(输出\) 设置为列数返回。  
  
## 返回值  
 对静态 **ATLCOLUMNINFO** 结构的指针。  
  
## 备注  
 此方法是一项高级重写。  
  
 此方法由多个基类实现调用检索特定客户端请求的列信息。  通常，此方法将调用 `IColumnsInfoImpl`。  如果重写此方法，您必须在 `CRowsetImpl`中放置方法派生类的版本。  由于方法在非 templatized 类可能放置，必须将 `pv` 设置为适当的 `CRowsetImpl`派生类。  
  
 下面的示例演示使用 **GetColumnInfo's** 条件。  在本示例中，**CMyRowset** 是 `CRowsetImpl`派生类。  若要重写此类的所有实例的 `GetColumnInfo` 中，将以下方法在 **CMyRowset** 类定义：  
  
 [!CODE [NVC_OLEDB_Provider#1](../CodeSnippet/VS_Snippets_Cpp/NVC_OLEDB_Provider#1)]  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [CRowsetImpl 类](../../data/oledb/crowsetimpl-class.md)