---
title: CRowset::AddRefRows | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowset<TAccessor>.AddRefRows
- CRowset.AddRefRows
- ATL.CRowset.AddRefRows
- AddRefRows
- CRowset::AddRefRows
- CRowset<TAccessor>::AddRefRows
- ATL::CRowset::AddRefRows
- ATL.CRowset<TAccessor>.AddRefRows
- ATL::CRowset<TAccessor>::AddRefRows
dev_langs:
- C++
helpviewer_keywords:
- AddRefRows method
ms.assetid: 590b5a24-870f-4c42-b0c8-28491f368a82
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 89c517f4ba2bfe06d5ff6410247490a8c81cb8fa
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="crowsetaddrefrows"></a>CRowset::AddRefRows
调用[irowset:: Addrefrows](https://msdn.microsoft.com/en-us/library/ms719619.aspx)以增加 （1) 的引用计数与当前行句柄。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT AddRefRows() throw();  
  
```  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 此方法递增当前行句柄的引用的计数。 调用[ReleaseRows](../../data/oledb/crowset-releaserows.md)以减少的计数。 Move 方法返回的行都具有一个引用计数。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [CRowset::ReleaseRows](../../data/oledb/crowset-releaserows.md)