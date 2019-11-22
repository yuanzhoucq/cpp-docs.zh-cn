---
title: CDaoIndexFieldInfo 结构
ms.date: 09/17/2019
f1_keywords:
- CDaoIndexFieldInfo
helpviewer_keywords:
- CDaoIndexFieldInfo structure [MFC]
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
ms.openlocfilehash: 10c786ef4fed9ecb3bbbb93526cd68a11e18d58c
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303664"
---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo 结构

`CDaoIndexFieldInfo` 结构包含有关为数据访问对象（DAO）定义的索引字段对象的信息。

DAO 受 Office 2013 的支持。 DAO 3.6 是最终版本，被视为已过时。

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
为索引字段对象唯一命名。 有关详细信息，请参阅 DAO 帮助中的主题 "名称属性"。

*m_bDescending*<br/>
指示索引对象定义的索引顺序。 如果订单为降序，则为 TRUE。

## <a name="remarks"></a>备注

索引对象可以具有多个字段，指示 tabledef （或基于表的记录集）对哪些字段进行索引。 上面对主要副本的引用指示了如何在[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)对象的 `m_pFieldInfos` 成员中返回信息，该对象通过调用[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo)类的 `GetIndexInfo` 成员函数获得。

索引对象和索引字段对象不由 MFC 类表示。 相反，DAO 对象类[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)类的基础 MFC 对象包含索引对象（称为索引集合）的集合。 反过来，每个索引对象都包含一个字段对象的集合。 这些类提供成员函数以访问索引信息的各个项，或者可以通过调用包含对象的 `GetIndexInfo` 成员函数，一次通过 `CDaoIndexInfo` 对象访问所有这些项。 然后，`CDaoIndexInfo` 对象具有指向 `CDaoIndexFieldInfo` 对象数组的数据成员 `m_pFieldInfos`。

调用包含 tabledef 或 recordset 对象的 `GetIndexInfo` 成员函数，该对象的索引集合存储有你感兴趣的索引对象。 然后访问[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)对象的 `m_pFieldInfos` 成员。 `m_pFieldInfos` 数组的长度存储在 `m_nFields`中。 `CDaoIndexFieldInfo` 还在调试版本中定义了 `Dump` 成员函数。 您可以使用 `Dump` 转储 `CDaoIndexFieldInfo` 对象的内容。

## <a name="requirements"></a>要求

**标头：** afxdao.h

## <a name="see-also"></a>另请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)<br/>
[CDaoRecordset::GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)
