---
title: IOpenRowsetImpl::CreateRowset | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IOpenRowsetImpl.CreateRowset
- IOpenRowsetImpl::CreateRowset
- CreateRowset
dev_langs:
- C++
helpviewer_keywords:
- CreateRowset method
ms.assetid: 69041cf6-7a2f-4409-a26e-6e984c24986e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7aa478d86ba21dd482c3507352fb7f321df2ee0e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
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
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IOpenRowsetImpl 类](../../data/oledb/iopenrowsetimpl-class.md)