---
title: "PROVIDER_COLUMN_ENTRY_WSTR |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROVIDER_COLUMN_ENTRY_WSTR
dev_langs: C++
helpviewer_keywords: PROVIDER_COLUMN_ENTRY_WSTR macro
ms.assetid: 70630bd5-d782-473b-9777-aebbbf5321c5
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cee2a21b91a01e73c980bd29902ad3cec85c6e82
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="providercolumnentrywstr"></a>PROVIDER_COLUMN_ENTRY_WSTR
表示提供程序支持的特定列。  
  
## <a name="syntax"></a>语法  
  
```  
  
PROVIDER_COLUMN_ENTRY_WSTR(  
name  
, ordinal, member )  
```  
  
#### <a name="parameters"></a>参数  
 *name*  
 [in]列名称。  
  
 `ordinal`  
 [in] 列号。 除非列是书签列，列数必须不为 0。  
  
 `member`  
 [in]将数据存储的数据类中的成员变量。  
  
## <a name="remarks"></a>备注  
 以 null 结尾的 Unicode 字符串，列数据时使用此宏[DBTYPE_WSTR](https://msdn.microsoft.com/en-us/library/ms711251.aspx)。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>另请参阅  
 [OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)