---
title: 'Csession:: Starttransaction |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CSession::StartTransaction
- StartTransaction
- ATL.CSession.StartTransaction
- CSession.StartTransaction
- ATL::CSession::StartTransaction
dev_langs:
- C++
helpviewer_keywords:
- StartTransaction method
ms.assetid: cd7bd2be-fad1-4e2b-932b-79d308efb8fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cddd3596befcba1e409d0f1575796438ee8c7011
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="csessionstarttransaction"></a>CSession::StartTransaction
开始此会话的新事务。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT StartTransaction(ISOLEVEL isoLevel = ISOLATIONLEVEL_READCOMMITTED,  
   ULONG isoFlags = 0,  
   ITransactionOptions* pOtherOptions = NULL,  
   ULONG* pulTransactionLevel = NULL) const throw();  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[ITransactionLocal::StartTransaction](https://msdn.microsoft.com/en-us/library/ms709786.aspx)中*OLE DB 程序员参考*。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[ITransactionLocal::StartTransaction](https://msdn.microsoft.com/en-us/library/ms709786.aspx)中*OLE DB 程序员参考*。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CSession 类](../../data/oledb/csession-class.md)