---
title: "CDaoTableDef 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDaoTableDef
- AFXDAO/CDaoTableDef
- AFXDAO/CDaoTableDef::CDaoTableDef
- AFXDAO/CDaoTableDef::Append
- AFXDAO/CDaoTableDef::CanUpdate
- AFXDAO/CDaoTableDef::Close
- AFXDAO/CDaoTableDef::Create
- AFXDAO/CDaoTableDef::CreateField
- AFXDAO/CDaoTableDef::CreateIndex
- AFXDAO/CDaoTableDef::DeleteField
- AFXDAO/CDaoTableDef::DeleteIndex
- AFXDAO/CDaoTableDef::GetAttributes
- AFXDAO/CDaoTableDef::GetConnect
- AFXDAO/CDaoTableDef::GetDateCreated
- AFXDAO/CDaoTableDef::GetDateLastUpdated
- AFXDAO/CDaoTableDef::GetFieldCount
- AFXDAO/CDaoTableDef::GetFieldInfo
- AFXDAO/CDaoTableDef::GetIndexCount
- AFXDAO/CDaoTableDef::GetIndexInfo
- AFXDAO/CDaoTableDef::GetName
- AFXDAO/CDaoTableDef::GetRecordCount
- AFXDAO/CDaoTableDef::GetSourceTableName
- AFXDAO/CDaoTableDef::GetValidationRule
- AFXDAO/CDaoTableDef::GetValidationText
- AFXDAO/CDaoTableDef::IsOpen
- AFXDAO/CDaoTableDef::Open
- AFXDAO/CDaoTableDef::RefreshLink
- AFXDAO/CDaoTableDef::SetAttributes
- AFXDAO/CDaoTableDef::SetConnect
- AFXDAO/CDaoTableDef::SetName
- AFXDAO/CDaoTableDef::SetSourceTableName
- AFXDAO/CDaoTableDef::SetValidationRule
- AFXDAO/CDaoTableDef::SetValidationText
- AFXDAO/CDaoTableDef::m_pDAOTableDef
- AFXDAO/CDaoTableDef::m_pDatabase
dev_langs: C++
helpviewer_keywords:
- CDaoTableDef [MFC], CDaoTableDef
- CDaoTableDef [MFC], Append
- CDaoTableDef [MFC], CanUpdate
- CDaoTableDef [MFC], Close
- CDaoTableDef [MFC], Create
- CDaoTableDef [MFC], CreateField
- CDaoTableDef [MFC], CreateIndex
- CDaoTableDef [MFC], DeleteField
- CDaoTableDef [MFC], DeleteIndex
- CDaoTableDef [MFC], GetAttributes
- CDaoTableDef [MFC], GetConnect
- CDaoTableDef [MFC], GetDateCreated
- CDaoTableDef [MFC], GetDateLastUpdated
- CDaoTableDef [MFC], GetFieldCount
- CDaoTableDef [MFC], GetFieldInfo
- CDaoTableDef [MFC], GetIndexCount
- CDaoTableDef [MFC], GetIndexInfo
- CDaoTableDef [MFC], GetName
- CDaoTableDef [MFC], GetRecordCount
- CDaoTableDef [MFC], GetSourceTableName
- CDaoTableDef [MFC], GetValidationRule
- CDaoTableDef [MFC], GetValidationText
- CDaoTableDef [MFC], IsOpen
- CDaoTableDef [MFC], Open
- CDaoTableDef [MFC], RefreshLink
- CDaoTableDef [MFC], SetAttributes
- CDaoTableDef [MFC], SetConnect
- CDaoTableDef [MFC], SetName
- CDaoTableDef [MFC], SetSourceTableName
- CDaoTableDef [MFC], SetValidationRule
- CDaoTableDef [MFC], SetValidationText
- CDaoTableDef [MFC], m_pDAOTableDef
- CDaoTableDef [MFC], m_pDatabase
ms.assetid: 7c5d2254-8475-43c4-8a6c-2d32ead194c9
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7b140d61689672f9d27b8078ad7d2eab732c1582
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cdaotabledef-class"></a>CDaoTableDef 类
表示基表或附加表的已存储定义。  
  
## <a name="syntax"></a>语法  
  
```  
class CDaoTableDef : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CDaoTableDef::CDaoTableDef](#cdaotabledef)|构造**CDaoTableDef**对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDaoTableDef::Append](#append)|向数据库添加新表。|  
|[CDaoTableDef::CanUpdate](#canupdate)|返回非零，如果可以更新表 （你可以修改字段或表属性的定义）。|  
|[CDaoTableDef::Close](#close)|关闭打开 tabledef。|  
|[CDaoTableDef::Create](#create)|创建一个表，该表可以添加到数据库使用[追加](#append)。|  
|[CDaoTableDef::CreateField](#createfield)|调用以创建表的字段。|  
|[CDaoTableDef::CreateIndex](#createindex)|调用以为表创建索引。|  
|[CDaoTableDef::DeleteField](#deletefield)|调用以从表中删除字段。|  
|[CDaoTableDef::DeleteIndex](#deleteindex)|调用以从表中删除索引。|  
|[CDaoTableDef::GetAttributes](#getattributes)|返回一个值，该值指示的一个或多个特征`CDaoTableDef`对象。|  
|[CDaoTableDef::GetConnect](#getconnect)|返回一个值，提供有关表的源的信息。|  
|[CDaoTableDef::GetDateCreated](#getdatecreated)|返回的日期和时间基表基础`CDaoTableDef`创建对象。|  
|[CDaoTableDef::GetDateLastUpdated](#getdatelastupdated)|返回的日期和时间的基表的设计所做的最新更改。|  
|[CDaoTableDef::GetFieldCount](#getfieldcount)|返回一个值，表示的表中的字段的数目。|  
|[CDaoTableDef::GetFieldInfo](#getfieldinfo)|返回表中的特定类型的字段的信息。|  
|[CDaoTableDef::GetIndexCount](#getindexcount)|返回表的索引的数。|  
|[CDaoTableDef::GetIndexInfo](#getindexinfo)|返回特定类型的表的索引有关的信息。|  
|[CDaoTableDef::GetName](#getname)|返回用户定义表的名称。|  
|[CDaoTableDef::GetRecordCount](#getrecordcount)|返回表中的记录数。|  
|[CDaoTableDef::GetSourceTableName](#getsourcetablename)|返回一个值，指定在源数据库中的附加表的名称。|  
|[CDaoTableDef::GetValidationRule](#getvalidationrule)|返回一个值，验证字段中的数据，因为它已更改或添加到表中。|  
|[CDaoTableDef::GetValidationText](#getvalidationtext)|返回一个值，指定应用程序显示如果字段对象的值不符合指定的验证规则的消息的文本。|  
|[CDaoTableDef::IsOpen](#isopen)|返回非零，如果表是打开。|  
|[CDaoTableDef::Open](#open)|打开存储在数据库中现有 tabledef 的 TableDef 的集合。|  
|[CDaoTableDef::RefreshLink](#refreshlink)|更新附加表的连接信息。|  
|[CDaoTableDef::SetAttributes](#setattributes)|设置一个值，该值指示的一个或多个特征`CDaoTableDef`对象。|  
|[CDaoTableDef::SetConnect](#setconnect)|设置一个值，提供有关表的源的信息。|  
|[CDaoTableDef::SetName](#setname)|设置表的名称。|  
|[CDaoTableDef::SetSourceTableName](#setsourcetablename)|设置一个值，指定在源数据库中的附加表的名称。|  
|[CDaoTableDef::SetValidationRule](#setvalidationrule)|设置一个值，验证字段中的数据，因为它已更改或添加到表中。|  
|[CDaoTableDef::SetValidationText](#setvalidationtext)|设置一个值，指定应用程序显示如果字段对象的值不符合指定的验证规则的消息的文本。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CDaoTableDef::m_pDAOTableDef](#m_pdaotabledef)|指向基础 tabledef 对象的 DAO 接口的指针。|  
|[CDaoTableDef::m_pDatabase](#m_pdatabase)|此表的源数据库。|  
  
## <a name="remarks"></a>备注  
 每个 DAO 数据库对象维护一个名为 TableDefs，包含所有已保存的 DAO tabledef 对象的集合。  
  
 操作表定义使用`CDaoTableDef`对象。 例如，你可以：  
  
-   检查任何本地、 附加，或外部数据库表中的字段和索引结构。  
  
-   调用`SetConnect`和`SetSourceTableName`附加的表和使用的成员函数`RefreshLink`成员函数以更新连接到附加表。  
  
-   调用`CanUpdate`成员函数来确定是否可以编辑表中的字段定义。  
  
-   获取或设置使用的验证条件`GetValidationRule`和`SetValidationRule`，和`GetValidationText`和`SetValidationText`成员函数。  
  
-   使用**打开**成员函数来创建表的、 动态集或快照类型`CDaoRecordset`对象。  
  
    > [!NOTE]
    >  DAO 数据库类有别于基于开放式数据库连接 (ODBC) 的 MFC 数据库类。 DAO 数据库类的所有名称都具有"CDao"前缀。 你仍可以访问 ODBC 数据源对于 DAO 类;DAO 类通常提供高级功能，因为它们是特定于 Microsoft Jet 数据库引擎。  
  
### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>若要使用 tabledef 对象要使用现有表，或创建新表  
  
1.  在所有情况下，首先构造`CDaoTableDef`对象，提供一个指向[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)表所属的对象。  
  
2.  然后执行以下操作，具体取决于希望：  
  
    -   若要使用现有的已保存表，调用 tabledef 对象[打开](#open)成员函数，提供已保存的表的名称。  
  
    -   若要创建新表，请调用 tabledef 对象[创建](#create)成员函数，提供的表的名称。 调用[CreateField](#createfield)和[CreateIndex](#createindex)若要向表中添加字段和索引。  
  
    -   调用[追加](#append)表的保存通过将其追加到数据库的 TableDefs 集合。 **创建**将 tabledef 放入打开状态，因此在调用**创建**不调用**打开**。  
  
        > [!TIP]
        >  创建已保存的表的最简单方法是创建它们，并将其存储在使用 Microsoft Access 数据库。 然后可以打开，并在 MFC 代码中使用它们。  
  
 若要使用 tabledef 对象已打开或创建，创建并打开`CDaoRecordset`对象，指定的名称与 tabledef **dbOpenTable**中的值`nOpenType`参数。  
  
 要使用 tabledef 对象创建`CDaoRecordset`对象，通常创建或打开 tabledef，如上所述，然后构造记录集对象，将指针传递给 tabledef 对象中，当您调用[cdaorecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open)。 你传递 tabledef 必须处于打开状态。 有关详细信息，请参阅类[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  
  
 当你完成使用 tabledef 对象时，调用其[关闭](../../mfc/reference/cdaorecordset-class.md#close)成员函数; 然后销毁 tabledef 对象。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoTableDef`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxdao.h  
  
##  <a name="append"></a>CDaoTableDef::Append  
 调用此成员函数调用之后[创建](#create)创建新的 tabledef 对象来将 tabledef 保存在数据库。  
  
```  
virtual void Append();
```  
  
### <a name="remarks"></a>备注  
 该函数将对象追加到数据库的 TableDefs 集合。 你可以使用 tabledef 作为临时对象同时定义通过不追加，但如果你想要保存并使用它，则必须调用**追加**。  
  
> [!NOTE]
>  如果你尝试附加未命名的 tabledef （包含 null 或空字符串），则 MFC 会引发异常。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"追加方法"。  
  
##  <a name="canupdate"></a>CDaoTableDef::CanUpdate  
 调用此成员函数可确定是否对表基础定义`CDaoTableDef`可以更改对象。  
  
```  
BOOL CanUpdate();
```  
  
### <a name="return-value"></a>返回值  
 如果可以修改表结构 （架构） 则为非 0 （添加或删除字段和索引），否则为 0。  
  
### <a name="remarks"></a>备注  
 默认情况下，新创建的表基础`CDaoTableDef`可以更新对象，并附加的表基础`CDaoTableDef`不能更新对象。 A`CDaoTableDef`对象可能是可更新，即使得到的结果集不可更新。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"可更新属性"。  
  
##  <a name="cdaotabledef"></a>CDaoTableDef::CDaoTableDef  
 构造**CDaoTableDef**对象。  
  
```  
CDaoTableDef(CDaoDatabase* pDatabase);
```  
  
### <a name="parameters"></a>参数  
 `pDatabase`  
 指向的指针[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象。  
  
### <a name="remarks"></a>备注  
 在构造对象之后, 必须调用[创建](#create)或[打开](#open)成员函数。 当你完成与对象时，必须调用其[关闭](#close)成员函数，并且销毁`CDaoTableDef`对象。  
  
##  <a name="close"></a>CDaoTableDef::Close  
 调用此成员函数来关闭并释放 tabledef 对象。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>备注  
 通常在调用之后**关闭**，如果它已分配了与删除 tabledef 对象**新**。  
  
 你可以调用[打开](#open)在调用后再次**关闭**。 这样可以重用 tabledef 对象。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"Close 方法"。  
  
##  <a name="create"></a>CDaoTableDef::Create  
 调用此成员函数来创建新的已保存的表。  
  
```  
virtual void Create(
    LPCTSTR lpszName,  
    long lAttributes = 0,  
    LPCTSTR lpszSrcTable = NULL,  
    LPCTSTR lpszConnect = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 指向包含表的名称的字符串的指针。  
  
 `lAttributes`  
 相对应的 tabledef 对象所表示的表的特征的值。 可以使用按位 OR 组合任何以下常量：  
  
|返回的常量|描述|  
|--------------|-----------------|  
|**dbAttachExclusive**|对于使用 Microsoft Jet 数据库引擎的数据库，指示该表是附加的表打开以供独占使用。|  
|**dbAttachSavePWD**|对于使用 Microsoft Jet 数据库引擎的数据库，指示的用户 ID 和密码附加表保存的连接信息。|  
|**dbSystemObject**|指示表提供 Microsoft Jet 数据库引擎的系统表。|  
|**dbHiddenObject**|指示表提供 Microsoft Jet 数据库引擎的隐藏的表。|  
  
 *lpszSrcTable*  
 指向包含源表名称的字符串的指针。 默认情况下，此值初始化为**NULL**。  
  
 `lpszConnect`  
 指向包含的默认连接字符串的字符串的指针。 默认情况下，此值初始化为**NULL**。  
  
### <a name="remarks"></a>备注  
 一旦具有名为 tabledef，然后，你可以调用[追加](#append)tabledef 保存数据库的 TableDefs 集合中。 在调用**追加**，tabledef 处于打开状态，并可以使用它来创建[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"CreateTableDef 方法"。  
  
##  <a name="createfield"></a>CDaoTableDef::CreateField  
 调用此成员函数可将字段添加到表。  
  
```  
void CreateField(
    LPCTSTR lpszName,  
    short nType,  
    long lSize,  
    long lAttributes = 0);  
  
void CreateField(CDaoFieldInfo& fieldinfo);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 指定此字段的名称的字符串表达式指向的指针。  
  
 `nType`  
 指示该字段的数据类型的值。 该设置可以是下列值之一：  
  
|类型|大小（字节）|描述|  
|----------|--------------------|-----------------|  
|**dbBoolean**|1 个字节|BOOL|  
|**dbByte**|1|BYTE|  
|**dbInteger**|2|int|  
|**dbLong**|4|long|  
|**dbCurrency**|8|货币 ( [COleCurrency](../../mfc/reference/colecurrency-class.md))|  
|**dbSingle**|4|float|  
|**dbDouble**|8|double|  
|**dbDate**|8|日期/时间 ( [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|  
|**dbText**|1 - 255|文本 ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|  
|**dbLongBinary**|0|长二进制文件 （OLE 对象）， [CLongBinary](../../mfc/reference/clongbinary-class.md)或[CByteArray](../../mfc/reference/cbytearray-class.md)|  
|**dbMemo**|0|备注 ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|  
  
 `lSize`  
 一个值，指示的最大大小，以字节为单位的字段的包含文本或包含文本或数字值的字段的固定的大小。 `lSize`对于除所有文本字段都忽略参数。  
  
 `lAttributes`  
 可以使用按位 OR 组合的字段，特征相对应的值。  
  
|返回的常量|描述|  
|--------------|-----------------|  
|**dbFixedField**|字段大小被固定的 （数字字段的默认值）。|  
|**dbVariableField**|字段大小是变量 （仅适用于文本字段）。|  
|**dbAutoIncrField**|新记录的字段值自动递增至一个唯一的长整数，它不能更改。 仅支持 Microsoft Jet 数据库表。|  
|**dbUpdatableField**|可以更改的字段值。|  
|**dbDescending**|对字段进行排序以降序 (Z-A 或 100-0) （仅适用于索引对象的字段集合中的字段对象） 的顺序。 如果省略此常量时，对字段进行排序以升序 (A-Z 或 0-100) 顺序 （默认值）。|  
  
 `fieldinfo`  
 对引用[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构。  
  
### <a name="remarks"></a>备注  
 A **DAOField**创建 (OLE) 对象并将其追加到的字段集合**DAOTableDef** (OLE) 对象。 除了其用于检查对象属性，还可以使用`CDaoFieldInfo`构造在 tabledef 中创建新字段的输入的参数。 第一个版本`CreateField`会更易于使用，但如果你想更精细的控制，你可以使用第二个版本`CreateField`，此方法采用`CDaoFieldInfo`参数。  
  
 如果你使用的版本`CreateField`采用`CDaoFieldInfo`参数，你必须仔细设置每个的以下成员`CDaoFieldInfo`结构：  
  
- **m_strName**  
  
- `m_nType`  
  
- **m_lSize**  
  
- **m_lAttributes**  
  
- **m_bAllowZeroLength**  
  
 其他成员`CDaoFieldInfo`应设置为**0**， **FALSE**，或空字符串，根据该成员，或`CDaoException`可能会出现。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"CreateField 方法"。  
  
##  <a name="createindex"></a>CDaoTableDef::CreateIndex  
 调用此函数可将索引添加到表。  
  
```  
void CreateIndex(CDaoIndexInfo& indexinfo);
```  
  
### <a name="parameters"></a>参数  
 `indexinfo`  
 对引用[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)结构。  
  
### <a name="remarks"></a>备注  
 索引指定访问从数据库表和接受重复的记录的记录的顺序。 索引还提供高效的数据访问。  
  
 无需创建索引对于表，但未建立索引的大型表，在访问特定记录或创建记录集可能需要长时间。 另一方面，创建过多索引降低更新、 追加、 和删除操作，因为所有索引将自动都更新。 当你决定创建哪些索引，请考虑这些因素。  
  
 以下成员`CDaoIndexInfo`必须设置结构：  
  
- **m_strName**必须提供名称。  
  
- `m_pFieldInfos`必须指向数组的`CDaoIndexFieldInfo`结构。  
  
- `m_nFields`必须指定的数组中的字段的数目`CDaoFieldInfo`结构。  
  
 剩余成员将被忽略的如果设置为**FALSE**。 此外， **m_lDistinctCount**成员时将忽略在创建索引。  
  
##  <a name="deletefield"></a>CDaoTableDef::DeleteField  
 调用此成员函数删除字段，并使其无法访问。  
  
```  
void DeleteField(LPCTSTR lpszName);  
void DeleteField(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 指向是现有字段的名称的字符串表达式的指针。  
  
 `nIndex`  
 表的从零开始的字段集合，按索引查找中的字段的索引。  
  
### <a name="remarks"></a>备注  
 你可以在具有不到数据库会追加一个新对象上使用此成员函数时，或者当[CanUpdate](#canupdate)返回非零值。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"删除方法"。  
  
##  <a name="deleteindex"></a>CDaoTableDef::DeleteIndex  
 调用此成员函数删除基础表中的索引。  
  
```  
void DeleteIndex(LPCTSTR lpszName);  
void DeleteIndex(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 指向现有索引的名称的字符串表达式的指针。  
  
 `nIndex`  
 数据库的从零开始 TableDefs 集合中，按索引查找索引对象的数组索引。  
  
### <a name="remarks"></a>备注  
 你可以在尚未已追加到数据库的新对象上使用此成员函数时，或者当[CanUpdate](#canupdate)返回非零值。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"删除方法"。  
  
##  <a name="getattributes"></a>CDaoTableDef::GetAttributes  
 有关`CDaoTableDef`对象，返回的值指定所代表的表格的特征`CDaoTableDef`对象，并可以是这些常量的总和：  
  
```  
long GetAttributes();
```  
  
### <a name="return-value"></a>返回值  
 返回一个值，该值指示的一个或多个特征`CDaoTableDef`对象。  
  
### <a name="remarks"></a>备注  
  
|返回的常量|描述|  
|--------------|-----------------|  
|**dbAttachExclusive**|对于使用 Microsoft Jet 数据库引擎的数据库，指示该表是附加的表打开以供独占使用。|  
|**dbAttachSavePWD**|对于使用 Microsoft Jet 数据库引擎的数据库，指示的用户 ID 和密码附加表保存的连接信息。|  
|**dbSystemObject**|指示表提供 Microsoft Jet 数据库引擎的系统表。|  
|**dbHiddenObject**|指示表提供 Microsoft Jet 数据库引擎的隐藏的表。|  
|**dbAttachedTable**|指示表从非 ODBC 数据库，如 Paradox 数据库附加的表。|  
|**dbAttachedODBC**|指示表附加的表从 ODBC 数据库，例如 Microsoft SQL Server。|  
  
 系统表是要包含各种内部信息的 Microsoft Jet 数据库引擎所创建的表。  
  
 隐藏的表是由 Microsoft Jet 数据库引擎创建供临时使用的表。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"特性属性"。  
  
##  <a name="getconnect"></a>CDaoTableDef::GetConnect  
 调用此成员函数来获取数据源的连接字符串。  
  
```  
CString GetConnect();
```  
  
### <a name="return-value"></a>返回值  
 A`CString`对象，其中包含表的路径和数据库类型。  
  
### <a name="remarks"></a>备注  
 有关`CDaoTableDef`对象，表示附加的表，`CString`对象 （数据库类型说明符和数据库的路径） 的一个或两个部分组成。  
  
 下表中所示的路径是包含数据库文件的目录的完整路径，并且必须在前面的标识符"数据库 ="。 在 （按与 Microsoft Jet 和 Microsoft Excel 一起数据库） 某些情况下，特定文件名包含在数据库路径参数。  
  
 中的表[CDaoTableDef::SetConnect](#setconnect)显示可能的数据库类型及其相应的数据库说明符和路径：  
  
 对于 Microsoft Jet 数据库基表，说明符是一个空字符串 ("")。  
  
 如果需要密码，但是未提供，ODBC 驱动程序将显示登录对话框第一次访问表时，会再次如果关闭并重新打开连接。 如果附加的表具有**dbAttachSavePWD**属性中，登录提示时不会显示表重新打开。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"连接属性"。  
  
##  <a name="getdatecreated"></a>CDaoTableDef::GetDateCreated  
 调用此函数可确定日期和时间表基础`CDaoTableDef`创建对象。  
  
```  
COleDateTime GetDateCreated();
```  
  
### <a name="return-value"></a>返回值  
 一个值，包含的日期和时间的表基础创建`CDaoTableDef`对象。  
  
### <a name="remarks"></a>备注  
 日期和时间设置均源自在其创建或上次更新基表的计算机。 在多用户环境中，用户应直接从文件服务器，为了避免出现差异; 获取这些设置也就是说，所有客户端应使用"标准"的时间源-可能是从一台服务器。  
  
 有关相关信息，请参阅 DAO 帮助中的主题"时间，上次更新属性"。  
  
##  <a name="getdatelastupdated"></a>CDaoTableDef::GetDateLastUpdated  
 调用此函数可确定日期和时间表基础**CDaoTableDef**上次更新对象。  
  
```  
COleDateTime GetDateLastUpdated();
```  
  
### <a name="return-value"></a>返回值  
 一个值，包含的日期和时间表基础**CDaoTableDef**上次更新对象。  
  
### <a name="remarks"></a>备注  
 日期和时间设置均源自在其创建或上次更新基表的计算机。 在多用户环境中，用户应直接从文件服务器，为了避免出现差异; 获取这些设置也就是说，所有客户端应使用"标准"的时间源-可能是从一台服务器。  
  
 有关相关信息，请参阅 DAO 帮助中的主题"时间，上次更新属性"。  
  
##  <a name="getfieldcount"></a>CDaoTableDef::GetFieldCount  
 调用此成员函数可检索的表中定义的字段的数目。  
  
```  
short GetFieldCount();
```  
  
### <a name="return-value"></a>返回值  
 表中的字段数。  
  
### <a name="remarks"></a>备注  
 如果其值为 0，但没有对象存储在集合上。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"计数属性"。  
  
##  <a name="getfieldinfo"></a>CDaoTableDef::GetFieldInfo  
 调用此成员函数来获取各种类型的有关 tabledef 中定义的某个字段的信息。  
  
```  
void GetFieldInfo(
    int nIndex,  
    CDaoFieldInfo& fieldinfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

 
void GetFieldInfo(
    LPCTSTR lpszName,  
    CDaoFieldInfo& fieldinfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 表的从零开始的字段集合，按索引查找中的字段对象的索引。  
  
 `fieldinfo`  
 对引用[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构。  
  
 `dwInfoOptions`  
 指定有关要检索的字段的信息的选项。 以及它们会导致要返回的函数，下面列出了可用的选项：  
  
- `AFX_DAO_PRIMARY_INFO`（默认值）名称、 类型、 大小，属性。 使用此选项以最快的性能。  
  
- `AFX_DAO_SECONDARY_INFO`主要的信息，加上： 序号位置，需要，允许零长度，排序规则顺序外的名称，源字段，源表  
  
- `AFX_DAO_ALL_INFO`主要和辅助信息，加上： 验证规则，验证文本，默认值  
  
 `lpszName`  
 指向对象的名称字段，按名称查找的指针。 名称是唯一的名称字段带有最多 64 个字符的字符串。  
  
### <a name="remarks"></a>备注  
 一个版本的函数，可按索引查找字段。 另一个版本中，可以按名称查找字段。  
  
 返回的信息的说明，请参阅[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构。 此结构具有对应于上面列出的说明中的信息的项的成员`dwInfoOptions`。 当请求在一个级别的信息时，可以为任何以前的级别的信息。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"特性属性"。  
  
##  <a name="getindexcount"></a>CDaoTableDef::GetIndexCount  
 调用此成员函数可获取的表的索引数。  
  
```  
short GetIndexCount();
```  
  
### <a name="return-value"></a>返回值  
 为表的索引数。  
  
### <a name="remarks"></a>备注  
 如果其值为 0，在没有其他索引集合中。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"计数属性"。  
  
##  <a name="getindexinfo"></a>CDaoTableDef::GetIndexInfo  
 调用此成员函数来获取各种类型的有关索引 tabledef 中定义的信息。  
  
```  
void GetIndexInfo(
    int nIndex,  
    CDaoIndexInfo& indexinfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

 
void GetIndexInfo(
    LPCTSTR lpszName,  
    CDaoIndexInfo& indexinfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 表的从零开始的索引集合中，通过在集合中的位置查找该索引对象的数字索引。  
  
 `indexinfo`  
 对引用[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)结构。  
  
 `dwInfoOptions`  
 指定要检索的索引有关的信息的选项。 以及它们会导致要返回的函数，下面列出了可用的选项：  
  
- `AFX_DAO_PRIMARY_INFO`名称，字段信息字段。 使用此选项以最快的性能。  
  
- `AFX_DAO_SECONDARY_INFO`主要的信息，加上： 主、 唯一、 聚集、 忽略 null 值，所需，外部  
  
- `AFX_DAO_ALL_INFO`主要和辅助信息，加上： 非重复计数  
  
 `lpszName`  
 指向按名称查找的名称的索引对象的指针。  
  
### <a name="remarks"></a>备注  
 一个版本的函数可以查找集合中其位置的索引。 另一个版本中，可以按名称查找索引。  
  
 返回的信息的说明，请参阅[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)结构。 此结构具有对应于上面列出的说明中的信息的项的成员`dwInfoOptions`。 当请求在一个级别的信息时，可以为任何以前的级别的信息。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"特性属性"。  
  
##  <a name="getname"></a>CDaoTableDef::GetName  
 调用此成员函数以获取基础表的用户定义名称。  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>返回值  
 表的用户定义名称。  
  
### <a name="remarks"></a>备注  
 此名称以字母开头，并且可以包含最多 64 个字符。 它可以包含数字和下划线字符，但不能包含标点或空格。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"名称属性"。  
  
##  <a name="getrecordcount"></a>CDaoTableDef::GetRecordCount  
 调用此成员函数，以找出多少条记录位于`CDaoTableDef`对象。  
  
```  
long GetRecordCount();
```  
  
### <a name="return-value"></a>返回值  
 访问 tabledef 对象中的记录数。  
  
### <a name="remarks"></a>备注  
 调用`GetRecordCount`的表类型`CDaoTableDef`对象反映在表中的记录的大致数目，添加和删除表记录时立即影响。 回滚事务将显示为记录计数的一部分，直到你调用[CDaoWorkSpace::CompactDatabase](../../mfc/reference/cdaoworkspace-class.md#compactdatabase)。 A`CDaoTableDef`不包含记录的对象具有的记录计数属性设置为 0。 使用附加的表或 ODBC 数据库时`GetRecordCount`始终返回-1。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"RecordCount 属性"。  
  
##  <a name="getsourcetablename"></a>CDaoTableDef::GetSourceTableName  
 调用此成员函数可检索附加源数据库中表的名称。  
  
```  
CString GetSourceTableName();
```  
  
### <a name="return-value"></a>返回值  
 A`CString`对象，它指定一个附加的表或空字符串的源名称，如果本机数据的表。  
  
### <a name="remarks"></a>备注  
 附加的表是链接到 Microsoft Jet 数据库的另一个数据库中的表。 附加表的数据保留在外部数据库，其中它可操作的其他应用程序。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"SourceTableName 属性"。  
  
##  <a name="getvalidationrule"></a>CDaoTableDef::GetValidationRule  
 调用此成员函数可检索 tabledef 的验证规则。  
  
```  
CString GetValidationRule();
```  
  
### <a name="return-value"></a>返回值  
 A **CString**验证字段中的数据，因为它已更改或添加到表中的对象。  
  
### <a name="remarks"></a>备注  
 与更新操作结合使用验证规则。 如果 tabledef 包含验证规则，则更新该 tabledef 必须匹配预先确定的条件之前在数据更改。 如果更改不匹配条件，包含的值的异常[GetValidationText](#getvalidationtext)引发。 有关`CDaoTableDef`对象，这`CString`是只读的附加的表和读/写对于基表。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"有效性规则属性"。  
  
##  <a name="getvalidationtext"></a>CDaoTableDef::GetValidationText  
 调用此函数可检索要显示当用户输入与验证规则不匹配的数据的字符串。  
  
```  
CString GetValidationText();
```  
  
### <a name="return-value"></a>返回值  
 A`CString`对象，它指定在用户输入与验证规则不匹配的数据时显示的文本。  
  
### <a name="remarks"></a>备注  
 有关`CDaoTableDef`对象，这`CString`是只读的附加的表和读/写对于基表。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"有效性文本属性"。  
  
##  <a name="isopen"></a>CDaoTableDef::IsOpen  
 调用此成员函数可确定是否`CDaoTableDef`对象当前处于打开状态。  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零如果`CDaoTableDef`对象是打开; 否则为 0。  
  
### <a name="remarks"></a>备注  
  
##  <a name="m_pdatabase"></a>CDaoTableDef::m_pDatabase  
 包含指向的[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)此表的对象。  
  
### <a name="remarks"></a>备注  
  
##  <a name="m_pdaotabledef"></a>CDaoTableDef::m_pDAOTableDef  
 包含指向 DAO tabledef 对象基础的 OLE 接口的`CDaoTableDef`对象。  
  
### <a name="remarks"></a>备注  
 如果你需要直接访问 DAO 接口，请使用此指针。  
  
##  <a name="open"></a>CDaoTableDef::Open  
 调用此成员函数以打开 tabledef 以前保存到数据库中的 TableDef 的集合。  
  
```  
virtual void Open(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 指向一个字符串，指定表名的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="refreshlink"></a>CDaoTableDef::RefreshLink  
 调用此成员函数以更新附加表的连接信息。  
  
```  
void RefreshLink();
```  
  
### <a name="remarks"></a>备注  
 通过调用更改附加表的连接信息[为表示](#setconnect)到相应`CDaoTableDef`对象，然后使用`RefreshLink`成员函数以更新的信息。 当调用`RefreshLink`，附加的表的属性将不会更改。  
  
 若要强制已修改连接信息才会生效，所有打开[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)必须关闭基于此 tabledef 对象。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"RefreshLink 方法"。  
  
##  <a name="setattributes"></a>CDaoTableDef::SetAttributes  
 设置一个值，该值指示的一个或多个特征`CDaoTableDef`对象。  
  
```  
void SetAttributes(long lAttributes);
```  
  
### <a name="parameters"></a>参数  
 `lAttributes`  
 所代表的表格的特征`CDaoTableDef`对象，并可以是这些常量的总和：  
  
|返回的常量|描述|  
|--------------|-----------------|  
|**dbAttachExclusive**|对于使用 Microsoft Jet 数据库引擎的数据库，指示该表是附加的表打开以供独占使用。|  
|**dbAttachSavePWD**|对于使用 Microsoft Jet 数据库引擎的数据库，指示的用户 ID 和密码附加表保存的连接信息。|  
|**dbSystemObject**|指示表提供 Microsoft Jet 数据库引擎的系统表。|  
|**dbHiddenObject**|指示表提供 Microsoft Jet 数据库引擎的隐藏的表。|  
  
### <a name="remarks"></a>备注  
 设置多个属性，就可以将其合并通过对使用按位 OR 运算符相应常量求和。 设置**dbAttachExclusive**在附加的表会生成异常。 结合以下值还生成一个异常：  
  
- **dbAttachExclusive &#124;dbAttachedODBC**  
  
- **dbAttachSavePWD &#124;dbAttachedTable**  
  
 有关相关信息，请参阅主题 DAO 帮助中的"特性属性"。  
  
##  <a name="setconnect"></a>CDaoTableDef::SetConnect  
 有关`CDaoTableDef`对象，表示附加的表，字符串对象 （数据库类型说明符和数据库的路径） 的一个或两个部分组成。  
  
```  
void SetConnect(LPCTSTR lpszConnect);
```  
  
### <a name="parameters"></a>参数  
 `lpszConnect`  
 指向一个字符串表达式，指定要传递到 ODBC 或可安装 ISAM 驱动程序的其他参数的指针。  
  
### <a name="remarks"></a>备注  
 下表中所示的路径是包含数据库文件的目录的完整路径，并且必须在前面的标识符"数据库 ="。 在 （按与 Microsoft Jet 和 Microsoft Excel 一起数据库） 某些情况下，特定文件名包含在数据库路径参数。  
  
> [!NOTE]
>  不要在路径的窗体的语句中包括等号两侧的空格"数据库 = 驱动器：\\\path"。 这将导致引发异常和连接失败。  
  
 下表显示可能的数据库类型及其相应的数据库说明符和路径：  
  
|数据库类型|说明符|路径|  
|-------------------|---------------|----------|  
|使用 Jet 数据库引擎的数据库|"[ `database`];"|" `drive`:\\\ *路径*\\\ *filename*。MDB"|  
|dBASE III|"dBASE III;"|" `drive`:\\\ *路径*"|  
|dBASE IV|"dBASE IV;"|" `drive`:\\\ *路径*"|  
|dBASE 5|"dBASE 5.0;"|" `drive`:\\\ *路径*"|  
|Paradox 3.x|"Paradox 3.x;"|" `drive`:\\\ *路径*"|  
|Paradox 4.x|"Paradox 4.x;"|" `drive`:\\\ *路径*"|  
|Paradox 5.x|"Paradox 5.x;"|" `drive`:\\\ *路径*"|  
|Excel 3.0|"Excel 3.0;"|" `drive`:\\\ *路径*\\\ *filename*。XLS"|  
|Excel 4.0|"Excel 4.0;"|" `drive`:\\\ *路径*\\\ *filename*。XLS"|  
|Excel 5.0 或 Excel 95|"Excel 5.0;"|" `drive`:\\\ *路径*\\\ *filename*。XLS"|  
|Excel 97|"Excel 8.0;"|" `drive`:\\\ *路径*\ *filename*。XLS"|  
|HTML 导入|"HTML 导入;"|" `drive`:\\\ *路径*\ *filename*"|  
|HTML 导出|"HTML 导出;"|" `drive`:\\\ *路径*"|  
|Text|"文本;"|"驱动器：\\\path"|  
|ODBC|"ODBC;数据库 = `database`;UID =*用户*;PWD =*密码*;DSN = *datasourcename;*LOGINTIMEOUT =*秒;*"（这可能不是所有服务器的完整连接字符串; 它只是一个示例。 它是非常重要，不能使用参数之间的空间。）|无|  
|Exchange|"Exchange;<br /><br /> MAPILEVEL = *folderpath*;<br /><br /> [TABLETYPE = {0 &#124; 1};]<br /><br /> [配置文件 =*配置文件*;]<br /><br /> [PWD =*密码*;]<br /><br /> [数据库 = `database`;]"|*"驱动器*:\\\ *路径*\\\ *filename*。MDB"|  
  
> [!NOTE]
>  Btrieve 截至 DAO 3.5 不再受支持。  
  
 你必须使用双反斜杠 (\\\\) 的连接字符串中。 如果修改了现有的连接使用的属性`SetConnect`，随后必须调用[RefreshLink](#refreshlink)。 如果要初始化连接属性使用`SetConnect`，您需要不调用`RefreshLink`，但你应选择这样做，首先追加 tabledef。  
  
 如果需要密码，但是未提供，ODBC 驱动程序将显示登录对话框第一次访问表时，会再次如果关闭并重新打开连接。  
  
 你可以设置的连接字符串`CDaoTableDef`对象提供的源参数**创建**成员函数。 你可以检查该设置将确定类型、 路径、 用户 ID、 密码或 ODBC 数据源的数据库。 有关详细信息，请参阅特定驱动程序的文档。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"连接属性"。  
  
##  <a name="setname"></a>CDaoTableDef::SetName  
 调用此成员函数以设置表的用户定义名称。  
  
```  
void SetName(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 指向一个字符串表达式，指定表的名称的指针。  
  
### <a name="remarks"></a>备注  
 名称必须以字母开头，并且可以包含最多 64 个字符。 它可以包含数字和下划线字符，但不能包含标点或空格。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"名称属性"。  
  
##  <a name="setsourcetablename"></a>CDaoTableDef::SetSourceTableName  
 调用此成员函数以指定附加表的名称或基本表的名称在其上`CDaoTableDef`基于对象，如同它存在于原始源中的数据。  
  
```  
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```  
  
### <a name="parameters"></a>参数  
 *lpszSrcTableName*  
 指向外部数据库中的指定表名称的字符串表达式的指针。 对于基表，设置是一个空字符串 ("")。  
  
### <a name="remarks"></a>备注  
 然后，你必须调用[RefreshLink](#refreshlink)。 此属性设置为空基表和读/写附加的表或未追加到集合的对象。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"SourceTableName 属性"。  
  
##  <a name="setvalidationrule"></a>CDaoTableDef::SetValidationRule  
 调用此成员函数可设置 tabledef 的验证规则。  
  
```  
void SetValidationRule(LPCTSTR lpszValidationRule);
```  
  
### <a name="parameters"></a>参数  
 *lpszValidationRule*  
 指向一个字符串表达式，验证操作的指针。  
  
### <a name="remarks"></a>备注  
 与更新操作结合使用验证规则。 如果 tabledef 包含验证规则，则更新该 tabledef 必须匹配预先确定的条件之前在数据更改。 如果更改不匹配条件，包含文本的异常[GetValidationText](#getvalidationtext)显示。  
  
 验证仅支持使用 Microsoft Jet 数据库引擎的数据库。 表达式不能引用用户定义函数、 域的聚合函数、 SQL 聚合函数或查询。 验证规则`CDaoTableDef`对象可以引用该对象中的多个字段。  
  
 例如，对于名为的字段`hire_date`和`termination_date`，验证规则可能是：  
  
 [!code-cpp[NVC_MFCDatabase#34](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]  
  
 有关相关信息，请参阅主题 DAO 帮助中的"有效性规则属性"。  
  
##  <a name="setvalidationtext"></a>CDaoTableDef::SetValidationText  
 调用此成员函数可设置的验证规则的异常文本`CDaoTableDef`与基础基表 Microsoft Jet 数据库引擎支持的对象。  
  
```  
void SetValidationText(LPCTSTR lpszValidationText);
```  
  
### <a name="parameters"></a>参数  
 *lpszValidationText*  
 指向一个字符串表达式，指定如果输入的数据显示的文本的指针是无效的。  
  
### <a name="remarks"></a>备注  
 不能设置附加表的验证文本。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"有效性文本属性"。  
  
## <a name="see-also"></a>请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDaoDatabase 类](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoRecordset 类](../../mfc/reference/cdaorecordset-class.md)
