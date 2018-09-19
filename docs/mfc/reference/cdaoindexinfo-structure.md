---
title: CDaoIndexInfo 结构 |Microsoft Docs
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoIndexInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Indexes collection
- CDaoIndexInfo structure [MFC]
ms.assetid: 251d8285-78ce-4716-a0b3-ccc3395fc437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2cfeaada169addc01bc09893db0dedba2b7528d0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403105"
---
# <a name="cdaoindexinfo-structure"></a>CDaoIndexInfo 结构

`CDaoIndexInfo`结构包含有关为数据访问对象 (DAO) 定义的索引对象的信息。

## <a name="syntax"></a>语法

```cpp
struct CDaoIndexInfo {
    CDaoIndexInfo();                    // Constructor
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

### <a name="parameters"></a>参数

*m_strName*<br/>
唯一地命名字段对象。 有关详细信息，请参阅主题 DAO 帮助中的"名称属性"。

*m_pFieldInfos*<br/>
指向数组的指针[CDaoIndexFieldInfo](../../mfc/reference/cdaoindexfieldinfo-structure.md)对象指示哪些 tabledef 或记录集字段在索引中的键字段。 每个对象标识的索引中的一个字段。 默认索引顺序为升序。 索引对象可以表示为每个记录的索引键的一个或多个字段。 可以对这些升序、 降序或组合。

*m_nFields*<br/>
存储中的字段数`m_pFieldInfos`。

*m_bPrimary*<br/>
如果主属性为 TRUE，表示主索引的索引对象。 主索引包含唯一地标识预定义顺序中的表中的所有记录的一个或多个字段。 索引字段必须是唯一的因为索引对象的唯一属性也设置为 TRUE 在 DAO 中。 如果主索引由多个字段组成，每个字段可以包含重复值，但所有索引的字段值的每个组合必须唯一。 主索引包含表的键，并且通常包含的主键相同的字段。

如果设置表的主键，主键自动定义作为主索引的表。 有关详细信息，请参阅"主属性"和"唯一属性"DAO 帮助中的主题。

> [!NOTE]
> 可以有，最多一个主索引的表。

*m_bUnique*<br/>
指示索引对象是否表示一个表的唯一索引。 如果此属性为 TRUE，表示是唯一的索引的索引对象。 唯一索引包含一个或多个逻辑上排列中唯一的预定义顺序的表中的所有记录的字段。 如果该索引包含的一个字段，该字段中的值必须是唯一针对整个表。 如果该索引包含的多个字段，每个字段可以包含重复值，但每个组合中所有索引的字段的值必须是唯一。

如果 Unique 和主索引对象的属性设置为 TRUE，索引是唯一和主要： 它唯一地标识预定义的逻辑顺序表中的所有记录。 如果主属性设置为 FALSE，则索引是辅助索引。 辅助索引 （密钥和非键） 以逻辑方式排列预定义顺序中的记录，但不作为表中的记录的标识符。

有关详细信息，请参阅"主属性"和"唯一属性"DAO 帮助中的主题。

*m_bClustered*<br/>
指示索引对象是否表示一个表的聚集的索引。 如果此属性为 TRUE，索引对象所表示的聚集的索引;否则，事实并非如此。 聚集的索引包含一个或多个非键字段、 合起来看，排列中预定义顺序的表中的所有记录。 具有聚集索引表中的数据按原义存储在指定的聚集索引的顺序。 聚集的索引提供了高效访问表中的记录。 有关详细信息，请参阅主题 DAO 帮助中的"群集属性"。

> [!NOTE]
> 使用 Microsoft Jet 数据库引擎，因为 Jet 数据库引擎不支持聚集的索引的数据库会忽略 Clustered 属性。

*m_bIgnoreNulls*<br/>
指示是否有索引字段中具有 Null 值的记录的索引条目。 如果此属性为 TRUE，则与 Null 值的字段没有索引条目。 若要使搜索更快地使用字段的记录，可以定义字段的索引。 如果允许 Null 项索引的字段中，并期待许多要为 Null 的项，可以将索引对象 IgnoreNulls 属性设置为 TRUE 以减少索引使用的存储空间量。 IgnoreNulls 属性设置和所需的属性设置共同决定是否具有一个为 Null 的索引值的记录具有索引条目，如下表所示。

|IgnoreNulls|必需|索引字段中，则为 null|
|-----------------|--------------|-------------------------|
|True|False|允许 null 值未添加的索引条目。|
|False|False|允许 null 值添加索引条目。|
|True 或 False|True|不允许; 的 null 值未添加的索引条目。|

有关详细信息，请参阅主题 DAO 帮助中的"IgnoreNulls 属性"。

*m_bRequired*<br/>
指示 DAO 索引对象是否需要非 Null 值。 如果此属性为 TRUE，则索引对象不允许 Null 值。 有关详细信息，请参阅主题 DAO 帮助中的"所需属性"。

> [!TIP]
> 可以设置此属性对于 DAO 索引对象或字段对象 （包含 tabledef、 记录集或 querydef 对象），将其设置为字段对象。 在此之前，索引对象都会检查其属性设置为字段对象的有效性。

*m_bForeign*<br/>
指示索引对象是否表示一个表中的外键。 如果此属性为 TRUE，则索引表示表中的外键。 外键包括一个或多个字段的外部表中唯一标识主表中的行。 Microsoft Jet 数据库引擎创建外部表的索引对象，并创建一种关系，强制实施引用完整性时设置外的属性。 有关详细信息，请参阅主题 DAO 帮助中的"外属性"。

*m_lDistinctCount*<br/>
指示在 index 对象关联的表中包含的唯一值数。 检查非重复计数属性以确定的唯一值或中索引键数。 任意键是只计算一次，即使在索引允许重复的值可能会多次出现的值。 此信息可在尝试通过评估索引信息来优化数据访问的应用程序中。 唯一值的数量也称为是索引对象的基数。 非重复计数属性将始终反映键的实际的数目在特定的时间。 例如，导致事务回滚的更改将不会立即反映在非重复计数属性。 有关详细信息，请参阅主题 DAO 帮助中的"非重复计数属性"。

## <a name="remarks"></a>备注

对主要、 次要和上面所有的引用指示如何通过返回的信息`GetIndexInfo`类中的成员函数[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo)并[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo)。

索引对象不表示由 MFC 类。 相反，DAO 对象类的基础 MFC 对象[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)包含称为索引集合的索引对象的集合。 这些类提供成员函数访问各个项的索引的信息，或可以访问它们使用一次性`CDaoIndexInfo`对象通过调用`GetIndexInfo`包含对象的成员函数。

`CDaoIndexInfo` 具有一个构造函数和析构函数以便正确地分配和解除分配中的索引字段信息`m_pFieldInfos`。

检索的信息`GetIndexInfo`tabledef 对象的成员函数存储在`CDaoIndexInfo`结构。 调用`GetIndexInfo`包含 tabledef 对象的索引集合中存储的索引对象的成员函数。 `CDaoIndexInfo` 此外定义了`Dump`成员函数在调试生成。 可以使用`Dump`转储的内容`CDaoIndexInfo`对象。

## <a name="requirements"></a>要求

**标头：** afxdao.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)
