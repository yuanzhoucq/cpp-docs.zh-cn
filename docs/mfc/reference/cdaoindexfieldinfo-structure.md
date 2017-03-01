---
title: "CDaoIndexFieldInfo 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoIndexFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoIndexFieldInfo structure
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
caps.latest.revision: 12
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
ms.openlocfilehash: 975b3a704936adc9d4205938bb2c757ab650f0d9
ms.lasthandoff: 02/24/2017

---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo 结构
`CDaoIndexFieldInfo`结构包含有关为数据访问对象 (DAO) 定义的索引字段对象的信息。  
  
## <a name="syntax"></a>语法  
  
```  
struct CDaoIndexFieldInfo  
{  
    CString m_strName;          // Primary  
    BOOL m_bDescending;         // Primary  
};  
```  
  
#### <a name="parameters"></a>参数  
 `m_strName`  
 唯一地命名索引字段对象。 有关详细信息，请参阅主题 DAO 帮助中的"名称属性"。  
  
 *m_bDescending*  
 指示由索引对象定义的索引顺序。 **TRUE**如果降序顺序。  
  
## <a name="remarks"></a>备注  
 Index 对象可以具有多个字段，指示在编制索引 tabledef 对象 （或基于表格的记录集） 的字段。 到更高版本的主副本的引用指示如何在返回的信息`m_pFieldInfos`的成员[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)获取通过调用对象`GetIndexInfo`类的成员函数[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo)。  
  
 索引对象和索引的字段对象不由 MFC 类表示。 相反，DAO 对象类的基础 MFC 对象[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)包含称为索引集合的索引对象的集合。 每个索引对象，包含的字段对象的集合。 这些类提供成员函数来访问各个项的索引信息，或可以访问它们同时与`CDaoIndexInfo`对象通过调用`GetIndexInfo`包含对象的成员函数。 `CDaoIndexInfo`对象，然后，有一个数据成员， `m_pFieldInfos`，，它指向的数组`CDaoIndexFieldInfo`对象。  
  
 调用`GetIndexInfo`在其索引集合是包含 tabledef 或记录集对象的成员函数存储您感兴趣的索引对象。 然后，访问`m_pFieldInfos`的成员[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)对象。 长度`m_pFieldInfos`数组存储在`m_nFields`。 `CDaoIndexFieldInfo`此外定义了`Dump`成员函数在调试生成。 您可以使用`Dump`转储的内容`CDaoIndexFieldInfo`对象。  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdao.h  
  
## <a name="see-also"></a>另请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)   
 [CDaoRecordset::GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)


