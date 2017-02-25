---
title: "CDaoIndexFieldInfo 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDaoIndexFieldInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoIndexFieldInfo 结构"
  - "DAO（数据访问对象）, 索引字段集合"
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# CDaoIndexFieldInfo 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CDaoIndexFieldInfo` 结构包含有关数据访问对象（DAO）定义的索引对象的信息 。  
  
## 语法  
  
```  
  
      struct CDaoIndexFieldInfo  
{  
   CString m_strName;          // Primary  
   BOOL m_bDescending;         // Primary  
};  
```  
  
#### 参数  
 `m_strName`  
 唯一命名索引字段对象。  有关详细信息，请参见主题“名称属性”在DAO 帮助中。  
  
 *m\_bDescending*  
 指出索引对象定义索引的顺序。  **TRUE**，如果顺序与降序。  
  
## 备注  
 索引对象可以拥有若干数目的字段，指示哪些字段\) tabledef 索引 \(或基于表的记录集。  对主上面的引用信息指示如何在调用获取的 [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) 对象的 `m_pFieldInfos` 成员返回类或 [CDaoTableDef](../Topic/CDaoTableDef::GetIndexInfo.md) [CDaoRecordset](../Topic/CDaoRecordset::GetIndexInfo.md)的 `GetIndexInfo` 成员函数。  
  
 索引对象和索引字段对象未由 MFC 类表示。  相反，基于类 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) 或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 的 MFC 对象的 DAO 对象包含索引对象集合，称为索引集合。  每个索引对象，然后，字段包含对象的集合。  这些类提供成员函数访问索引信息各个项，也可同时用 `GetIndexInfo`对象访问它们，通过调用包含对象的 `CDaoIndexInfo` 成员函数。  `CDaoIndexInfo` 对象，然后，它具有数据成员，即 `m_pFieldInfos`，指向 `CDaoIndexFieldInfo` 对象的数组。  
  
 调用集合索引存储索引对象您感兴趣 tabledef 或包含的记录集对象的 `GetIndexInfo` 成员函数中。  然后访问 [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) 对象的 `m_pFieldInfos` 成员。  `m_pFieldInfos` 数组的长度。`m_nFields`中。  `CDaoIndexFieldInfo` 还定义了函数调试版本的 `Dump` 成员。  您可以使用`Dump` 显示`CDaoIndexFieldInfo`对象的内容。  
  
## 要求  
 **头文件：** afxdao.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetIndexInfo](../Topic/CDaoTableDef::GetIndexInfo.md)   
 [CDaoRecordset::GetIndexInfo](../Topic/CDaoRecordset::GetIndexInfo.md)