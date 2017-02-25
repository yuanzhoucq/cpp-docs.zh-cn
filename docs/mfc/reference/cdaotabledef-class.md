---
title: "CDaoTableDef Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDaoTableDef"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoTableDef class"
  - "数据库类 [C++], DAO"
  - "database tables [C++], attached table definition"
  - "database tables [C++], base table definition"
  - "tabledefs [C++]"
ms.assetid: 7c5d2254-8475-43c4-8a6c-2d32ead194c9
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CDaoTableDef Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示一个基表或一个附加的表的存储的定义。  
  
## 语法  
  
```  
class CDaoTableDef : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDaoTableDef::CDaoTableDef](../Topic/CDaoTableDef::CDaoTableDef.md)|构造 **CDaoTableDef** 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDaoTableDef::Append](../Topic/CDaoTableDef::Append.md)|添加新表到数据库。|  
|[CDaoTableDef::CanUpdate](../Topic/CDaoTableDef::CanUpdate.md)|返回非零，如果表可更新\(可以修改字段或表属性的定义）。|  
|[CDaoTableDef::Close](../Topic/CDaoTableDef::Close.md)|关闭打开tabledef。|  
|[CDaoTableDef::Create](../Topic/CDaoTableDef::Create.md)|创建使用 [追加](../Topic/CDaoTableDef::Append.md)，可以添加到该数据库的表。|  
|[CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md)|调用创建表的一个字段。|  
|[CDaoTableDef::CreateIndex](../Topic/CDaoTableDef::CreateIndex.md)|调用创建表的索引。|  
|[CDaoTableDef::DeleteField](../Topic/CDaoTableDef::DeleteField.md)|调用从表中删除字段。|  
|[CDaoTableDef::DeleteIndex](../Topic/CDaoTableDef::DeleteIndex.md)|调用从表中删除索引。|  
|[CDaoTableDef::GetAttributes](../Topic/CDaoTableDef::GetAttributes.md)|返回一 `CDaoTableDef` 对象的一个或多个属性的值。|  
|[CDaoTableDef::GetConnect](../Topic/CDaoTableDef::GetConnect.md)|返回提供有关表中的信息的值。|  
|[CDaoTableDef::GetDateCreated](../Topic/CDaoTableDef::GetDateCreated.md)|返回基础 `CDaoTableDef` 对象的基表创建日期和时间。|  
|[CDaoTableDef::GetDateLastUpdated](../Topic/CDaoTableDef::GetDateLastUpdated.md)|返回执行的最新更改的日期和时间。这个基表的设计。|  
|[CDaoTableDef::GetFieldCount](../Topic/CDaoTableDef::GetFieldCount.md)|返回在表中表示字段的值。|  
|[CDaoTableDef::GetFieldInfo](../Topic/CDaoTableDef::GetFieldInfo.md)|返回给定类型有关字段的信息在表中。|  
|[CDaoTableDef::GetIndexCount](../Topic/CDaoTableDef::GetIndexCount.md)|返回索引数表的。|  
|[CDaoTableDef::GetIndexInfo](../Topic/CDaoTableDef::GetIndexInfo.md)|返回给定类型有关索引的信息表的。|  
|[CDaoTableDef::GetName](../Topic/CDaoTableDef::GetName.md)|返回表的用户定义的名称。|  
|[CDaoTableDef::GetRecordCount](../Topic/CDaoTableDef::GetRecordCount.md)|在表中返回记录数。|  
|[CDaoTableDef::GetSourceTableName](../Topic/CDaoTableDef::GetSourceTableName.md)|返回在源数据库指定一个附加的表的名称的值。|  
|[CDaoTableDef::GetValidationRule](../Topic/CDaoTableDef::GetValidationRule.md)|返回验证字段中的数据的值，则已更改或添加到表中。|  
|[CDaoTableDef::GetValidationText](../Topic/CDaoTableDef::GetValidationText.md)|返回指定消息文本您的应用程序显示的值字段，则对象的值不满足指定的验证规则。|  
|[CDaoTableDef::IsOpen](../Topic/CDaoTableDef::IsOpen.md)|如果表处于打开状态，返回非零。|  
|[CDaoTableDef::Open](../Topic/CDaoTableDef::Open.md)|打开数据库中的TableDef的集合存储的现有tabledef。|  
|[CDaoTableDef::RefreshLink](../Topic/CDaoTableDef::RefreshLink.md)|更新一个附加的表的连接信息。|  
|[CDaoTableDef::SetAttributes](../Topic/CDaoTableDef::SetAttributes.md)|设置一 `CDaoTableDef` 对象的一个或多个属性的值。|  
|[CDaoTableDef::SetConnect](../Topic/CDaoTableDef::SetConnect.md)|设置提供有关表中的信息的值。|  
|[CDaoTableDef::SetName](../Topic/CDaoTableDef::SetName.md)|设置为表的名称。|  
|[CDaoTableDef::SetSourceTableName](../Topic/CDaoTableDef::SetSourceTableName.md)|设置在源数据库指定一个附加的表的名称的值。|  
|[CDaoTableDef::SetValidationRule](../Topic/CDaoTableDef::SetValidationRule.md)|设置验证字段中的数据的值，则已更改或添加到表中。|  
|[CDaoTableDef::SetValidationText](../Topic/CDaoTableDef::SetValidationText.md)|设置指定消息文本您的应用程序显示的值字段，则对象的值不满足指定的验证规则。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CDaoTableDef::m\_pDAOTableDef](../Topic/CDaoTableDef::m_pDAOTableDef.md)|对基础tabledef对象的DAO接口的指针。|  
|[CDaoTableDef::m\_pDatabase](../Topic/CDaoTableDef::m_pDatabase.md)|此表的源数据库。|  
  
## 备注  
 每个DAO数据库对象维护集合，调用TableDefs，包含所有已保存的DAO tabledef对象。  
  
 使用 `CDaoTableDef` 对象，则操作表定义。  例如，您可以：  
  
-   检查所有本地字段和索引结构，附加或外部数据库中的表。  
  
-   调用附加的表的 `SetConnect` 和 `SetSourceTableName` 成员函数，并使用 `RefreshLink` 成员函数更新与附加表的连接。  
  
-   调用 `CanUpdate` 成员函数确定是否可以在此表中编辑字段定义。  
  
-   使用 `GetValidationRule` 和 `SetValidationRule`和 `GetValidationText` 和 `SetValidationText` 成员函数，获取或设置的验证条件。  
  
-   使用 **Open** 成员函数创建表、dynaset\-或快照型 `CDaoRecordset` 对象。  
  
    > [!NOTE]
    >  DAO数据库选件类根据了开放式数据库连接的MFC数据库选件类都一目了然\(odbc）。  所有DAO数据库类名具有“CDao”前缀。  您仍然可以访问使用DAO选件类的ODBC数据源;，因为它们是特定于Microsoft Jet数据库引擎，DAO选件类通常提供优越功能。  
  
### 使用tabledef对象都与现有表使用或创建新表  
  
1.  在所有情况下，请首先构造 `CDaoTableDef` 对象，指向该表所属的 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 对象。  
  
2.  然后根据执行以下操作，您需要:  
  
    -   若要使用现有保存该表，调用tabledef对象的 [打开](../Topic/CDaoTableDef::Open.md) 成员函数，提供所保存的表的名称。  
  
    -   若要创建新表，请调用tabledef对象的 [创建](../Topic/CDaoTableDef::Create.md) 成员函数，提供了表的名称。  调用 [CreateField](../Topic/CDaoTableDef::CreateField.md) 和 [CreateIndex](../Topic/CDaoTableDef::CreateIndex.md) 添加字段和索引到表。  
  
    -   调用 [追加](../Topic/CDaoTableDef::Append.md) 通过追加将保存该表添加到数据库的TableDefs集合。  **Create** 将tabledef到一个打开状态，因此，在调用 **Create** 后不要调用 **Open**。  
  
        > [!TIP]
        >  方便地创建保存的表中创建和存储在数据库中使用Microsoft Access。  然后可以将MFC代码可以打开并使用它们。  
  
 若要使用您已打开或创建的tabledef对象，创建并打开一 `CDaoRecordset` 对象，指定tabledef名称与 **dbOpenTable** 的值在 `nOpenType` 参数。  
  
 在调用 [CDaoRecordset::Open](../Topic/CDaoRecordset::Open.md)时，要使用tabledef对象创建 `CDaoRecordset` 对象，可以创建或上述通常会打开一tabledef，然后构造记录集对象，通过指向您的tabledef对象。  通过的tabledef必须在打开状态。  有关更多信息，请参见选件类 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  
  
 使用完tabledef对象时，请调用 [关闭](../Topic/CDaoRecordset::Close.md) 成员函数;然后销毁tabledef对象。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoTableDef`  
  
## 要求  
 **Header:** afxdao.h  
  
## 请参阅  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDaoDatabase Class](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoRecordset Class](../../mfc/reference/cdaorecordset-class.md)