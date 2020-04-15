---
title: CDaoFieldInfo 结构
ms.date: 09/17/2019
f1_keywords:
- CDaoFieldInfo
helpviewer_keywords:
- DAO (Data Access Objects), Fields collection
- CDaoFieldInfo structure [MFC]
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
ms.openlocfilehash: 9466386fefc6e5ab8fcf89bf497c1d5219e3e807
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368399"
---
# <a name="cdaofieldinfo-structure"></a>CDaoFieldInfo 结构

该`CDaoFieldInfo`结构包含有关为数据访问对象 （DAO） 定义的字段对象的信息。

通过 Office 2013 支持 DAO。 DAO 3.6 是最终版本，它被视为过时版本。

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
唯一地命名字段对象。 有关详细信息，请参阅 DAO 帮助中的主题"名称属性"。

*m_nType*<br/>
指示字段数据类型的值。 有关详细信息，请参阅 DAO 帮助中的主题"类型属性"。 此属性的值可以是以下值之一：

- `dbBoolean`是/否，与 TRUE/FALSE 相同

- `dbByte`字节

- `dbInteger`短

- `dbLong`长

- `dbCurrency`货币;请参阅 MFC 类[COle 货币](../../mfc/reference/colecurrency-class.md)

- `dbSingle`单

- `dbDouble`双

- `dbDate`日期/时间;请参阅 MFC 类[COleDatetime](../../atl-mfc-shared/reference/coledatetime-class.md)

- `dbText`文本;请参阅 MFC 类[CString](../../atl-mfc-shared/reference/cstringt-class.md)

- `dbLongBinary`长二进制（OLE 对象）;您可能希望使用 MFC 类[CByteArray](../../mfc/reference/cbytearray-class.md)而不是类`CLongBinary`，`CByteArray`因为更丰富、更易于使用。

- `dbMemo`备忘录;请参阅 MFC 类`CString`

- `dbGUID`与远程过程调用一起使用的全局唯一标识符/通用唯一标识符。 有关详细信息，请参阅 DAO 帮助中的主题"类型属性"。

> [!NOTE]
> 不要对二进制数据使用字符串数据类型。 这将导致数据通过 Unicode/ANSI 翻译层，从而导致开销增加，并可能导致意外的翻译。

*m_lSize*<br/>
指示包含文本或包含文本或数值的字段对象的固定大小的 DAO 字段对象的最大大小（以字节为单位）的值。 有关详细信息，请参阅 DAO 帮助中的主题"大小属性"。 大小可以是以下值之一：

|类型|大小(字节)|说明|
|----------|--------------------|-----------------|
|`dbBoolean`|1 字节|是/否（与真/假相同）|
|`dbByte`|1|Byte|
|`dbInteger`|2|Integer|
|`dbLong`|4|Long|
|`dbCurrency`|8|货币 （[COle 货币](../../mfc/reference/colecurrency-class.md)）|
|`dbSingle`|4|Single|
|`dbDouble`|8|Double|
|`dbDate`|8|日期/时间 （[COleDatetime](../../atl-mfc-shared/reference/coledatetime-class.md)）|
|`dbText`|1 - 255|文本 （[CString](../../atl-mfc-shared/reference/cstringt-class.md)）|
|`dbLongBinary`|0|长二进制（OLE 对象;[CBytearray](../../mfc/reference/cbytearray-class.md);使用而不是`CLongBinary`。|
|`dbMemo`|0|备忘录 （[CString](../../atl-mfc-shared/reference/cstringt-class.md)）|
|`dbGUID`|16|与远程过程调用一起使用的全局唯一标识符/通用唯一标识符。|

*m_lAttributes*<br/>
指定表def、记录集、查询def或索引对象中包含的字段对象的特征。 返回的值可以是这些常量的总和，这些常量是使用C++位或 （**&#124;**） 运算符创建的：

- `dbFixedField`字段大小是固定的（数字字段的默认值）。

- `dbVariableField`字段大小是可变的（仅限文本字段）。

- `dbAutoIncrField`新记录的字段值将自动递增为无法更改的唯一长整数。 仅支持 Microsoft Jet 数据库表。

- `dbUpdatableField`可以更改字段值。

- `dbDescending`字段按降序（Z - A 或 100 - 0）顺序排序（仅适用于索引对象的字段集合中的字段对象;在 MFC 中，索引对象本身包含在 tabledef 对象中）。 如果省略此常量，则字段按升序（A - Z 或 0 - 100）顺序排序（默认值）。

检查此属性的设置时，可以使用C++位 - AND 运算符 （**&**） 来测试特定属性。 设置多个属性时，可以通过将适当的常量与位 OR （**&#124;**） 运算符组合来组合它们。 有关详细信息，请参阅 DAO 帮助中的主题"属性属性"。

*m_nOrdinalPosition*<br/>
指定希望 DAO 字段对象表示的字段相对于其他字段显示的数字顺序的值。 您可以使用[CDaoTableDef 设置此属性：创建字段](../../mfc/reference/cdaotabledef-class.md#createfield)。 有关详细信息，请参阅 DAO 帮助中的主题"位置属性"。

*m_bRequired*<br/>
指示 DAO 字段对象是否需要非 Null 值。 如果此属性为 TRUE，则该字段不允许 Null 值。 如果"必需"设置为 FALSE，则该字段可以包含 Null 值以及满足"允许零长度"和"验证规则"属性设置指定的条件的值。 有关详细信息，请参阅 DAO 帮助中的主题"必需属性"。 您可以使用[CDaoTableDef：：createField](../../mfc/reference/cdaotabledef-class.md#createfield)为表def设置此属性。

*m_bAllowZeroLength*<br/>
指示空字符串 （""） 是否是具有文本或备忘录数据类型的 DAO 字段对象的有效值。 如果此属性为 TRUE，则空字符串是有效的值。 可以将此属性设置为 FALSE，以确保不能使用空字符串来设置字段的值。 有关详细信息，请参阅 DAO 帮助中的主题"允许零长度属性"。 您可以使用[CDaoTableDef：：createField](../../mfc/reference/cdaotabledef-class.md#createfield)为表def设置此属性。

*m_lCollatingOrder*<br/>
指定文本中排序顺序的顺序，用于字符串比较或排序。 有关详细信息，请参阅 DAO 帮助中的主题"为数据访问自定义 Windows 注册表设置"。 有关返回的可能值的列表，请参阅`m_lCollatingOrder`[CDao 数据库信息](../../mfc/reference/cdaodatabaseinfo-structure.md)结构的成员。 您可以使用[CDaoTableDef：：createField](../../mfc/reference/cdaotabledef-class.md#createfield)为表def设置此属性。

*m_strForeignName*<br/>
在关系中指定与主表中的字段对应的外表中的 DAO 字段对象的名称的值。 有关详细信息，请参阅 DAO 帮助中的"外名属性"主题。

*m_strSourceField*<br/>
指示字段的名称，该字段是表def、记录集或查询def对象中包含的 DAO 字段对象的原始数据源。 此属性指示与字段对象关联的原始字段名称。 例如，可以使用此属性确定查询字段中的数据的原始源，其名称与基础表中的字段名称无关。 有关详细信息，请参阅 DAO 帮助中的主题"源字段、源表属性"。 您可以使用[CDaoTableDef：：createField](../../mfc/reference/cdaotabledef-class.md#createfield)为表def设置此属性。

*m_strSourceTable*<br/>
指示表的名称，该表是表def、记录集或查询def对象中包含的 DAO 字段对象的原始数据源。 此属性指示与字段对象关联的原始表名称。 例如，可以使用此属性确定查询字段中的数据的原始源，其名称与基础表中的字段名称无关。 有关详细信息，请参阅 DAO 帮助中的主题"源字段、源表属性"。 您可以使用[CDaoTableDef：：createField](../../mfc/reference/cdaotabledef-class.md#createfield)为表def设置此属性。

*m_strValidationRule*<br/>
在字段中更改或添加到表中的数据时验证数据的值。 有关详细信息，请参阅 DAO 帮助中的主题"验证规则属性"。 您可以使用[CDaoTableDef：：createField](../../mfc/reference/cdaotabledef-class.md#createfield)为表def设置此属性。

有关表defs的相关信息，请参阅`m_strValidationRule`[CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md)结构的成员。

*m_strValidationText*<br/>
如果 DAO 字段对象的值不符合验证规则属性设置指定的验证规则，则指定应用程序显示的消息文本的值。 有关详细信息，请参阅 DAO 帮助中的主题"验证文本属性"。 您可以使用[CDaoTableDef：：createField](../../mfc/reference/cdaotabledef-class.md#createfield)为表def设置此属性。

*m_strDefaultValue*<br/>
DAO 字段对象的默认值。 创建新记录时，默认值属性设置将自动输入为字段的值。 有关详细信息，请参阅 DAO 帮助中的主题"默认值属性"。 您可以使用[CDaoTableDef：：createField](../../mfc/reference/cdaotabledef-class.md#createfield)为表def设置此属性。

## <a name="remarks"></a>备注

`GetFieldInfo`对上述主要、次要和全部的引用指示成员函数如何返回[CDaoTableDef、CDaoQueryDef](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)和[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)中的成员函数。

字段对象不由 MFC 类表示。 相反，以下类 MFC 对象的基础 DAO 对象包含字段对象的集合[：CDaoTableDef、CDaoRecordset](../../mfc/reference/cdaotabledef-class.md)和[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)。 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 这些类提供成员函数以访问字段信息的一些单个项，或者您可以通过调用包含对象`CDaoFieldInfo``GetFieldInfo`的成员函数同时使用对象访问它们。

除了用于检查对象属性外，您还可以使用`CDaoFieldInfo`构造输入参数以在 tabledef 中创建新字段。 更简单的选项可用于此任务，但如果需要更精细的控制，可以使用[CDaoTableDef：：createField](../../mfc/reference/cdaotabledef-class.md#createfield)采用`CDaoFieldInfo`参数的版本。

`GetFieldInfo`成员函数（包含字段的类）检索的信息存储在`CDaoFieldInfo`结构中。 调用包含`GetFieldInfo`对象的成员函数，其中字段集合中存储字段对象。 `CDaoFieldInfo`还在调试生成中`Dump`定义成员函数。 可以使用`Dump`转储`CDaoFieldInfo`对象的内容。

## <a name="requirements"></a>要求

**标题：** afxdao.h

## <a name="see-also"></a>另请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef：获取菲尔德信息](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)<br/>
[CDaoRecordset：获取菲尔德信息](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)<br/>
[CDaoQueryDef：获取菲尔德信息](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)
