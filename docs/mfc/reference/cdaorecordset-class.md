---
title: "CDaoRecordset Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDaoRecordset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoRecordset 类"
  - "记录, CDaoRecordSet"
  - "记录集, 类型"
ms.assetid: 2322067f-1027-4662-a5d7-aa2fc7488630
caps.latest.revision: 26
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoRecordset Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示从数据源中选择的一组记录。  
  
## 语法  
  
```  
  
class CDaoRecordset : public CObject  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDaoRecordset::CDaoRecordset](../Topic/CDaoRecordset::CDaoRecordset.md)|构造 `CDaoRecordset` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDaoRecordset::AddNew](../Topic/CDaoRecordset::AddNew.md)|为添加新记录准备。  调用 [更新](../Topic/CDaoRecordset::Update.md) 添加完。|  
|[CDaoRecordset::CanAppend](../Topic/CDaoRecordset::CanAppend.md)|如果新记录，可以添加到记录集通过 [AddNew](../Topic/CDaoRecordset::AddNew.md) 成员函数，返回非零。|  
|[CDaoRecordset::CanBookmark](../Topic/CDaoRecordset::CanBookmark.md)|如果记录集支持书签，返回非零。|  
|[CDaoRecordset::CancelUpdate](../Topic/CDaoRecordset::CancelUpdate.md)|取消任何挂起更新由于 [编辑](../Topic/CDaoRecordset::Edit.md) 或 [AddNew](../Topic/CDaoRecordset::AddNew.md) 操作。|  
|[CDaoRecordset::CanRestart](../Topic/CDaoRecordset::CanRestart.md)|如果 [再次查询](../Topic/CDaoRecordset::Requery.md) 可以调用同样，运行记录集的查询返回非零。|  
|[CDaoRecordset::CanScroll](../Topic/CDaoRecordset::CanScroll.md)|如果通过记录，将返回非零。|  
|[CDaoRecordset::CanTransact](../Topic/CDaoRecordset::CanTransact.md)|如果数据源支持事务，返回非零。|  
|[CDaoRecordset::CanUpdate](../Topic/CDaoRecordset::CanUpdate.md)|返回非零，如果记录集可更新\(可以添加，更新或删除记录）。|  
|[CDaoRecordset::Close](../Topic/CDaoRecordset::Close.md)|关闭记录集。|  
|[CDaoRecordset::Delete](../Topic/CDaoRecordset::Delete.md)|从记录集中删除当前记录。  必须显式移动到另一个记录在该删除操作之后。|  
|[CDaoRecordset::DoFieldExchange](../Topic/CDaoRecordset::DoFieldExchange.md)|调用交换数据\(在两个方向\)在记录集的字段数据成员和数据源中的相应的记录之间。  实现DAO记录字段交换\(DFX）。|  
|[CDaoRecordset::Edit](../Topic/CDaoRecordset::Edit.md)|为当前记录的更改准备。  调用 **Update** 完成编辑。|  
|[CDaoRecordset::FillCache](../Topic/CDaoRecordset::FillCache.md)|加载所有或本地缓存的部分包含从ODBC数据源的数据的记录集对象中。|  
|[CDaoRecordset::Find](../Topic/CDaoRecordset::Find.md)|查找特定字符串的第一，下，条、最后位置满足指定条件的一个动态类型的记录集并使记录当前记录。|  
|[CDaoRecordset::FindFirst](../Topic/CDaoRecordset::FindFirst.md)|隔离第一个记录满足指定条件的一个动态类型或快照型记录集并使记录当前记录。|  
|[CDaoRecordset::FindLast](../Topic/CDaoRecordset::FindLast.md)|隔离最后一条记录满足指定条件的一个动态类型或快照型记录集并使记录当前记录。|  
|[CDaoRecordset::FindNext](../Topic/CDaoRecordset::FindNext.md)|隔离下一条记录满足指定条件的一个动态类型或快照型记录集并使记录当前记录。|  
|[CDaoRecordset::FindPrev](../Topic/CDaoRecordset::FindPrev.md)|隔离上一条记录满足指定条件的一个动态类型或快照型记录集并使记录当前记录。|  
|[CDaoRecordset::GetAbsolutePosition](../Topic/CDaoRecordset::GetAbsolutePosition.md)|返回记录集对象的当前记录的数字。|  
|[CDaoRecordset::GetBookmark](../Topic/CDaoRecordset::GetBookmark.md)|返回表示在记录的书签的值。|  
|[CDaoRecordset::GetCacheSize](../Topic/CDaoRecordset::GetCacheSize.md)|返回从ODBC在数据源动态类型的记录集指定的记录数包含本地数据缓存的值。|  
|[CDaoRecordset::GetCacheStart](../Topic/CDaoRecordset::GetCacheStart.md)|返回在要缓存的记录集指定第一条记录书签的值。|  
|[CDaoRecordset::GetCurrentIndex](../Topic/CDaoRecordset::GetCurrentIndex.md)|返回包含索引的名称 `CString` 最近使用在索引中，表类型的 `CDaoRecordset`。|  
|[CDaoRecordset::GetDateCreated](../Topic/CDaoRecordset::GetDateCreated.md)|返回基础 `CDaoRecordset` 对象的基表创建日期和时间|  
|[CDaoRecordset::GetDateLastUpdated](../Topic/CDaoRecordset::GetDateLastUpdated.md)|返回执行的最新更改的日期和时间对基础 `CDaoRecordset` 对象的基表的设计。|  
|[CDaoRecordset::GetDefaultDBName](../Topic/CDaoRecordset::GetDefaultDBName.md)|返回默认的数据源的名称。|  
|[CDaoRecordset::GetDefaultSQL](../Topic/CDaoRecordset::GetDefaultSQL.md)|页中获取执行的默认SQL字符串。|  
|[CDaoRecordset::GetEditMode](../Topic/CDaoRecordset::GetEditMode.md)|返回一个状态编辑当前记录的值。|  
|[CDaoRecordset::GetFieldCount](../Topic/CDaoRecordset::GetFieldCount.md)|返回表示字段数在记录集中的值。|  
|[CDaoRecordset::GetFieldInfo](../Topic/CDaoRecordset::GetFieldInfo.md)|返回给定类型有关字段的信息在记录集。|  
|[CDaoRecordset::GetFieldValue](../Topic/CDaoRecordset::GetFieldValue.md)|返回一个字段的值在记录集中。|  
|[CDaoRecordset::GetIndexCount](../Topic/CDaoRecordset::GetIndexCount.md)|因记录集的表中检索索引的数目。|  
|[CDaoRecordset::GetIndexInfo](../Topic/CDaoRecordset::GetIndexInfo.md)|返回各种有关索引的信息。|  
|[CDaoRecordset::GetLastModifiedBookmark](../Topic/CDaoRecordset::GetLastModifiedBookmark.md)|用于确定最近添加的或更新的记录。|  
|[CDaoRecordset::GetLockingMode](../Topic/CDaoRecordset::GetLockingMode.md)|返回在编辑器中，一个值锁的类型有效。|  
|[CDaoRecordset::GetName](../Topic/CDaoRecordset::GetName.md)|返回包含记录集的名称 `CString`。|  
|[CDaoRecordset::GetParamValue](../Topic/CDaoRecordset::GetParamValue.md)|检索在基础DAOParameter对象存储的指定参数的当前值。|  
|[CDaoRecordset::GetPercentPosition](../Topic/CDaoRecordset::GetPercentPosition.md)|返回当前记录的位置作为百分比总记录数。|  
|[CDaoRecordset::GetRecordCount](../Topic/CDaoRecordset::GetRecordCount.md)|返回在记录集对象获取记录数。|  
|[CDaoRecordset::GetSQL](../Topic/CDaoRecordset::GetSQL.md)|获取SQL字符串用于为记录集选择记录。|  
|[CDaoRecordset::GetType](../Topic/CDaoRecordset::GetType.md)|调用确定记录集的类型:表类型，动态类型或快照类型。|  
|[CDaoRecordset::GetValidationRule](../Topic/CDaoRecordset::GetValidationRule.md)|返回包含验证数据值的 `CString`，以便在输入字段。|  
|[CDaoRecordset::GetValidationText](../Topic/CDaoRecordset::GetValidationText.md)|检索显示的文本，当验证规则不足时。|  
|[CDaoRecordset::IsBOF](../Topic/CDaoRecordset::IsBOF.md)|如果将记录集定位，在第一条记录之前，返回非零。  没有当前记录。|  
|[CDaoRecordset::IsDeleted](../Topic/CDaoRecordset::IsDeleted.md)|如果记录集在已删除的记录，确定返回非零。|  
|[CDaoRecordset::IsEOF](../Topic/CDaoRecordset::IsEOF.md)|如果记录集在最后一条记录后，确定返回非零。  没有当前记录。|  
|[CDaoRecordset::IsFieldDirty](../Topic/CDaoRecordset::IsFieldDirty.md)|如果更改了，返回非零在当前记录的指定的字段。|  
|[CDaoRecordset::IsFieldNull](../Topic/CDaoRecordset::IsFieldNull.md)|返回非零，则在当前记录的指定字段为Null \(具有值）。|  
|[CDaoRecordset::IsFieldNullable](../Topic/CDaoRecordset::IsFieldNullable.md)|返回非零，则在当前记录的指定字段可以设置为Null \(具有值）。|  
|[CDaoRecordset::IsOpen](../Topic/CDaoRecordset::IsOpen.md)|如果 [打开](../Topic/CDaoRecordset::Open.md) 之前，调用返回非零。|  
|[CDaoRecordset::Move](../Topic/CDaoRecordset::Move.md)|确定记录集到指定的记录数从当前记录的任一方向。|  
|[CDaoRecordset::MoveFirst](../Topic/CDaoRecordset::MoveFirst.md)|在记录集中的第一条记录确定当前记录。|  
|[CDaoRecordset::MoveLast](../Topic/CDaoRecordset::MoveLast.md)|在记录集中的最后一条记录确定当前记录。|  
|[CDaoRecordset::MoveNext](../Topic/CDaoRecordset::MoveNext.md)|在记录集的下一条记录确定当前记录。|  
|[CDaoRecordset::MovePrev](../Topic/CDaoRecordset::MovePrev.md)|在记录集的上一条记录确定当前记录。|  
|[CDaoRecordset::Open](../Topic/CDaoRecordset::Open.md)|创建从表、动态集或快照的新记录集。|  
|[CDaoRecordset::Requery](../Topic/CDaoRecordset::Requery.md)|再次运行记录集的查询刷新选定的记录。|  
|[CDaoRecordset::Seek](../Topic/CDaoRecordset::Seek.md)|定位记录满足当前索引的指定条件的已标记的表类型的记录集对象并使记录当前记录。|  
|[CDaoRecordset::SetAbsolutePosition](../Topic/CDaoRecordset::SetAbsolutePosition.md)|将记录集对象的当前记录的数字。|  
|[CDaoRecordset::SetBookmark](../Topic/CDaoRecordset::SetBookmark.md)|在包含指定书签的记录定位记录集。|  
|[CDaoRecordset::SetCacheSize](../Topic/CDaoRecordset::SetCacheSize.md)|设置从ODBC在数据源动态类型的记录集指定的记录数包含本地数据缓存的值。|  
|[CDaoRecordset::SetCacheStart](../Topic/CDaoRecordset::SetCacheStart.md)|将设置缓存的记录集指定第一条记录书签的值。|  
|[CDaoRecordset::SetCurrentIndex](../Topic/CDaoRecordset::SetCurrentIndex.md)|调用中设置表类型的记录集的索引。|  
|[CDaoRecordset::SetFieldDirty](../Topic/CDaoRecordset::SetFieldDirty.md)|标记在当前记录的指定字段为已更改。|  
|[CDaoRecordset::SetFieldNull](../Topic/CDaoRecordset::SetFieldNull.md)|设置指定字段的值在当前记录为Null \(具有值）。|  
|[CDaoRecordset::SetFieldValue](../Topic/CDaoRecordset::SetFieldValue.md)|设置一个字段的值在记录集中。|  
|[CDaoRecordset::SetFieldValueNull](../Topic/CDaoRecordset::SetFieldValueNull.md)|设置一个字段的值在记录集中为Null。  （具有值）。|  
|[CDaoRecordset::SetLockingMode](../Topic/CDaoRecordset::SetLockingMode.md)|设置指示实现的锁的类型在编译期间的值。|  
|[CDaoRecordset::SetParamValue](../Topic/CDaoRecordset::SetParamValue.md)|将基础DAOParameter对象存储的指定参数的当前值|  
|[CDaoRecordset::SetParamValueNull](../Topic/CDaoRecordset::SetParamValueNull.md)|将指定的参数的当前值为Null \(具有值）。|  
|[CDaoRecordset::SetPercentPosition](../Topic/CDaoRecordset::SetPercentPosition.md)|将当前记录的位置添加到位置百分比总记录数对应于记录集。|  
|[CDaoRecordset::Update](../Topic/CDaoRecordset::Update.md)|通过保存新记录或已编辑的数据完成 `AddNew` 或 **Edit** 操作在数据源。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CDaoRecordset::m\_bCheckCacheForDirtyFields](../Topic/CDaoRecordset::m_bCheckCacheForDirtyFields.md)|包含指示字段是否的标志将自动标记为已更改。|  
|[CDaoRecordset::m\_nFields](../Topic/CDaoRecordset::m_nFields.md)|在记录集选件类包含字段数据成员的数目和记录集选择的列数从数据源。|  
|[CDaoRecordset::m\_nParams](../Topic/CDaoRecordset::m_nParams.md)|在记录集选件类—参数数目包含参数数据成员的数目通过与记录集的查询|  
|[CDaoRecordset::m\_pDAORecordset](../Topic/CDaoRecordset::m_pDAORecordset.md)|对基础记录集对象的DAO接口的指针。|  
|[CDaoRecordset::m\_pDatabase](../Topic/CDaoRecordset::m_pDatabase.md)|此设置结果的源数据库。  包含指向 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 对象。|  
|[CDaoRecordset::m\_strFilter](../Topic/CDaoRecordset::m_strFilter.md)|包含用于的字符串构造SQL **WHERE** 语句。|  
|[CDaoRecordset::m\_strSort](../Topic/CDaoRecordset::m_strSort.md)|包含用于的字符串构造SQL **ORDER BY** 语句。|  
  
## 备注  
 称为“记录集”，`CDaoRecordset` 对象均以以下三种形式:  
  
-   表型记录集表示可以使用单个数据库表检查，添加，更改或删除记录的基表。  
  
-   动态集型记录集是可能具有可更新记录查询的结果。  这些记录集是一组记录可以使用检查，添加，更改的实例或者从一个基础数据库表或表删除记录。  动态集型记录集可以在数据库包含一个或多个表的字段。  
  
-   快照型记录集是静态副本的一组记录可以使用查找数据或生成报表的属性。  这些记录集在数据库包含一个或多个表的字段，但不能更新。  
  
 每次打开，记录集的每个窗体表示已修复的一组记录记录集。  当您移动到一个表类型的记录集或动态类型的记录集时的记录，它反映所做的更改对记录，在记录集打开，由其他用户或已在应用程序中的其他记录集。  （快照型记录集不能更新。）可以直接使用 `CDaoRecordset` 或从派生 `CDaoRecordset`特定的记录集选件类。  然后，您可以：  
  
-   滚动记录。  
  
-   设置索引和快速查找记录使用 [查找](../Topic/CDaoRecordset::Seek.md)（仅表型记录集）。  
  
-   查找记录基于字符串比较："\<"、"\<\="、"\="、"\>\=" 或 "\>"（动态类型和快照型记录集）。  
  
-   更新记录并指定一个锁定模式\(除快照型记录集）。  
  
-   筛选记录它从这些选择可用在数据源的记录集约束。  
  
-   排序记录集。  
  
-   参数化记录集自定义该控件的信息选择未知直到运行时。  
  
 类别 `CDaoRecordset` 提供接口类似于选件类 `CRecordset`。  主要区别在于选件类 `CDaoRecordset` 访问数据。数据访问对象基于OLE的\(DAO）。  通过开放式数据库连接\(odbc\)类别 `CRecordset` 访问DBMS和该DBMS的ODBC驱动程序。  
  
> [!NOTE]
>  DAO数据库选件类根据了开放式数据库连接的MFC数据库选件类都一目了然\(odbc）。  所有DAO数据库类名具有“CDao”前缀。  您仍然可以访问使用DAO选件类的ODBC数据源;，因为它们是特定于Microsoft Jet数据库引擎，DAO选件类通常提供优越功能。  
  
 可以直接使用 `CDaoRecordset` 或从 `CDaoRecordset`派生选件类。  如果要使用记录集选件类，请打开数据库并构造记录集对象，通过构造函数指针到您的 `CDaoDatabase` 对象。  还可以构造 `CDaoRecordset` 对象并使MFC创建自己的临时 `CDaoDatabase` 对象。  然后调用记录集的 [打开](../Topic/CDaoRecordset::Open.md) 成员函数，指定对象是否是一个表类型的记录集、一个动态类型的记录集或一个快照型记录集。  调用 **Open** 选择数据从数据库并检索第一条记录。  
  
 使用对象的成员函数和数据成员设置为滚动记录并对它们。  可用的操作取决于对象是否是一个表类型的记录集、一个动态类型的记录集或一个快照型记录集，因此，它是否可更新或只读—这是由数据库或开放式数据库连接\(odbc\)数据源的功能。  若要刷新可能已更改或添加的记录，因为 **Open** 调用，调用对象的 [再次查询](../Topic/CDaoRecordset::Requery.md) 成员函数。  当您完成使用协定时，调用对象的 **Close** 成员函数和销毁对象。  
  
 `CDaoRecordset` 使用DAO记录支持读取和更新的字段交换\(DFX\)记录字段将您的 `CDaoRecordset` 或 `CDaoRecordset`派生类的类型安全的C\+\+成员。  使用 [GetFieldValue](../Topic/CDaoRecordset::GetFieldValue.md) 和 [SetFieldValue](../Topic/CDaoRecordset::SetFieldValue.md)，可在数据库中还可以实现列动态绑定，而不使用DFX结构。  
  
 有关相关信息，请参见主题“记录集对象” DAO帮助。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoRecordset`  
  
## 要求  
 **Header:** afxdao.h  
  
## 请参阅  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDaoTableDef Class](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoWorkspace Class](../../mfc/reference/cdaoworkspace-class.md)   
 [CDaoDatabase Class](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoQueryDef Class](../../mfc/reference/cdaoquerydef-class.md)