---
title: 'TN053: DAO 的自定义 DFX 例程数据库类 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.dfx
dev_langs:
- C++
helpviewer_keywords:
- MFC, DAO and
- database classes [MFC], DAO
- DAO [MFC], MFC
- DFX (DAO record field exchange) [MFC], custom routines
- TN053
- DAO [MFC], classes
- DFX (DAO record field exchange) [MFC]
- custom DFX routines [MFC]
ms.assetid: fdcf3c51-4fa8-4517-9222-58aaa4f25cac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 47d1c9769055e0ab69f57f58b136b7844cb1f860
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386088"
---
# <a name="tn053-custom-dfx-routines-for-dao-database-classes"></a>TN053：DAO 数据库类的自定义 DFX 例程
> [!NOTE]
>  Visual c + + 环境和向导不支持 DAO （尽管 DAO 类包括并且仍可以使用它们）。 Microsoft 建议你使用[OLE DB 模板](../data/oledb/ole-db-templates.md)或[ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)为新项目。 你只应在维护现有应用程序使用 DAO。  
  
 此技术说明描述的 DAO 记录字段交换 (DFX) 机制。 若要帮助了解 DFX 例程中发生的情况`DFX_Text`函数将作为示例的详细信息中所述。 作为此技术说明的信息的其他源，你可以检查的代码适用于其他各个 DFX 函数。 你可能不需要自定义 DFX 例程通常可能需要自定义 RFX 例程 （与 ODBC 数据库类一起使用）。  
  
 此技术说明包含：  
  
-   DFX 概述  
  
- [示例](#_mfcnotes_tn053_examples)使用 DAO 记录字段交换和动态绑定  
  
- [DFX 的工作原理](#_mfcnotes_tn053_how_dfx_works)  
  
- [自定义 DFX 例程的用途](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)  
  
- [DFX_Text 的详细信息](#_mfcnotes_tn053_details_of_dfx_text)  
  
 **DFX 概述**  
  
 DAO 记录字段交换机制 (DFX) 用于简化的检索和更新数据时使用该过程`CDaoRecordset`类。 使用的数据成员简化该流程`CDaoRecordset`类。 通过从派生`CDaoRecordset`，可以将数据成员添加到派生的类表示表或查询中的每个字段。 此"静态绑定"机制非常简单，但它可能不会所有应用程序选择的数据提取/更新方法。 DFX 检索每个绑定的字段每次更改当前记录。 如果你正在开发的性能敏感型应用程序不需要提取每个字段，货币更改时，"动态绑定"通过`CDaoRecordset::GetFieldValue`和`CDaoRecordset::SetFieldValue`可能选择的数据访问方法。  
  
> [!NOTE]
>  DFX 和动态绑定不会互相排斥，因此可以使用混合使用静态和动态的绑定中。  
  
## <a name="_mfcnotes_tn053_examples"></a> 示例 1-使用的 DAO 记录字段交换仅  
  
 (假定`CDaoRecordset`-派生类`CMySet`尚未打开)  
  
```  
// Add a new record to the customers table  
myset.AddNew();

myset.m_strCustID = _T("MSFT");

myset.m_strCustName = _T("Microsoft");

myset.Update();
```  
  
 **示例 2-使用动态绑定仅**  
  
 (假设使用`CDaoRecordset`类， `rs`，并已打开)  
  
```  
// Add a new record to the customers table  
COleVariant  varFieldValue1 (_T("MSFT"),
    VT_BSTRT);

//Note: VT_BSTRT flags string type as ANSI,
    instead of UNICODE default  
COleVariant  varFieldValue2  (_T("Microsoft"),
    VT_BSTRT);

rs.AddNew();

rs.SetFieldValue(_T("Customer_ID"),
    varFieldValue1);

rs.SetFieldValue(_T("Customer_Name"),
    varFieldValue2);

rs.Update();
```  
  
 **示例 3-使用的 DAO 记录字段交换和动态绑定**  
  
 (假定使用的浏览雇员数据`CDaoRecordset`-派生类`emp`)  
  
```  
// Get the employee's data so that it can be displayed  
emp.MoveNext();

 
// If user wants to see employee's photograph,  
// fetch it  
COleVariant varPhoto;  
if (bSeePicture)  
    emp.GetFieldValue(_T("photo"),
    varPhoto);

 
// Display the data  
PopUpEmployeeData(emp.m_strFirstName,  
    emp.m_strLastName,
    varPhoto);
```  
  
## <a name="_mfcnotes_tn053_how_dfx_works"></a> DFX 的工作原理  
  
 DFX 机制的工作原理类似方式和使用 MFC ODBC 类的记录字段交换 (RFX) 机制。 DFX 和 RFX 的原则是相同，但有许多内部差异。 DFX 函数的设计时，由单个 DFX 例程共享几乎所有代码。 在最高级别 DFX 仅将执行几项操作。  
  
-   DFX 构造 SQL**选择**子句和 SQL**参数**子句，如有必要。  
  
-   DFX 构造 DAO 的使用的绑定结构`GetRows`函数 （稍后将详细介绍）。  
  
-   DFX 管理用于检测已更新的字段 （如果正在使用双缓冲） 的数据缓冲区  
  
-   DFX 管理**NULL**和**DIRTY**状态数组和更新在必要时设置值。  
  
 DFX 核心机制是`CDaoRecordset`派生类的`DoFieldExchange`函数。 此函数将调度到适当的操作类型的各个 DFX 函数的调用。 之前调用`DoFieldExchange`内部的 MFC 函数设置的操作类型。 以下列表显示的各种操作类型和简短描述。  
  
|操作|描述|  
|---------------|-----------------|  
|**AddToParameterList**|生成参数子句|  
|**AddToSelectList**|生成 SELECT 子句|  
|**BindField**|将设置绑定结构|  
|**BindParam**|设置参数值|  
|**修正**|设置 NULL 状态|  
|**AllocCache**|为脏检查分配缓存|  
|**StoreField**|将当前记录保存到缓存|  
|**LoadField**|为成员值的还原缓存|  
|**FreeCache**|释放缓存|  
|`SetFieldNull`|设置字段状态和为 NULL 的值|  
|**MarkForAddNew**|将标记字段脏否则伪 NULL|  
|**MarkForEdit**|标记字段脏如果不匹配缓存|  
|**SetDirtyField**|设置字段值标记为已更新|  
  
 在下一步的部分中，每个操作将会详细说明了为`DFX_Text`。  
  
 若要了解有关 DAO 记录字段交换过程的最重要功能是它使用`GetRows`函数`CDaoRecordset`对象。 DAO`GetRows`函数可通过多种方式在工作。 此技术说明将只简要介绍`GetRows`按原样此技术说明的范围之外。  
  
 DAO`GetRows`可通过多种方式在工作。  
  
-   它可以一次获取多个记录和多个字段的数据。 这允许进行更快的数据访问，处理大型数据结构和为每个字段的相应偏移量的复杂性和每个记录的结构中的数据。 MFC 能不会利用此提取机制的多个记录。  
  
-   另一种方法`GetRows`可以工作是允许程序员可以指定绑定的检索到的数据的一个记录的数据的每个字段的地址。  
  
-   DAO 将还"回调"到调用方的可变长度列以便允许调用方分配的内存。 此第二个功能具有的最小化的数据副本数，以及允许进入的类成员的直接存储数据的优点 (`CDaoRecordset`派生类)。 此第二个机制是 MFC 使用将绑定到数据成员中的方法`CDaoRecordset`派生类。  
  
##  <a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a> 自定义 DFX 例程的用途  
 很明显来自任何 DFX 函数中实现的最重要操作必须能够设置所需的数据结构成功调用此讨论`GetRows`。 有大量的 DFX 函数，也必须支持其他操作，但不为重要或复杂正确准备`GetRows`调用。  
  
 在联机文档中介绍的 DFX 用法。 从根本上来说，有两个要求。 首先，必须将成员添加到`CDaoRecordset`派生类为每个绑定的字段和参数。 以下这`CDaoRecordset::DoFieldExchange`应重写。 请注意该成员的数据类型非常重要。 它应匹配数据库中字段的数据，或至少可转换为该类型。 例如在数据库中，例如一个长整型数值字段始终可以转换为文本并绑定到`CString`成员，但数据库中的文本字段可能不一定转换为数值的表示形式，如长整型，并绑定到长 integer 成员。 DAO 和 Microsoft Jet 数据库引擎负责转换 （而非 MFC）。  
  
##  <a name="_mfcnotes_tn053_details_of_dfx_text"></a> DFX_Text 的详细信息  
 如前所述，阐释 DFX 的工作方式的最好办法是工作讲解了一个示例。 为此目的经过深谙`DFX_Text`工作相当有助于提供 DFX 的至少一个基本的了解。  
  
 **AddToParameterList**  
 此操作生成 SQL**参数**子句 ("`Parameters <param name>, <param type> ... ;`") 所需的 Jet。 每个参数是名为，并键入 （在 RFX 调用中指定）。 请参阅函数**CDaoFieldExchange::AppendParamType**函数以查看各类型的名称。 情况下`DFX_Text`，使用的类型是`text`。  
  
 **AddToSelectList**  
 生成 SQL**选择**子句。 此 DFX 调用指定的列名称只是相当直接方式会追加 ("`SELECT <column name>, ...`")。  
  
 **BindField**  
 而最复杂的操作。 如前文所述这是 DAO 绑定结构由`GetRows`设置。 正如您可以从代码中看到`DFX_Text`的结构中的信息类型包括使用的 DAO 类型 (**DAO_CHAR**或**DAO_WCHAR**的情况下`DFX_Text`)。 此外，使用的绑定类型是还设置。 在前面某一节中`GetRows`已说明只是暂时，但却不足以解释 MFC 使用的绑定的类型始终是直接地址绑定 (**DAOBINDING_DIRECT**)。 此外可变长度列绑定 (如`DFX_Text`)，以便 MFC 可以控制的内存分配，并指定正确的长度的地址使用回调绑定。 这意味着是该 MFC 可以总是判断出 DAO"where"将数据，从而允许直接绑定到成员变量。 绑定结构的其余部分是使用的内存分配回调函数和列绑定 （通过列名称绑定时） 的类型的地址等填充的。  
  
 **BindParam**  
 这是一个简单的操作调用`SetParamValue`与参数成员中指定的参数值。  
  
 **修正**  
 在填充**NULL**的每个字段的状态。  
  
 `SetFieldNull`  
 此操作仅将标记为每个字段状态**NULL**和的成员变量的值设置为**PSEUDO_NULL**。  
  
 **SetDirtyField**  
 调用`SetFieldValue`的每个字段标记为已更新。  
  
 所有剩余操作只需处理使用数据缓存。 缓存的数据是用来进一步简化某些操作的当前记录中的数据的额外缓冲区。 例如，可以自动检测"脏"的字段。 联机文档中所述它可以完全地或在字段级别关闭它们。 缓冲区的实现利用地图。 使用此映射，以匹配数据的"绑定"字段的地址的动态分配副本 (或`CDaoRecordset`派生数据成员)。  
  
 **AllocCache**  
 动态分配的缓存的字段值，并将其添加到代码图。  
  
 **FreeCache**  
 删除缓存的字段的值并将其从映射中删除。  
  
 **StoreField**  
 将当前的字段值复制到数据缓存。  
  
 **LoadField**  
 将缓存的值复制到字段成员。  
  
 **MarkForAddNew**  
 检查当前字段值是否非**NULL**并将其标记脏如有必要。  
  
 **MarkForEdit**  
 将数据缓存与当前字段值进行比较，并将标记已更新，如有必要。  
  
> [!TIP]
>  在标准数据类型的现有 DFX 例程的模型你自定义 DFX 例程。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

