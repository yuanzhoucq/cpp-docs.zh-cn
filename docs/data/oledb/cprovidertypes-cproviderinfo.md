---
title: "CProviderTypes，CProviderInfo |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- m_bIsLong
- m_szLocalTypeName
- m_guidType
- m_bCaseSensitive
- m_szVersion
- m_szCreateParams
- IS_NULLABLE
- m_bAutoUniqueValue
- LITERAL_SUFFIX
- COLUMN_SIZE
- CProviderTypes
- LOCAL_TYPE_NAME
- MINIMUM_SCALE
- m_nMinScale
- m_nColumnSize
- m_szLiteralSuffix
- m_bFixedPrecScale
- m_szLiteralPrefix
- m_nMaxScale
- m_szTypeLib
- m_nDataType
- m_bUnsignedAttribute
- m_nSearchable
- m_bBestMatch
- m_szTypeName
- DATA_TYPE
- MAXIMUM_SCALE
- CProviderInfo
- FIXED_PREC_SCALE
- m_bIsNullable
- IS_LONG
dev_langs:
- C++
helpviewer_keywords:
- DATA_TYPE
- MAXIMUM_SCALE
- m_nMinScale
- m_guidType
- LOCAL_TYPE_NAME
- m_bAutoUniqueValue
- m_bBestMatch
- m_bIsLong
- m_bUnsignedAttribute
- CProviderInfo parameter class
- FIXED_PREC_SCALE
- m_nColumnSize
- m_szVersion
- CProviderTypes typedef class
- m_szCreateParams
- IS_NULLABLE
- m_bIsNullable
- m_szTypeLib
- m_szLiteralPrefix
- m_nMaxScale
- m_nDataType
- m_bCaseSensitive
- m_bFixedPrecScale
- m_nSearchable
- MINIMUM_SCALE
- m_szTypeName
- m_szLocalTypeName
- IS_LONG
- LITERAL_SUFFIX
- COLUMN_SIZE
- m_szLiteralSuffix
ms.assetid: 6f1620ff-c2f0-4f5b-931c-27b0cd2a580d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a0218aa7774b08db2e8ee727fd1aa8343286d352
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="cprovidertypes-cproviderinfo"></a>CProviderTypes，CProviderInfo
调用 typedef 类**CProviderTypes**来实现其参数类**CProviderInfo**。  
  
## <a name="remarks"></a>备注  
 请参阅[架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)有关使用 typedef 类的详细信息。  
  
 此类将标识支持的数据提供程序 （基） 数据类型。  
  
 下表列出了类数据成员及其对应的 OLE DB 列。 请参阅[PROVIDER_TYPES 行集](https://msdn.microsoft.com/en-us/library/ms709785.aspx)中*OLE DB 程序员参考*有关的架构和列的详细信息。  
  
|数据成员|OLE DB 列|  
|------------------|--------------------|  
|m_szTypeName|TYPE_NAME|  
|m_nDataType|DATA_TYPE|  
|m_nColumnSize|COLUMN_SIZE|  
|m_szLiteralPrefix|LITERAL_PREFIX|  
|m_szLiteralSuffix|LITERAL_SUFFIX|  
|m_szCreateParams|CREATE_PARAMS|  
|m_bIsNullable|IS_NULLABLE|  
|m_bCaseSensitive|CASE_SENSITIVE|  
|m_nSearchable|可搜索|  
|m_bUnsignedAttribute|UNSIGNED_ATTRIBUTE|  
|m_bFixedPrecScale|FIXED_PREC_SCALE|  
|m_bAutoUniqueValue|AUTO_UNIQUE_VALUE|  
|m_szLocalTypeName|LOCAL_TYPE_NAME|  
|m_nMinScale|MINIMUM_SCALE|  
|m_nMaxScale|MAXIMUM_SCALE|  
|m_guidType|GUID|  
|m_szTypeLib|类型库|  
|m_szVersion|VERSION|  
|m_bIsLong|IS_LONG|  
|m_bBestMatch|BEST_MATCH|  
  
## <a name="requirements"></a>惠?  
 **标头：** atldbsch.h  
  
## <a name="see-also"></a>请参阅  
 [CRestrictions 类](../../data/oledb/crestrictions-class.md)