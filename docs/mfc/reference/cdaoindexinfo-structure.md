---
title: "CDaoIndexInfo 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoIndexInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Indexes collection
- CDaoIndexInfo structure [MFC]
ms.assetid: 251d8285-78ce-4716-a0b3-ccc3395fc437
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2617f8cb0d56098c0fef774dc56d56fa182e2482
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cdaoindexinfo-structure"></a>CDaoIndexInfo 结构
`CDaoIndexInfo`结构包含有关为数据访问对象 (DAO) 定义的索引对象的信息。  
  
## <a name="syntax"></a>语法  
  
```  
struct CDaoIndexInfo {  
    CDaoIndexInfo();
*// Constructor  
    CString m_strName;  // Primary  
    CDaoIndexFieldInfo* m_pFieldInfos;  // Primary  
    short m_nFields;    // Primary  
    BOOL m_bPrimary;    // Secondary  
    BOOL m_bUnique;     // Secondary  
    BOOL m_bClustered;  // Secondary  
    BOOL m_bIgnoreNulls;                // Secondary  
    BOOL m_bRequired;   // Secondary  
    BOOL m_bForeign;    // Secondary  
    long m_lDistinctCount;              // All  
 *// Below the // Implementation comment: *// Destructor, not otherwise documented  
};   
```  
  
#### <a name="parameters"></a>参数  
 `m_strName`  
 唯一地命名字段对象。 有关详细信息，请参阅主题 DAO 帮助中的"名称属性"。  
  
 `m_pFieldInfos`  
 指向数组的指针[CDaoIndexFieldInfo](../../mfc/reference/cdaoindexfieldinfo-structure.md) ，该值指示哪些 tabledef 或记录集字段索引中的键字段的对象。 每个对象标识索引中的一个字段。 默认索引顺序为升序。 索引对象可以具有表示为每个记录的索引键的一个或多个字段。 可以对这些升序、 降序或组合。  
  
 `m_nFields`  
 存储中的字段数`m_pFieldInfos`。  
  
 *m_bPrimary*  
 如果主属性为**TRUE**，索引对象表示主索引。 主索引包含唯一标识预定义的顺序中的表中的所有记录的一个或多个字段。 索引字段必须是唯一的因为索引对象的唯一属性也设置为**TRUE**在 DAO 中。 如果主索引包含多个字段，每个字段可以包含重复值，但所有编制索引的字段中值的每个组合必须唯一。 主索引包含表的键，并且通常包含为主键相同的字段。  
  
 当你设置表的主键时，为主键被自动定义为表的主索引。 有关详细信息，请参阅"主属性"和"唯一 Property"DAO 帮助中的主题。  
  
> [!NOTE]
>  可以有，最多，对表的一个主索引。  
  
 *m_bUnique*  
 指示索引对象是否表示表的唯一索引。 如果此属性为**TRUE**，索引对象代表中是唯一的索引。 唯一索引包含一个或多个以逻辑方式排列中唯一的预定义的顺序的表中的所有记录的字段。 如果索引包含一个字段，该字段中的值必须是整个表的唯一的。 如果索引包含多个字段，每个字段可以包含重复值，但所有编制索引的字段中值的每个组合必须唯一。  
  
 如果索引对象的唯一和主属性设置为**TRUE**，此索引是唯一的并且主： 唯一标识预定义的逻辑顺序中的表中的所有记录。 如果主属性设置为**FALSE**，索引是辅助索引。 辅助索引 （密钥和非键） 进行逻辑排列预定义的顺序中的记录，但不作为表中的记录的标识符。  
  
 有关详细信息，请参阅"主属性"和"唯一 Property"DAO 帮助中的主题。  
  
 *m_bClustered*  
 指示索引对象是否表示表的聚集的索引。 如果此属性为**TRUE**，索引对象表示聚集的索引; 否则，不。 聚集的索引由一个或多个非键字段、 合起来看，排列中的预定义的顺序的表中的所有记录。 具有聚集索引，表中的数据按原义存储在指定的聚集索引的顺序。 聚集的索引提供对表中的记录的高效访问。 有关详细信息，请参阅主题 DAO 帮助中的"群集属性"。  
  
> [!NOTE]
>  使用 Microsoft Jet 数据库引擎，因为 Jet 数据库引擎不支持聚集的索引的数据库的情况下，将忽略此聚集索引属性。  
  
 *m_bIgnoreNulls*  
 指示是否在其索引字段中具有 Null 值的记录的索引条目。 如果此属性为**TRUE**，具有 Null 值的字段不具有索引条目。 若要使搜索更快地使用的字段的记录，你可以定义字段的索引。 如果不允许索引字段中的 Null 项和期待许多要为 Null 的项，则可以设置到索引对象的 IgnoreNulls 属性**TRUE**以减少索引使用的存储空间量。 IgnoreNulls 属性设置和所需的属性设置一起确定是否具有 Null 索引值的记录将索引条目时，具有以下表所示。  
  
|IgnoreNulls|必需|在索引字段为 null|  
|-----------------|--------------|-------------------------|  
|True|False|允许; 的 null 值添加没有索引条目。|  
|False|False|允许; 的 null 值添加的索引条目。|  
|True 或 False|True|不允许; 的 null 值添加没有索引条目。|  
  
 有关详细信息，请参阅主题 DAO 帮助中的"IgnoreNulls 属性"。  
  
 `m_bRequired`  
 指示 DAO 索引对象是否需要非 Null 值。 如果此属性为**TRUE**，索引对象不允许 Null 值。 有关详细信息，请参阅主题 DAO 帮助中的"所需属性"。  
  
> [!TIP]
>  当你可以设置此属性对于 DAO 索引对象或字段对象 （包含按 tabledef、 记录集或 querydef 对象中） 时，将其设置的字段对象。 之前的索引对象，会检查字段对象的属性设置的有效性。  
  
 *m_bForeign*  
 指示索引对象是否表示表的外键。 如果此属性为**TRUE**，索引表示外的键表中。 外键包含一个或多个外部表中唯一标识字段主表中的行。 Microsoft Jet 数据库引擎创建外部表的索引对象，并创建强制实施引用完整性的关系时设置外的属性。 有关详细信息，请参阅主题 DAO 帮助中的"外属性"。  
  
 *m_lDistinctCount*  
 指示索引对象的关联的表中包含的唯一值的数目。 检查 DistinctCount 属性以确定的唯一值或中索引键数。 任意键是只计算一次，即使可能会有多个出现的该值索引允许重复值。 此信息很有用的应用程序尝试通过评估索引信息优化数据访问。 唯一值的数量也称为是索引对象的基数。 DistinctCount 属性不会始终反映键的实际的数目在特定的时间。 例如，由事务回滚引起的更改将不会立即反映在 DistinctCount 属性中。 有关详细信息，请参阅主题 DAO 帮助中的"非重复计数属性"。  
  
## <a name="remarks"></a>备注  
 对主、 辅助数据库，以及所有上面的引用指示如何通过返回的信息`GetIndexInfo`类中的成员函数[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo)和[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo)。  
  
 索引对象不由 MFC 类表示。 相反，DAO 对象类的基础 MFC 对象[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)包含称为索引集合的索引对象的集合。 这些类提供成员函数来访问各个项的索引信息，或可以访问其在一次与`CDaoIndexInfo`对象通过调用`GetIndexInfo`包含对象的成员函数。  
  
 `CDaoIndexInfo`具有一个构造函数和析构函数以正确地分配和释放中的索引字段信息`m_pFieldInfos`。  
  
 检索的信息`GetIndexInfo`成员函数的 tabledef 对象存储在`CDaoIndexInfo`结构。 调用`GetIndexInfo`包含 tabledef 对象的索引集合中存储索引对象的成员函数。 `CDaoIndexInfo`此外定义`Dump`成员函数在调试生成。 你可以使用`Dump`以转储的内容`CDaoIndexInfo`对象。  
  
## <a name="requirements"></a>惠?  
 **标头：** afxdao.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)

