---
title: CDaoParameterInfo 结构
ms.date: 09/17/2019
f1_keywords:
- CDaoParameterInfo
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
ms.openlocfilehash: 6d594bbeec34e400eb074c136e3467e78b35c4ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368983"
---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo 结构

该`CDaoParameterInfo`结构包含有关为数据访问对象 （DAO） 定义的参数对象的信息。 DAO 3.6 是最终版本，它被视为过时版本。

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
唯一地命名参数对象。 有关详细信息，请参阅 DAO 帮助中的主题"名称属性"。

*m_nType*<br/>
指示参数对象的数据类型的值。 有关可能值的列表，请参阅[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构*的m_nType*成员。 有关详细信息，请参阅 DAO 帮助中的主题"类型属性"。

*m_varValue*<br/>
存储在[COleVariant](../../mfc/reference/colevariant-class.md)对象中的参数的值。

## <a name="remarks"></a>备注

对上述主要和次要的引用指示类`CDaoQueryDef`中的[GetparameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo)成员函数如何返回信息。

MFC 不封装类中的 DAO 参数对象。 DAO 查询def 对象的基础`CDaoQueryDef`MFC 对象在其参数集合中存储参数。 要访问[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)对象中的参数对象，请将特定参数名称的`GetParameterInfo`querydef 对象的成员函数或索引调用到参数集合中。 您可以使用[CDaoQueryDef：：获取参数计数](../../mfc/reference/cdaoquerydef-class.md#getparametercount)成员函数，并`GetParameterInfo`结合循环通过参数集合。

[CDaoQueryDef检索的信息：获取参数信息](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo)成员函数存储在结构`CDaoParameterInfo`中。 调用`GetParameterInfo`存储参数对象的查询def对象。

> [!NOTE]
> 如果只想获取或设置参数的值，请使用类`CDaoRecordset`的[GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue)和[SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue)成员函数。

`CDaoParameterInfo`还在调试生成中`Dump`定义成员函数。 可以使用`Dump`转储`CDaoParameterInfo`对象的内容。

## <a name="requirements"></a>要求

**标题：** afxdao.h

## <a name="see-also"></a>另请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef 类](../../mfc/reference/cdaoquerydef-class.md)
