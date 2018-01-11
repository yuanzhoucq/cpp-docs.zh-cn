---
title: "CDaoIndexFieldInfo 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CDaoIndexFieldInfo
dev_langs: C++
helpviewer_keywords:
- CDaoIndexFieldInfo structure [MFC]
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0b745a6f450bdf96389f49c673dc623b614e04db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo 结构
`CDaoIndexFieldInfo`结构包含的数据访问对象 (DAO) 定义的索引字段对象有关的信息。  
  
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
 唯一名称的索引字段对象。 有关详细信息，请参阅主题 DAO 帮助中的"名称属性"。  
  
 *m_bDescending*  
 指示由索引对象的索引顺序。 **TRUE**如果降序顺序。  
  
## <a name="remarks"></a>备注  
 索引对象可以具有多个字段，指示在编制索引 tabledef （或基于表的记录集） 的字段。 对主上面的引用指示如何在返回的信息`m_pFieldInfos`的成员[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)通过调用获取对象`GetIndexInfo`类的成员函数[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo)。  
  
 索引对象和索引字段对象不由 MFC 类表示。 相反，DAO 对象类的基础 MFC 对象[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)包含称为索引集合的索引对象的集合。 每个索引对象，反过来，包含的字段对象的集合。 这些类提供成员函数来访问各个项的索引信息，或可以访问其在一次与`CDaoIndexInfo`对象通过调用`GetIndexInfo`包含对象的成员函数。 `CDaoIndexInfo`对象，然后，有一个数据成员， `m_pFieldInfos`，指向数组的`CDaoIndexFieldInfo`对象。  
  
 调用`GetIndexInfo`你感兴趣索引对象存储在其索引集合是包含 tabledef 或记录集对象的成员函数。 然后访问`m_pFieldInfos`的成员[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)对象。 长度`m_pFieldInfos`数组存储在`m_nFields`。 `CDaoIndexFieldInfo`此外定义`Dump`成员函数在调试生成。 你可以使用`Dump`以转储的内容`CDaoIndexFieldInfo`对象。  
  
## <a name="requirements"></a>惠?  
 **标头：** afxdao.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)   
 [CDaoRecordset::GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)

