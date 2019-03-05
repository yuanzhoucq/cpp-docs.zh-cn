---
title: CDaoFieldInfo 结构
ms.date: 11/04/2016
f1_keywords:
- CDaoFieldInfo
helpviewer_keywords:
- DAO (Data Access Objects), Fields collection
- CDaoFieldInfo structure [MFC]
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
ms.openlocfilehash: a5c4013a323c85ad19a3fade20f76852e053362a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57275137"
---
# <a name="cdaofieldinfo-structure"></a>CDaoFieldInfo 结构

`CDaoFieldInfo`结构包含有关为数据访问对象 (DAO) 定义的字段对象的信息。

## <a name="syntax"></a>语法

```
struct CDaoFieldInfo
{
    CString m_strName;           // Primary
    short m_nType;               // Primary
    long m_lSize;                // Primary
    long m_lAttributes;          // Primary
    short m_nOrdinalPosition;    // Secondary
    BOOL m_bRequired;            // Secondary
    BOOL m_bAllowZeroLength;     // Secondary
    long m_lCollatingOrder;      // Secondary
    CString m_strForeignName;    // Secondary
    CString m_strSourceField;    // Secondary
    CString m_strSourceTable;    // Secondary
    CString m_strValidationRule; // All
    CString m_strValidationText; // All
    CString m_strDefaultValue;   // All
};
```

#### <a name="parameters"></a>参数

*m_strName*<br/>
唯一地命名字段对象。 有关详细信息，请参阅主题 DAO 帮助中的"名称属性"。

*m_nType*<br/>
一个值，指示该字段的数据类型。 有关详细信息，请参阅主题 DAO 帮助中的"类型属性"。 此属性的值可以是以下值之一：

- `dbBoolean` 是/否，TRUE/FALSE 相同

- `dbByte` Byte

- `dbInteger` 短

- `dbLong` 长

- `dbCurrency` 货币;请参阅 MFC 类[COleCurrency](../../mfc/reference/colecurrency-class.md)

- `dbSingle` 单个

- `dbDouble` 双精度

- `dbDate` 日期/时间;请参阅 MFC 类[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)

- `dbText` 文本;请参阅 MFC 类[CString](../../atl-mfc-shared/reference/cstringt-class.md)

- `dbLongBinary` 长二进制文件 （OLE 对象）;您可能想要使用的 MFC 类[CByteArray](../../mfc/reference/cbytearray-class.md)而不是类`CLongBinary`作为`CByteArray`更丰富、 更容易使用。

- `dbMemo` 备注;请参阅 MFC 类 `CString`

- `dbGUID` 是全局唯一标识符/通用唯一标识符与远程过程调用一起使用。 有关详细信息，请参阅主题 DAO 帮助中的"类型属性"。

> [!NOTE]
>  请不要将字符串数据类型用于二进制数据。 这将导致你的数据通过 Unicode/ANSI 转换层，从而导致开销增加和可能是意外的转换传递。

*m_lSize*<br/>
一个值，指示最大大小 （字节） 包含文本或包含文本或数字值的字段对象的固定的大小的 DAO 字段对象。 有关详细信息，请参阅主题 DAO 帮助中的"大小属性"。 大小可以是下列值之一：

|类型|大小(字节)|描述|
|----------|--------------------|-----------------|
|`dbBoolean`|1 个字节|是/否 （等同于 True/False）|
|`dbByte`|1|Byte|
|`dbInteger`|2|整数|
|`dbLong`|4|Long|
|`dbCurrency`|8|货币 ([COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|Single|
|`dbDouble`|8|Double|
|`dbDate`|8|日期/时间 ([COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|文本 ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|长二进制文件 （OLE 对象;[CByteArray](../../mfc/reference/cbytearray-class.md); 而不是使用`CLongBinary`)|
|`dbMemo`|0|备注 ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbGUID`|16|是全局唯一标识符/通用唯一标识符与远程过程调用一起使用。|

*m_lAttributes*<br/>
指定包含 tabledef、 记录集、 querydef 或索引对象的字段对象的特征。 返回的值可以是两个常数，创建使用 c + + 按位 OR sum (**&#124;**) 运算符：

- `dbFixedField` 字段大小被固定的 （默认值为数值字段）。

- `dbVariableField` 字段大小是变量 （仅适用于文本字段）。

- `dbAutoIncrField` 新记录的字段值自动递增到一个唯一的长整数，它不能更改。 仅支持 Microsoft Jet 数据库表。

- `dbUpdatableField` 可以更改字段值。

- `dbDescending` 字段按降序 (Z-A 或 100-0) （仅适用于字段对象中的索引对象的字段集合; 在 MFC 中，对象本身包含在 tabledef 对象的索引） 的顺序。 如果省略此常量，该字段按升序 (A-Z 或 0-100) 顺序 （默认值）。

在检查此属性的设置时，您可以使用 c + + 按位-和运算符 (**&**) 若要测试特定的属性。 当设置多个属性，可以将它们合并与按位 OR 组合的相应常量 (**&#124;**) 运算符。 有关详细信息，请参阅主题 DAO 帮助中的"特性属性"。

*m_nOrdinalPosition*<br/>
一个值，指定要在其中 DAO 字段对象代表要显示相对于其他域的域的数字顺序。 可以设置此属性与[CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。 有关详细信息，请参阅主题 DAO 帮助中的"OrdinalPosition 属性"。

*m_bRequired*<br/>
指示 DAO 字段对象是否需要非 Null 值。 如果此属性为 TRUE，则该字段不允许 Null 值。 如果需要设置为 FALSE，该字段包含 Null 值，以及满足由允许空字符串和 ValidationRule 属性设置指定的条件的值。 有关详细信息，请参阅主题 DAO 帮助中的"所需属性"。 您可以为设置此属性与 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。

*m_bAllowZeroLength*<br/>
指示是否为空字符串 ("") 是具有数据类型为文本或备忘录的 DAO 字段对象的有效值。 如果此属性为 TRUE，则为空字符串是有效的值。 可以将此属性设置为 FALSE，则确保您不能使用空字符串来设置字段的值。 有关详细信息，请参阅主题 DAO 帮助中的"允许空字符串属性"。 您可以为设置此属性与 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。

*m_lCollatingOrder*<br/>
指定以文本字符串比较或排序的排序顺序的序列。 有关详细信息，请参阅主题中的"自定义 Windows 注册表设置的数据访问"DAO 帮助。 返回的可能值的列表，请参阅`m_lCollatingOrder`的成员[CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md)结构。 您可以为设置此属性与 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。

*m_strForeignName*<br/>
一个值，在一个关系指定对应于主表中字段的外部表中的 DAO 字段对象的名称。 有关详细信息，请参阅主题 DAO 帮助中的"ForeignName 属性"。

*m_strSourceField*<br/>
指示 tabledef、 记录集或 querydef 对象包含的 DAO 字段对象的数据的原始源的字段的名称。 此属性指示与字段对象关联的原始字段名称。 例如，可以使用此属性以确定其名称为与基础表中的字段的名称不相关的查询字段中的数据的原始源。 有关详细信息，请参阅 DAO 帮助中的主题"SourceField，SourceTable 属性"。 您可以为设置此属性与 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。

*m_strSourceTable*<br/>
指示 tabledef、 记录集或 querydef 对象包含的 DAO 字段对象的数据的原始源的表的名称。 此属性指示与字段对象关联的原始表名称。 例如，可以使用此属性以确定其名称为与基础表中的字段的名称不相关的查询字段中的数据的原始源。 有关详细信息，请参阅 DAO 帮助中的主题"SourceField，SourceTable 属性"。 您可以为设置此属性与 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。

*m_strValidationRule*<br/>
一个值，用于验证字段中的数据，因为它已更改或添加到表中。 有关详细信息，请参阅主题 DAO 帮助中的"ValidationRule 属性"。 您可以为设置此属性与 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。

Tabledefs 有关的信息，请参阅`m_strValidationRule`的成员[CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md)结构。

*m_strValidationText*<br/>
一个值，指定你的应用程序显示如果 DAO 字段对象的值不符合验证规则 ValidationRule 属性设置指定的消息的文本。 有关详细信息，请参阅主题 DAO 帮助中的"有效性文本属性"。 您可以为设置此属性与 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。

*m_strDefaultValue*<br/>
DAO 字段对象的默认值。 创建一条新记录时，DefaultValue 属性设置将自动输入作为值的字段。 有关详细信息，请参阅主题 DAO 帮助中的"默认值属性"。 您可以为设置此属性与 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。

## <a name="remarks"></a>备注

对主要、 次要和上面所有的引用指示如何通过返回的信息`GetFieldInfo`类中的成员函数[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)， [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)，并[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)。

不由 MFC 类表示的字段对象。 相反，MFC 对象的以下类的 DAO 对象包含的字段对象的集合：[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)， [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)，和[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)。 这些类提供成员函数来访问字段的信息，一些单个项或可以访问它们使用一次性`CDaoFieldInfo`对象通过调用`GetFieldInfo`包含对象的成员函数。

除了用于检查对象属性使用，还可以使用`CDaoFieldInfo`构造在 tabledef 对象中创建新的字段的输入的参数。 更简单的选项可用于此任务中，但如果您希望更精细的控制，可以使用的版本[CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)采用`CDaoFieldInfo`参数。

检索的信息`GetFieldInfo`（的包含字段的类） 的成员函数存储在`CDaoFieldInfo`结构。 调用`GetFieldInfo`其字段集合中存储的字段对象的包含对象的成员函数。 `CDaoFieldInfo` 此外定义了`Dump`成员函数在调试生成。 可以使用`Dump`转储的内容`CDaoFieldInfo`对象。

## <a name="requirements"></a>要求

**标头：** afxdao.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetFieldInfo](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)<br/>
[CDaoRecordset::GetFieldInfo](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)<br/>
[CDaoQueryDef::GetFieldInfo](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)
