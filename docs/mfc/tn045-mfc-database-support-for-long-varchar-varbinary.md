---
title: "TN045：针对长型 Varchar/Varbinary 的 MFC/数据库支持 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TN045"
  - "Varbinary 数据类型"
  - "Varchar 数据类型"
ms.assetid: cf572c35-5275-45b5-83df-5f0e36114f40
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN045：针对长型 Varchar/Varbinary 的 MFC/数据库支持
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。  因此，某些过程和主题可能已过时或不正确。  要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 使用 MFC 数据库类，此注释说明如何检索和发送 ODBC **SQL\_LONGVARCHAR** 和一个 **SQL\_LONGVARBINARY** 数据类型。  
  
## 长 Varchar\/Varbinary 支持大纲显示  
 ODBC **SQL\_LONG\_VARCHAR** 和一个 **SQL\_LONGBINARY** 数据类型 \(称为此处长数据列\) 可以保存巨额数据。  可以处理此数据的 3 种方法：  
  
-   绑定到 `CString`\/`CByteArray`。  
  
-   将其绑定到 `CLongBinary`。  
  
-   请勿将其绑定并请勿手动检索并不发送长数据值，数据库类无关。  
  
 三种方法中的每一个都有自己的优点和缺点。  
  
 长数据没有为列对查询的参数支持。  对 outputColumns 仅支持。  
  
## 绑定长数据列。CString\/CByteArray  
 优点：  
  
 此方法很简单，了解您熟悉，并与类一起使用。  框架为 `CString` 提供 `CFormView`。支持 `DDX_Text`。  您有许多与 `CString` 和 `CByteArray` 类的一般字符串或集合功能，并且，您能够控制内存分配的数量在本地表示数据值。  在 **编辑** 或 `AddNew` 函数调用中，维护字段数据框架旧副本，并且，框架可以自动检测对数据的更改时的。  
  
> [!NOTE]
>  由于 `CString` 为处理的处理字符数据和 `CByteArray` 设计二进制数据，建议您将字符数据 \(**SQL\_LONGVARCHAR**\) 到 `CString`和二进制数据 \(**SQL\_LONGVARBINARY**\) 到 `CByteArray`。  
  
 `CString` 和 `CByteArray` 中 RFX 函数具有允许重写分配内存的默认大小表示数据列检索的值的其他参数。  注意以下函数声明的 nMaxLength 参数：  
  
```  
void AFXAPI RFX_Text(CFieldExchange* pFX, const char *szName,  
    CString& value, int nMaxLength = 255, int nColumnType =  
    SQL_VARCHAR);  
  
void AFXAPI RFX_Binary(CFieldExchange* pFX, const char *szName,   
    CByteArray& value,int nMaxLength = 255);  
```  
  
 如果检索长数据列到 `CString` 或 `CByteArray`，最大值返回的数据量。是，默认情况下，255 字节。  任何忽略本之外。  在这种情况下，则框架将引发 **AFX\_SQL\_ERROR\_DATA\_TRUNCATED**异常。  不过，您可以显式 nMaxLength 增加到最大值，与 **MAXINT**。  
  
> [!NOTE]
>  MFC 使用 **SQLBindColumn** 函数 nMaxLength 值设置的本地缓冲区。  这是数据存储的本地缓冲区，并且实际上不影响 ODBC 驱动程序返回的数据量。  `RFX_Text` 和 `RFX_Binary` 仅调用一次调用 **SQLFetch** 使用从后端数据库中检索数据。  每 ODBC 驱动程序在这些在一次获取可以返回的数量不同的绑定数据。  在异常情况下，**AFX\_SQL\_ERROR\_DATA\_TRUNCATED** 将会引发此限制。nMaxLength 小于设置的可能值。  在这种情况下，对使用 `RFX_LongBinary` 开关的而不是 `RFX_Text` 或 `RFX_Binary`，以便所有数据来检索。  
  
 ClassWizard 将绑定到 `CString`或 **SQL\_LONGVARBINARY** 设置为 **SQL\_LONGVARCHAR** 的 `CByteArray`。  如果要将多您检索长数据列的 255 字节，则可以提供 nMaxLength 的显式值。  
  
 在长数据列绑定到 `CString` 或 `CByteArray`，更新工作字段数据，当绑定到 SQL\_**VARCHAR** 或 SQL\_**VARBINARY**。  在 **编辑**中，那么，当调用 **更新** 检测到数据值的更改以及正确时，将列的错误值和空数据值将缓存和的比较。  
  
## 绑定长数据列。CLongBinary  
 如果长度的数据列可能包含更多字节 **MAXINT** 数据，则可能应考虑检索到 `CLongBinary`。  
  
 优点：  
  
 检索这整个长度的数据列，直到活动内存。  
  
 缺点：  
  
 数据在内存保持。  此方法对于大量数据也是高成本。  必须调用绑定的数据成员 `SetFieldDirty` 可以确保字段在 **更新** 操作中。  
  
 如果检索长数据列到数据库，`CLongBinary`类会检查长数据列的总大小，则分配足够大 `HGLOBAL` 内存段保存为整个数据值。  数据库类将整个数据检索值分配到的 `HGLOBAL`。  
  
 如果数据源未能返回长数据列的预期大小，框架将引发异常。**AFX\_SQL\_ERROR\_SQL\_NO\_TOTAL**。  如果尝试将 `HGLOBAL` 分配内存失败，标准异常。  
  
 ClassWizard 将 **SQL\_LONGVARCHAR** 或 **SQL\_LONGVARBINARY** 绑定对的 `CLongBinary`。  变量作为 Select `CLongBinary` 输入添加成员变量"对话框。  ClassWizard 将添加 `RFX_LongBinary` 调用添加到 `DoFieldExchange` 调用并将绑定字段的总数。  
  
 若要更新长数据列值，请先确保分配的 `HGLOBAL` 是否足够大以通过对 `CLongBinary`调用 `m_hData` 的 **::GlobalSize** 成员保存新数据。  如果是太小，请释放 `HGLOBAL` 并将适当的大小。  再以反映新的范围的 `m_dwDataLength`。  
  
 否则，如果 `m_dwDataLength` 大于，则替换数据的大小，您可以发布并重新指派 `HGLOBAL`，或者将它分配。  确保表示在 `m_dwDataLength`实际上字节数。  
  
## CLongBinary 更新工作原理  
 了解不必要的更新 `CLongBinary` 的工作方式，但可能很有用，例如有关如何将长数据值添加到数据源，因此，如果您选择第三，下述方法。  
  
> [!NOTE]
>  为了在更新可以包括的 `CLongBinary` 字段中，必须显式调用字段的 `SetFieldDirty`。  如果您对字段的所有更改，包括设置为 Null，则仍必须调用 `SetFieldDirty`。  还必须调用 `SetFieldNull`，并且第二个参数是 **FALSE**字段，标记为有值。  
  
 当更新 `CLongBinary` 字段，数据库类使用 ODBC 的 **DATA\_AT\_EXEC** 机制时 \(请参见上 rgbValue 参数 **SQLSetPos** 的 ODBC 文档\)。  当框架准备时插入或更新语句，而不是指向 `HGLOBAL` 包含数据，`CLongBinary` 的 *地址* 设置为列中的 *值* 和长度标志设置为 **SQL\_DATA\_AT\_EXEC**。  之后，更新语句，当发送给数据源，将 **SQLExecDirect** 返回 **SQL\_NEED\_DATA**。  此通知框架 param 的该列的值实际上是 `CLongBinary`的地址。  框架的一次调用 **SQLGetData** 使用一小缓冲区，驱动程序希望返回数据的实际长度。  如果您的驱动返回程序二进制大对象 \(BLOB\) 的实际长度，MFC 需要重新分配同一多空间提取 BLOB。  如果数据源返回 **SQL\_NO\_TOTAL**，指示它无法确定 BLOB 的大小，将 MFC 创建较小的块。  默认是首字母大小 64K，后面的块是双重范围；例如，第二个是 128K，第三列的宽度为 256K，依此类推。  初始范围是可配置的。  
  
## 不绑定：数据检索的发送\/直接从使用 SQLGetData 的 ODBC  
 此方法可完全跳过数据库类和事务使用长数据列。  
  
 优点：  
  
 如果必要，可以缓存数据到磁盘，或者决定动态检索的数据量。  
  
 缺点：  
  
 未获取框架的 **编辑** 或 `AddNew` 支持，因此，您必须编写代码执行基本功能 \(**删除** 内工作，因为它不是列级操作\)。  
  
 在这种情况下，长时间的数据行必须在记录集中 SELECT 列表，但是，不应绑定到由框架。  做到这一点的一种方法是将自己的 SQL 提供语句通过 `GetDefaultSQL` 或作为参数。lpszSQL `CRecordset`**打开** 函数而绑定的额外列的 RFX\_ 函数调用。  ODBC 要求未绑定的字段中限制的字段右侧显示，因此，未绑定的列添加到的末尾。选择列表。  
  
> [!NOTE]
>  由于长数据列不是框架绑定，则的更改将不会处理 `CRecordset::Update` 调用。  必须创建和发送需的 SQL **INSERT** 和 **UPDATE** 语句。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)