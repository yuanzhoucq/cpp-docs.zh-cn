---
title: 'TN043: RFX 例程 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- RFX
dev_langs:
- C++
helpviewer_keywords:
- RFX (record field exchange), architecture
- TN043
- RFX (record field exchange)
ms.assetid: f552d0c1-2c83-4389-b472-42c9940aa713
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f6a46867edc4ea2f314c167da4215b869af3ab17
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="tn043-rfx-routines"></a>TN043：RFX 例程
> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 本说明介绍记录字段交换 (RFX) 体系结构。 它还介绍了如何编写**RFX_** 过程。  
  
## <a name="overview-of-record-field-exchange"></a>记录字段交换的概述  
 C + + 代码完成所有记录集字段函数。 没有任何特殊的资源或神奇的宏。 机制的核心是必须在每个派生的记录集类中重写虚函数。 始终，则该文件位于此窗体：  
  
```  
void CMySet::DoFieldExchange(CFieldExchange* pFX)  
{ *//{{AFX_FIELD_MAP(CMySet)  
 <recordset exchange field type call>  
 <recordset exchange function call> *//}}AFX_FIELD_MAP  
}  
```  
  
 特殊格式 AFX 注释允许 ClassWizard 定位和编辑此函数中的代码。 与 ClassWizard 不兼容的代码应放置在特殊格式注释之外中。  
  
 在上面的示例中，< recordset_exchange_field_type_call > 采用的形式：  
  
```  
pFX->SetFieldType(CFieldExchange::outputColumn);
```  
  
 和 < recordset_exchange_function_call > 采用的形式：  
  
```  
RFX_Custom(pFX, "Col2",
    m_Col2);
```  
  
 大多数**RFX_** 函数具有三个自变量，如上所示，但某些 (例如`RFX_Text`和`RFX_Binary`) 具有其他可选自变量。  
  
 多个**RFX_** 可能包括在每个`DoDataExchange`函数。  
  
 请参阅 afxdb.h 有关的所有记录集字段交换例程 MFC 提供的列表。  
  
 记录集字段调用是一种注册的内存位置 （通常是数据成员） 的方式，用于存储字段数据的**CMySet**类。  
  
## <a name="notes"></a>说明  
 记录集字段函数旨在仅适用于`CRecordset`类。 它们不是通常可供任何其他 MFC 类。  
  
 在标准 c + + 中的构造函数，通常一个块以与中设置的数据的初始值`//{{AFX_FIELD_INIT(CMylSet)`和`//}}AFX_FIELD_INIT`注释。  
  
 每个**RFX_** 函数必须支持各种操作，范围从返回到存档中准备用于编辑字段的字段的字段的更新状态。  
  
 每个调用的函数`DoFieldExchange`(例如`SetFieldNull`， `IsFieldDirty`)，没有围绕对调用其自身初始化`DoFieldExchange`。  
  
## <a name="how-does-it-work"></a>它是如何工作的  
 不需要了解以下以使用记录字段交换。 但是，了解此后台进行的活动的工作原理将帮助你编写自己的 exchange 过程。  
  
 `DoFieldExchange`非常相似，成员函数即将`Serialize`成员函数 — 它负责获取或设置数据向/从外部窗体 （在此事例的列从 ODBC 查询的结果） 从/到类中的成员数据。 `pFX`参数是执行数据交换的上下文，它是类似于`CArchive`参数`CObject::Serialize`。 `pFX` (`CFieldExchange`对象) 具有操作标记，它是相似，但的泛化`CArchive`方向标志。 RFX 函数可能需要支持以下操作：  
  
- **BindParam** -指示 ODBC 应在其中检索参数数据  
  
- **BindFieldToColumn** -指示其中 ODBC 必须检索/存款 outputColumn 数据  
  
- **修正**-设置**CString/CByteArray**长度设置为 NULL 状态位  
  
- **MarkForAddNew** -标记脏如果值已更改，因为 AddNew 调用  
  
- **MarkForUpdate** -标记脏如果值已更改，因为编辑调用  
  
- **名称**-追加标记为已更新的字段的字段名称  
  
- **名称值**-追加"\<列名称 > ="标记为已更新的字段  
  
- **值**-追加""跟分隔符，如 '，' 或 '  
  
- `SetFieldDirty` -设置状态位脏 （即已更改） 字段  
  
- `SetFieldNull` -设置状态位，该值指示字段的 null 值  
  
- `IsFieldDirty` -返回脏状态位值  
  
- `IsFieldNull` -返回状态 null 位值  
  
- `IsFieldNullable` -返回 TRUE，如果字段可以保存 NULL 值  
  
- **StoreField** -存档字段值  
  
- **LoadField** -重新加载存档字段值  
  
- **GetFieldInfoValue** -返回的字段上的常规信息  
  
- **GetFieldInfoOrdinal** -返回的字段上的常规信息  
  
## <a name="user-extensions"></a>用户扩展  
 有多种方法来扩展默认 RFX 机制。 你可以  
  
-   添加新的数据类型。 例如：  
  
 ```  
    CBookmark 
 ```  
  
-   添加新的 exchange 过程 (RFX_)。  
  
 ```  
    void AFXAPI RFX_Bigint(CFieldExchange* pFX,
    const char *szName,  
    BIGINT& value);

 ```  
  
-   具有`DoFieldExchange`成员函数有条件地包括其他 RFX 调用或任何其他有效的 c + + 语句。  
  
 ```  
    while (posExtraFields != NULL)  
 {  
    RFX_Text(pFX,
    m_listName.GetNext(posExtraFields),   
    m_listValue.GetNext(posExtraValues));

 }  
 ```  
  
> [!NOTE]
>  此类代码的 ClassWizard 无法编辑，应仅在特殊格式注释之外使用。  
  
## <a name="writing-a-custom-rfx"></a>编写自定义 RFX  
 若要编写自己的自定义 RFX 函数，但还是建议你复制现有 RFX 函数，并将它修改为自己的意图。 选择要复制右 RFX 可以使你的作业要容易得多。 某些 RFX 函数具有一些在决定要将复制时，应考虑到的唯一属性。  
  
 **RFX_Long 和 RFX_Int**:  
 这些是最简单的 RFX 函数。 数据值不需要任何特殊的解释，并且为固定的数据大小。  
  
 **RFX_Single 和 RFX_Double**:  
 如 RFX_Long 和 RFX_Int 上述，这些函数很简单，并可以广泛使用的默认实现。 它们存储在 dbflt.cpp 而不是 dbrfx.cpp，但是，若要启用加载运行时仅当在显式引用时浮点库。  
  
 **RFX_Text 和 RFX_Binary**:  
 这两个函数预分配静态缓冲区以保存字符串/二进制文件的信息，并必须注册这些缓冲区 ODBC SQLBindCol 而不是注册 （&） 值。 因此，这两个函数具有大量的特殊情况代码。  
  
 `RFX_Date`：  
 ODBC 返回自己 TIMESTAMP_STRUCT 数据结构中的日期和时间信息。 此函数动态分配 TIMESTAMP_STRUCT 作为代理用于发送和接收日期时间数据。 各种操作必须使用 c + + 之间传输的日期和时间信息`CTime`对象和 TIMESTAMP_STRUCT 代理。 这将增加复杂性此函数有相当大，但它是如何使用代理服务器进行数据转换的一个很好示例。  
  
 `RFX_LongBinary`：  
 这是唯一的类库不使用列绑定来接收和发送数据的 RFX 函数。 此函数将忽略 BindFieldToColumn 操作而是在修正操作时，分配的存储空间来容纳传入的 SQL_LONGVARCHAR 或 SQL_LONGVARBINARY 数据，然后执行 SQLGetData 呼叫将检索到的已分配存储的值。 在准备将发送回数据源 （如名称和值的操作） 的数据值时，此函数将使用 ODBC 的 DATA_AT_EXEC 功能。 请参阅[技术说明 45](../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)有关使用 SQL_LONGVARBINARY 和 SQL_LONGVARCHARs 的详细信息。  
  
 编写你自己时**RFX_** 函数，你通常将能够使用**CFieldExchange::Default**来实现对指定的操作。 查看操作的默认实现。 如果它执行该操作将你编写你**RFX_** 函数可以委托到**CFieldExchange::Default。** 你可以看到的调用的示例**CFieldExchange::Default** dbrfx.cpp 中  
  
 务必要调用`IsFieldType`开头的你 RFX 函数，并且如果它返回 FALSE，则立即返回。 此机制会让参数从正在执行的操作**outputColumns**，反之亦然 (如调用**BindParam**上**outputColumn**)。 此外，`IsFieldType`自动将跟踪的数**outputColumns** (`m_nFields`) 以及参数 (`m_nParams`)。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

