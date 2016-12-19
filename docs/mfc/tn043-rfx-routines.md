---
title: "TN043：RFX 例程 | Microsoft Docs"
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
  - "RFX"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "记录字段交换 (RFX)"
  - "记录字段交换 (RFX), 体系结构"
  - "TN043"
ms.assetid: f552d0c1-2c83-4389-b472-42c9940aa713
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN043：RFX 例程
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。  因此，某些过程和主题可能已过时或不正确。  要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 此注释说明记录字段交换 \(RFX\) 体系结构。  还描述如何编写 **RFX\_** 过程。  
  
## 记录字段交换概述  
 所有记录集字段完成函数与 C\+\+ 代码。  无特殊的资源或魔术宏。  机制的重点是在每个派生的记录集类必须重写的虚函数。  它始终被找到以此形式：  
  
```  
void CMySet::DoFieldExchange(CFieldExchange* pFX)  
{  
  //{{AFX_FIELD_MAP(CMySet)  
  <recordset exchange field type call>  
  <recordset exchange function call>  
  //}}AFX_FIELD_MAP  
}  
```  
  
 特定格式 AFX 注释允许 ClassWizard 定位和编辑此函数中的代码。  代码与兼容 ClassWizard 应放置在特殊形式注释。  
  
 在上面的示例中，\<recordset\_exchange\_field\_type\_call\> 窗体：  
  
```  
pFX->SetFieldType(CFieldExchange::outputColumn);  
```  
  
 并 \<recordset\_exchange\_function\_call\> 窗体：  
  
```  
RFX_Custom(pFX, "Col2", m_Col2);  
```  
  
 **RFX\_** 大多数函数有三参数如上所述，但一些 \(即  `RFX_Text` 和 `RFX_Binary`\) 具有不同的可选参数。  
  
 **RFX\_** 多个在每个 `DoDataExchange` 可以包含函数。  
  
 对于所有记录集字段交换例程列表参见“afxdb.h”随 MFC。  
  
 调用记录集字段是注册内存位置方式 \(通常存储字段数据成员\) 数据。**CMySet** 类。  
  
## 注释  
 记录集字段函数设计为仅与 `CRecordset` 类一起使用。  这些由任何其他 MFC 类通常不可用。  
  
 初始值数据中标准 C\+\+ 构造函数设置，通常在具有 `//{{AFX_FIELD_INIT(CMylSet)` 和 `//}}AFX_FIELD_INIT` 的注释块。  
  
 每个 **RFX\_** 函数必须支持多种操作，大小从返回字段的已更新状态到存档字段为准备编辑字段。  
  
 `DoFieldExchange` 调用的每个函数 \(例如，`SetFieldNull`\)，`IsFieldDirty`在调用来执行它自己的初始化为 `DoFieldExchange`。  
  
## 它如何工作？  
 不需要了解下面即可使用记录字段交换。  但是，了解这如何在后台工作可帮助您编写自己交换过程。  
  
 `DoFieldExchange` 成员函数非常类似 `Serialize` 成员函数 \(它获取或设置与应用\/或窗体外部 \(在这种情况下从 ODBC 查询结果的列的数据运行\) 从\/至在类的数据成员。  参数 `pFX` 是执行上下文数据交换和参数与 `CArchive` 类似于 `CObject::Serialize`。  `pFX` \( `CFieldExchange` 对象\)。具有操作指示符，类似，`CArchive`，但方向标志的泛化。  RFX 函数。必须支持以下操作：  
  
-   **BindParam** \- 指示应在哪里 ODBC 检索参数数据  
  
-   **BindFieldToColumn** \- 指示 ODBC 不得不检索\/都 outputColumn 数据  
  
-   **Fixup** \- **CString\/CByteArray** 集合长度，设置 NULL 状态位  
  
-   如果值发生变化，因为 AddNew 调用，**MarkForAddNew** \- 标记错误  
  
-   如果值发生变化，因为编辑调用，**MarkForUpdate** \- 标记错误  
  
-   **名称** \- 将字段标记为坏域名。  
  
-   **NameValue** \- 请追加“\<列名 \=\>”?对于字段标记的错误  
  
-   **值** \- 将“?”分隔符，如“”或" "后跟  
  
-   `SetFieldDirty` \- 集合状态位的错误 \(即变化\) 字段  
  
-   `SetFieldNull` \- 集合状态正好一个字段为空值  
  
-   `IsFieldDirty` \- 返回值已更新状态位  
  
-   `IsFieldNull` \- 返回值 null 状态位  
  
-   `IsFieldNullable` \- 返回 true，则表示字段可以为 null 值  
  
-   **StoreField** \- 将字段值  
  
-   **LoadField** \- Reload 存档的字段  
  
-   **GetFieldInfoValue** \- 有关字段的返回常规信息  
  
-   **GetFieldInfoOrdinal** \- 有关字段的返回常规信息  
  
## 用户扩展  
 有多种方法来扩展默认 RFX 机制。  您可以：  
  
-   添加新数据类型。  例如：  
  
    ```  
    CBookmark  
    ```  
  
-   添加新的 RFX\_ 交换过程 \(???\)。  
  
    ```  
    void AFXAPI RFX_Bigint(CFieldExchange* pFX, const char *szName,  
        BIGINT& value);  
    ```  
  
-   具有 `DoFieldExchange` 成员函数有条件地包括附加的 RFX 调用或任何其他的有效 C\+\+ 语句。  
  
    ```  
    while (posExtraFields != NULL)  
    {  
        RFX_Text(pFX, m_listName.GetNext(posExtraFields),   
            m_listValue.GetNext(posExtraValues));  
    }  
    ```  
  
> [!NOTE]
>  此代码不受 ClassWizard 编辑，只应在特定格式注释。  
  
## 编写自定义 RFX  
 若要自己编写自定义提供 RFX 函数，建议要复制现有的 RFX 函数并修改其赋的用途。  选择正确的 RFX 复制可以使这一工作变得更容易。  有些 RFX 函数还应考虑到，在确定哪些复制时的几个属性。  
  
 **RFX\_Long 和 RFX\_Int**:  
 以下是最简单的 RFX 函数。  数据值不需要任何特定说明，这样，数据大小是固定的。  
  
 **RFX\_Single 和 RFX\_Double**:  
 与上面 RFX\_Long 和 RFX\_Int，这些函数是简单的，并可以详尽地利用默认实现。  只有为显式引用时，将在 dbflt.cpp 存储而不是 dbrfx.cpp，但是，启用加载运行时浮点库。  
  
 **RFX\_Text 和 RFX\_Binary**:  
 这两种函数预分配静态缓冲区保存字符串或二进制信息，并且必须注册 ODBC 的 SQLBindCol 这些缓冲区 \(而不是注册 &值。  因此，这两个函数具有许多特定大小写的代码。  
  
 `RFX_Date`:  
 ODBC 返回和时间信息。它们的 TIMESTAMP\_STRUCT 数据结构。  此函数 TIMESTAMP\_STRUCT 动态分配为“代理”发送和接收的日期时间数据。  各操作必须将日期和时间信息。C\+\+ `CTime` 对象和 TIMESTAMP\_STRUCT 代理之间。  这样可大大如果此函数，但是，它是一个很好的示例演示如何为使用代理数据传输。  
  
 `RFX_LongBinary`:  
 决不使用列绑定接收和发送数据的类库 RFX 函数。  此函数在操作链接地址信息时忽略 BindFieldToColumn 操作，并且，分配存储空间保存传入的 SQL\_LONGVARCHAR 或 SQL\_LONGVARBINARY 数据，然后执行 SQLGetData 调用检索值到分配的存储区。  准备将数据值设置回数据源 \(如 NameValue 和操作值\) 时，此函数使用 ODBC 的 DATA\_AT\_EXEC 功能。  参见 [技术说明 45](../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md) SQL\_LONGVARBINARY 和有关使用 SQL\_LONGVARCHARs 一起使用的更多信息。  
  
 当编写自己的 **RFX\_** 函数时，您经常可以使用 **CFieldExchange::Default** 来实现特定操作。  查看默认的实现。相关的操作。  如果它可以在运行操作委托给 **CFieldExchange::Default.**的 **RFX\_** 函数编写您可以看到对的调用在 dbrfx.cpp **CFieldExchange::Default** 的示例  
  
 如果返回错误，RFX 在函数的开头调用 `IsFieldType`，并且立即返回是重要的。  此机制在 **outputColumns**禁止执行的操作参数，反之亦然 \(如调用 **outputColumn**的 **BindParam**。\)  此外，`IsFieldType` 自动记录计数 **outputColumns** \(`m_nFields`\) 和 params \(`m_nParams`\)。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)