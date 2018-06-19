---
title: CDaoRelationFieldInfo 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoRelationFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationFieldInfo structure [MFC]
ms.assetid: 47cb89ca-dc80-47ce-96fd-cc4b88512558
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e53daaaa5ef4997762342cbfb74ae4d5fa96097d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366156"
---
# <a name="cdaorelationfieldinfo-structure"></a>CDaoRelationFieldInfo 结构
`CDaoRelationFieldInfo`结构包含有关中的数据访问对象 (DAO) 定义的关系的字段的信息。  
  
## <a name="syntax"></a>语法  
  
```  
struct CDaoRelationFieldInfo  
{  
    CString m_strName;           // Primary  
    CString m_strForeignName;    // Primary  
};  
```  
  
#### <a name="parameters"></a>参数  
 `m_strName`  
 关系的主表中的字段的名称。  
  
 `m_strForeignName`  
 关系的外表中的字段的名称。  
  
## <a name="remarks"></a>备注  
 DAO 关系对象主表和外部表中定义该关系的字段中指定的字段。 对主上述结构定义中的引用指示如何在返回的信息`m_pFieldInfos`的成员[CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)通过调用获取对象[GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)类的成员函数`CDaoDatabase`。  
  
 关系对象和关系字段对象不由 MFC 类表示。 相反，DAO 对象类的基础 MFC 对象[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)包含称为关系集合的关系对象的集合。 每个关系对象，反过来，包含关系字段对象的集合。 每个关系字段对象与外部表中的字段关联的主表中的字段。 综上所述，关系字段对象定义一组字段在每个表中，它们共同定义该关系。 `CDaoDatabase` 让您访问具有关系对象`CDaoRelationInfo`对象通过调用`GetRelationInfo`成员函数。 `CDaoRelationInfo`对象，然后，有一个数据成员， `m_pFieldInfos`，指向数组的`CDaoRelationFieldInfo`对象。  
  
 调用[GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)的包含的成员函数`CDaoDatabase`对象的集合是的关系存储你感兴趣的关系对象。 然后访问`m_pFieldInfos`的成员[CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)对象。 `CDaoRelationFieldInfo` 此外定义`Dump`成员函数在调试生成。 你可以使用`Dump`以转储的内容`CDaoRelationFieldInfo`对象。  
  
## <a name="requirements"></a>要求  
 **标头：** afxdao.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoRelationInfo 结构](../../mfc/reference/cdaorelationinfo-structure.md)
