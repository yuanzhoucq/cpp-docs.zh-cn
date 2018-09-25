---
title: CDaoIndexFieldInfo 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoIndexFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoIndexFieldInfo structure [MFC]
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1593ad1997baf0b5ce262f3177f0f063b49cec6e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378639"
---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo 结构

`CDaoIndexFieldInfo`结构包含的数据访问对象 (DAO) 定义一个索引的字段对象有关的信息。

## <a name="syntax"></a>语法

```
struct CDaoIndexFieldInfo
{
    CString m_strName;          // Primary
    BOOL m_bDescending;         // Primary
};
```

#### <a name="parameters"></a>参数

*m_strName*<br/>
唯一地命名索引字段对象。 有关详细信息，请参阅主题 DAO 帮助中的"名称属性"。

*m_bDescending*<br/>
指示由索引对象定义的索引顺序。 如果顺序为降序，则为 TRUE。

## <a name="remarks"></a>备注

索引对象可以具有多个字段，指示在编制索引 tabledef 对象 （或基于表的记录集） 的字段。 到更高版本的主副本的引用指示如何在返回的信息`m_pFieldInfos`的成员[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)获取通过调用对象`GetIndexInfo`类的成员函数[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo)。

一个 MFC 类不表示索引对象和索引的字段对象。 相反，DAO 对象类的基础 MFC 对象[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)包含称为索引集合的索引对象的集合。 每个索引对象，包含的字段对象的集合。 这些类提供成员函数访问各个项的索引的信息，或可以访问它们使用一次性`CDaoIndexInfo`对象通过调用`GetIndexInfo`包含对象的成员函数。 `CDaoIndexInfo`对象，然后，有一个数据成员， `m_pFieldInfos`，，它指向的数组`CDaoIndexFieldInfo`对象。

调用`GetIndexInfo`包含 tabledef 或记录集对象的集合是其索引中的成员函数存储你感兴趣的索引对象。 然后，访问`m_pFieldInfos`的成员[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)对象。 长度`m_pFieldInfos`数组存储在`m_nFields`。 `CDaoIndexFieldInfo` 此外定义了`Dump`成员函数在调试生成。 可以使用`Dump`转储的内容`CDaoIndexFieldInfo`对象。

## <a name="requirements"></a>要求

**标头：** afxdao.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)<br/>
[CDaoRecordset::GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)

