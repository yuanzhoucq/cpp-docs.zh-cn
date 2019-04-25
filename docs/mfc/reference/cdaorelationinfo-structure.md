---
title: CDaoRelationInfo 结构
ms.date: 06/25/2018
f1_keywords:
- CDaoRelationInfo
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationInfo structure [MFC]
ms.assetid: 92dda090-fe72-4090-84ec-429498a48aad
ms.openlocfilehash: 7d1c86732966d8222582dc6d4527af89963a5cdc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152821"
---
# <a name="cdaorelationinfo-structure"></a>CDaoRelationInfo 结构

`CDaoRelationInfo`结构包含有关定义字段中的两个表之间的关系的信息[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象。

## <a name="syntax"></a>语法

```cpp
struct CDaoRelationInfo
{
    CDaoRelationInfo();                     // Constructor
    CString m_strName;                      // Primary
    CString m_strTable;                     // Primary
    CString m_strForeignTable;              // Primary
    long m_lAttributes;                     // Secondary
    CDaoRelationFieldInfo* m_pFieldInfos;   // Secondary
    short m_nFields;                        // Secondary
    // Below the // Implementation comment:
    // Destructor, not otherwise documented
};
```

#### <a name="parameters"></a>参数

*m_strName*<br/>
唯一地命名关系对象。 有关详细信息，请参阅主题 DAO 帮助中的"名称属性"。

*m_strTable*<br/>
命名关系中的主表。

*m_strForeignTable*<br/>
关系中的外部表进行命名。 外部表是用来包含外键表。 通常情况下，使用外部表建立或强制实施引用完整性。 外部表通常是一个对多关系的多方。 外部表的示例包括表包含有关美国的州或加拿大省或客户订单的代码。

*m_lAttributes*<br/>
包含有关关系类型的信息。 此成员的值可以是以下任一项：

- `dbRelationUnique` 关系是一对一的。

- `dbRelationDontEnforce` 关系不是强制实施 （没有引用完整性）。

- `dbRelationInherited` 包含两个附加的表的非当前数据库中存在关系。

- `dbRelationLeft` 关系是左的联接。 左外部联接包含的所有记录从第一个 （左侧） 的两个表，即使第二个 （右侧） 表中的记录没有匹配值。

- `dbRelationRight` 关系是右联接。 右外部联接包含从第二个记录的所有 （右侧） 的两个表，即使没有匹配的第一个 （左侧） 表中的记录值。

- `dbRelationUpdateCascade` 级联更新。

- `dbRelationDeleteCascade` 级联删除操作。

*m_pFieldInfos*<br/>
指向数组的指针[CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md)结构。 该数组包含一个对象关系中的每个字段。 `m_nFields`数据成员提供的数组元素计数。

*m_nFields*<br/>
数`CDaoRelationFieldInfo`中的对象`m_pFieldInfos`数据成员。

## <a name="remarks"></a>备注

对主数据库和辅助上述引用指示如何通过返回的信息[GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)类中的成员函数`CDaoDatabase`。

由 MFC 类不表示关系的对象。 而是基础的 MFC 对象的 DAO 对象`CDaoDatabase`类维护关系对象的集合：`CDaoDatabase`提供成员函数来访问关系的信息，或您的一些单个项可以与一次性全部访问它们`CDaoRelationInfo`对象通过调用`GetRelationInfo`包含的数据库对象的成员函数。

检索的信息[CDaoDatabase::GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)成员函数存储在`CDaoRelationInfo`结构。 `CDaoRelationInfo` 此外定义了`Dump`成员函数在调试生成。 可以使用`Dump`转储的内容`CDaoRelationInfo`对象。

## <a name="requirements"></a>要求

**标头：** afxdao.h

## <a name="see-also"></a>请参阅

[CDaoRelationFieldInfo 结构](../../mfc/reference/cdaorelationfieldinfo-structure.md)
