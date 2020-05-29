---
title: TN045：MFC-数据库支持长瓦尔查尔-瓦二进制
ms.date: 11/04/2016
helpviewer_keywords:
- TN045
- Varbinary data type
- Varchar data type
ms.assetid: cf572c35-5275-45b5-83df-5f0e36114f40
ms.openlocfilehash: 55a68ba970d0a26163f426d51818c701c13ed051
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750279"
---
# <a name="tn045-mfcdatabase-support-for-long-varcharvarbinary"></a>TN045：针对长型 Varchar/Varbinary 的 MFC/数据库支持

> [!NOTE]
> 以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

本说明介绍如何使用 MFC 数据库类检索和发送 ODBC **SQL_LONGVARCHAR**和**SQL_LONGVARBINARY**数据类型。

## <a name="overview-of-long-varcharvarbinary-support"></a>长瓦尔查尔/瓦二进制支持概述

ODBC **SQL_LONG_VARCHAR**和**SQL_LONGBINARY**数据类型（此处称为长数据列）可以保存大量数据。 有三种方法可以处理这些数据：

- 绑定到`CString`/`CByteArray`。

- 绑定到`CLongBinary`。

- 完全不要绑定它，并手动检索和发送长数据值，与数据库类无关。

这三种方法各有优缺点。

查询的参数不支持长数据列。 它们仅支持输出列。

## <a name="binding-a-long-data-column-to-a-cstringcbytearray"></a>将长数据列绑定到 CString/CByteArray

优点：

此方法易于理解，并且您使用熟悉的类。 该框架为`CFormView``CString`提供了`DDX_Text`对 的支持。 您具有大量常规字符串或集合功能`CString`和`CByteArray`类，您可以控制在本地分配的内存量以保存数据值。 框架在或`Edit``AddNew`函数调用期间维护字段数据的旧副本，并且框架可以自动检测对数据的更改。

> [!NOTE]
> 由于`CString`用于处理字符`CByteArray`数据，以及处理二进制数据，因此建议您将字符数据 **（SQL_LONGVARCHAR**）`CString`放入 中，并将二进制数据 **（SQL_LONGVARBINARY）** 放入`CByteArray`中。

RFX 函数`CString`，并且`CByteArray`具有一个附加参数，允许您覆盖已分配内存的默认大小，以保存数据列的检索值。 请注意以下函数声明中的 nMaxLength 参数：

```cpp
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

如果将长数据列检索到`CString`或`CByteArray`中，默认情况下，返回的最大数据量为 255 字节。 除此以外的任何内容都将被忽略。 在这种情况下，框架将AFX_SQL_ERROR_DATA_TRUNCATED**引发异常。** 幸运的是，您可以显式将 nMaxLength 增加到更大的值，最高为**MAXINT**。

> [!NOTE]
> MFC 使用 nMaxLength 的值来设置`SQLBindColumn`函数的本地缓冲区。 这是用于存储数据的本地缓冲区，实际上不会影响 ODBC 驱动程序返回的数据量。 `RFX_Text`并`RFX_Binary`仅进行一次调用`SQLFetch`，用于从后端数据库检索数据。 每个 ODBC 驱动程序对可在单个提取中返回的数据量有不同的限制。 此限制可能比 nMaxLength 中设置的值小得多，在这种情况下，将引发**异常AFX_SQL_ERROR_DATA_TRUNCATED。** 在这些情况下，切换到使用`RFX_LongBinary`而不是`RFX_Text`或`RFX_Binary`这样，以便检索所有数据。

ClassWizard 会将**SQL_LONGVARCHAR**绑定到`CString`，或将**SQL_LONGVARBINARY**绑定`CByteArray`到 如果要将超过 255 个字节分配给检索长数据列，则可以为 nMaxLength 提供显式值。

当长数据列绑定`CString`到 或`CByteArray`时，更新字段的工作方式与绑定到SQL_**VARCHAR**或SQL_**VARBINARY**时的工作方式相同。 在`Edit`期间，数据值将缓存离开，并在调用时`Update`进行比较，以检测对数据值的更改并适当地设置列的"脏"和"空"值。

## <a name="binding-a-long-data-column-to-a-clongbinary"></a>将长数据列绑定到 CLongBinary

如果长数据列可能包含更多**MAXINT**字节的数据，则可能需要考虑将其检索到 中`CLongBinary`。

优点：

这将检索整个长数据列，最多可访问内存。

缺点：

数据存储在内存中。 对于大量数据来说，这种方法的成本也高得令人望而却步。 您必须调用`SetFieldDirty`绑定的数据成员，以确保该字段包含在`Update`操作中。

如果将长数据列检索到 中`CLongBinary`，数据库类将检查长数据列的总大小，然后分配足够大的`HGLOBAL`内存段以容纳整个数据值。 然后，数据库类将整个数据值检索到分配的`HGLOBAL`中。

如果数据源无法返回长数据列的预期大小，则框架将AFX_SQL_ERROR_SQL_NO_TOTAL**引发异常。** 如果尝试分配 失败`HGLOBAL`，将引发标准内存异常。

ClassWizard 会`CLongBinary`为您绑定**SQL_LONGVARCHAR**或**SQL_LONGVARBINARY。** 在`CLongBinary`"添加成员变量"对话框中选择"变量类型"。 然后，ClassWizard 将`RFX_LongBinary`呼叫添加到您的`DoFieldExchange`呼叫，并增加绑定字段的总数。

`HGLOBAL`要更新长数据列值，首先通过在`CLongBinary`m_hData 成员上调用 **：： GlobalSize，** 确保已分配的值足够大以*m_hData*保存新数据。 如果太小，释放 并`HGLOBAL`分配一个适当的大小。 然后设置*m_dwDataLength*以反映新大小。

否则，如果*m_dwDataLength*大于要替换的数据的大小，则可以释放并重新分配 ，`HGLOBAL`也可以将其保留为分配。 请确保指示*m_dwDataLength*中实际使用的字节数。

## <a name="how-updating-a-clongbinary-works"></a>更新 CLongBinary 的工作原理

不必了解更新`CLongBinary`如何工作，但如果选择下面介绍的第三种方法，则了解如何向数据源发送长数据值的示例可能很有用。

> [!NOTE]
> 为了在更新中`CLongBinary`包含字段，必须显式调用`SetFieldDirty`该字段。 如果对字段进行任何更改（包括将其设置为 Null），则必须调用`SetFieldDirty`。 您还必须调用`SetFieldNull`，第二个参数为**FALSE，** 以将字段标记为具有值。

更新`CLongBinary`字段时，数据库类使用 ODBC**的DATA_AT_EXEC**机制（请参阅有关`SQLSetPos`rgbValue 参数的 ODBC 文档）。 当框架准备插入或更新语句时，`HGLOBAL`而不是指向包含数据，而是将 的地址*address*`CLongBinary`设置为列*的值*，长度指示器设置为**SQL_DATA_AT_EXEC**。 稍后，当更新语句发送到数据源时，`SQLExecDirect`将返回**SQL_NEED_DATA**。 这将提醒框架，此列的参数值实际上是 的地址`CLongBinary`。 框架使用小`SQLGetData`缓冲区调用一次，期望驱动程序返回数据的实际长度。 如果驱动程序返回二进制大型对象（BLOB）的实际长度，MFC 将重新分配获取 BLOB 所需的空间。 如果数据源返回**SQL_NO_TOTAL**，指示它无法确定 BLOB 的大小，则 MFC 将创建较小的块。 默认初始大小为 64K，后续块的大小将是两倍;例如，第二个将是 128K，第三个是 256K，等等。 初始大小是可配置的。

## <a name="not-binding-retrievingsending-data-directly-from-odbc-with-sqlgetdata"></a>不绑定：使用 SQLGetData 直接从 ODBC 检索/发送数据

使用此方法，您可以完全绕过数据库类，并自行处理长数据列。

优点：

如有必要，可以将数据缓存到磁盘，也可以动态决定要检索的数据量。

缺点：

您没有得到框架`Edit`或`AddNew`支持，您必须自己编写代码以执行基本功能（`Delete`虽然确实工作，因为它不是列级操作）。

在这种情况下，长数据列必须位于记录集的选择列表中，但不应受框架的约束。 这样做的一种方法是通过`GetDefaultSQL`或作为 lpszSQL 参数`CRecordset``Open`提供您自己的 SQL 语句，而不是将附加列与RFX_函数调用绑定。 ODBC 要求未绑定字段显示在绑定字段的右侧，因此将未绑定列或列添加到选择列表的末尾。

> [!NOTE]
> 由于长数据列不受框架的约束，因此不会通过`CRecordset::Update`调用处理对它的更改。 您必须自己创建并发送所需的 SQL **INSERT**和**更新**语句。

## <a name="see-also"></a>请参阅

[技术说明（按编号）](../mfc/technical-notes-by-number.md)<br/>
[按类别分类的技术说明](../mfc/technical-notes-by-category.md)
