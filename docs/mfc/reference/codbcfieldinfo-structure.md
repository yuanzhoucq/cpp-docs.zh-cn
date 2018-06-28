---
title: CODBCFieldInfo 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CODBCFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- ODBC [MFC], data source information
- CODBCFieldInfo structure [MFC]
ms.assetid: 92598b4f-facc-4108-b282-63a179ff79ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ede515f0b8bc95d454fec48c6c6bd2109c43ce74
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040189"
---
# <a name="codbcfieldinfo-structure"></a>CODBCFieldInfo 结构
`CODBCFieldInfo`结构包含有关 ODBC 数据源中的字段的信息。  
  
## <a name="syntax"></a>语法  
  
```  
struct CODBCFieldInfo  
{  
    CString m_strName;  
    SWORD m_nSQLType;  
    UDWORD m_nPrecision;  
    SWORD m_nScale;  
    SWORD m_nNullability;  
};  
```  
  
#### <a name="parameters"></a>参数  
 *m_strName*  
 字段的名称。  
  
 *m_nSQLType*  
 SQL 数据类型的字段。 这可以是 ODBC SQL 数据类型或特定于驱动程序的 SQL 数据类型。 有关有效的 ODBC SQL 数据类型的列表，请参阅 Windows SDK 中的"SQL 数据类型"。 有关特定于驱动程序的 SQL 数据类型的信息，请参阅驱动程序的文档。  
  
 *m_nPrecision*  
 字段的最大精度。 有关详细信息，请参阅 Windows SDK 中的"精度、 小数位数、 长度和显示大小"。  
  
 *m_nScale*  
 字段的小数位数。 有关详细信息，请参阅 Windows SDK 中的"精度、 小数位数、 长度和显示大小"。  
  
 *m_nNullability*  
 是否字段接受 Null 值。 这可以是两个值之一： **SQL_NULLABLE**如果字段接受 Null 值，或**SQL_NO_NULLS**如果字段不接受 Null 值。  
  
## <a name="remarks"></a>备注  
 若要检索此信息，请调用[CRecordset::GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo)。  
  
## <a name="requirements"></a>要求  
 **标头：** afxdb.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRecordset::GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo)   
 [CRecordset::GetFieldValue](../../mfc/reference/crecordset-class.md#getfieldvalue)


