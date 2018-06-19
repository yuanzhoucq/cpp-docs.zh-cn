---
title: 'Irowsetlocateimpl:: Getrowsat |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetRowsAt
- IRowsetLocateImpl.GetRowsAt
- ATL::IRowsetLocateImpl::GetRowsAt
- IRowsetLocateImpl::GetRowsAt
- ATL.IRowsetLocateImpl.GetRowsAt
dev_langs:
- C++
helpviewer_keywords:
- GetRowsAt method
ms.assetid: 6aeb09dc-3aa8-4729-97a8-144dd27063f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e94d14e276f5ff7a24c5064fe482def49fd61335
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105252"
---
# <a name="irowsetlocateimplgetrowsat"></a>IRowsetLocateImpl::GetRowsAt
提取行开头指定偏移量从书签的行。  
  
## <a name="syntax"></a>语法  
  
```cpp
      STDMETHOD (GetRowsAt )(HWATCHREGION /* hReserved1 */,  
   HCHAPTER hReserved2,  
   DBBKMARK cbBookmark,  
   const BYTE* pBookmark,  
   DBROWOFFSET lRowsOffset,  
   DBROWCOUNT cRows,  
   DBCOUNTITEM* pcRowsObtained,  
   HROW** prghRows);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[IRowsetLocate::GetRowsAt](https://msdn.microsoft.com/en-us/library/ms723031.aspx)中*OLE DB 程序员参考*。  
  
## <a name="remarks"></a>备注  
 若要改为提取从光标位置，使用[IRowset::GetRowsAt](https://msdn.microsoft.com/en-us/library/ms723031.aspx)。  
  
 `IRowsetLocateImpl::GetRowsAt` 不会更改光标位置。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IRowsetLocateImpl 类](../../data/oledb/irowsetlocateimpl-class.md)   
 [IRowsetLocateImpl::GetRowsByBookmark](../../data/oledb/irowsetlocateimpl-getrowsbybookmark.md)