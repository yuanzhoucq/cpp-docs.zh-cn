---
title: "CAccessorRowset::GetColumnInfo | Microsoft Docs"
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
  - "CAccessorRowset.GetColumnInfo"
  - "CAccessorRowset::GetColumnInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetColumnInfo 方法"
ms.assetid: 8ade2388-3c58-43cd-8ed6-499ee0531291
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAccessorRowset::GetColumnInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从已打开的行集合获取列信息。  
  
## 语法  
  
```  
  
      HRESULT GetColumnInfo(  
   DBORDINAL* pulColumns,  
   DBCOLUMNINFO** ppColumnInfo,  
   LPOLESTR* ppStrings   
) const;  
HRESULT GetColumnInfo(  
   DBORDINAL* pColumns,  
   DBCOLUMNINFO** ppColumnInfo   
);  
```  
  
#### 参数  
 有关更多信息，请参见 [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx)（在 *OLE DB 程序员参考* 中）。  
  
## 返回值  
 标准版`HRESULT`。  
  
## 备注  
 用户必须释放返回的列信息属性和字符串缓冲区。  使用 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) 并需要覆盖绑定时，请使用此方法的第二个版本中。  
  
 有关更多信息，请参见 [OLE DB 程序员参考](https://msdn.microsoft.com/en-us/library/ms722704.aspx)（在  中）。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CAccessorRowset 类](../../data/oledb/caccessorrowset-class.md)