---
title: 'Iopenrowsetimpl:: Createrowset |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IOpenRowsetImpl.CreateRowset
- IOpenRowsetImpl::CreateRowset
- CreateRowset
dev_langs:
- C++
helpviewer_keywords:
- CreateRowset method
ms.assetid: 69041cf6-7a2f-4409-a26e-6e984c24986e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2d4554a2aeee3218ce505dc2c135167a3e38d55c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105174"
---
# <a name="iopenrowsetimplcreaterowset"></a>IOpenRowsetImpl::CreateRowset
创建一个行集对象。 不直接由用户调用。 请参阅[IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx)中*OLE DB 程序员参考。*  
  
## <a name="syntax"></a>语法  
  
```cpp
      template template <class RowsetClass  
      >  
HRESULT CreateRowset(IUnknown* pUnkOuter,  
   DBID* pTableID,  
   DBID* pIndexID,  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset,  
   RowsetClass*& pRowsetObj);  
```  
  
#### <a name="parameters"></a>参数  
 `RowsetClass`  
 模板类成员表示用户的行集类。 通常由向导生成。  
  
 `pRowsetObj`  
 [out]指向一个行集对象的指针。 通常不使用此参数，但如果必须将其传递到 COM 对象之前行集上执行更多的工作，可以使用它。 生存期`pRowsetObj`受`ppRowset`。  
  
 其他参数，请参阅[IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx)中*OLE DB 程序员参考。*  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IOpenRowsetImpl 类](../../data/oledb/iopenrowsetimpl-class.md)