---
title: "CDaoTableDefInfo 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDaoTableDefInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoTableDefInfo 结构"
  - "DAO（数据访问对象）, TableDefs 集合"
ms.assetid: c01ccebb-5615-434e-883c-4f60eac943dd
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# CDaoTableDefInfo 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CDaoTableDefInfo` 结构包含有关用于数据访问对象 tabledef \(DAO\) 定义的对象的信息。  
  
## 语法  
  
```  
  
      struct CDaoTableDefInfo  
{  
   CString m_strName;               // Primary  
   BOOL m_bUpdatable;               // Primary  
   long m_lAttributes;              // Primary  
   COleDateTime m_dateCreated;      // Secondary  
   COleDateTime m_dateLastUpdated;  // Secondary  
   CString m_strSrcTableName;       // Secondary  
   CString m_strConnect;            // Secondary  
   CString m_strValidationRule;     // All  
   CString m_strValidationText;     // All  
   long m_lRecordCount;             // All  
};  
```  
  
#### 参数  
 `m_strName`  
 唯一命名 tabledef 对象。  若要直接检索此属性的值，调用 [GetName](../Topic/CDaoTableDef::GetName.md) tabledef 对象的成员函数。  有关更多信息，请参见主题“属性名称”DAO 帮助。  
  
 `m_bUpdatable`  
 指示进行更改是否可对表。  快速确定表是否是可更新中打开表的 `CDaoTableDef` 对象并调用对象的成员函数。[CanUpdate](../Topic/CDaoTableDef::CanUpdate.md) `CanUpdate` 始终返回非零 \(**TRUE**\) 新生成 tabledef 对象和 0 \(**FALSE**\) 连接的 tabledef 对象。  新 tabledef 只有对象可追加到当前用户具有写入权限的数据库。  如果表中只包含 nonupdatable 字段，`CanUpdate` 返回 0。  在一个或多个字段是可更新的，则 `CanUpdate` 返回非零值。  您只能编辑可更新的字段。  有关更多信息，请参见主题“可更新的属性”DAO 帮助。  
  
 `m_lAttributes`  
 指定 tabledef 对象表示表的特性。  若要检索、tabledef 的当前属性，请调用成员函数。[GetAttributes](../Topic/CDaoTableDef::GetAttributes.md) 返回的值可以是这些长常数的组合 \(使用按位或 \(  **&#124;**\) 运算符：  
  
-   使用 Microsoft Jet 数据库引擎的数据库的\)**dbAttachExclusive**，指示表用于独占使用打开的连接的表。  
  
-   使用 Microsoft Jet 数据库引擎的数据库的\)**dbAttachSavePWD**，指示用户 ID 和密码的连接表中保存的连接信息。  
  
-   **dbSystemObject** 表指示是 Microsoft Jet 数据库引擎提供的系统表。（只读。）  
  
-   **dbHiddenObject** 表指示是 Microsoft Jet 数据库引擎提供的一个隐藏窗体 \(用于临时使用\)。（只读。）  
  
-   指示**dbAttachedTable** 表是从非 ODBC 数据库的连接的冲突表，例如数据库。  
  
-   **dbAttachedODBC** 表是一个 ODBC 数据库的连接的表，例如 Microsoft SQL Server。  
  
 `m_dateCreated`  
 表创建日期和时间。  直接检索表创建日期，调用 `CDaoTableDef` 对象的函数 [GetDateCreated](../Topic/CDaoTableDef::GetDateCreated.md) 成员与表。  请参见下面的说明。更多信息。  有关相关信息，请参见主题“DateCreated，LastUpdated 属性”DAO 帮助。  
  
 `m_dateLastUpdated`  
 进行的最近更改的日期和时间对表的设计。  直接检索表是最新更新的日期，请调用 `CDaoTableDef` 对象的函数 [GetDateLastUpdated](../Topic/CDaoTableDef::GetDateLastUpdated.md) 成员与表。  请参见下面的说明。更多信息。  有关相关信息，请参见主题“DateCreated，LastUpdated 属性”DAO 帮助。  
  
 *m\_strSrcTableName*  
 指定连接表的名称，如果有\)。  直接检索源表名称，请调用 `CDaoTableDef` 对象的函数 [GetSourceTableName](../Topic/CDaoTableDef::GetSourceTableName.md) 成员与表。  
  
 `m_strConnect`  
 提供有关源打开数据库中的信息。  通过调用 `CDaoTableDef` 对象的函数 [GetConnect](../Topic/CDaoTableDef::GetConnect.md) 成员检查该属性。  有关的更多信息请连接字符串，请参见 `GetConnect`。  
  
 `m_strValidationRule`  
 验证在 tabledef 的数据的值字段，从而更改或添加到表。  验证为使用 Microsoft Jet 数据库引擎的数据库。仅支持。  直接检索验证规则，请调用 `CDaoTableDef` 对象的函数 [GetValidationRule](../Topic/CDaoTableDef::GetValidationRule.md) 成员与表。  有关相关信息，请参见主题“ValidationRule 属性”DAO 帮助。  
  
 `m_strValidationText`  
 指定消息文本应用程序应该显示的值，如果属性指定 ValidationRule 的验证规则是不够的。  有关相关信息，请参见主题“ValidationText 属性”DAO 帮助。  
  
 *m\_lRecordCount*  
 在 tabledef 对象访问记录数。  此属性为只读。  直接检索记录数量，请调用 `CDaoTableDef` 对象的成员函数。[GetRecordCount](../Topic/CDaoTableDef::GetRecordCount.md) `GetRecordCount` 的文档进一步介绍记录数量。  如果表包含大量记录，请注意将检索此计数的，这是一个耗时的操作。  
  
## 备注  
 tabledef 是 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)类对象。  为 Main，附属的引用和所有的指示信息如何通过类 `CDaoDatabase`中的 [GetTableDefInfo](../Topic/CDaoDatabase::GetTableDefInfo.md) 成员函数返回。  
  
 [CDaoDatabase::GetTableDefInfo](../Topic/CDaoDatabase::GetTableDefInfo.md) 成员函数检索的信息在 `CDaoTableDefInfo` 结构存储。  调用集合 TableDefs tabledef 对象存储 `CDaoDatabase` 对象的 `GetTableDefInfo` 成员函数中。  `CDaoTableDefInfo` 还定义了函数调试版本的 `Dump` 成员。  可以使用 `Dump` 转储 `CDaoTableDefInfo` 对象的内容。  
  
 日期和时间设置从基表创建或之前更新计算机的派生。  在多用户环境中，用户应直接从文件的服务器获得这些设置以避免在 DateCreated 和属性设置 LastUpdated 的变体。  
  
## 要求  
 **页眉：** afxdao.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef Class](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoDatabase Class](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoTableDef::CanUpdate](../Topic/CDaoTableDef::CanUpdate.md)   
 [CDaoTableDef::GetAttributes](../Topic/CDaoTableDef::GetAttributes.md)   
 [CDaoTableDef::GetDateCreated](../Topic/CDaoTableDef::GetDateCreated.md)   
 [CDaoTableDef::GetDateLastUpdated](../Topic/CDaoTableDef::GetDateLastUpdated.md)   
 [CDaoTableDef::GetRecordCount](../Topic/CDaoTableDef::GetRecordCount.md)   
 [CDaoTableDef::GetSourceTableName](../Topic/CDaoTableDef::GetSourceTableName.md)   
 [CDaoTableDef::GetValidationRule](../Topic/CDaoTableDef::GetValidationRule.md)   
 [CDaoTableDef::GetValidationText](../Topic/CDaoTableDef::GetValidationText.md)