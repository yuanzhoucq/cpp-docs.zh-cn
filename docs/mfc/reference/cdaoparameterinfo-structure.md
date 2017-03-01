---
title: "CDaoParameterInfo 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoParameterInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoParameterInfo structure
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
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
ms.openlocfilehash: b41d26b736ea9f84c53f71dbd71949f74fb8ae52
ms.lasthandoff: 02/24/2017

---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo 结构
`CDaoParameterInfo`结构包含有关为数据访问对象 (DAO) 定义的参数对象的信息。  
  
## <a name="syntax"></a>语法  
  
```  
struct CDaoParameterInfo  
{  
    CString m_strName;       // Primary  
    short m_nType;           // Primary  
    ColeVariant m_varValue;  // Secondary  
};  
```  
  
#### <a name="parameters"></a>参数  
 `m_strName`  
 唯一地命名参数对象。 有关详细信息，请参阅主题 DAO 帮助中的"名称属性"。  
  
 `m_nType`  
 一个值，该值指示参数对象的数据类型。 有关可能的值的列表，请参阅`m_nType`的成员[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构。 有关详细信息，请参阅主题 DAO 帮助中的"类型属性"。  
  
 *m_varValue*  
 中存储的参数的值[COleVariant](../../mfc/reference/colevariant-class.md)对象。  
  
## <a name="remarks"></a>备注  
 对主和辅助数据库更高版本的引用指示如何通过返回的信息[GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo)类中的成员函数`CDaoQueryDef`。  
  
 MFC 不封装 DAO 类中的参数对象。 DAO querydef 对象基础 MFC`CDaoQueryDef`对象在其参数集合中存储的参数。 若要访问中的参数对象[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)对象，请调用 querydef 对象`GetParameterInfo`成员函数的一个特定的参数名称或参数集合中的索引。 您可以使用[CDaoQueryDef::GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount)成员函数结合`GetParameterInfo`来遍历参数集合。  
  
 检索的信息[CDaoQueryDef::GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo)成员函数存储在`CDaoParameterInfo`结构。 调用`GetParameterInfo`其参数集合中存储的参数对象的 querydef 对象。  
  
> [!NOTE]
>  如果您想要获取或设置只有一个参数的值，请使用[GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue)和[SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue)类的成员函数`CDaoRecordset`。  
  
 `CDaoParameterInfo`此外定义了`Dump`成员函数在调试生成。 您可以使用`Dump`转储的内容`CDaoParameterInfo`对象。  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdao.h  
  
## <a name="see-also"></a>另请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoQueryDef 类](../../mfc/reference/cdaoquerydef-class.md)

