---
title: "TN053：DAO 数据库类的自定义 DFX 例程 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.dfx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "自定义 DFX 例程 [C++]"
  - "DAO [C++], 类"
  - "DAO [C++], MFC"
  - "数据库类 [C++], DAO"
  - "DFX（DAO 记录字段交换）[C++]"
  - "DFX（DAO 记录字段交换）[C++], 自定义例程"
  - "MFC [C++], DAO 和"
  - "TN053"
ms.assetid: fdcf3c51-4fa8-4517-9222-58aaa4f25cac
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# TN053：DAO 数据库类的自定义 DFX 例程
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  从 Visual C\+\+ .NET 起，Visual C\+\+ 环境和向导不再支持 DAO（不过提供了 DAO 类，仍可供您使用）。  Microsoft 建议对新项目使用 [OLE DB 模板](../data/oledb/ole-db-templates.md) 或 [ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)。  DAO 只应用于维护现有的应用程序。  
  
 此技术说明描述 DAO 记录字段交换 \(DFX\) 机制。  若要帮助了解 DFX 在例程时，`DFX_Text` 函数将详细说明作为示例。  作为附加的信息源。此方法声明，可以检查代码的其他各个 DFX 函数。  与您通常可能不需要自定义例程 DFX，如可能需要自定义例程 RFX \(使用 ODBC 数据库类\)。  
  
 此技术声明一：  
  
-   DFX 概述  
  
-   使用 DAO 记录字段交换和动态绑定的[示例](#_mfcnotes_tn053_examples)  
  
-   [DFX 如何工作](#_mfcnotes_tn053_how_dfx_works)  
  
-   [哪些自定义例程 DFX](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)  
  
-   [DFX\_Text 详细信息](#_mfcnotes_tn053_details_of_dfx_text)  
  
 **DFX 概述**  
  
 DAO 记录字段交换机制 \(DFX\) 用于简化过程检索并更新数据，当使用 `CDaoRecordset` 类时。  使用 `CDaoRecordset` 类的数据成员，但简化。  通过从 `CDaoRecordset`派生，您可以添加数据成员为表示表或查询的派生类的每个字段。  此“静态”绑定机制是简单的，但是，它可能不是数据获取\/更新选项方式的所有应用程序。  每当当前记录发生更改，DFX 检索每个绑定字段。  如果开发不需要提取每个性能敏感的应用程序，则更改货币时，“动态绑定”通过 `CDaoRecordset::GetFieldValue` 和 `CDaoRecordset::SetFieldValue` 可以是数据访问选定方法。  
  
> [!NOTE]
>  DFX 和动态绑定不互相排斥，因此，可以使用静态和动态绑定的混合使用。  
  
 **示例 \- 对 DAO 只用于的记录字段交换**  
  
 \(假定 `CDaoRecordset` 派生类已经打开的 `CMySet` \)  
  
```  
// Add a new record to the customers table  
myset.AddNew();  
myset.m_strCustID = _T("MSFT");  
myset.m_strCustName = _T("Microsoft");  
myset.Update();  
```  
  
 **示例 2 \- 对仅动态绑定的使用**  
  
 使用 `CDaoRecordset` 类，`rs`\(，假设，并已打开\)  
  
```  
// Add a new record to the customers table  
COleVariant  varFieldValue1 ( _T("MSFT"), VT_BSTRT );  
//Note: VT_BSTRT flags string type as ANSI, instead of UNICODE default  
COleVariant  varFieldValue2  (_T("Microsoft"), VT_BSTRT );  
rs.AddNew();  
rs.SetFieldValue(_T("Customer_ID"), varFieldValue1);  
rs.SetFieldValue(_T("Customer_Name"), varFieldValue2);  
rs.Update();  
```  
  
 **示例 3 \- 对 DAO 记录字段交换和动态绑定的使用**  
  
 \(假定具有浏览 `CDaoRecordset`的雇员数据派生类 `emp`\)  
  
```  
// Get the employee's data so that it can be displayed  
emp.MoveNext();  
  
// If user wants to see employee's photograph,  
// fetch it  
COleVariant varPhoto;  
if (bSeePicture)  
   emp.GetFieldValue(_T("photo"), varPhoto);  
  
// Display the data  
PopUpEmployeeData(emp.m_strFirstName,  
    emp.m_strLastName, varPhoto);  
```  
  
 **DFX 如何工作**  
  
 DFX 机制工作到 MFC ODBC 使用的记录字段交换 \(RFX\) 机制相似的类。  RFX 和 DFX 原则是相同的，但有许多内部差异。  DFX 的函数在此设计所有代码实际上由单个的 DFX 例程共享。  在最上层的 DFX 只执行一些事件。  
  
-   DFX 如有必要，构造 SQL **SELECT** 子句和 SQL **参数** 子句。  
  
-   DAO 的 DFX 构造函数使用 `GetRows` 的约束结构 \(更多在之后\)。  
  
-   DFX 管理使用的数据缓冲区检测错误的字段 \(如果使用双缓冲。\)  
  
-   DFX 如果需要管理状态和设置数组，**NULL** 和 **DIRTY** 值。更新。  
  
 核心 DFX 机制中心为 `CDaoRecordset` 派生类的 `DoFieldExchange` 函数。  此函数将调用相应的操作类型的单个的 DFX 函数。  在调用 `DoFieldExchange` 之前设置内部 MFC 函数操作类型。  下表显示各种操作类型和简要说明。  
  
|Operation|说明|  
|---------------|--------|  
|**AddToParameterList**|子句生成参数|  
|**AddToSelectList**|生成选定子句|  
|**BindField**|设置绑定结构|  
|**BindParam**|设置参数值|  
|**链接地址信息**|集使状态无效|  
|**AllocCache**|分配错误的检查的缓存|  
|**StoreField**|保存当前记录到缓存中|  
|**LoadField**|还原缓存为成员值|  
|**FreeCache**|版本缓存|  
|`SetFieldNull`|字段设置 NULL 的状态 & 值|  
|**MarkForAddNew**|标记已更新字段，即使不是假空|  
|**MarkForEdit**|如果不与缓存，标记已更新字段|  
|**SetDirtyField**|设置标记为坏标记的字段|  
  
 在下一部分，各个操作为 `DFX_Text`是更详细说明。  
  
 若要了解有关的最重要的功能 DAO 记录字段交换过程是使用 `CDaoRecordset` 对象的 `GetRows` 函数。  DAO `GetRows` 工作函数可以有多种方式。  此技术声明简单仅描述 `GetRows`，它不在范围此技术声明外部。  
  
 DAO `GetRows` 可以使用了几种方法。  
  
-   可以一次获取多个日志和数据多个字段。  这样操作的问题的更快的数据访问大型数据结构并相应的偏移量。的每个字段和数据记录每个结构中。  MFC 不利用此多个记录以提取的机制。  
  
-   `GetRows` 可以起作用的另一种方式是使程序员为每个字段的数据检索的记录的指定绑定地址。  
  
-   DAO 也将“调用”调用方为可变长度的列以授予调用方分配内存。  第二个函数具有最小化次数、复制数据以及允许直接优点到数据存储类 \(派生自 `CDaoRecordset` 类\) 的成员。  第二种机制是 MFC 使用方法绑定到 `CDaoRecordset` 派生类的数据成员。  
  
##  <a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a> 哪些自定义例程 DFX  
 它从本讨论不同的 DFX 在所有函数实现的最重要的操作必须是具备设置必需数据结构成功调用 `GetRows`。  有很多其他操作 DFX 函数必须支持，但无同样关键或复杂性。正确对 `GetRows` 调用做准备。  
  
 使用 DFX 在联机文档中描述。  实质上，有两个要求。  首先，成员必须添加到每个绑定字段和参数的 `CDaoRecordset` 派生类。  此 `CDaoRecordset::DoFieldExchange` 后应重写。  注意成员的数据类型是非常重要的。  应该从匹配字段的数据的数据库中或至少可转换为该类型。  例如在数据库的数值范围，例如长时间的整数，始终可以将文本和限制为 `CString` 成员，即，但数据库的文本字段可以无需转换为数值表示形式，如长整数和边界为长整数成员。  DAO 和 Microsoft Jet 数据库引擎负责将运行 MFC \(而不是\)。  
  
##  <a name="_mfcnotes_tn053_details_of_dfx_text"></a> DFX\_Text 详细信息  
 如上所述，最佳方式解释 DFX 如何工作是通过工作示例。  因此查看 `DFX_Text` internals 应非常好工作提供帮助使用 DFX 的有基本的了解。  
  
 **AddToParameterList**  
 此运算生成 Jet \("`Parameters <param name>, <param type> ... ;`"\) 需要的 SQL **参数** 子句。  每个参数被命名和类型化 \(外接 RFX 调用中指定\)。  参见函数 **CDaoFieldExchange::AppendParamType** 函数以查看各个类型的名称。  对于 `DFX_Text`，使用的类型为 `text`。  
  
 **AddToSelectList**  
 生成 SQL **SELECT** 子句。  这相当简单的，因为调用 DFX 指定列名追加"`SELECT <column name>, ...`"\)。  
  
 **BindField**  
 最复杂操作。  如上所述这是绑定结构的 DAO 使用由 `GetRows` 设置的。  您可以从 `DFX_Text` 的代码查看信息类型结构中包括 DAO 类型使用了 \(**DAO\_CHAR** 或 **DAO\_WCHAR** \(对于 `DFX_Text`\)。  此外，使用的绑定类型。  在早期的 `GetRows` 节仅简要介绍了，但说明就足够了 MFC 使用的绑定类型总是直接地址的绑定 \(**DAOBINDING\_DIRECT**\)。  附加为可变长度的列绑定 \(如 `DFX_Text`\) 绑定回调使用，使 MFC 能够控制内存分配正确和指定长度的地址。  这意味着是该 MFC 能够始终调用 DAO“一”，从而允许将数据直接绑定到中的成员变量。  绑定结构的其余部分填充与内存分配回调函数和绑定列类型地址的内容 \(由绑定列名\)。  
  
 **BindParam**  
 这是调用具有参数中成员指定的参数值 `SetParamValue` 的简单操作。  
  
 **Fixup**  
 填充每个字段的 **NULL** 状态。  
  
 `SetFieldNull`  
 此操作只指示每个字段状态并将成员变量为 **NULL** 值为 **PSEUDO\_NULL**。  
  
 **SetDirtyField**  
 调用每字段标记的错误的 `SetFieldValue`。  
  
 所有剩余的操作只处理数据缓存。  数据缓存是的额外数据的缓冲区。用于确定功能更为简单的当前记录的。  例如，“能自动检测错误”的字段。  如联机文档所述它能被关闭在完全或优先级别。  缓冲区实现使用的映射。  此映射用于进行数据的动态分配的副本“绑定”字段 \(或 `CDaoRecordset` 派生的数据成员的地址。\)  
  
 **AllocCache**  
 动态分配缓存值的并将其添加到映射。  
  
 **FreeCache**  
 缓存删除的字段并映射从移除。  
  
 **StoreField**  
 复制当前字段值到数据缓存。  
  
 **LoadField**  
 缓存的值复制到字段成员。  
  
 **MarkForAddNew**  
 如果当前字段值，如果需要，非**NULL** 并将其标记为错误检查。  
  
 **MarkForEdit**  
 如有必要，对与数据缓存的当前和错误值的标记。  
  
> [!TIP]
>  模型对现有的 DFX 例程的 DFX 自定义例程标准数据类型。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)