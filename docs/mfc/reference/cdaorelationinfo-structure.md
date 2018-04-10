---
title: CDaoRelationInfo 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CDaoRelationInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationInfo structure [MFC]
ms.assetid: 92dda090-fe72-4090-84ec-429498a48aad
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 047b81ebaa903d2b9bdddcf6c606d1e9fe649482
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cdaorelationinfo-structure"></a>CDaoRelationInfo 结构
`CDaoRelationInfo`结构包含有关定义字段中两个表之间的关系的信息[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象。  
  
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
 在关系中的主表进行命名。  
  
 *m_strForeignTable*  
 在关系的外表进行命名。 外部表是用于包含外键表。 通常，可以使用外部表用于建立或强制引用完整性。 外部表通常是一个对多关系的多方。 外部表的示例包括表包含美国的州或加拿大省或客户订单的代码。  
  
 `m_lAttributes`  
 包含有关关系类型的信息。 此成员的值可以是以下任一项：  
  
- **dbRelationUnique**关系是一对一。  
  
- **dbRelationDontEnforce**关系不是强制执行 （没有引用完整性）。  
  
- **dbRelationInherited**包含两个附加的表的非当前数据库中存在的关系。  
  
- **dbRelationLeft**的关系是左的联接。 左外部联接包括的所有记录从第一个 （左侧） 的两个表，即使第二个 （右侧） 表中的记录没有匹配值。  
  
- **dbRelationRight**关系是正确的联接。 右外部联接包括所有从第二个记录 （右侧） 的两个表，即使有没有匹配的第一个 （左侧） 表中的记录值。  
  
- **两**更新会级联发生。  
  
- **dbRelationDeleteCascade**将级联删除。  
  
 `m_pFieldInfos`  
 指向数组的指针[CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md)结构。 该数组包含关系中每个字段的一个对象。 `m_nFields`数据成员提供的数组元素的计数。  
  
 `m_nFields`  
 数`CDaoRelationFieldInfo`中的对象`m_pFieldInfos`数据成员。  
  
## <a name="remarks"></a>备注  
 对主要和辅助上面的引用指示如何通过返回的信息[GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)类中的成员函数`CDaoDatabase`。  
  
 关系对象不由 MFC 类表示。 相反，基础的 MFC 对象的 DAO 对象`CDaoDatabase`类维护的关系对象的集合：`CDaoDatabase`提供成员函数来访问关系信息，或你的某些单个项可以使用在一次访问它们`CDaoRelationInfo`对象通过调用`GetRelationInfo`包含的数据库对象的成员函数。  
  
 检索的信息[CDaoDatabase::GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)成员函数将存储在`CDaoRelationInfo`结构。 `CDaoRelationInfo`此外定义`Dump`成员函数在调试生成。 你可以使用`Dump`以转储的内容`CDaoRelationInfo`对象。  
  
## <a name="requirements"></a>惠?  
 **标头：** afxdao.h  
  
## <a name="see-also"></a>请参阅  
 [CDaoRelationFieldInfo 结构](../../mfc/reference/cdaorelationfieldinfo-structure.md)
