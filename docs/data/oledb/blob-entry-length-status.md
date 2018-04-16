---
title: BLOB_ENTRY_LENGTH_STATUS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- BLOB_ENTRY_LENGTH_STATUS
dev_langs:
- C++
helpviewer_keywords:
- BLOB_ENTRY_LENGTH_STATUS macro
ms.assetid: 09da67de-421b-4853-9a26-760e38324502
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6fe176d984937a39a3f76981f57388a69f21c0f9
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="blobentrylengthstatus"></a>BLOB_ENTRY_LENGTH_STATUS
与使用`BEGIN_COLUMN_MAP`和`END_COLUMN_MAP`要绑定的二进制大型对象 ([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx))。 类似于[BLOB_ENTRY](../../data/oledb/blob-entry.md)，只不过此宏还可获取的长度和 BLOB 列的状态。  
  
## <a name="syntax"></a>语法  
  
```cpp
BLOB_ENTRY_LENGTH_STATUS(  
    nOrdinal,  
    IID,  
    flags,  
    data,
    length,
    status )  
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
  
 *length*  
 [out]BLOB 列 （实际） 长度以字节为单位。  
  
 *status*  
 [out]BLOB 数据列的状态。  
  
## <a name="example"></a>示例  
 请参阅[如何检索 BLOB？](../../data/oledb/retrieving-a-blob.md)。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [宏和全局函数 OLE DB 使用者模板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB_ENTRY](../../data/oledb/blob-entry.md)   
 [BLOB_ENTRY_LENGTH](../../data/oledb/blob-entry-length.md)   
 [BLOB_ENTRY_STATUS](../../data/oledb/blob-entry-status.md)