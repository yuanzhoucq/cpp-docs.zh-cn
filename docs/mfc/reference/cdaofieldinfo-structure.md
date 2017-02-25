---
title: "CDaoFieldInfo 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDaoFieldInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoFieldInfo 结构"
  - "DAO（数据访问对象）, 字段集合"
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# CDaoFieldInfo 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CDaoFieldInfo` 结构包含有关数据访问对象（DAO）定义的字段对象的信息 。  
  
## 语法  
  
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
  
#### 参数  
 `m_strName`  
 唯一命名字段对象。  有关详细信息，请参见主题“名称属性”在DAO 帮助中。  
  
 `m_nType`  
 指示字段的数据类型的值。  有关详细信息，请参见主题“类型属性”在DAO 帮助中。  此属性的值可以是下列值之一。  
  
-   为或不是的**dbBoolean**，然后 **TRUE**\/**FALSE**相同  
  
-   **dbByte** Byte  
  
-   **dbInteger** Short  
  
-   **dbLong** Long  
  
-   货币**dbCurrency**;请参见 [COleCurrency](../../mfc/reference/colecurrency-class.md)MFC 类  
  
-   **dbSingle** Single  
  
-   **dbDouble** Double  
  
-   **dbDate**日期\/时间请参见 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)MFC 类  
  
-   **dbText**文本请参见 [CString](../../atl-mfc-shared/reference/cstringt-class.md)MFC 类  
  
-   **dbLongBinary** 长二进制 \(OLE 对象\);因为 `CByteArray` 更丰富、更易于使用，则可能需要改用 [CByteArray](../../mfc/reference/cbytearray-class.md) MFC 类而不是 `CLongBinary` 类。  
  
-   Text;**dbMemo**参见 MFC `CString`类  
  
-   **dbGUID** 全局唯一标识符 \(GUID\)\/全局唯一标识符用于远程过程调用。  有关更多信息，请参见本主题中 DAO 帮助中的“类型属性”。  
  
> [!NOTE]
>  不要为二进制数据使用 String 数据类型。  这让数据通过 Unicode\/ANSI 转换层，从而增加的开销以及可能意外的转换。  
  
 *m\_lSize*  
 指示最大大小，以字节中，DAO 字段对象包含文本或固定字段对象包含文本或数字值。  有关详细信息，请参见主题“大小属性”在DAO 帮助中。  大小可以是下列值之一：  
  
|类型|大小\(字节\)|说明|  
|--------|--------------|--------|  
|**dbBoolean**|1 个字节|Yes\/No \(same as True\/False\)|  
|**dbByte**|1|Byte|  
|**dbInteger**|2|Integer|  
|**dbLong**|4|Long|  
|**dbCurrency**|8|Currency \([COleCurrency](../../mfc/reference/colecurrency-class.md)\)|  
|**dbSingle**|4|Single|  
|**dbDouble**|8|Double|  
|**dbDate**|8|日期\/时间 \([COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)\)|  
|**dbText**|1 \- 255|Text \([CString](../../atl-mfc-shared/reference/cstringt-class.md)\)|  
|**dbLongBinary**|0|长二进制 \(OLE 对象；[CByteArray](../../mfc/reference/cbytearray-class.md);使用而非 `CLongBinary`\)|  
|**dbMemo**|0|Memo \([CString](../../atl-mfc-shared/reference/cstringt-class.md)\)|  
|**dbGUID**|16|dbGUID 全局唯一标识符 \(GUID\)\/全局唯一标识符用于远程过程调用。|  
  
 `m_lAttributes`  
 指定记录集、querydef 对象、tabledef 或索引字段包含的对象的特性。  返回的值可以是这些常量的总和，使用 C\+\+ 创建一种按位或 \(  **&#124;**\) operator:  
  
-   **dbFixedField** 字段长度修复 \(数字字段的默认值\)。  
  
-   **dbVariableField** 字段长度是可变 \(纯文本字段\)。  
  
-   **dbAutoIncrField** 用于新记录的字段值会自动递增到无法更改的单个长的整数。  仅支持使用 Microsoft Jet 数据库表。  
  
-   **dbUpdatableField** 字段值可以更改。  
  
-   **dbDescending** 字段在停止存储 \(Z \(或 100 \- 0\) 排序顺序 \(仅应用于索引对象的字段集合的字段对象；在 MFC 中，索引对象在 tabledef 包含对象\)。  如果省略了该常数，字段中登高 \(A\-Z 或 0 \- 100\) 排序 \(默认\) 排序。  
  
 当检查此属性时，将可以使用 C\+\+ 位与运算符 \(**&**\) 测试特定特性。  当为多个属性时，可以通过将适当的常数将它们用按位或 \(  **&#124;**\) operator.  有关详细信息，请参见主题“属性 属性”在DAO 帮助中。  
  
 *m\_nOrdinalPosition*  
 指定数字顺序需要字段的值是显示的 DAO 字段对象表示相对于其他字段。  可以使用 [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md)设置了此属性。  有关详细信息，请参见主题“定序位置 属性”在DAO 帮助中。  
  
 `m_bRequired`  
 指示 DAO 字段对象是否需要一个非空值。  如果此属性 **TRUE**，字段不允许空值。  如果设置为 **FALSE**，AllowZeroLength 和字段可能包含与 ValidationRule 属性指定的条件的空值并设置值。  有关详细信息，请参见主题“需要的属性”在DAO 帮助中。  可以设置一 tabledef 的此属性与 [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md)。  
  
 *m\_bAllowZeroLength*  
 一个空字符串 \(""\) DAO 字段是否为对象的一个有效值。文本或备忘录数据类型。  如果此属性 **TRUE**，空字符串是有效值。  可以将此属性设置为 **FALSE** 不确保可以使用空字符串设置的字段值。  有关详细信息，请参见主题“AllowZeroLength 属性”在DAO 帮助中。  可以设置一 tabledef 的此属性与 [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md)。  
  
 `m_lCollatingOrder`  
 文本中指定用于字符串比较或排序的排序顺序的序列。  有关详细信息，请参见主题“自定义 Windows 数据访问的注册表设置”DAO 帮助。  对于返回可能值的列表，请参见 [CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md) 结构的 **m\_lCollatingOrder** 成员中。  可以设置一 tabledef 的此属性与 [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md)。  
  
 `m_strForeignName`  
 该关系，DAO 外表中指定对象名称字段在主表中对应的字段的值。  有关详细信息，请参见主题“ForeignNam 属性”在DAO 帮助中。  
  
 *m\_strSourceField*  
 指示是初始数据源tabledef 或 querydef 对象、记录集包含的 DAO 字段对象字段的名称。  此属性指示原始字段与字段对象。  例如，您可能使用此属性确保的初始数据源。名称与字段名称无关的基础是在表中查询字段。  有关详细信息，请参见主题“SourceField，SourceTable 属性”DAO 帮助。  可以设置一 tabledef 的此属性与 [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md)。  
  
 *m\_strSourceTable*  
 指示是初始数据源tabledef 或 querydef 对象、记录集包含的 DAO 字段对象字段的名称。  此属性指示原始字段与字段对象。  例如，您可能使用此属性确保的初始数据源。名称与字段名称无关的基础是在表中查询字段。  有关详细信息，请参见主题“SourceField，SourceTable 属性”DAO 帮助。  可以设置一 tabledef 的此属性与 [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md)。  
  
 `m_strValidationRule`  
 在字段验证数据的值，更改或添加到表。  有关详细信息，请参见主题“ValidationRule属性”在DAO 帮助中。  可以设置一 tabledef 的此属性与 [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md)。  
  
 有关 tabledefs 的相关信息，请参见 [CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md) 结构的 **m\_strValidationRule** 成员中。  
  
 `m_strValidationText`  
 指定消息文本应用程序显示的值，则对象 ValidationRule DAO 字段的值不符合指定属性设置的验证规则。  有关详细信息，请参见主题“ValidationText属性”在DAO 帮助中。  可以设置一 tabledef 的此属性与 [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md)。  
  
 *m\_strDefaultValue*  
 DAO 字段对象的默认值。  当新记录时创建，DefaultValue 属性设置自动进入，当字段的值。  有关详细信息，请参见主题“DefaultValue属性”在DAO 帮助中。  可以设置一 tabledef 的此属性与 [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md)。  
  
## 备注  
 主键，二级键和所有上面的引用指示信息如何由 `GetFieldInfo` 成员函数返回类[CDaoTableDef](../Topic/CDaoTableDef::GetFieldInfo.md), [CDaoQueryDef](../Topic/CDaoQueryDef::GetFieldInfo.md), 以及[CDaoRecordset](../Topic/CDaoRecordset::GetFieldInfo.md).  
  
 字段对象不被 MFC 类表示。  相反，基于下面类的 MFC 对象的 DAO 字段对象包含对象的集合：[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)。  这些类提供成员函数访问索引信息各个项，也可同时用 `GetFieldInfo`对象访问它们，通过调用包含对象的 `CDaoFieldInfo` 成员函数。  
  
 除了其检查对象的属性使用外，您还可以使用 `CDaoFieldInfo` 构造中创建的新字段的输入参数 tabledef 的。  更简单的选项用于此任务，都可用，但是，如果您希望更细致的控制，可以使用 [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md) 采用 `CDaoFieldInfo` 参数的版本。  
  
 `GetFieldInfo` 成员函数中的信息包含字段\) \(类在 `CDaoFieldInfo` 结构存储。  调用字段集合字段对象存储包含对象的 `GetFieldInfo` 成员函数中。  `CDaoFieldInfo` 还定义了函数调试版本的 `Dump` 成员。  您可以使用`Dump` 显示`CDaoFieldInfo`对象的内容。  
  
## 要求  
 **头文件：** afxdao.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetFieldInfo](../Topic/CDaoTableDef::GetFieldInfo.md)   
 [CDaoRecordset::GetFieldInfo](../Topic/CDaoRecordset::GetFieldInfo.md)   
 [CDaoQueryDef::GetFieldInfo](../Topic/CDaoQueryDef::GetFieldInfo.md)