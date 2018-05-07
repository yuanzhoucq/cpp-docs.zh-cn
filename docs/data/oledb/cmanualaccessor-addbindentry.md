---
title: 'Cmanualaccessor:: Addbindentry |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 59793bd61b17fe2ead4948932efa1b583da8e1a8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
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
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)   
 [DBViewer 示例](../../visual-cpp-samples.md)