---
title: "BLOB_ENTRY |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BLOB_ENTRY
dev_langs: C++
helpviewer_keywords: BLOB_ENTRY macro
ms.assetid: 89e40678-0869-49ed-b502-0fa2630a9081
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ac3a4760777b2a6b4cb5d24787c3ae5edb6c3640
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="blobentry"></a>BLOB_ENTRY
与使用`BEGIN_COLUMN_MAP`和`END_COLUMN_MAP`要绑定的二进制大型对象 ([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx))。  
  
## <a name="syntax"></a>语法  
  
```  
  
BLOB_ENTRY(  
nOrdinal  
,  
 IID  
,   
flags  
,   
data  
 )  
  
```  
  
#### <a name="parameters"></a>参数  
 `nOrdinal`  
 [in] 列号。  
  
 *IID*  
 [in]接口的 GUID，如**IDD_ISequentialStream**，可用来检索 BLOB。  
  
 `flags`  
 [in]定义由 OLE 结构化存储模型的存储模式标志 (例如， **STGM_READ**)。  
  
 `data`  
 [in] 用户记录中的对应数据成员。  
  
## <a name="example"></a>示例  
 请参阅[如何检索 BLOB？](../../data/oledb/retrieving-a-blob.md)。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>另请参阅  
 [宏和全局函数 OLE DB 使用者模板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB_ENTRY_LENGTH](../../data/oledb/blob-entry-length.md)   
 [BLOB_ENTRY_LENGTH_STATUS](../../data/oledb/blob-entry-length-status.md)   
 [BLOB_ENTRY_STATUS](../../data/oledb/blob-entry-status.md)