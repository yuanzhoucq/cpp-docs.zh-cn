---
title: "CDaoRelationInfo 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoRelationInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationInfo structure
ms.assetid: 92dda090-fe72-4090-84ec-429498a48aad
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
ms.openlocfilehash: 7c3a8195aed2c3b3fe5c78c98afcc6e72a83cc21
ms.lasthandoff: 02/24/2017

---
# <a name="cdaorelationinfo-structure"></a>CDaoRelationInfo 结构
`CDaoRelationInfo`结构包含有关定义字段中两个表之间的关系信息[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象。  
  
## <a name="syntax"></a>语法  
  
```  
struct CDaoRelationInfo  
{  
    CDaoRelationInfo();
*// Constructor  
    CString m_strName;      // Primary  
    CString m_strTable;     // Primary  
    CString m_strForeignTable;              // Primary  
    long m_lAttributes;     // Secondary  
    CDaoRelationFieldInfo* m_pFieldInfos;   // Secondary  
    short m_nFields;        // Secondary *// Below the // Implementation comment: *// Destructor, not otherwise documented  
};  
```  
  
#### <a name="parameters"></a>参数  
 `m_strName`  
 唯一地命名关系对象。 有关详细信息，请参阅主题 DAO 帮助中的"名称属性"。  
  
 *m_strTable*  
 关系中主键的表进行命名。  
  
 *m_strForeignTable*  
 关系中的外部表进行命名。 外部表是用于包含外键的表。 通常，可以使用外部表来建立或强制实施引用完整性。 外部表通常是一种一对多关系的多方。 外部表的示例包括表中包含美国的州或加拿大省市自治区或客户订单的代码。  
  
 `m_lAttributes`  
 包含有关关系类型的信息。 此成员的值可以是以下任一情况︰  
  
- **dbRelationUnique**关系是一对一。  
  
- **dbRelationDontEnforce**关系不是强制执行 （无参照完整性）。  
  
- **dbRelationInherited**包含两个附加的表的非当前数据库中存在的关系。  
  
- **dbRelationLeft**的关系是左的联接。 左外部联接包含的所有记录从第一个 （左侧） 两个表，即使有第二个 （右） 表中的记录没有匹配的值。  
  
- **dbRelationRight**的关系是正确的联接。 右外部联接包含的所有记录中第二个 （右） 的两个表，即使没有匹配的第一个 （左侧） 表中的记录值。  
  
- **两**将级联更新。  
  
- **dbRelationDeleteCascade**将级联删除。  
  
 `m_pFieldInfos`  
 指向数组的指针[CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md)结构。 该数组包含一个对象，该关系中每个字段。 `m_nFields`数据成员提供了数组元素的计数。  
  
 `m_nFields`  
 数`CDaoRelationFieldInfo`中的对象`m_pFieldInfos`数据成员。  
  
## <a name="remarks"></a>备注  
 对主和辅助数据库更高版本的引用指示如何通过返回的信息[GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)类中的成员函数`CDaoDatabase`。  
  
 关系对象不由 MFC 类表示。 改为基础的 MFC 对象的 DAO 对象`CDaoDatabase`类维护关系对象的集合︰`CDaoDatabase`提供成员函数来访问某些各个项的关系的信息，或者您可以访问它们同时与`CDaoRelationInfo`对象通过调用`GetRelationInfo`包含的数据库对象的成员函数。  
  
 检索的信息[CDaoDatabase::GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)成员函数存储在`CDaoRelationInfo`结构。 `CDaoRelationInfo`此外定义了`Dump`成员函数在调试生成。 您可以使用`Dump`转储的内容`CDaoRelationInfo`对象。  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdao.h  
  
## <a name="see-also"></a>另请参阅  
 [CDaoRelationFieldInfo 结构](../../mfc/reference/cdaorelationfieldinfo-structure.md)

