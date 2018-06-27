---
title: TN045： 针对长型 Varchar Varbinary 的 MFC 数据库支持 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.data
dev_langs:
- C++
helpviewer_keywords:
- TN045
- Varbinary data type
- Varchar data type
ms.assetid: cf572c35-5275-45b5-83df-5f0e36114f40
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1454be53dce60f5e84e03b895575c480d972c4c0
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956862"
---
# <a name="tn045-mfcdatabase-support-for-long-varcharvarbinary"></a>TN045：针对长型 Varchar/Varbinary 的 MFC/数据库支持
> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 本说明介绍如何检索和发送 ODBC **SQL_LONGVARCHAR**和**SQL_LONGVARBINARY**数据类型使用 MFC 数据库类。  
  
## <a name="overview-of-long-varcharvarbinary-support"></a>长型 Varchar/Varbinary 支持概述  
 ODBC **SQL_LONG_VARCHAR**和**SQL_LONGBINARY** （此处称为作为长时间的数据列） 的数据类型可以容纳大量数据。 有三种方法可以处理此数据：  
  
-   将其绑定到`CString` / `CByteArray`。  
  
-   将其绑定到`CLongBinary`。  
  
-   不要将其所有绑定和检索和发送的长整型数据值手动，独立于数据库类。  
  
 每三个方法都有优点和缺点。  
  
 参数的查询不支持的长整型数据列。 它们仅支持 outputColumns。  
  
## <a name="binding-a-long-data-column-to-a-cstringcbytearray"></a>绑定到 CString/CByteArray 的长整型数据列  
 优点：  
  
 这种方法是易于理解，并可与熟悉的类。 该框架提供`CFormView`支持`CString`与`DDX_Text`。 有大量的与常规的字符串或集合功能`CString`和`CByteArray`类，并且你可以控制分配本地来保存的数据值的内存量。 框架维护过程中的字段数据的旧副本`Edit`或`AddNew`函数调用和框架可以自动检测为你的数据的更改。  
  
> [!NOTE]
>  由于`CString`旨在用于对字符数据处理和`CByteArray`用于处理二进制数据，建议你将字符数据 (**SQL_LONGVARCHAR**) 到`CString`，和二进制数据 (**SQL_LONGVARBINARY**) 到`CByteArray`。  
  
 RFX 函数以`CString`和`CByteArray`具有的其他自变量可以在其中你重写已分配的内存来存放的数据列检索到的值的默认大小。 请注意以下函数声明中的 nMaxLength 自变量：  
  
```  
void AFXAPI RFX_Text(CFieldExchange* pFX,
    const char *szName,  
    CString& value,
    int nMaxLength = 255,
    int nColumnType = 
    SQL_VARCHAR);

 
void AFXAPI RFX_Binary(CFieldExchange* pFX,
    const char *szName,   
    CByteArray& value,
    int nMaxLength = 255);
```  
  
 如果检索到的长整型数据列`CString`或`CByteArray`，最多可以返回的数据量，默认情况下是 255 个字节。 除此之外的任何内容将被忽略。 在这种情况下，框架将引发异常**AFX_SQL_ERROR_DATA_TRUNCATED**。 幸运的是，你可以显式增加到更高值 nMaxLength 达**MAXINT**。  
  
> [!NOTE]
>  MFC 使用 nMaxLength 的值来设置的本地缓冲区`SQLBindColumn`函数。 这是存储的数据的本地缓冲区，并不实际影响 ODBC 驱动程序返回的数据量。 `RFX_Text` 和`RFX_Binary`只进行了上面某调用使用`SQLFetch`从后端数据库检索数据。 每个 ODBC 驱动程序可以读取一次返回的数据量上具有的不同限制。 此限制可能会比在设置 nMaxLength，在这种情况下该异常的值小得多**AFX_SQL_ERROR_DATA_TRUNCATED**将引发。 在这些情况下，切换到使用`RFX_LongBinary`而不是`RFX_Text`或`RFX_Binary`，以便可以检索所有数据。  
  
 将绑定 ClassWizard **SQL_LONGVARCHAR**到`CString`，或**SQL_LONGVARBINARY**到`CByteArray`为你。 如果你想要分配到检索的长整型数据列超过 255 个字节，然后可以只提供 nMaxLength 显式值。  
  
 当长整型数据列绑定到`CString`或`CByteArray`，更新字段的运行一样的当绑定到 SQL_ 方式**VARCHAR**或 SQL_**VARBINARY**。 期间`Edit`，离开及更高版本进行比较时缓存的数据值`Update`调用以检测更改的数据值和一组 Dirty 并相应地 Null 的列的值。  
  
## <a name="binding-a-long-data-column-to-a-clongbinary"></a>绑定到 CLongBinary 的长整型数据列  
 如果你的长整型数据列可能包含更多**MAXINT**字节的数据，你可能考虑检索到`CLongBinary`。  
  
 优点：  
  
 检索整个长数据列中的，最大可用内存。  
  
 缺点：  
  
 数据保存在内存中。 此方法也是有关的数据量非常大成本过高。 必须调用`SetFieldDirty`对于绑定的数据成员，以确保字段包括在`Update`操作。  
  
 如果检索到的长整型数据列`CLongBinary`，数据库类将检查的总大小的长整型数据列，然后分配`HGLOBAL`内存段大到足以保留它的整个数据值。 数据库类然后检索到该分配的整个数据值`HGLOBAL`。  
  
 如果数据源不能返回的长整型数据列的预期的大小，框架将引发异常**AFX_SQL_ERROR_SQL_NO_TOTAL**。 如果尝试分配`HGLOBAL`失败，会引发一个标准内存异常。  
  
 将绑定 ClassWizard **SQL_LONGVARCHAR**或**SQL_LONGVARBINARY**到`CLongBinary`为你。 选择`CLongBinary`作为添加成员变量对话框中的变量类型。 然后，ClassWizard 将添加`RFX_LongBinary`调用你`DoFieldExchange`调用和递增绑定字段的总数。  
  
 若要更新长数据列的值，首先请确保已分配`HGLOBAL`足够大，能够容纳新数据，通过调用 **:: GlobalSize**上*m_hData*的成员`CLongBinary`。 如果太小，释放`HGLOBAL`并分配一个适当的大小。 然后设置*m_dwDataLength*以反映新的大小。  
  
 否则为如果*m_dwDataLength*大于大小的要替换的数据，你可以释放和重新分配`HGLOBAL`，或将其分配保留。 请确保以指示中实际使用的字节数*m_dwDataLength*。  
  
## <a name="how-updating-a-clongbinary-works"></a>如何更新 CLongBinary 工作原理  
 不需要了解如何更新`CLongBinary`工作原理，但它可能会有用如何长整型数据值发送到数据源，例如如果你选择了此第三个方法，如下所述。  
  
> [!NOTE]
>  为了使`CLongBinary`字段要包括在更新中，你必须明确地调用`SetFieldDirty`的字段。 如果进行任何更改的字段，包括将其设置为 Null，则必须调用`SetFieldDirty`。 你还必须调用`SetFieldNull`，第二个参数为**FALSE**，将标记为具有一个值的字段。  
  
 在更新时`CLongBinary`字段中，数据库类使用 ODBC 的**DATA_AT_EXEC**机制 (请参阅有关 ODBC 文档`SQLSetPos`的 rgbValue 自变量)。 当框架准备 insert 或 update 语句，而不是指向`HGLOBAL`包含数据，*地址*的`CLongBinary`被设置为*值*的列相反，设置为的长度指示符**SQL_DATA_AT_EXEC**。 随后，在 update 语句发送到数据源，`SQLExecDirect`将返回**SQL_NEED_DATA**。 这会提醒 framework 此列的参数的值是实际的地址`CLongBinary`。 框架调用`SQLGetData`一次使用一个较小的缓冲区，应为要返回的数据的实际长度的驱动程序。 如果驱动程序返回二进制大型对象 (BLOB) 的实际长度，则 MFC 将一样多的空间重新分配进行提取 BLOB 所需。 如果数据源返回**SQL_NO_TOTAL**，指示它无法确定 BLOB 的大小，MFC 将创建较小的块。 默认初始大小为 64 K 和后续块将双精度的大小;例如，第二个将为 128k，第三个为 256k，依此类推。 初始大小是可配置。  
  
## <a name="not-binding-retrievingsending-data-directly-from-odbc-with-sqlgetdata"></a>不绑定： 检索/直接从发送数据与 SQLGetData ODBC  
 使用此方法您完全绕过数据库类中，并自行处理长整型数据列。  
  
 优点：  
  
 你可以缓存数据磁盘如有必要，或者决定动态数据量来检索。  
  
 缺点：  
  
 你不会获得框架的`Edit`或`AddNew`支持，并且你必须编写代码以执行基本功能 (`Delete`的工作原理，因为它不是列级别操作)。  
  
 在这种情况下，长整型数据列必须是记录集，选择列表中，但应未绑定到由框架。 一种办法这是为了提供通过你自己 SQL 语句`GetDefaultSQL`或者作为 lpszSQL 参数`CRecordset`的`Open`函数，并不将绑定的 RFX_ 函数调用的额外列。 ODBC 需要绑定字段右侧显示的未绑定的字段，因此将未绑定的列添加到选择列表的末尾。  
  
> [!NOTE]
>  由框架未绑定的长整型数据列，因为对它的更改不会处理与`CRecordset::Update`调用。 你必须创建并发送所需的 SQL**插入**和**更新**语句自己。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

