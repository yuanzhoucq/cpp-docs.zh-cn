---
title: "CDaoTableDefInfo 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoTableDefInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoTableDefInfo structure [MFC]
- DAO (Data Access Objects), TableDefs collection
ms.assetid: c01ccebb-5615-434e-883c-4f60eac943dd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e949cb0348cb55fcee5a940b5753a5a8197e600b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cdaotabledefinfo-structure"></a>CDaoTableDefInfo 结构
`CDaoTableDefInfo`结构包含有关 tabledef 对象定义的数据访问对象 (DAO) 的信息。  
  
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
 `m_strName`  
 唯一地命名 tabledef 对象。 若要直接检索此属性的值，调用 tabledef 对象[GetName](../../mfc/reference/cdaotabledef-class.md#getname)成员函数。 有关详细信息，请参阅主题 DAO 帮助中的"名称属性"。  
  
 `m_bUpdatable`  
 指示是否可以对表进行更改。 确定表是否可更新的快速方式是打开`CDaoTableDef`表对象并调用对象的[CanUpdate](../../mfc/reference/cdaotabledef-class.md#canupdate)成员函数。 `CanUpdate`始终返回非零 (**TRUE**) 对于新创建的 tabledef 对象和零 (**FALSE**) 附加的 tabledef 对象。 可以将新 tabledef 对象追加到当前用户对其具有写权限的数据库。 如果表中包含不可更新字段，`CanUpdate`返回 0。 在一个或多个字段都是可更新，`CanUpdate`返回非零值。 你可以编辑仅可更新的字段。 有关详细信息，请参阅主题 DAO 帮助中的"可更新属性"。  
  
 `m_lAttributes`  
 指定由 tabledef 对象表示的表的特性。 若要检索 tabledef 对象的当前属性，调用其[GetAttributes](../../mfc/reference/cdaotabledef-class.md#getattributes)成员函数。 返回的值可以是这些长常量的组合 (使用按位 OR (**&#124;**) 运算符):  
  
- **dbAttachExclusive**对于使用 Microsoft Jet 数据库引擎的数据库，该值指示该表是附加的表打开以供独占使用。  
  
- **dbAttachSavePWD**对于使用 Microsoft Jet 数据库引擎的数据库，指示的用户 ID 和密码附加表保存的连接信息。  
  
- **dbSystemObject**指示该表是提供 Microsoft Jet 数据库引擎的系统表。 （只读。）  
  
- **dbHiddenObject**指示该表是提供 Microsoft Jet 数据库引擎 （供临时使用） 的隐藏的表。 （只读。）  
  
- **dbAttachedTable**指示该表是从非 ODBC 数据库，如 Paradox 数据库附加的表。  
  
- **dbAttachedODBC**指示表是否附加的表从 ODBC 数据库，例如 Microsoft SQL Server。  
  
 `m_dateCreated`  
 日期和时间该表的创建。 若要直接检索表的创建的日期，调用[GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated)成员函数`CDaoTableDef`与该表关联的对象。 有关详细信息，请参阅下面的注释。 有关相关信息，请参阅 DAO 帮助中的主题"时间，上次更新属性"。  
  
 `m_dateLastUpdated`  
 日期和时间的表的设计所做的最新更改。 若要直接检索上次更新表的日期，调用[GetDateLastUpdated](../../mfc/reference/cdaotabledef-class.md#getdatelastupdated)成员函数`CDaoTableDef`与该表关联的对象。 有关详细信息，请参阅下面的注释。 有关相关信息，请参阅 DAO 帮助中的主题"时间，上次更新属性"。  
  
 *m_strSrcTableName*  
 如果有的话，请指定附加表的名称。 若要直接检索源表名称，请调用[GetSourceTableName](../../mfc/reference/cdaotabledef-class.md#getsourcetablename)成员函数`CDaoTableDef`与该表关联的对象。  
  
 `m_strConnect`  
 提供有关打开数据库的源的信息。 你可以通过调用检查此属性[GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect)成员函数你`CDaoTableDef`对象。 有关详细信息连接字符串，请参阅`GetConnect`。  
  
 `m_strValidationRule`  
 一个值，验证 tabledef 字段中的数据，因为它们被更改或添加到表中。 验证仅支持使用 Microsoft Jet 数据库引擎的数据库。 若要直接检索验证规则，请调用[GetValidationRule](../../mfc/reference/cdaotabledef-class.md#getvalidationrule)成员函数`CDaoTableDef`与该表关联的对象。 有关相关信息，请参阅主题 DAO 帮助中的"有效性规则属性"。  
  
 `m_strValidationText`  
 一个值，指定如果不满足由 ValidationRule 属性指定的验证规则，应显示你的应用程序的消息的文本。 有关相关信息，请参阅主题 DAO 帮助中的"有效性文本属性"。  
  
 *m_lRecordCount*  
 访问 tabledef 对象中的记录数。 此属性设置为只读。 若要直接检索的记录计数，调用[GetRecordCount](../../mfc/reference/cdaotabledef-class.md#getrecordcount)成员函数`CDaoTableDef`对象。 文档`GetRecordCount`介绍进一步的记录计数。 请注意，检索此计数可耗时的操作是否表中包含多个记录。  
  
## <a name="remarks"></a>备注  
 Tabledef 是类的对象[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)。 对主、 辅助数据库，以及所有上面的引用指示如何通过返回的信息[GetTableDefInfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo)类中的成员函数`CDaoDatabase`。  
  
 检索的信息[CDaoDatabase::GetTableDefInfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo)成员函数将存储在`CDaoTableDefInfo`结构。 调用`GetTableDefInfo`成员函数`CDaoDatabase`tabledef 对象存储在其 TableDefs 集合中的对象。 `CDaoTableDefInfo`此外定义`Dump`成员函数在调试生成。 你可以使用`Dump`以转储的内容`CDaoTableDefInfo`对象。  
  
 日期和时间设置均源自在其创建或上次更新基表的计算机。 在多用户环境中，用户应该会看到这些设置直接从文件服务器，以避免在时间中的差异以及上次更新属性设置。  
  
## <a name="requirements"></a>惠?  
 **标头：** afxdao.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef 类](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoDatabase 类](../../mfc/reference/cdaodatabase-class.md)
