---
title: "CDaoIndexInfo 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDaoIndexInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoIndexInfo 结构"
  - "DAO（数据访问对象）, 索引集合"
ms.assetid: 251d8285-78ce-4716-a0b3-ccc3395fc437
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# CDaoIndexInfo 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CDaoIndexInfo` 结构包含有关数据访问对象（DAO）定义的索引对象的信息 。  
  
## 语法  
  
```  
  
      struct CDaoIndexInfo {  
   CDaoIndexInfo( );                   // Constructor  
   CString m_strName;                  // Primary  
   CDaoIndexFieldInfo* m_pFieldInfos;  // Primary  
   short m_nFields;                    // Primary  
   BOOL m_bPrimary;                    // Secondary  
   BOOL m_bUnique;                     // Secondary  
   BOOL m_bClustered;                  // Secondary  
   BOOL m_bIgnoreNulls;                // Secondary  
   BOOL m_bRequired;                   // Secondary  
   BOOL m_bForeign;                    // Secondary  
   long m_lDistinctCount;              // All  
  
   // Below the // Implementation comment:  
   // Destructor, not otherwise documented  
};   
```  
  
#### 参数  
 `m_strName`  
 唯一命名字段对象。  有关详细信息，请参见主题“名称属性”在DAO 帮助中。  
  
 `m_pFieldInfos`  
 指向[CDaoIndexFieldInfo](../../mfc/reference/cdaoindexfieldinfo-structure.md) 对象的数组的指针指示哪些表结构或记录集字段是索引的关键字段。  每个对象标识索引的字段。  默认索引顺序是升序的。  索引对象可以拥有表示各个记录的一个或多个键索引字段。  这些对象可以是升序，降序或组合。  
  
 `m_nFields`  
 存储在 `m_pFieldInfos`中的字段数。  
  
 *m\_bPrimary*  
 如果主要属性是 **TRUE**，索引对象表示主索引。  主索引包括一个或多个字段，在表格中以预定义的顺序位移的表示所有记录。  因为索引字段必须是唯一的，索引对象的单个属性在DAO中也设置为**TRUE**。  如果主索引由多个字段，各字段能包含重复值，但是，来自所有索引字段的值的每种组合必须是唯一的。  主索引包括表的键并且通常包含相同的字段作为主键。  
  
 当你为一个表设置主键，主键将自动定为表的索引。  有关更多信息，请参见主题“主要属性”和“唯一属性”在DAO 帮助中。  
  
> [!NOTE]
>  表可以有至多一个主索引。  
  
 *m\_bUnique*  
 指出索引对象是否表示表的唯一索引。  如果此属性 **TRUE**，索引对象表示索引是唯一的。  唯一索引包括一个或多个字段,在一个表中以唯一的，预定义的顺序逻辑地安排所有记录  如果索引包含一个字段，在该字段值必须对整个表是唯一的。  如果索引由多个字段组成，各字段能包含重复值，但是，来自所有索引字段的值的每种组合必须是唯一的。  
  
 如果索引对象的唯一主属性设置为 **TRUE**，那么索引是唯一的并且是主的：其唯一标识表中的所有记录以预定义，逻辑的顺序。  如果主要属性设置为 **FALSE**，该索引是二级索引。  次级索引 \(两个键和非键\) 在表中不作为记录的标识符以预定义的顺序逻辑地安排记录。  
  
 有关更多信息，请参见主题“主要属性”和“唯一属性”在DAO 帮助中。  
  
 *m\_bClustered*  
 指出索引对象是否表示表的聚集索引。  如果此属性 **TRUE**，索引对象表示聚集索引；否则，它不是。  聚集索引由一个或多个非键字段组成，合起来，在表中以预定义顺序安排所有字段。  用聚集索引，表中的数据逐条的存储在由聚集索引指定的顺序中  聚集索引提供对表中记录高效的访问。  有关更多信息，请参见主题"聚集属性"在DAO帮助中。  
  
> [!NOTE]
>  数据库集群属性将被忽略,使用Microsoft Jet数据库引擎，因为Jet 数据库引擎不支持聚集索引。  
  
 *m\_bIgnoreNulls*  
 指示在索引字段中是否有 具有null 值用于记录的索引条目记录。  如果此属性 **TRUE**，字段空值没有索引项。  为了使用字段搜索记录更快，你可以为字段定义索引。  如果在索引字段允许 null 输入并期望很多输入为空，可以将索引对象的属性设置为 IgnoreNulls **TRUE** 减少索引使用的存储空间。  IgnoreNulls 的属性的设置和所需的属性的设置一起决定空索引值的记录是否有索引输入，如下表所示。  
  
|IgnoreNulls|必需|索引字段中的 Null|  
|-----------------|--------|-----------------|  
|True|False|允许空值；不会添加索引输入。|  
|False|False|允许空值；添加索引输入。|  
|True 或 False|True|不允许空值；不会添加索引输入。|  
  
 有关更多信息，请参见主题 "忽略空值属性" 在 DAO 帮助中。  
  
 `m_bRequired`  
 指示 DAO 索引对象是否需要一个非空值。  如果此属性 **TRUE**，索引对象不允许空值。  有关更多信息，请参见主题 "所需属性" 在 DAO 帮助中。  
  
> [!TIP]
>  当你可以为 DAO 索引对象或者字段对象 \(由表结构、记录集或查询结构对象包含\)设置这个属性，为字段对象设置它。  字段对象的属性设置的有效性将在索引对象之前检查。  
  
 *m\_bForeign*  
 指出索引对象是否在表示表示外键。  如果此属性 **TRUE**,索引在表中表示外键。  外键由一个或多个在外表中的字段组成，唯一标识主表中的一行。  Microsoft Jet 数据库引擎为外表创建索引对象并当创建一个强制引用完整性关系时设置外部属性，。  有关更多信息，请参见请参见主题 "外部属性" 在 DAO 帮助中。  
  
 *m\_lDistinctCount*  
 指示包含在在关联表中的索引对象唯一值的数量。  检查 DistinctCount 属性确定在索引中唯一值或键的数量。  任意键仅计数一次，即使该值可能有多次出现，如果索引允许重复值。  此信息在尝试通过计算索引信息优化数据访问的应用程序中很有用。  唯一值的数目也称为索引对象的基数。  在特定时间 DistinctCount 属性并非会反映键的实际数量。  例如，事务回滚引起的改变将不会立刻反映在中 DistinctCount 属性中。  有关更多信息，请参见主题 "DistinctCount属性" 在 DAO 帮助中。  
  
## 备注  
 主键，二级键和所有上面的引用指示信息如何由 `GetIndexInfo` 成员函数返回，该函数在类 [CDaoTableDef](../Topic/CDaoTableDef::GetIndexInfo.md) 和 [CDaoRecordset](../Topic/CDaoRecordset::GetIndexInfo.md).  
  
 索引对象不被 MFC 类表示。  相反，基于类 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) 或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 的 MFC 对象的 DAO 对象包含索引对象集合，称为索引集合。  这些类提供成员函数访问索引信息各个项，也可同时用 `GetIndexInfo`对象访问它们，通过调用包含对象的 `CDaoIndexInfo` 成员函数。  
  
 `CDaoIndexInfo` 具有一个构造函数和析构函数用于正确分配和解除分配在`m_pFieldInfos`中的索引字段信息。  
  
 由表结构对象的 `GetIndexInfo` 成员函数检索到的信息储存在 `CDaoIndexInfo` 结构中。  调用存储索引集合索引对象包含表结构对象的 `GetIndexInfo` 成员函数。  `CDaoIndexInfo` 还定义了函数调试版本的 `Dump` 成员。  您可以使用`Dump` 显示`CDaoIndexInfo`对象的内容。  
  
## 要求  
 **页眉：** afxdao.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetIndexInfo](../Topic/CDaoTableDef::GetIndexInfo.md)