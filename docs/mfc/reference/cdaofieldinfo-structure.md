---
title: "CDaoFieldInfo 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Fields collection
- CDaoFieldInfo structure
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 15db0c56480dfefb9fc8806c08596e37c7d38eb2
ms.lasthandoff: 02/24/2017

---
# <a name="cdaofieldinfo-structure"></a>CDaoFieldInfo 结构
`CDaoFieldInfo`结构包含有关数据访问对象 (DAO) 定义的字段对象的信息。  
  
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
 一个值，指示该字段的数据类型。 有关详细信息，请参阅主题 DAO 帮助中的"类型属性"。 此属性的值可以是以下项之一︰  
  
- **dbBoolean** Yes/No 相同**TRUE**/**FALSE**  
  
- **dbByte**字节  
  
- **dbInteger**短  
  
- **dbLong**长  
  
- **dbCurrency**货币，请参阅 MFC 类[COleCurrency](../../mfc/reference/colecurrency-class.md)  
  
- **dbSingle**单个  
  
- **dbDouble** Double  
  
- **dbDate**日期/时间，请参阅 MFC 类[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)  
  
- **dbText**文本; 请参阅 MFC 类[CString](../../atl-mfc-shared/reference/cstringt-class.md)  
  
- **dbLongBinary**长二进制 （OLE 对象）; 您可能想要使用的 MFC 类[CByteArray](../../mfc/reference/cbytearray-class.md)而不是类`CLongBinary`作为`CByteArray`更丰富、 更容易使用。  
  
- **dbMemo**备注，请参阅 MFC 类`CString`  
  
- **dbGUID**全局唯一标识符/通用唯一标识符用于远程过程调用。 有关详细信息，请参阅主题 DAO 帮助中的"类型属性"。  
  
> [!NOTE]
>  不要使用字符串数据类型为二进制数据。 这将导致您的数据以通过 Unicode/ANSI 转换层，从而提高了系统开销和可能是意外的转换。  
  
 *m_lSize*  
 一个值，指示最大大小 （字节） 包含文本或包含文本或数字值的字段对象的固定的大小的 DAO 字段对象。 有关详细信息，请参阅主题 DAO 帮助中的"大小属性"。 大小可以是下列值之一︰  
  
|类型|大小(字节)|说明|  
|----------|--------------------|-----------------|  
|**dbBoolean**|1 个字节|是/否 （等同于 True/False）|  
|**dbByte**|1|字节|  
|**dbInteger**|2|整数|  
|**dbLong**|4|Long|  
|**dbCurrency**|8|货币 ([COleCurrency](../../mfc/reference/colecurrency-class.md))|  
|**dbSingle**|4|Single|  
|**dbDouble**|8|Double|  
|**dbDate**|8|日期/时间 ([COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|  
|**dbText**|1 - 255|文本 ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|  
|**dbLongBinary**|0|长二进制文件 （OLE 对象;[CByteArray](../../mfc/reference/cbytearray-class.md); 而不是使用`CLongBinary`)|  
|**dbMemo**|0|备注 ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|  
|**dbGUID**|16|是全局唯一标识符/通用唯一标识符用于远程过程调用。|  
  
 `m_lAttributes`  
 指定的字段对象 tabledef、 记录集、 querydef 或索引对象包含的特性。 返回的值可以是两个常数，使用 c + + 创建的按位 OR sum (**|**) 运算符︰  
  
- **dbFixedField**字段大小固定的 （默认值为数值字段）。  
  
- **dbVariableField**字段大小是变量 （仅适用于文本字段）。  
  
- **dbAutoIncrField**新记录的字段值自动递增到一个唯一的长整数，它不能更改。 仅支持 Microsoft Jet 数据库表。  
  
- **dbUpdatableField**可更改字段值。  
  
- **dbDescending**对字段进行排序以降序 (Z-A 或 100-0) （仅适用于字段对象字段集合中的索引对象; 在 MFC 中，对象本身包含在 tabledef 对象的索引） 的顺序。 如果省略此常量，该字段按升序 (A-Z 或 0-100) 顺序 （默认值）。  
  
 在检查此属性的设置时，您可以使用 c + + 按位-和运算符 (**&**) 若要测试对特定的属性。 在设置多个属性时，可以将这些组合与位或组合的相应常量 (**|**) 运算符。 有关详细信息，请参阅主题 DAO 帮助中的"特性属性"。  
  
 *m_nOrdinalPosition*  
 一个值，指定要在其中 DAO field 对象代表要显示相对于其他域的域的数字顺序。 您可以设置此属性与[CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。 有关详细信息，请参阅主题 DAO 帮助中的"OrdinalPosition 属性"。  
  
 `m_bRequired`  
 指示是否 DAO field 对象需要非 Null 值。 如果此属性为**TRUE**，该字段不允许 Null 值。 如果所需的设置为**FALSE**，该字段只能包含 Null 值，以及满足由填和 ValidationRule 属性设置指定的条件的值。 有关详细信息，请参阅主题 DAO 帮助中的"所需属性"。 您可以为设置此属性与 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。  
  
 *m_bAllowZeroLength*  
 指示是否为空字符串 ("") 数据类型为文本或 Memo DAO 字段将是有效值。 如果此属性为**TRUE**，空字符串是有效的值。 可以将此属性设置为**FALSE**以确保您不能使用空字符串来设置字段的值。 有关详细信息，请参阅主题 DAO 帮助中的"允许空字符串属性"。 您可以为设置此属性与 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。  
  
 `m_lCollatingOrder`  
 用于字符串比较或排序的文本中指定的排序顺序的序列。 有关详细信息，请参阅"自定义 Windows 注册表设置为数据访问"DAO 帮助中的主题。 返回的可能值的列表，请参阅**m_lCollatingOrder**的成员[CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md)结构。 您可以为设置此属性与 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。  
  
 `m_strForeignName`  
 一个值，在关系中，指定对应于主表中一个字段的外部表中的 DAO 字段对象的名称。 有关详细信息，请参阅主题 DAO 帮助中的"ForeignName 属性"。  
  
 *m_strSourceField*  
 指示 tabledef、 记录集或 querydef 对象包含的 DAO 字段对象的数据的原始源的字段的名称。 此属性指示与字段对象相关联的原始字段名称。 例如，可以使用此属性以确定其名称为与基础表中的字段的名称不相关的查询字段中的数据的原始源。 有关详细信息，请参阅 DAO 帮助中的主题"SourceField，SourceTable 属性"。 您可以为设置此属性与 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。  
  
 *m_strSourceTable*  
 指示 tabledef、 记录集或 querydef 对象包含的 DAO 字段对象的数据的原始源的表的名称。 此属性指示与字段对象相关联的原始表名称。 例如，可以使用此属性以确定其名称为与基础表中的字段的名称不相关的查询字段中的数据的原始源。 有关详细信息，请参阅 DAO 帮助中的主题"SourceField，SourceTable 属性"。 您可以为设置此属性与 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。  
  
 `m_strValidationRule`  
 一个值，因为它已更改或添加到表验证字段中的数据。 有关详细信息，请参阅主题 DAO 帮助中的"有效性规则属性"。 您可以为设置此属性与 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。  
  
 Tabledefs 的相关信息，请参阅**m_strValidationRule**的成员[CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md)结构。  
  
 `m_strValidationText`  
 一个值，指定您的应用程序显示如果 DAO 字段对象的值不符合验证规则 ValidationRule 属性设置指定的消息的文本。 有关详细信息，请参阅主题 DAO 帮助中的"有效性文本属性"。 您可以为设置此属性与 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。  
  
 *m_strDefaultValue*  
 DAO field 对象的默认值。 创建一条新记录时，DefaultValue 属性设置为自动输入作为值为该字段。 有关详细信息，请参阅主题 DAO 帮助中的"默认值属性"。 您可以为设置此属性与 tabledef [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)。  
  
## <a name="remarks"></a>备注  
 对主、 辅助数据库，并且所有上面引用指示如何通过返回的信息`GetFieldInfo`类中的成员函数[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)， [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)，和[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)。  
  
 Field 对象不由 MFC 类表示。 相反，下面的类的 MFC 对象的 DAO 对象包含字段对象的集合︰ [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)， [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)，和[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)。 这些类提供成员函数来访问字段的信息，一些单个项或可以访问它们同时与`CDaoFieldInfo`对象通过调用`GetFieldInfo`包含对象的成员函数。  
  
 除了其用于检查对象属性，还可以使用`CDaoFieldInfo`构造在 tabledef 对象中创建新的字段的输入的参数。 更简单的选项都可用于此任务中，但如果您想更精细的控制，您可以使用的版本[CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)采用`CDaoFieldInfo`参数。  
  
 检索的信息`GetFieldInfo`（的包含字段的类） 的成员函数存储在`CDaoFieldInfo`结构。 调用`GetFieldInfo`field 对象存储在其字段集合中的包含对象的成员函数。 `CDaoFieldInfo`此外定义了`Dump`成员函数在调试生成。 您可以使用`Dump`转储的内容`CDaoFieldInfo`对象。  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdao.h  
  
## <a name="see-also"></a>另请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetFieldInfo](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)   
 [CDaoRecordset::GetFieldInfo](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)   
 [CDaoQueryDef::GetFieldInfo](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)


