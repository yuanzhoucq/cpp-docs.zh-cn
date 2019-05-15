---
title: TN045:为长型 Varchar-varbinary 的 MFC 数据库支持
ms.date: 11/04/2016
helpviewer_keywords:
- TN045
- Varbinary data type
- Varchar data type
ms.assetid: cf572c35-5275-45b5-83df-5f0e36114f40
ms.openlocfilehash: 3e8b356027e5c5b7c604a0354624d9f11e32fb9a
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611052"
---
# <a name="tn045-mfcdatabase-support-for-long-varcharvarbinary"></a>TN045:长 Varchar/Varbinary 的 MFC/数据库支持

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

本说明介绍如何检索和发送 ODBC **SQL_LONGVARCHAR**并**SQL_LONGVARBINARY**数据类型使用 MFC 数据库类。

## <a name="overview-of-long-varcharvarbinary-support"></a>长 Varchar/Varbinary 支持概述

ODBC **SQL_LONG_VARCHAR**并**SQL_LONGBINARY** （此处称为作为长时间的数据列） 的数据类型可以保存大量数据。 有 3 种方法可以处理此数据：

- 将其绑定到`CString` / `CByteArray`。

- 将其绑定到`CLongBinary`。

- 不要将其所有绑定和检索并发送长数据值手动，独立于数据库类。

每三个方法都有优点和缺点。

为参数的查询不支持长数据列。 仅支持为 outputColumns。

## <a name="binding-a-long-data-column-to-a-cstringcbytearray"></a>绑定到 CString/CByteArray 的长整型数据列

优点：

这种方法是很好理解，并使用熟悉的类。 该框架提供了`CFormView`支持`CString`与`DDX_Text`。 你可以自由使用常规字符串或集合的功能`CString`和`CByteArray`类，并且您可以控制分配本地以保存数据值的内存量。 框架维护过程中的字段数据的旧副本`Edit`或`AddNew`函数调用和框架可以自动为您检测数据更改。

> [!NOTE]
>  由于`CString`专为处理字符数据，并`CByteArray`适用于二进制数据，建议将字符数据 (**SQL_LONGVARCHAR**) 到`CString`，和二进制数据 (**SQL_LONGVARBINARY**) 到`CByteArray`。

为函数 RFX`CString`和`CByteArray`具有的其他参数，它允许您重写已分配的内存来存放的数据列检索到的值的默认大小。 请注意以下函数声明中的 nMaxLength 参数：

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

如果检索到的长整型数据列`CString`或`CByteArray`，返回的数据量，默认情况下为 255 个字节的最大值。 超出此限制的任何内容将被忽略。 在这种情况下，框架将引发的异常**AFX_SQL_ERROR_DATA_TRUNCATED**。 幸运的是，您可以显式增加到更高值 nMaxLength 达**MAXINT**。

> [!NOTE]
>  MFC 使用 nMaxLength 的值来设置的本地缓冲区`SQLBindColumn`函数。 这是用于存储数据的本地缓冲区，没有实际影响的 ODBC 驱动程序返回的数据量。 `RFX_Text` 并`RFX_Binary`只能进行一个调用使用`SQLFetch`从后端数据库检索数据。 每个 ODBC 驱动程序可以读取一次返回的数据量上具有不同的限制。 此限制可能会比在设置 nMaxLength，在这种情况下该异常的值更小**AFX_SQL_ERROR_DATA_TRUNCATED**将引发。 在这些情况下，切换到使用`RFX_LongBinary`而不是`RFX_Text`或`RFX_Binary`，以便可以检索所有数据。

将绑定 ClassWizard **SQL_LONGVARCHAR**到`CString`，或**SQL_LONGVARBINARY**到`CByteArray`为您。 如果你想要分配到其中检索长整型数据列超过 255 个字节，然后可以提供 nMaxLength 一个显式值。

当长整型数据列绑定到`CString`或`CByteArray`，更新字段的运行与相同时绑定到 SQL_ 方式**VARCHAR**或 SQL_**VARBINARY**。 期间`Edit`，即可及更高版本进行比较时缓存数据值`Update`调用来检测数据更改值和一组繁琐并相应地为 Null 的列的值。

## <a name="binding-a-long-data-column-to-a-clongbinary"></a>绑定到 CLongBinary 的长整型数据列

如果你的长整型数据的列可能包含更多**MAXINT**个字节的数据，你可能考虑检索到`CLongBinary`。

优点：

这将检索整个长数据列中的，最多可用内存。

缺点：

数据保存在内存中。 这种方法也是成本过高的数据量非常大的。 必须调用`SetFieldDirty`绑定的数据成员，以确保该字段包含在`Update`操作。

如果检索到的长整型数据列`CLongBinary`，数据库类将检查的总大小的长整型数据列，然后分配`HGLOBAL`内存段足以容纳它的整个数据值。 数据库类然后检索到已分配的整个数据值`HGLOBAL`。

如果数据源不能返回长整型数据列的预期的大小，该框架将引发的异常**AFX_SQL_ERROR_SQL_NO_TOTAL**。 如果尝试分配`HGLOBAL`失败，将标准内存引发异常。

将绑定 ClassWizard **SQL_LONGVARCHAR**或**SQL_LONGVARBINARY**到`CLongBinary`为您。 选择`CLongBinary`作为添加成员变量对话框中的变量类型。 然后添加类向导，将`RFX_LongBinary`向调用您`DoFieldExchange`调用并递增绑定字段的总数。

若要更新长时间的数据列的值，首先请确保已分配`HGLOBAL`足够大以保存您的新数据通过调用 **:: GlobalSize**上*m_hData*隶属`CLongBinary`。 如果因过小，释放`HGLOBAL`并分配一个适当的大小。 然后设置*m_dwDataLength*以反映新的大小。

否则为如果*m_dwDataLength*是大小超出了大小的要替换的数据，可以释放并重新分配`HGLOBAL`，或将其分配。 请确保以指示实际使用中的字节数*m_dwDataLength*。

## <a name="how-updating-a-clongbinary-works"></a>如何更新 CLongBinary 工作原理

不需要了解如何更新`CLongBinary`的工作原理，但它可能会很有用，如何将长数据值发送到数据源，例如如果你选择此第三个方法，如下所述。

> [!NOTE]
>  为了使`CLongBinary`字段要包含在更新中，您必须显式调用`SetFieldDirty`的字段。 如果对一个字段，包括将其设置为 Null，进行任何更改必须调用`SetFieldDirty`。 你还必须调用`SetFieldNull`，其中第二个参数是**FALSE**，将标记为具有一个值的字段。

更新时`CLongBinary`字段中，数据库类使用 ODBC 的**DATA_AT_EXEC**机制 (请参阅 ODBC 文档`SQLSetPos`的 rgbValue 参数)。 当该框架准备的 insert 或 update 语句，而不是指向`HGLOBAL`包含的数据*地址*的`CLongBinary`设置为*值*的列相反，并且长度指示器设置为**SQL_DATA_AT_EXEC**。 随后，在 update 语句发送到数据源`SQLExecDirect`将返回**SQL_NEED_DATA**。 这会提醒框架，此列的参数的值是实际的地址`CLongBinary`。 框架将调用`SQLGetData`一次用小缓冲区应为驱动程序返回数据的实际长度。 如果该驱动程序返回二进制大型对象 (BLOB) 的实际长度，MFC 将一样多的空间重新分配所需提取 BLOB。 如果数据源返回**SQL_NO_TOTAL**，指示它无法确定 BLOB 的大小，MFC 将创建较小的块。 默认初始大小为 64 K 和后续块将大小增加一倍;例如，第二个将为 128k，第三个为 256k，依此类推。 初始大小进行配置。

## <a name="not-binding-retrievingsending-data-directly-from-odbc-with-sqlgetdata"></a>未绑定：直接从 ODBC 使用 SQLGetData 检索/发送数据

使用此方法完全绕过数据库类中，并且自己处理的长整型数据列。

优点：

可以缓存数据磁盘如有必要，或确定要检索动态多少数据。

缺点：

别让框架的`Edit`或`AddNew`支持，并且您必须编写代码来执行基本的功能 (`Delete`的工作原理，因为它不是列级别操作)。

在这种情况下，长整型数据列必须是记录集，选择列表中，但应未绑定到框架。 一个方法可以解决这是为了提供通过你自己 SQL 语句`GetDefaultSQL`或者作为 lpszSQL 参数`CRecordset`的`Open`函数，并绑定 RFX_ 函数调用的额外列。 ODBC 需要绑定字段右侧显示的未绑定的字段，因此将未绑定的列添加到选择列表的末尾。

> [!NOTE]
>  由框架未绑定的长整型数据列，因为对它的更改不会处理与`CRecordset::Update`调用。 必须创建并发送所需的 SQL**插入**并**更新**语句自己。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
