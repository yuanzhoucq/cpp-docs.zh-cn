---
title: "CDaoTableDef 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
dev_langs:
- C++
helpviewer_keywords:
- database classes [C++], DAO
- tabledefs [C++]
- CDaoTableDef class
- database tables [C++], attached table definition
- database tables [C++], base table definition
ms.assetid: 7c5d2254-8475-43c4-8a6c-2d32ead194c9
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 8bfd0ef3c63c243cabb0a4f841ba278fbeed4ae8
ms.lasthandoff: 02/24/2017

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
  
|名称|说明|  
|----------|-----------------|  
|[CDaoTableDef::Append](#append)|向数据库添加新表。|  
|[CDaoTableDef::CanUpdate](#canupdate)|返回非零，如果可以更新表 （您可以修改字段或表属性的定义）。|  
|[CDaoTableDef::Close](#close)|关闭打开 tabledef。|  
|[CDaoTableDef::Create](#create)|创建一个表，该表可以添加到数据库使用[追加](#append)。|  
|[CDaoTableDef::CreateField](#createfield)|调用以创建一个表的字段。|  
|[CDaoTableDef::CreateIndex](#createindex)|调用以创建表的索引。|  
|[CDaoTableDef::DeleteField](#deletefield)|调用以从表中删除字段。|  
|[CDaoTableDef::DeleteIndex](#deleteindex)|调用以从表中删除索引。|  
|[CDaoTableDef::GetAttributes](#getattributes)|返回一个值，该值指示的一个或多个特征`CDaoTableDef`对象。|  
|[CDaoTableDef::GetConnect](#getconnect)|返回一个值，提供有关表的源的信息。|  
|[CDaoTableDef::GetDateCreated](#getdatecreated)|返回的日期和时间基表基础`CDaoTableDef`创建对象。|  
|[CDaoTableDef::GetDateLastUpdated](#getdatelastupdated)|返回的日期和时间对基础表的设计所做的最新更改。|  
|[CDaoTableDef::GetFieldCount](#getfieldcount)|返回一个值，表示表中的字段数。|  
|[CDaoTableDef::GetFieldInfo](#getfieldinfo)|返回表中的特定类型的字段的信息。|  
|[CDaoTableDef::GetIndexCount](#getindexcount)|返回表的索引的数目。|  
|[CDaoTableDef::GetIndexInfo](#getindexinfo)|返回特定类型的表的索引有关的信息。|  
|[CDaoTableDef::GetName](#getname)|返回用户定义表的名称。|  
|[CDaoTableDef::GetRecordCount](#getrecordcount)|返回表中的记录数。|  
|[CDaoTableDef::GetSourceTableName](#getsourcetablename)|返回一个值，指定源数据库中的附加表的名称。|  
|[CDaoTableDef::GetValidationRule](#getvalidationrule)|返回一个值，因为它已更改或添加到表验证字段中的数据。|  
|[CDaoTableDef::GetValidationText](#getvalidationtext)|返回一个值，指定您的应用程序显示如果字段对象的值不符合指定的验证规则的消息的文本。|  
|[CDaoTableDef::IsOpen](#isopen)|返回非零，如果表是模式打开。|  
|[CDaoTableDef::Open](#open)|此时将打开存储在数据库中现有 tabledef 的 TableDef 的集合。|  
|[CDaoTableDef::RefreshLink](#refreshlink)|更新附加表的连接信息。|  
|[CDaoTableDef::SetAttributes](#setattributes)|设置一个值，该值指示的一个或多个特征`CDaoTableDef`对象。|  
|[CDaoTableDef::SetConnect](#setconnect)|设置一个值，提供有关表的源的信息。|  
|[CDaoTableDef::SetName](#setname)|设置表的名称。|  
|[CDaoTableDef::SetSourceTableName](#setsourcetablename)|设置一个值，指定源数据库中的附加表的名称。|  
|[CDaoTableDef::SetValidationRule](#setvalidationrule)|设置一个值，因为它已更改或添加到表验证字段中的数据。|  
|[CDaoTableDef::SetValidationText](#setvalidationtext)|设置一个值，指定您的应用程序显示如果字段对象的值不符合指定的验证规则的消息的文本。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CDaoTableDef::m_pDAOTableDef](#m_pdaotabledef)|指向基础 tabledef 对象的 DAO 接口的指针。|  
|[CDaoTableDef::m_pDatabase](#m_pdatabase)|此表的源数据库。|  
  
## <a name="remarks"></a>备注  
 每个 DAO 数据库对象会维护一个名为 TableDefs，包含所有已保存的 DAO tabledef 对象的集合。  
  
 处理表定义使用`CDaoTableDef`对象。 例如，你可以：  
  
-   检查任何本地、 附加或外部数据库表中的字段和索引结构。  
  
-   调用`SetConnect`和`SetSourceTableName`成员函数以附加的表，并使用`RefreshLink`成员函数以更新连接到附加的表。  
  
-   调用`CanUpdate`成员函数可确定是否可以编辑表中的字段定义。  
  
-   获取或设置使用的验证条件`GetValidationRule`和`SetValidationRule`，和`GetValidationText`和`SetValidationText`成员函数。  
  
-   使用**打开**成员函数来创建表、 动态集，或快照类型`CDaoRecordset`对象。  
  
    > [!NOTE]
    >  DAO 数据库类中是不同于基于开放式数据库连接 (ODBC) 的 MFC 数据库类。 DAO 数据库类的所有名称都具有"CDao"前缀。 您仍然可以访问 ODBC 数据源对于 DAO 类中;DAO 类通常会提供卓越功能，因为它们是特定于 Microsoft Jet 数据库引擎。  
  
### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>若要使用 tabledef 对象要使用现有表，也可以创建一个新表  
  
1.  在所有情况下，首先构建了`CDaoTableDef`对象，提供一个指向[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象传递给该表所属。  
  
2.  然后执行以下操作，具体取决于您的想法︰  
  
    -   若要使用现有的已保存表时，调用 tabledef 对象[打开](#open)成员函数，提供的已保存的表的名称。  
  
    -   若要创建新表，请调用 tabledef 对象[创建](#create)成员函数，提供的表的名称。 调用[CreateField](#createfield)和[CreateIndex](#createindex)若要向表中添加字段和索引。  
  
    -   调用[追加](#append)以便通过将其追加到该数据库的 TableDefs 集合保存该表。 **创建**将 tabledef 放入打开的状态，因此在调用**创建**不调用**打开**。  
  
        > [!TIP]
        >  若要创建已保存的表的最简单方法是创建它们，并将其存储在使用 Microsoft Access 数据库中。 然后可以打开并在您的 MFC 代码中使用它们。  
  
 若要使用 tabledef 对象已打开或创建，创建并打开`CDaoRecordset`对象，指定的名称与 tabledef **dbOpenTable**中的值`nOpenType`参数。  
  
 若要使用 tabledef 对象来创建`CDaoRecordset`对象时，通常创建或打开 tabledef 对象，如上所述，然后构造一个记录集对象，将指针传递给 tabledef 对象，当您调用[cdaorecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open)。 您传递的 tabledef 必须处于打开状态。 有关详细信息，请参见类[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  
  
 当您完成使用 tabledef 对象时，调用其[关闭](../../mfc/reference/cdaorecordset-class.md#close)成员函数; 然后销毁 tabledef 对象。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoTableDef`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdao.h  
  
##  <a name="append"></a>CDaoTableDef::Append  
 在您调用后调用此成员函数[创建](#create)以创建新的 tabledef 对象将 tabledef 保存在数据库中。  
  
```  
virtual void Append();
```  
  
### <a name="remarks"></a>备注  
 该函数将对象追加到该数据库的 TableDefs 集合。 时，可以使用 tabledef 作为临时对象定义通过不追加，但如果您想要保存并使用它，则必须调用**追加**。  
  
> [!NOTE]
>  如果尝试附加未命名的 tabledef （包含 null 或空字符串），则 MFC 将引发异常。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"追加方法"。  
  
##  <a name="canupdate"></a>CDaoTableDef::CanUpdate  
 调用此成员函数以确定是否对基础表的定义`CDaoTableDef`对象可以进行更改。  
  
```  
BOOL CanUpdate();
```  
  
### <a name="return-value"></a>返回值  
 如果可以修改表结构 （架构），则为非 （添加或删除字段和索引），否则为 0。  
  
### <a name="remarks"></a>备注  
 默认情况下，新创建的表基础`CDaoTableDef`可以更新对象，并附加的表基础`CDaoTableDef`无法更新此对象。 一个`CDaoTableDef`对象可能是可更新，即使生成的记录集是不可更新。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"可更新属性"。  
  
##  <a name="cdaotabledef"></a>CDaoTableDef::CDaoTableDef  
 构造**CDaoTableDef**对象。  
  
```  
CDaoTableDef(CDaoDatabase* pDatabase);
```  
  
### <a name="parameters"></a>参数  
 `pDatabase`  
 一个指向[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象。  
  
### <a name="remarks"></a>备注  
 构造该对象，则必须调用[创建](#create)或[打开](#open)成员函数。 当您完成与该对象时，必须调用其[关闭](#close)成员函数，并销毁`CDaoTableDef`对象。  
  
##  <a name="close"></a>CDaoTableDef::Close  
 调用此成员函数以关闭和释放 tabledef 对象。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>备注  
 通常在调用之后**关闭**，如果它已分配与删除 tabledef 对象**新**。  
  
 您可以调用[打开](#open)在调用后再次**关闭**。 这样就可以重用 tabledef 对象。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"Close 方法"。  
  
##  <a name="create"></a>CDaoTableDef::Create  
 调用此成员函数以创建新的已保存的表。  
  
```  
virtual void Create(
    LPCTSTR lpszName,  
    long lAttributes = 0,  
    LPCTSTR lpszSrcTable = NULL,  
    LPCTSTR lpszConnect = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 指向包含的表的名称的字符串的指针。  
  
 `lAttributes`  
 表格 tabledef 对象所表示的特性相对应的值。 您可以使用位或组合任意个以下常量︰  
  
|常量|说明|  
|--------------|-----------------|  
|**dbAttachExclusive**|对于使用 Microsoft Jet 数据库引擎的数据库，该值指示表是一个附加的表打开以供独占使用。|  
|**dbAttachSavePWD**|对于使用 Microsoft Jet 数据库引擎的数据库，指示用户 ID 和附加表的密码将与连接信息一起保存。|  
|**dbSystemObject**|指示表是由 Microsoft Jet 数据库引擎提供的系统表。|  
|**dbHiddenObject**|指示表是提供 Microsoft Jet 数据库引擎的隐藏的表。|  
  
 *lpszSrcTable*  
 指向包含源表名称的字符串的指针。 默认情况下此值被初始化为**NULL**。  
  
 `lpszConnect`  
 指向包含的默认连接字符串的字符串的指针。 默认情况下此值被初始化为**NULL**。  
  
### <a name="remarks"></a>备注  
 一旦您具有名为 tabledef，然后，您可以调用[追加](#append)tabledef 保存数据库的 TableDefs 集合中。 在调用**追加**且 tabledef 是处于打开状态，可用来创建[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"CreateTableDef 方法"。  
  
##  <a name="createfield"></a>CDaoTableDef::CreateField  
 调用该成员函数以向表中添加一个字段。  
  
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
 一个指向指定此字段的名称的字符串表达式。  
  
 `nType`  
 指示该字段的数据类型的值。 此设置可以是下列值之一︰  
  
|类型|大小（字节）|说明|  
|----------|--------------------|-----------------|  
|**dbBoolean**|1 个字节|BOOL|  
|**dbByte**|1|BYTE|  
|**dbInteger**|2|int|  
|**dbLong**|4|long|  
|**dbCurrency**|8|货币 ( [COleCurrency](../../mfc/reference/colecurrency-class.md))|  
|**dbSingle**|4|浮动|  
|**dbDouble**|8|double|  
|**dbDate**|8|日期/时间 ( [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|  
|**dbText**|1 – 255|文本 ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|  
|**dbLongBinary**|0|长二进制文件 （OLE 对象）， [CLongBinary](../../mfc/reference/clongbinary-class.md)或[CByteArray](../../mfc/reference/cbytearray-class.md)|  
|**dbMemo**|0|备注 ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|  
  
 `lSize`  
 一个值，指示最大大小，以字节为单位的字段的包含的文本或包含文本或数字值的字段的固定的大小。 `lSize`对于除的所有文本字段，将都忽略参数。  
  
 `lAttributes`  
 可以使用按位 OR 组合的字段和特性相对应的值。  
  
|常量|描述|  
|--------------|-----------------|  
|**dbFixedField**|此字段大小被固定的 （默认值为数值字段）。|  
|**dbVariableField**|此字段大小是 （仅适用于文本字段） 的变量。|  
|**dbAutoIncrField**|新记录的字段值自动递增到一个唯一的长整数，它不能更改。 仅支持 Microsoft Jet 数据库表。|  
|**dbUpdatableField**|可以更改字段值。|  
|**dbDescending**|对字段进行排序以降序 (Z-A 或 100 – 0) （仅适用于索引对象的字段集合中的字段对象） 的顺序。 如果省略此常量，该字段按升序 (A – Z 或 0-100) 顺序 （默认值）。|  
  
 `fieldinfo`  
 对引用[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构。  
  
### <a name="remarks"></a>备注  
 一个**DAOField**创建并追加到的字段集合 (OLE) 对象**DAOTableDef** (OLE) 的对象。 除了其用于检查对象属性，还可以使用`CDaoFieldInfo`构造在 tabledef 对象中创建新的字段的输入的参数。 第一个版本`CreateField`会更易于使用，但如果您想更精细的控制，您可以使用第二版`CreateField`，此方法采用`CDaoFieldInfo`参数。  
  
 如果您使用的版本`CreateField`采用`CDaoFieldInfo`参数，您必须小心地将每个以下的成员的`CDaoFieldInfo`结构︰  
  
- **m_strName**  
  
- `m_nType`  
  
- **m_lSize**  
  
- **m_lAttributes**  
  
- **m_bAllowZeroLength**  
  
 其他成员`CDaoFieldInfo`应设置为**0**， **FALSE**，或空字符串时，根据该成员，或`CDaoException`可能会出现。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"CreateField 方法"。  
  
##  <a name="createindex"></a>CDaoTableDef::CreateIndex  
 调用此函数可向表添加索引。  
  
```  
void CreateIndex(CDaoIndexInfo& indexinfo);
```  
  
### <a name="parameters"></a>参数  
 `indexinfo`  
 对引用[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)结构。  
  
### <a name="remarks"></a>备注  
 索引指定的顺序访问从数据库表和接受重复的记录的记录。 索引还提供高效的数据访问。  
  
 不需要创建索引的表，但在大型未编制索引的表，访问特定的记录或创建一个记录集可能需要长时间。 另一方面，创建太多索引降低更新、 添加和删除操作，如自动更新的所有索引。 当您决定创建哪些索引，请考虑这些因素。  
  
 以下成员`CDaoIndexInfo`必须设置结构︰  
  
- **m_strName**必须提供名称。  
  
- `m_pFieldInfos`必须指向数组的`CDaoIndexFieldInfo`结构。  
  
- `m_nFields`必须在数组中指定的字段数`CDaoFieldInfo`结构。  
  
 剩余成员将被忽略的如果设置为**FALSE**。 此外， **m_lDistinctCount**成员时将忽略在创建索引。  
  
##  <a name="deletefield"></a>CDaoTableDef::DeleteField  
 调用该成员函数以删除某字段，使其无法访问。  
  
```  
void DeleteField(LPCTSTR lpszName);  
void DeleteField(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 一个指向现有字段的名称的字符串表达式。  
  
 `nIndex`  
 在表的从零开始的字段集合中，对于通过索引查找字段的索引。  
  
### <a name="remarks"></a>备注  
 您可以在不追加到数据库的新对象上使用此成员函数时，或者当[CanUpdate](#canupdate)返回非零值。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"删除方法"。  
  
##  <a name="deleteindex"></a>CDaoTableDef::DeleteIndex  
 调用此成员函数删除基础表中的索引。  
  
```  
void DeleteIndex(LPCTSTR lpszName);  
void DeleteIndex(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 一个指向现有索引的名称的字符串表达式。  
  
 `nIndex`  
 在数据库的从零开始 TableDefs 集合中，对于通过索引查找的索引对象的数组索引。  
  
### <a name="remarks"></a>备注  
 可以在没有已追加到该数据库的新对象上使用此成员函数时，或者当[CanUpdate](#canupdate)返回非零值。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"删除方法"。  
  
##  <a name="getattributes"></a>CDaoTableDef::GetAttributes  
 有关`CDaoTableDef`对象，则返回值指定所表示的表的特征`CDaoTableDef`对象，并可能这些常量中的总和︰  
  
```  
long GetAttributes();
```  
  
### <a name="return-value"></a>返回值  
 返回一个值，该值指示的一个或多个特征`CDaoTableDef`对象。  
  
### <a name="remarks"></a>备注  
  
|常量|说明|  
|--------------|-----------------|  
|**dbAttachExclusive**|对于使用 Microsoft Jet 数据库引擎的数据库，该值指示表是一个附加的表打开以供独占使用。|  
|**dbAttachSavePWD**|对于使用 Microsoft Jet 数据库引擎的数据库，指示用户 ID 和附加表的密码将与连接信息一起保存。|  
|**dbSystemObject**|指示表是由 Microsoft Jet 数据库引擎提供的系统表。|  
|**dbHiddenObject**|指示表是提供 Microsoft Jet 数据库引擎的隐藏的表。|  
|**dbAttachedTable**|指示表是从非 ODBC 数据库，如 Paradox 数据库附加的表。|  
|**dbAttachedODBC**|指示表为附加从 ODBC 数据库，如 Microsoft SQL Server 表。|  
  
 系统表是由 Microsoft Jet 数据库引擎，以包含各种内部信息创建一个表。  
  
 隐藏的表是由 Microsoft Jet 数据库引擎创建供临时使用的表。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"特性属性"。  
  
##  <a name="getconnect"></a>CDaoTableDef::GetConnect  
 调用该成员函数以获取数据源的连接字符串。  
  
```  
CString GetConnect();
```  
  
### <a name="return-value"></a>返回值  
 一个`CString`对象，其中包含表的路径和数据库类型。  
  
### <a name="remarks"></a>备注  
 有关`CDaoTableDef`对象，表示一个附加的表，`CString`对象 （数据库类型说明符和指向数据库的路径） 的一个或两个部分组成。  
  
 下表中所示的路径是包含数据库文件的目录的完整路径，并且必须由标识符前面"数据库 ="。 在某些情况下 （如与 Microsoft Jet 和 Microsoft Excel 一起数据库） 中的特定文件名包括在数据库路径参数。  
  
 中的表[CDaoTableDef::SetConnect](#setconnect)显示可能的数据库类型及其相应的数据库说明符和路径︰  
  
 对于 Microsoft Jet 数据库基表，说明符是一个空字符串 ("")。  
  
 如果需要密码，但是未提供，ODBC 驱动程序将显示登录对话框首次访问表时，会再次关闭并重新打开连接。 如果附加的表具有**dbAttachSavePWD**属性中，登录提示将不会出现重新打开表时。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"连接属性"。  
  
##  <a name="getdatecreated"></a>CDaoTableDef::GetDateCreated  
 调用此函数可确定日期和时间表基础`CDaoTableDef`创建对象。  
  
```  
COleDateTime GetDateCreated();
```  
  
### <a name="return-value"></a>返回值  
 一个值，包含的日期和时间的基础表创建`CDaoTableDef`对象。  
  
### <a name="remarks"></a>备注  
 日期和时间设置均源自的计算机在其创建或上次更新时间的基础表。 在多用户环境中，用户应直接从文件服务器，为了避免出现差异; 获取这些设置也就是说，所有客户端应使用"标准"的时间源 — 可能从一台服务器。  
  
 有关相关信息，请参阅 DAO 帮助中的主题"DateCreated，上次更新属性"。  
  
##  <a name="getdatelastupdated"></a>CDaoTableDef::GetDateLastUpdated  
 调用此函数可确定日期和时间表基础**CDaoTableDef**上次更新对象。  
  
```  
COleDateTime GetDateLastUpdated();
```  
  
### <a name="return-value"></a>返回值  
 一个包含基础表的日期和时间值**CDaoTableDef**上次更新对象。  
  
### <a name="remarks"></a>备注  
 日期和时间设置均源自的计算机在其创建或上次更新时间的基础表。 在多用户环境中，用户应直接从文件服务器，为了避免出现差异; 获取这些设置也就是说，所有客户端应使用"标准"的时间源 — 可能从一台服务器。  
  
 有关相关信息，请参阅 DAO 帮助中的主题"DateCreated，上次更新属性"。  
  
##  <a name="getfieldcount"></a>CDaoTableDef::GetFieldCount  
 调用此成员函数可检索的表中定义的字段的数目。  
  
```  
short GetFieldCount();
```  
  
### <a name="return-value"></a>返回值  
 表中的字段数。  
  
### <a name="remarks"></a>备注  
 如果其值为 0，该集合有任何对象。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"计数属性"。  
  
##  <a name="getfieldinfo"></a>CDaoTableDef::GetFieldInfo  
 调用该成员函数以获取有关 tabledef 中定义的字段的信息的各种类型。  
  
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
 指定有关要检索的字段的信息的选项。 以及它们会导致返回的函数，这里列出了可用的选项︰  
  
- `AFX_DAO_PRIMARY_INFO`（默认值）名称、 类型、 大小 （属性）。 此选项用于最快的性能。  
  
- `AFX_DAO_SECONDARY_INFO`主要信息加上︰ 序号位置，必需的允许零长度，比较其排列顺序，外部名称、 源字段中，源表  
  
- `AFX_DAO_ALL_INFO`主要和次要信息加上︰ 验证规则，验证文本，默认值  
  
 `lpszName`  
 指向对象的名称字段，按名称查找的指针。 名称是唯一命名字段与最多为 64 个字符的字符串。  
  
### <a name="remarks"></a>备注  
 该函数的一个版本，可以按索引查找字段。 另一个版本中，可以按名称查找字段。  
  
 返回的信息的说明，请参阅[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构。 这种结构有对应于上面的说明中列出的信息的项目的成员`dwInfoOptions`。 当请求在某一级别的信息时，可以为任何以前的级别的信息。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"特性属性"。  
  
##  <a name="getindexcount"></a>CDaoTableDef::GetIndexCount  
 调用此成员函数以获取表的索引数。  
  
```  
short GetIndexCount();
```  
  
### <a name="return-value"></a>返回值  
 为表的索引的数目。  
  
### <a name="remarks"></a>备注  
 如果其值为 0，该集合没有索引。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"计数属性"。  
  
##  <a name="getindexinfo"></a>CDaoTableDef::GetIndexInfo  
 调用此成员函数来获取各种 tabledef 中定义了索引有关的信息。  
  
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
 在表的从零开始的索引集合中，通过在集合中的位置查找该索引对象的数字索引。  
  
 `indexinfo`  
 对引用[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)结构。  
  
 `dwInfoOptions`  
 指定要检索的索引有关的信息的选项。 以及它们会导致返回的函数，这里列出了可用的选项︰  
  
- `AFX_DAO_PRIMARY_INFO`名称、 字段信息的字段。 此选项用于最快的性能。  
  
- `AFX_DAO_SECONDARY_INFO`主要信息加上︰ 主要、 Unique、 聚集索引、 忽略空值，必需的外部  
  
- `AFX_DAO_ALL_INFO`主要和次要信息加上︰ 非重复计数  
  
 `lpszName`  
 一个指向按名称查找索引对象的名称。  
  
### <a name="remarks"></a>备注  
 该函数的一个版本，可以通过在集合中的位置的索引查找。 另一个版本中，可以按名称查找索引。  
  
 返回的信息的说明，请参阅[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)结构。 这种结构有对应于上面的说明中列出的信息的项目的成员`dwInfoOptions`。 当请求在某一级别的信息时，可以为任何以前的级别的信息。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"特性属性"。  
  
##  <a name="getname"></a>CDaoTableDef::GetName  
 调用该成员函数以获取基础表的用户定义名称。  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>返回值  
 表的用户定义名称。  
  
### <a name="remarks"></a>备注  
 此名称以字母开头，并且可以包含最多为 64 个字符。 可以包含数字和下划线字符，但不能包括标点符号和空格。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"名称属性"。  
  
##  <a name="getrecordcount"></a>CDaoTableDef::GetRecordCount  
 调用此成员函数以找出多少条记录位于`CDaoTableDef`对象。  
  
```  
long GetRecordCount();
```  
  
### <a name="return-value"></a>返回值  
 访问 tabledef 对象中的记录数。  
  
### <a name="remarks"></a>备注  
 调用`GetRecordCount`表类型`CDaoTableDef`对象反映的近似表中的记录数，如添加和删除表记录立即受影响。 回滚事务将显示为属于的记录数，直到您调用[CDaoWorkSpace::CompactDatabase](../../mfc/reference/cdaoworkspace-class.md#compactdatabase)。 一个`CDaoTableDef`不包含记录的对象具有的记录计数属性设置为 0。 在使用附加的表或 ODBC 数据库`GetRecordCount`始终返回-1。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"RecordCount 属性"。  
  
##  <a name="getsourcetablename"></a>CDaoTableDef::GetSourceTableName  
 调用该成员函数以检索附加源数据库中表的名称。  
  
```  
CString GetSourceTableName();
```  
  
### <a name="return-value"></a>返回值  
 一个`CString`对象，它指定附加的表或空字符串的源名称，如果本机数据的表。  
  
### <a name="remarks"></a>备注  
 附加的表是链接到 Microsoft Jet 数据库的另一个数据库中的表。 附加表的数据保留在外部数据库，其中它可由其他应用程序操作。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"SourceTableName 属性"。  
  
##  <a name="getvalidationrule"></a>CDaoTableDef::GetValidationRule  
 调用此成员函数以检索 tabledef 对象的验证规则。  
  
```  
CString GetValidationRule();
```  
  
### <a name="return-value"></a>返回值  
 一个**CString**验证字段中的数据，因为它已更改或添加到表的对象。  
  
### <a name="remarks"></a>备注  
 与更新操作结合使用验证规则。 如果 tabledef 对象包含的验证规则，对该 tabledef 的更新必须匹配预先确定的条件之前的数据更改。 如果更改不匹配条件，异常包含的值的[GetValidationText](#getvalidationtext)引发。 有关`CDaoTableDef`对象时，这`CString`是只读的附加的表和基础表的读/写。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"有效性规则属性"。  
  
##  <a name="getvalidationtext"></a>CDaoTableDef::GetValidationText  
 调用此函数可检索要在用户输入与验证规则不匹配的数据时显示的字符串。  
  
```  
CString GetValidationText();
```  
  
### <a name="return-value"></a>返回值  
 一个`CString`对象，它指定当用户输入与验证规则不匹配的数据显示的文本。  
  
### <a name="remarks"></a>备注  
 有关`CDaoTableDef`对象时，这`CString`是只读的附加的表和基础表的读/写。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"有效性文本属性"。  
  
##  <a name="isopen"></a>CDaoTableDef::IsOpen  
 调用此成员函数以确定是否`CDaoTableDef`对象当前处于打开状态。  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果非零`CDaoTableDef`对象是打开; 否则为 0。  
  
### <a name="remarks"></a>备注  
  
##  <a name="m_pdatabase"></a>CDaoTableDef::m_pDatabase  
 包含一个指向[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)此表的对象。  
  
### <a name="remarks"></a>备注  
  
##  <a name="m_pdaotabledef"></a>CDaoTableDef::m_pDAOTableDef  
 包含指向 DAO tabledef 对象基础的 OLE 接口的指针`CDaoTableDef`对象。  
  
### <a name="remarks"></a>备注  
 如果您需要直接访问 DAO 接口，请使用此指针。  
  
##  <a name="open"></a>CDaoTableDef::Open  
 调用该成员函数以打开 tabledef 以前保存到数据库中的 TableDef 的集合。  
  
```  
virtual void Open(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 指向一个字符串，指定表名的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="refreshlink"></a>CDaoTableDef::RefreshLink  
 调用该成员函数以更新附加表的连接信息。  
  
```  
void RefreshLink();
```  
  
### <a name="remarks"></a>备注  
 通过调用更改附加表的连接信息[为表示](#setconnect)相应`CDaoTableDef`对象，然后使用`RefreshLink`成员函数以更新的信息。 当您调用`RefreshLink`，附加的表的属性不会更改。  
  
 若要强制已修改连接信息才会生效，所有打开[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)必须关闭此 tabledef 所基于的对象。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"RefreshLink 方法"。  
  
##  <a name="setattributes"></a>CDaoTableDef::SetAttributes  
 设置一个值，该值指示的一个或多个特征`CDaoTableDef`对象。  
  
```  
void SetAttributes(long lAttributes);
```  
  
### <a name="parameters"></a>参数  
 `lAttributes`  
 所表示的表的特征`CDaoTableDef`对象，并可能这些常量中的总和︰  
  
|常量|说明|  
|--------------|-----------------|  
|**dbAttachExclusive**|对于使用 Microsoft Jet 数据库引擎的数据库，该值指示表是一个附加的表打开以供独占使用。|  
|**dbAttachSavePWD**|对于使用 Microsoft Jet 数据库引擎的数据库，指示用户 ID 和附加表的密码将与连接信息一起保存。|  
|**dbSystemObject**|指示表是由 Microsoft Jet 数据库引擎提供的系统表。|  
|**dbHiddenObject**|指示表是提供 Microsoft Jet 数据库引擎的隐藏的表。|  
  
### <a name="remarks"></a>备注  
 设置多个属性，你可以将这些组合通过对相应的常量使用按位 OR 运算符求和。 设置**dbAttachExclusive**在附加的表会生成异常。 下面将数值组合也产生了异常︰  
  
- **dbAttachExclusive |dbAttachedODBC**  
  
- **dbAttachSavePWD |dbAttachedTable**  
  
 有关相关信息，请参阅主题 DAO 帮助中的"特性属性"。  
  
##  <a name="setconnect"></a>CDaoTableDef::SetConnect  
 有关`CDaoTableDef`对象，表示一个附加的表中，字符串对象 （数据库类型说明符和指向数据库的路径） 的一个或两个部分组成。  
  
```  
void SetConnect(LPCTSTR lpszConnect);
```  
  
### <a name="parameters"></a>参数  
 `lpszConnect`  
 一个指向指定要传递到 ODBC 或可安装 ISAM 驱动程序的其他参数的字符串表达式。  
  
### <a name="remarks"></a>备注  
 下表中所示的路径是包含数据库文件的目录的完整路径，并且必须由标识符前面"数据库 ="。 在某些情况下 （如与 Microsoft Jet 和 Microsoft Excel 一起数据库） 中的特定文件名包括在数据库路径参数。  
  
> [!NOTE]
>  不在路径形式的语句包含等号两侧的空格"数据库 = 驱动器︰\\\path"。 这将导致引发异常和连接失败。  
  
 下表显示可能的数据库类型及其相应的数据库说明符和路径︰  
  
|数据库类型|说明符|路径|  
|-------------------|---------------|----------|  
|使用 Jet 数据库引擎的数据库|"[ `database`];"|" `drive`:\\\ *path*\\\ *filename*.MDB"|  
|dBASE III|"dBASE III;"|" `drive`:\\\ *path*"|  
|dBASE IV|"dBASE IV;"|" `drive`:\\\ *path*"|  
|dBASE 5|"dBASE 5.0;"|" `drive`:\\\ *path*"|  
|Paradox 3.x|"Paradox 3.x;"|" `drive`:\\\ *path*"|  
|Paradox 4.x|"Paradox 4.x;"|" `drive`:\\\ *path*"|  
|Paradox 5.x|"Paradox 5.x;"|" `drive`:\\\ *path*"|  
|Excel 3.0|"Excel 3.0;"|" `drive`:\\\ *path*\\\ *filename*.XLS"|  
|Excel 4.0|"Excel 4.0;"|" `drive`:\\\ *path*\\\ *filename*.XLS"|  
|Excel 5.0 或 Excel 95|"Excel 5.0;"|" `drive`:\\\ *path*\\\ *filename*.XLS"|  
|Excel 97|"Excel 8.0;"|" `drive`:\\\ *path*\ *filename*.XLS"|  
|HTML 导入|"HTML 导入;"|" `drive`:\\\ *path*\ *filename*"|  
|HTML 导出|"HTML 导出;"|" `drive`:\\\ *path*"|  
|Text|"Text";|"驱动器︰\\\path"|  
|ODBC|"ODBC;数据库 = `database`;UID= *user*;PWD =*密码*;DSN = *datasourcename;*LOGINTIMEOUT =*秒;*"（这可能不是所有服务器的完整连接字符串; 它只是一个示例。 它是非常重要，不需要参数之间的空格。）|无|  
|交换|"交换;<br /><br /> MAPILEVEL = *folderpath*;<br /><br /> [TABLETYPE = {0 | 1};]<br /><br /> [配置文件 =*配置文件*;]<br /><br /> [PWD =*密码*;]<br /><br /> [数据库 = `database`;]"|*"drive*:\\\ *path*\\\ *filename*.MDB"|  
  
> [!NOTE]
>  Btrieve 截至 DAO 3.5 不再受支持。  
  
 您必须使用双反斜杠 (\\\\) 的连接字符串中。 如果您已修改现有的连接使用的属性`SetConnect`，您必须随后调用[RefreshLink](#refreshlink)。 如果在初始化时使用的连接属性`SetConnect`，您需要不调用`RefreshLink`，但您应选择这样做，首先附加 tabledef。  
  
 如果需要密码，但是未提供，ODBC 驱动程序将显示登录对话框首次访问表时，会再次关闭并重新打开连接。  
  
 您可以设置的连接字符串`CDaoTableDef`对象通过提供对在 source 参数**创建**成员函数。 您可以检查设置，以确定类型、 路径、 用户 ID、 密码或 ODBC 数据源的数据库。 有关详细信息，请参阅特定的驱动程序的文档。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"连接属性"。  
  
##  <a name="setname"></a>CDaoTableDef::SetName  
 调用该成员函数以设置用户定义表的名称。  
  
```  
void SetName(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 一个指向指定表的名称的字符串表达式。  
  
### <a name="remarks"></a>备注  
 名称必须以字母开头，并且可以包含最多为 64 个字符。 可以包含数字和下划线字符，但不能包括标点符号和空格。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"名称属性"。  
  
##  <a name="setsourcetablename"></a>CDaoTableDef::SetSourceTableName  
 调用此成员函数以指定附加表的名称或基础表的名称在其上`CDaoTableDef`基于对象，如同它存在于原始源中的数据。  
  
```  
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```  
  
### <a name="parameters"></a>参数  
 *lpszSrcTableName*  
 一个指向外部数据库中指定的表名称的字符串表达式。 对于基表，设置是一个空字符串 ("")。  
  
### <a name="remarks"></a>备注  
 然后，您必须调用[RefreshLink](#refreshlink)。 此属性设置为空的基础表和读/写附加的表或对象不会追加到集合。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"SourceTableName 属性"。  
  
##  <a name="setvalidationrule"></a>CDaoTableDef::SetValidationRule  
 调用此成员函数可设置 tabledef 对象的验证规则。  
  
```  
void SetValidationRule(LPCTSTR lpszValidationRule);
```  
  
### <a name="parameters"></a>参数  
 *lpszValidationRule*  
 验证操作的字符串表达式指向的指针。  
  
### <a name="remarks"></a>备注  
 与更新操作结合使用验证规则。 如果 tabledef 对象包含的验证规则，对该 tabledef 的更新必须匹配预先确定的条件之前的数据更改。 如果更改不匹配条件，包含文本的异常[GetValidationText](#getvalidationtext)显示。  
  
 仅用于使用 Microsoft Jet 数据库引擎的数据库支持验证。 表达式不能引用用户定义函数、 域聚合函数、 SQL 聚合函数或查询。 验证规则`CDaoTableDef`对象可以引用该对象中的多个字段。  
  
 例如，对于名为字段`hire_date`和`termination_date`，验证规则可能是︰  
  
 [!code-cpp[NVC_MFCDatabase #&34;](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]  
  
 有关相关信息，请参阅主题 DAO 帮助中的"有效性规则属性"。  
  
##  <a name="setvalidationtext"></a>CDaoTableDef::SetValidationText  
 调用此成员函数可设置的验证规则的异常文本`CDaoTableDef`具有 Microsoft Jet 数据库引擎支持的基础表对象。  
  
```  
void SetValidationText(LPCTSTR lpszValidationText);
```  
  
### <a name="parameters"></a>参数  
 *lpszValidationText*  
 指定如果输入数据显示的文本的字符串表达式的指针是无效的。  
  
### <a name="remarks"></a>备注  
 不能设置附加表的验证文本。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"有效性文本属性"。  
  
## <a name="see-also"></a>另请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDaoDatabase 类](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoRecordset 类](../../mfc/reference/cdaorecordset-class.md)

