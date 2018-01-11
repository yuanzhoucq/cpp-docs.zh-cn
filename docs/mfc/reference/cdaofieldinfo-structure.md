---
title: "CDaoFieldInfo 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CDaoFieldInfo
dev_langs: C++
helpviewer_keywords:
- DAO (Data Access Objects), Fields collection
- CDaoFieldInfo structure [MFC]
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 63fdab9bae7238f427ff2015beffd53570603af4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cdaofieldinfo-structure"></a>CDaoFieldInfo 结构
`CDaoFieldInfo`结构包含的数据访问对象 (DAO) 定义的字段对象有关的信息。  
  
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
 `m_strName`  
 唯一地命名字段对象。 有关详细信息，请参阅主题 DAO 帮助中的"名称属性"。  
  
 `m_nType`  
 一个值，指示该字段的数据类型。 有关详细信息，请参阅主题 DAO 帮助中的"类型属性"。 此属性的值可以是以下项之一：  
  
- **dbBoolean**是/否，与相同**TRUE**/**FALSE**  
  
- **dbByte**字节  
  
- **dbInteger**短  
  
- **dbLong**长  
  
- **dbCurrency**货币; 请参阅 MFC 类[COleCurrency](../../mfc/reference/colecurrency-class.md)  
  
- **dbSingle**单个  
  
- **dbDouble** Double  
  
- **dbDate**日期/时间，请参阅 MFC 类[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)  
  
- **dbText**文本; 请参阅 MFC 类[CString](../../atl-mfc-shared/reference/cstringt-class.md)  
  
- **dbLongBinary**长二进制 （OLE 对象）; 你可能想要使用 MFC 类[CByteArray](../../mfc/reference/cbytearray-class.md)而不是类`CLongBinary`作为`CByteArray`是更丰富、 更轻松地使用。  
  
- **dbMemo**备注，请参阅 MFC 类`CString`  
  
- **dbGUID**全局唯一标识符/全局唯一标识符用于远程过程调用。 有关详细信息，请参阅主题 DAO 帮助中的"类型属性"。  
  
> [!NOTE]
>  不要使用字符串数据类型对二进制数据。 这将导致你的数据来通过 Unicode/ANSI 转换层，从而导致开销增加和可能意外转换。  
  
 *m_lSize*  
 一个值，指示的最大大小，以字节为单位，包含文本或字段对象，其中包含文本或数字值的固定的大小的 DAO 字段对象。 有关详细信息，请参阅主题 DAO 帮助中的"大小属性"。 大小可以是以下值之一：  
  
|类型|大小(字节)|描述|  
|----------|--------------------|-----------------|  
|**dbBoolean**|1 个字节|是/否 （等同于 True/False）|  
|**dbByte**|1|Byte|  
|**dbInteger**|2|整数|  
|**dbLong**|4|Long|  
|**dbCurrency**|8|货币 ([COleCurrency](../../mfc/reference/colecurrency-class.md))|  
|**dbSingle**|4|Single|  
|**dbDouble**|8|Double|  
|**dbDate**|8|日期/时间 ([COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|  
|**dbText**|1 - 255|文本 ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|  
|**dbLongBinary**|0|长二进制文件 （OLE 对象;[CByteArray](../../mfc/reference/cbytearray-class.md); 而不是使用`CLongBinary`)|  
|**dbMemo**|0|备注 ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|  
|**dbGUID**|16|全局唯一标识符/全局唯一标识符用于远程过程调用。|  
  
 `m_lAttributes`  
 指定字段包含的对象由 tabledef、 记录集、 querydef 或索引对象的特性。 返回的值可以是两个常数，创建使用 c + + 按位 OR 的总和 (**&#124;**) 运算符：  
  
- **dbFixedField**字段大小固定 （数字字段的默认值）。  
  
- **dbVariableField**字段大小是变量 （仅适用于文本字段）。  
  
- **dbAutoIncrField**新记录的字段值自动递增到一个唯一的长整数，它不能更改。 仅支持 Microsoft Jet 数据库表。  
  
- **dbUpdatableField**可以更改的字段值。  
  
- **dbDescending**降序进行排序的字段 (Z-A 或 100-0) （仅适用于索引对象的字段集合中; MFC，对象本身包含在 tabledef 对象的索引中的字段对象） 的顺序。 如果省略此常量时，对字段进行排序以升序 (A-Z 或 0-100) 顺序 （默认值）。  
  
 在检查此属性的设置时，你可以使用 c + + 按位-和运算符 (**&**) 来测试特定的属性。 在设置多个属性时，你可以通过将与按位 OR 结合使用的相应常量组合它们 (**&#124;**) 运算符。 有关详细信息，请参阅主题 DAO 帮助中的"特性属性"。  
  
 *m_nOrdinalPosition*  
 一个值，指定要在其中由 DAO 字段对象表示要显示相对于其他字段的字段的数字顺序。 你可以设置此属性与[CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。 有关详细信息，请参阅主题 DAO 帮助中的"OrdinalPosition 属性"。  
  
 `m_bRequired`  
 指示 DAO 字段对象是否需要非 Null 值。 如果此属性为**TRUE**，该字段不允许 Null 值。 如果需要将设为**FALSE**，该字段只能包含 Null 值，以及满足填和 ValidationRule 属性设置指定的条件的值。 有关详细信息，请参阅主题 DAO 帮助中的"所需属性"。 你可以将此属性设置为与 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。  
  
 *m_bAllowZeroLength*  
 指示是否为空字符串 ("") 是具有数据类型为文本或备注的 DAO 字段对象的有效值。 如果此属性为**TRUE**，空字符串是有效的值。 你可以将此属性设置为**FALSE**以确保你不能使用空字符串来设置字段值。 有关详细信息，请参阅主题 DAO 帮助中的"允许空字符串属性"。 你可以将此属性设置为与 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。  
  
 `m_lCollatingOrder`  
 用于字符串比较或排序的文本中指定的排序顺序的序列。 有关详细信息，请参阅"自定义 Windows 注册表设置的数据访问"DAO 帮助中的主题。 返回的可能值的列表，请参阅**m_lCollatingOrder**的成员[CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md)结构。 你可以将此属性设置为与 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。  
  
 `m_strForeignName`  
 一个值，在一个关系，指定 DAO 字段对象对应于主表中一个字段的外部表中的名称。 有关详细信息，请参阅主题 DAO 帮助中的"ForeignName 属性"。  
  
 *m_strSourceField*  
 指示 tabledef、 记录集或 querydef 对象包含的 DAO 字段对象的数据的原始源的字段的名称。 此属性指示与字段对象相关联的原始字段名称。 例如，可以使用此属性以确定其名称为与基础表中的字段的名称不相关的查询字段中的数据的原始源。 有关详细信息，请参阅 DAO 帮助中的主题"SourceField，SourceTable 属性"。 你可以将此属性设置为与 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。  
  
 *m_strSourceTable*  
 指示 tabledef、 记录集或 querydef 对象包含的 DAO 字段对象的数据的原始源的表的名称。 此属性指示与字段对象相关联的原始表名称。 例如，可以使用此属性以确定其名称为与基础表中的字段的名称不相关的查询字段中的数据的原始源。 有关详细信息，请参阅 DAO 帮助中的主题"SourceField，SourceTable 属性"。 你可以将此属性设置为与 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。  
  
 `m_strValidationRule`  
 一个值，验证字段中的数据，因为它已更改或添加到表中。 有关详细信息，请参阅主题 DAO 帮助中的"有效性规则属性"。 你可以将此属性设置为与 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。  
  
 有关 tabledefs 的相关信息，请参阅**m_strValidationRule**的成员[CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md)结构。  
  
 `m_strValidationText`  
 一个值，指定应用程序显示如果 DAO 字段对象的值不满足由 ValidationRule 属性设置指定的验证规则的消息的文本。 有关详细信息，请参阅主题 DAO 帮助中的"有效性文本属性"。 你可以将此属性设置为与 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。  
  
 *m_strDefaultValue*  
 DAO 字段对象的默认值。 创建一条新记录时，DefaultValue 属性设置为自动输入作为值的字段。 有关详细信息，请参阅主题 DAO 帮助中的"DefaultValue 属性"。 你可以将此属性设置为与 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。  
  
## <a name="remarks"></a>备注  
 对主、 辅助数据库，以及所有上面的引用指示如何通过返回的信息`GetFieldInfo`类中的成员函数[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)， [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)，和[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)。  
  
 字段对象不由 MFC 类表示。 相反，基础下面的类的 MFC 对象的 DAO 对象包含的字段对象的集合： [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)， [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)，和[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)。 这些类提供成员函数，以便访问某些单独项的字段信息或可以访问其在一次与`CDaoFieldInfo`对象通过调用`GetFieldInfo`包含对象的成员函数。  
  
 除了其用于检查对象属性，还可以使用`CDaoFieldInfo`构造在 tabledef 中创建新字段的输入的参数。 更简单的选项都可用于此任务中，但如果你想更精细的控制，你可以使用的版本[CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)采用`CDaoFieldInfo`参数。  
  
 检索的信息`GetFieldInfo`（的包含字段的类） 的成员函数将存储在`CDaoFieldInfo`结构。 调用`GetFieldInfo`字段对象存储在其字段集合中的包含对象的成员函数。 `CDaoFieldInfo`此外定义`Dump`成员函数在调试生成。 你可以使用`Dump`以转储的内容`CDaoFieldInfo`对象。  
  
## <a name="requirements"></a>惠?  
 **标头：** afxdao.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetFieldInfo](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)   
 [CDaoRecordset::GetFieldInfo](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)   
 [CDaoQueryDef::GetFieldInfo](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)

