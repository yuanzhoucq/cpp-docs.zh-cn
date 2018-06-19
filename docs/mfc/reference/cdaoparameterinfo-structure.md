---
title: CDaoParameterInfo 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoParameterInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e743e7456c185acd100c898cfb946182d63ce63
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366234"
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
 唯一命名的参数对象。 有关详细信息，请参阅主题 DAO 帮助中的"名称属性"。  
  
 `m_nType`  
 一个值，该值指示参数对象的数据类型。 有关可能的值的列表，请参阅`m_nType`的成员[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构。 有关详细信息，请参阅主题 DAO 帮助中的"类型属性"。  
  
 *m_varValue*  
 存储中的参数值[COleVariant](../../mfc/reference/colevariant-class.md)对象。  
  
## <a name="remarks"></a>备注  
 对主要和辅助上面的引用指示如何通过返回的信息[GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo)类中的成员函数`CDaoQueryDef`。  
  
 MFC 不封装 DAO 类中的参数对象。 DAO querydef 对象基础 MFC`CDaoQueryDef`对象存储在其参数集合中的参数。 若要访问中的参数对象[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)对象，请调用 querydef 对象`GetParameterInfo`特定参数名称或参数集合的索引的成员函数。 你可以使用[CDaoQueryDef::GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount)结合的成员函数`GetParameterInfo`循环访问的参数集合。  
  
 检索的信息[CDaoQueryDef::GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo)成员函数将存储在`CDaoParameterInfo`结构。 调用`GetParameterInfo`其参数集合中存储的参数对象的 querydef 对象。  
  
> [!NOTE]
>  如果你想要获取或设置仅参数的值，请使用[GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue)和[SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue)类的成员函数`CDaoRecordset`。  
  
 `CDaoParameterInfo` 此外定义`Dump`成员函数在调试生成。 你可以使用`Dump`以转储的内容`CDaoParameterInfo`对象。  
  
## <a name="requirements"></a>要求  
 **标头：** afxdao.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoQueryDef 类](../../mfc/reference/cdaoquerydef-class.md)
