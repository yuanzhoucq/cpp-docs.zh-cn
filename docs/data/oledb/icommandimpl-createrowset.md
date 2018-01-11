---
title: "Icommandimpl:: Createrowset |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ICommandImpl::CreateRowset
- ICommandImpl.CreateRowset
- CreateRowset
dev_langs: C++
helpviewer_keywords: CreateRowset method
ms.assetid: a0890009-205e-4970-879f-01ed9d6a93f1
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4fecb21b35e3941862cc38edc28a2b1e25ff6bcc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="icommandimplcreaterowset"></a>ICommandImpl::CreateRowset
由调用[执行](../../data/oledb/icommandimpl-execute.md)创建单个行集。  
  
## <a name="syntax"></a>语法  
  
```  
  
      template <class   
      RowsetClass  
      >  
HRESULT CreateRowset(  
   IUnknown* pUnkOuter,  
   REFIID riid,  
   DBPARAMS* pParams,  
   DBROWCOUNT* pcRowsAffected,  
   IUnknown** ppRowset,  
   RowsetClass*& pRowsetObj   
);  
```  
  
#### <a name="parameters"></a>参数  
 `RowsetClass`  
 模板类成员表示用户的行集类。 通常由向导生成。  
  
 `pUnkOuter`  
 [in]指向控制**IUnknown**接口如果正在聚合的一部分创建的行集; 否则，它为 null。  
  
 `riid`  
 [in]对应于`riid`中`ICommand::Execute`。  
  
 `pParams`  
 [输入/输出]对应于`pParams`中`ICommand::Execute`。  
  
 `pcRowsAffected`  
 对应于`pcRowsAffected`中`ICommand::Execute`。  
  
 `ppRowset`  
 [输入/输出]对应于`ppRowset`中`ICommand::Execute`。  
  
 `pRowsetObj`  
 [out]指向一个行集对象的指针。 通常不使用此参数，但如果必须将其传递到 COM 对象之前行集上执行更多的工作，可以使用它。 生存期`pRowsetObj`受`ppRowset`。  
  
## <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。 请参阅`ICommand::Execute`有关的典型值列表。  
  
## <a name="remarks"></a>备注  
 若要创建多个行集，或提供你自己创建不同的行集的条件，将对不同调用`CreateRowset`中**执行**。  
  
 请参阅[ICommand::Execute](https://msdn.microsoft.com/en-us/library/ms718095.aspx)中*OLE DB 程序员参考。*  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [ICommandImpl 类](../../data/oledb/icommandimpl-class.md)