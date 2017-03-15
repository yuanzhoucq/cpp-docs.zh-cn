---
title: "CDaoRelationFieldInfo 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoRelationFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationFieldInfo structure
ms.assetid: 47cb89ca-dc80-47ce-96fd-cc4b88512558
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
ms.openlocfilehash: 23d7497502f611cf2311e574556186dc5f7c7d3d
ms.lasthandoff: 02/24/2017

---
# <a name="cdaorelationfieldinfo-structure"></a>CDaoRelationFieldInfo 结构
`CDaoRelationFieldInfo`结构包含有关数据访问对象 (DAO) 的方式定义的关系中的字段信息。  
  
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
 主表中的关系的字段的名称。  
  
 `m_strForeignName`  
 外的关系的表中字段的名称。  
  
## <a name="remarks"></a>备注  
 DAO 关系对象的主表和外部表中定义该关系的字段中指定的字段。 对主以上结构定义中引用所指示如何在返回的信息`m_pFieldInfos`的成员[CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)获取通过调用对象[GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)类的成员函数`CDaoDatabase`。  
  
 不由 MFC 类表示关系的对象和关系字段对象。 相反，DAO 对象类的基础 MFC 对象[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)包含称为关系集合的关系对象的集合。 每个关系对象，包含关系字段对象的集合。 每个关系 field 对象与外部表中的字段关联的主表中的字段。 合起来看，关系字段对象定义一组字段在每个表中，它们共同定义该关系。 `CDaoDatabase`使您能够访问具有关系对象`CDaoRelationInfo`对象通过调用`GetRelationInfo`成员函数。 `CDaoRelationInfo`对象，然后，有一个数据成员， `m_pFieldInfos`，，它指向的数组`CDaoRelationFieldInfo`对象。  
  
 调用[GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)成员函数包含`CDaoDatabase`中它的集合是的关系存储您感兴趣的关系对象的对象。 然后，访问`m_pFieldInfos`的成员[CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)对象。 `CDaoRelationFieldInfo`此外定义了`Dump`成员函数在调试生成。 您可以使用`Dump`转储的内容`CDaoRelationFieldInfo`对象。  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdao.h  
  
## <a name="see-also"></a>另请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoRelationInfo 结构](../../mfc/reference/cdaorelationinfo-structure.md)

