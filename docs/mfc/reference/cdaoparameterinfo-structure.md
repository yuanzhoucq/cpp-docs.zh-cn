---
title: CDaoParameterInfo 结构
ms.date: 11/04/2016
f1_keywords:
- CDaoParameterInfo
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
ms.openlocfilehash: 62addd44f8aa8fceafef6a27244994a2ec6b766b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399780"
---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo 结构

`CDaoParameterInfo`结构包含的数据访问对象 (DAO) 定义的参数对象有关的信息。

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

*m_strName*<br/>
唯一地命名参数对象。 有关详细信息，请参阅主题 DAO 帮助中的"名称属性"。

*m_nType*<br/>
一个值，指示参数对象的数据类型。 有关可能的值的列表，请参阅*m_nType*的成员[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构。 有关详细信息，请参阅主题 DAO 帮助中的"类型属性"。

*m_varValue*<br/>
存储中的参数的值[COleVariant](../../mfc/reference/colevariant-class.md)对象。

## <a name="remarks"></a>备注

对主数据库和辅助上述引用指示如何通过返回的信息[GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo)类中的成员函数`CDaoQueryDef`。

MFC 不封装 DAO 类中的参数对象。 DAO querydef 对象基础的 MFC`CDaoQueryDef`对象在其参数集合中存储参数。 若要访问中的参数对象[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)对象，请调用 querydef 对象`GetParameterInfo`成员函数的特定参数名称或参数集合的索引。 可以使用[CDaoQueryDef::GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount)成员函数结合`GetParameterInfo`遍历参数集合。

检索的信息[CDaoQueryDef::GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo)成员函数存储在`CDaoParameterInfo`结构。 调用`GetParameterInfo`其参数集合中存储的参数对象的 querydef 对象。

> [!NOTE]
>  如果你想要获取或设置参数值，请使用[GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue)并[SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue)类的成员函数`CDaoRecordset`。

`CDaoParameterInfo` 此外定义了`Dump`成员函数在调试生成。 可以使用`Dump`转储的内容`CDaoParameterInfo`对象。

## <a name="requirements"></a>要求

**标头：** afxdao.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef 类](../../mfc/reference/cdaoquerydef-class.md)
