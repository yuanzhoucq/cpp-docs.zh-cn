---
title: "BLOB_NAME |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BLOB_NAME
dev_langs: C++
helpviewer_keywords: BLOB_NAME macro
ms.assetid: 757acd0d-946d-447d-937e-94ecd700ba38
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d15a0eb22f2b5234d01b8de07479691258d4d500
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="blobname"></a>BLOB_NAME
与使用`BEGIN_COLUMN_MAP`和`END_COLUMN_MAP`要绑定的二进制大型对象 ([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx))。 类似于[BLOB_ENTRY](../../data/oledb/blob-entry.md)，只不过此宏采用而不是列号的列名称。  
  
## <a name="syntax"></a>语法  
  
```  
  
BLOB_NAME(  
pszName  
,   
IID  
,   
flags  
,   
data )  
```  
  
#### <a name="parameters"></a>参数  
 `pszName`  
 [in]指向的列名称的指针。 名称必须是 Unicode 字符串。 你可以完成此操作通过将放在 L 的所有引用，例如： `L"MyColumn"`。  
  
 *IID*  
 [in]接口的 GUID，如**IDD_ISequentialStream**，可用来检索 BLOB。  
  
 `flags`  
 [in]定义由 OLE 结构化存储模型的存储模式标志 (例如， **STGM_READ**)。  
  
 `data`  
 [in] 用户记录中的对应数据成员。  
  
## <a name="example"></a>示例  
 请参阅[如何检索 BLOB？](../../data/oledb/retrieving-a-blob.md)。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [宏和全局函数 OLE DB 使用者模板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB_NAME_LENGTH](../../data/oledb/blob-name-length.md)   
 [BLOB_NAME_LENGTH_STATUS](../../data/oledb/blob-name-length-status.md)   
 [BLOB_NAME_STATUS](../../data/oledb/blob-name-status.md)