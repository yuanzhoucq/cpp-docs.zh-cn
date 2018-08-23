---
title: CDaoDatabaseInfo 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoDatabaseInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoDatabaseInfo structure [MFC]
- DAO (Data Access Objects), Databases collection
ms.assetid: 68e9e0da-8382-4fc6-8115-1b1519392ddb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0815d248b6726d830fc50af9886c729c34ba2f29
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336469"
---
# <a name="cdaodatabaseinfo-structure"></a>CDaoDatabaseInfo 结构
`CDaoDatabaseInfo`结构包含有关数据库对象的数据访问对象 (DAO) 定义的信息。  
  
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
 *m_strName*  
 唯一地命名的数据库对象。 若要直接检索此属性，请调用[CDaoDatabase::GetName](../../mfc/reference/cdaodatabase-class.md#getname)。 有关详细信息，请参阅主题 DAO 帮助中的"名称属性"。  
  
 *m_bUpdatable*  
 指示是否可以对数据库进行更改。 若要直接检索此属性，请调用[CDaoDatabase::CanUpdate](../../mfc/reference/cdaodatabase-class.md#canupdate)。 有关详细信息，请参阅主题 DAO 帮助中的"可更新属性"。  
  
 *m_bTransactions*  
 指示数据源是否支持事务，更高版本回滚后更改一系列的录制 （取消） 或已提交 （保存）。 如果数据库基于 Microsoft Jet 数据库引擎，事务属性为非零值，您可以使用事务。 其他数据库引擎可能不支持事务。 若要直接检索此属性，请调用[CDaoDatabase::CanTransact](../../mfc/reference/cdaodatabase-class.md#cantransact)。 有关详细信息，请参阅主题 DAO 帮助中的"事务属性"。  
  
 *m_strVersion*  
 指示 Microsoft Jet 数据库引擎的版本。 若要直接检索此属性的值，请调用数据库对象的[GetVersion](../../mfc/reference/cdaodatabase-class.md#getversion)成员函数。 有关详细信息，请参阅主题 DAO 帮助中的"版本属性"。  
  
 *m_lCollatingOrder*  
 指定以文本字符串比较或排序的排序顺序的序列。 可能的值包括：  
  
- `dbSortGeneral` 使用常规的 （英语、 法语、 德语、 葡萄牙语、 意大利语、 和现代西班牙语） 排序顺序。  
  
- `dbSortArabic` 使用阿拉伯语的排序顺序。  
  
- `dbSortCyrillic` 使用俄语的排序顺序。  
  
- `dbSortCzech` 使用捷克语排序顺序。  
  
- `dbSortDutch` 使用荷兰语排序顺序。  
  
- `dbSortGreek` 使用希腊语排序顺序。  
  
- `dbSortHebrew` 使用希伯来语排序顺序。  
  
- `dbSortHungarian` 使用匈牙利语排序顺序。  
  
- `dbSortIcelandic` 使用 Icelandic 排序顺序。  
  
- `dbSortNorwdan` 使用挪威或丹麦语的排序顺序。  
  
- `dbSortPDXIntl` 使用 Paradox 国际排序顺序。  
  
- `dbSortPDXNor` 使用 Paradox 挪威或丹麦语的排序顺序。  
  
- `dbSortPDXSwe` 使用 Paradox 瑞典语或芬兰语排序顺序。  
  
- `dbSortPolish` 使用波兰语排序顺序。  
  
- `dbSortSpanish` 使用西班牙语排序顺序。  
  
- `dbSortSwedFin` 使用瑞典语或芬兰语排序顺序。  
  
- `dbSortTurkish` 使用土耳其语排序顺序。  
  
- `dbSortUndefined` 排序顺序是未定义或未知。  
  
 有关详细信息，请参阅主题中的"自定义 Windows 注册表设置的数据访问"DAO 帮助。  
  
 *m_nQueryTimeout*  
 ODBC 数据库上运行一次查询时发生超时错误之前的 Microsoft Jet 数据库引擎等待的秒数。 默认超时值为 60 秒。 当 QueryTimeout 设置为 0 时，会发生无超时;这会导致程序停止响应。 若要直接检索此属性的值，请调用数据库对象的[GetQueryTimeout](../../mfc/reference/cdaodatabase-class.md#getquerytimeout)成员函数。 有关详细信息，请参阅主题 DAO 帮助中的"QueryTimeout 属性"。  
  
 *m_strConnect*  
 提供有关源的打开的数据库的信息。 有关信息大约连接字符串，并直接检索此属性的值的信息，请参阅[CDaoDatabase::GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect)成员函数。 有关详细信息，请参阅主题 DAO 帮助中的"连接属性"。  
  
## <a name="remarks"></a>备注  
 数据库是基础类的 MFC 对象的 DAO 对象[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)。 对主要、 次要和上面所有的引用指示如何通过返回的信息[CDaoWorkspace::GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo)成员函数。  
  
 检索的信息[CDaoWorkspace::GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo)成员函数存储在`CDaoDatabaseInfo`结构。 调用`GetDatabaseInfo`为`CDaoWorkspace`其数据库集合中存储的数据库对象的对象。 `CDaoDatabaseInfo` 此外定义了`Dump`成员函数在调试生成。 可以使用`Dump`转储的内容`CDaoDatabaseInfo`对象。  
  
## <a name="requirements"></a>要求  
 **标头：** afxdao.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoWorkspace 类](../../mfc/reference/cdaoworkspace-class.md)   
 [CDaoDatabase 类](../../mfc/reference/cdaodatabase-class.md)
