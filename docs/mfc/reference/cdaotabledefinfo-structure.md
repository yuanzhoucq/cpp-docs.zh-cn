---
title: CDaoTableDefInfo 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoTableDefInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoTableDefInfo structure [MFC]
- DAO (Data Access Objects), TableDefs collection
ms.assetid: c01ccebb-5615-434e-883c-4f60eac943dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0563cf930d9722adf175a2b82c1e7788ea3d066a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415819"
---
# <a name="cdaotabledefinfo-structure"></a>CDaoTableDefInfo 结构

`CDaoTableDefInfo`结构包含有关 tabledef 对象定义为数据访问对象 (DAO) 的信息。

## <a name="syntax"></a>语法

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

#### <a name="parameters"></a>参数

*m_strName*<br/>
唯一地命名 tabledef 对象。 若要直接检索此属性的值，请调用 tabledef 对象[GetName](../../mfc/reference/cdaotabledef-class.md#getname)成员函数。 有关详细信息，请参阅主题 DAO 帮助中的"名称属性"。

*m_bUpdatable*<br/>
指示是否可以对表进行更改。 若要确定表是否为可更新的快速方法是打开`CDaoTableDef`对象的表，并调用对象的[CanUpdate](../../mfc/reference/cdaotabledef-class.md#canupdate)成员函数。 `CanUpdate` 始终返回非零值 (TRUE) 的新创建的 tabledef 对象和一个附加的 tabledef 对象为 0 (FALSE)。 可以仅向当前用户对其具有写入权限的数据库追加新 tabledef 对象。 如果表包含仅不可更新字段，`CanUpdate`返回 0。 在一个或多个字段都是可更新，`CanUpdate`返回非零值。 可以编辑可更新的字段。 有关详细信息，请参阅主题 DAO 帮助中的"可更新属性"。

*m_lAttributes*<br/>
指定由 tabledef 对象表示的表的特征。 若要检索 tabledef 对象的当前属性，请调用其[GetAttributes](../../mfc/reference/cdaotabledef-class.md#getattributes)成员函数。 返回的值可以是这些长整数常量的组合 (使用按位 OR (**&#124;**) 运算符):

- `dbAttachExclusive` 对于使用 Microsoft Jet 数据库引擎的数据库，指示表是附加的表打开以供独占使用。

- `dbAttachSavePWD` 对于使用 Microsoft Jet 数据库引擎的数据库，指示与连接信息一起保存的用户 ID 和附加表的密码。

- `dbSystemObject` 指示表是由 Microsoft Jet 数据库引擎提供的系统表。 （只读。）

- `dbHiddenObject` 指示表是由 Microsoft Jet 数据库引擎 （供临时使用） 提供一个隐藏的表。 （只读。）

- `dbAttachedTable` 指示表是从非 ODBC 数据库，如 Paradox 数据库附加的表。

- `dbAttachedODBC` 指示表是附加从 ODBC 数据库，例如 Microsoft SQL Server 表。

*m_dateCreated*<br/>
日期和时间创建表。 若要直接检索表的创建的日期，请调用[GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated)成员函数的`CDaoTableDef`与表关联的对象。 有关详细信息，请参阅下面的注释。 相关信息，请参阅 DAO 帮助中的主题"DateCreated，上次更新属性"。

*m_dateLastUpdated*<br/>
日期和时间对表的设计所做的最新更改。 若要直接检索上次更新表的日期，请调用[GetDateLastUpdated](../../mfc/reference/cdaotabledef-class.md#getdatelastupdated)成员函数的`CDaoTableDef`与表关联的对象。 有关详细信息，请参阅下面的注释。 相关信息，请参阅 DAO 帮助中的主题"DateCreated，上次更新属性"。

*m_strSrcTableName*<br/>
如果有，请指定附加表的名称。 若要直接检索源表名称，请调用[GetSourceTableName](../../mfc/reference/cdaotabledef-class.md#getsourcetablename)成员函数的`CDaoTableDef`与表关联的对象。

*m_strConnect*<br/>
提供有关源的打开的数据库的信息。 您可以检查此属性通过调用[GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect)成员函数在`CDaoTableDef`对象。 有关详细信息连接字符串，请参阅`GetConnect`。

*m_strValidationRule*<br/>
一个值，因为更改或添加到表验证 tabledef 字段中的数据。 验证仅支持使用 Microsoft Jet 数据库引擎的数据库。 若要直接检索验证规则，请调用[GetValidationRule](../../mfc/reference/cdaotabledef-class.md#getvalidationrule)成员函数的`CDaoTableDef`与表关联的对象。 有关相关信息，请参阅主题 DAO 帮助中的"ValidationRule 属性"。

*m_strValidationText*<br/>
一个值，指定如果不满足有效性规则属性中指定的验证规则，应显示你的应用程序的消息的文本。 有关相关信息，请参阅主题 DAO 帮助中的"有效性文本属性"。

*m_lRecordCount*<br/>
访问 tabledef 对象中的记录数。 此属性设置为只读。 若要直接检索的记录数，请调用[GetRecordCount](../../mfc/reference/cdaotabledef-class.md#getrecordcount)成员函数的`CDaoTableDef`对象。 有关文档`GetRecordCount`介绍更多的记录数。 请注意，检索此计数可以是一个耗时的操作是否表包含多个记录。

## <a name="remarks"></a>备注

Tabledef 是类的对象[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)。 对主要、 次要和上面所有的引用指示如何通过返回的信息[GetTableDefInfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo)类中的成员函数`CDaoDatabase`。

检索的信息[cdaodatabase:: Gettabledefinfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo)成员函数存储在`CDaoTableDefInfo`结构。 调用`GetTableDefInfo`成员函数的`CDaoDatabase`tabledef 对象存储在其 TableDefs 集合对象。 `CDaoTableDefInfo` 此外定义了`Dump`成员函数在调试生成。 可以使用`Dump`转储的内容`CDaoTableDefInfo`对象。

日期和时间设置派生自基础表已创建或上次更新的计算机。 在多用户环境中，用户应该会看到这些设置直接从文件服务器，以避免 DateCreated 差异以及上次更新属性设置。

## <a name="requirements"></a>要求

**标头：** afxdao.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef 类](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoDatabase 类](../../mfc/reference/cdaodatabase-class.md)
