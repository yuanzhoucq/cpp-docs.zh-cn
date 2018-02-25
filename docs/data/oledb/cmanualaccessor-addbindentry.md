---
title: "Cmanualaccessor:: Addbindentry |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CManualAccessor::AddBindEntry
- ATL.CManualAccessor.AddBindEntry
- CManualAccessor::AddBindEntry
- AddBindEntry
- CManualAccessor.AddBindEntry
dev_langs:
- C++
helpviewer_keywords:
- AddBindEntry method
ms.assetid: 8556dda9-dda1-4f67-96bc-6031e6c6a271
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1e99e9822b60152fc8daa6f101bcca2ea7e60c25
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="cmanualaccessoraddbindentry"></a>CManualAccessor::AddBindEntry
将绑定条目添加到输出列。  
  
## <a name="syntax"></a>语法  
  
```
void AddBindEntry(DBORDINAL nOrdinal,  
   DBTYPE wType,  DBLENGTH nColumnSize,  
   void* pData,  
   void* pLength = NULL,  
   void* pStatus = NULL) throw ();  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)中*OLE DB 程序员参考*。  
  
 `nOrdinal`  
 [in]列号。  
  
 `wType`  
 [in]数据类型。  
  
 `nColumnSize`  
 [in]以字节为单位的列大小。  
  
 `pData`  
 [in]指向存储在缓冲区中的列数据的指针。  
  
 `pLength`  
 [in]指向字段长度，如果所需的指针。  
  
 `pStatus`  
 [in]指向要将绑定到列的状态，如果所需的变量的指针。  
  
## <a name="remarks"></a>备注  
 若要使用此功能，必须先调用[CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md)。 无法添加更多项中指定的列数比`CreateAccessor`。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)   
 [DBViewer 示例](../../visual-cpp-samples.md)