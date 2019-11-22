---
title: CDaoDatabaseInfo 结构
ms.date: 09/17/2019
f1_keywords:
- CDaoDatabaseInfo
helpviewer_keywords:
- CDaoDatabaseInfo structure [MFC]
- DAO (Data Access Objects), Databases collection
ms.assetid: 68e9e0da-8382-4fc6-8115-1b1519392ddb
ms.openlocfilehash: 60972aa3ecaef4d38c9a0d0ecc70477796aa37aa
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2019
ms.locfileid: "74304249"
---
# <a name="cdaodatabaseinfo-structure"></a>CDaoDatabaseInfo 结构

`CDaoDatabaseInfo` 结构包含有关为数据访问对象（DAO）定义的数据库对象的信息。 DAO 3.6 是最终版本，被视为已过时。

## <a name="syntax"></a>语法

```
struct CDaoDatabaseInfo
{
    CString m_strName;       // Primary
    BOOL m_bUpdatable;       // Primary
    BOOL m_bTransactions;    // Primary
    CString m_strVersion;    // Secondary
    long m_lCollatingOrder;  // Secondary
    short m_nQueryTimeout;   // Secondary
    CString m_strConnect;    // All
};
```

#### <a name="parameters"></a>参数

*m_strName*<br/>
为数据库对象唯一命名。 若要直接检索此属性，请调用[CDaoDatabase：： GetName](../../mfc/reference/cdaodatabase-class.md#getname)。 有关详细信息，请参阅 DAO 帮助中的主题 "名称属性"。

*m_bUpdatable*<br/>
指示是否可以对数据库进行更改。 若要直接检索此属性，请调用[CDaoDatabase：： CanUpdate](../../mfc/reference/cdaodatabase-class.md#canupdate)。 有关详细信息，请参阅 DAO 帮助中的主题 "可更新属性"。

*m_bTransactions*<br/>
指示数据源是否支持事务-记录一系列可供稍后回滚（取消）或已提交（保存）的更改。 如果数据库基于 Microsoft Jet 数据库引擎，则事务属性为非零值，你可以使用事务。 其他数据库引擎可能不支持事务。 若要直接检索此属性，请调用[CDaoDatabase：： CanTransact](../../mfc/reference/cdaodatabase-class.md#cantransact)。 有关详细信息，请参阅 DAO 帮助中的 "事务属性" 主题。

*m_strVersion*<br/>
指示 Microsoft Jet 数据库引擎的版本。 若要直接检索此属性的值，请调用数据库对象的[GetVersion](../../mfc/reference/cdaodatabase-class.md#getversion)成员函数。 有关详细信息，请参阅 DAO 帮助中的 "版本属性" 主题。

*m_lCollatingOrder*<br/>
指定文本中用于字符串比较或排序的排序顺序的序列。 可能的值包括：

- `dbSortGeneral` 使用常规（英语、法语、德语、葡萄牙语、意大利语和新式西班牙语）的排序顺序。

- `dbSortArabic` 使用阿拉伯语排序顺序。

- `dbSortCyrillic` 使用俄语排序顺序。

- `dbSortCzech` 使用捷克语排序顺序。

- `dbSortDutch` 使用荷兰排序顺序。

- `dbSortGreek` 使用希腊语排序顺序。

- `dbSortHebrew` 使用希伯来语排序顺序。

- `dbSortHungarian` 使用匈牙利语排序顺序。

- `dbSortIcelandic` 使用冰岛语排序顺序。

- `dbSortNorwdan` 使用挪威语或丹麦语排序顺序。

- `dbSortPDXIntl` 使用 Paradox 国际排序顺序。

- `dbSortPDXNor` 使用 Paradox 挪威语或丹麦语排序顺序。

- `dbSortPDXSwe` 使用 Paradox 瑞典语或芬兰语排序顺序。

- `dbSortPolish` 使用波兰语排序顺序。

- `dbSortSpanish` 使用西班牙语排序顺序。

- `dbSortSwedFin` 使用瑞典语或芬兰语排序顺序。

- `dbSortTurkish` 使用土耳其语排序顺序。

- `dbSortUndefined` 未定义或未知排序顺序。

有关详细信息，请参阅 DAO 帮助中的 "自定义用于数据访问的 Windows 注册表设置" 主题。

*m_nQueryTimeout*<br/>
当查询在 ODBC 数据库上运行时，Microsoft Jet 数据库引擎等待的秒数，出现超时错误。 默认超时值为60秒。 如果将 QueryTimeout 设置为0，则不会发生超时;这可能会导致程序停止响应。 若要直接检索此属性的值，请调用数据库对象的[GetQueryTimeout](../../mfc/reference/cdaodatabase-class.md#getquerytimeout)成员函数。 有关详细信息，请参阅 DAO 帮助中的主题 "QueryTimeout 属性"。

*m_strConnect*<br/>
提供有关打开的数据库的源的信息。 有关连接字符串的信息，以及有关直接检索此属性的值的信息，请参阅[CDaoDatabase：： GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect)成员函数。 有关详细信息，请参阅 DAO 帮助中的 "连接属性" 主题。

## <a name="remarks"></a>备注

数据库是[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)类的 MFC 对象基础的 DAO 对象。 对主要、次要和以上的引用指示了[CDaoWorkspace：： oomads.getdatabaseinfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo)成员函数返回信息的方式。

[CDaoWorkspace：： oomads.getdatabaseinfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo)成员函数检索的信息存储在 `CDaoDatabaseInfo` 结构中。 为数据库集合中存储数据库对象的 `CDaoWorkspace` 对象调用 `GetDatabaseInfo`。 `CDaoDatabaseInfo` 还在调试版本中定义了 `Dump` 成员函数。 您可以使用 `Dump` 转储 `CDaoDatabaseInfo` 对象的内容。

## <a name="requirements"></a>要求

**标头：** afxdao.h

## <a name="see-also"></a>另请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoWorkspace 类](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoDatabase 类](../../mfc/reference/cdaodatabase-class.md)
