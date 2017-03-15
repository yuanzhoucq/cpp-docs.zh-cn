---
title: "CUtlProps::OnPropertyChanged | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OnPropertyChanged"
  - "CUtlProps.OnPropertyChanged"
  - "CUtlProps::OnPropertyChanged"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OnPropertyChanged 方法"
ms.assetid: c5924210-b685-46c4-87f8-1b81e5bd3378
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CUtlProps::OnPropertyChanged
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

调用在设置属性后处理链接的属性。  
  
## 语法  
  
```  
  
      virtual HRESULT OnPropertyChanged(  
   ULONG /* iCurSet */,  
   DBPROP* pDBProp   
);  
```  
  
#### 参数  
 `iCurSet`  
 索引属性设置数组中；零，如果只有一个属性。  
  
 `pDBProp`  
 属性 ID 和新值在 [DBPROP](https://msdn.microsoft.com/en-us/library/ms717970.aspx) 结构。  
  
## 返回值  
 标准 `HRESULT`。  默认返回值为 `S_OK`。  
  
## 备注  
 如果希望处理被链接的属性，如书签或来更新的值依赖于另一个属性的值，应重写此函数。  
  
## 示例  
 在此函数中，用户从 `DBPROP*` 参数获取属性 ID。  现在，将链接 ID 属性比较可能的。  如果找到属性时，`SetProperties` 调用与其他与属性结合现在将设置属性。  在这种情况下，获取一，如果 `DBPROP_IRowsetLocate`、`DBPROP_LITERALBOOKMARKS`或 `DBPROP_ORDEREDBOOKMARKS` 属性，可设置 `DBPROP_BOOKMARKS` 属性。  
  
 [!CODE [NVC_OLEDB_Provider#2](../CodeSnippet/VS_Snippets_Cpp/NVC_OLEDB_Provider#2)]  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [CUtlProps 类](../../data/oledb/cutlprops-class.md)