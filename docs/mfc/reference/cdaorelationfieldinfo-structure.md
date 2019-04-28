---
title: CDaoRelationFieldInfo 结构
ms.date: 11/04/2016
f1_keywords:
- CDaoRelationFieldInfo
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationFieldInfo structure [MFC]
ms.assetid: 47cb89ca-dc80-47ce-96fd-cc4b88512558
ms.openlocfilehash: 85dd853a9aae41a87bbe7ef5c69e22846678cf8a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62206103"
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

*m_strName*<br/>
关系的主表中的字段的名称。

*m_strForeignName*<br/>
关系的外表中的字段的名称。

## <a name="remarks"></a>备注

DAO 关系对象的主表和外部表中定义的关系的字段中指定的字段。 对上面的结构定义中的主引用指示如何在返回的信息`m_pFieldInfos`的成员[CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)获取通过调用对象[GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)类的成员函数`CDaoDatabase`。

一个 MFC 类不表示关系对象和关系的字段对象。 相反，DAO 对象类的基础 MFC 对象[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)包含称为关系集合的关系对象的集合。 每个关系对象，包含关系字段对象的集合。 关系字段的每个对象与外部表中的字段关联的主表中的字段。 合起来看，关系字段对象定义一组字段在每个表中，它们共同定义关系。 `CDaoDatabase` 使您能够访问具有关系对象`CDaoRelationInfo`对象通过调用`GetRelationInfo`成员函数。 `CDaoRelationInfo`对象，然后，有一个数据成员， `m_pFieldInfos`，，它指向的数组`CDaoRelationFieldInfo`对象。

调用[GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)成员函数的包含`CDaoDatabase`中它的集合是的关系存储你感兴趣的关系对象的对象。 然后，访问`m_pFieldInfos`的成员[CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)对象。 `CDaoRelationFieldInfo` 此外定义了`Dump`成员函数在调试生成。 可以使用`Dump`转储的内容`CDaoRelationFieldInfo`对象。

## <a name="requirements"></a>要求

**标头：** afxdao.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoRelationInfo 结构](../../mfc/reference/cdaorelationinfo-structure.md)
