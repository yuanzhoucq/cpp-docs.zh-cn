---
title: 'Caccessorrowset:: Getcolumninfo |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetColumnInfo
- CAccessorRowset.GetColumnInfo
- CAccessorRowset::GetColumnInfo
dev_langs:
- C++
helpviewer_keywords:
- GetColumnInfo method
ms.assetid: 8ade2388-3c58-43cd-8ed6-499ee0531291
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 46f645ba2f662cad38fa962cea543f7530418530
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="caccessorrowsetgetcolumninfo"></a>CAccessorRowset::GetColumnInfo
从打开的行集中获取列信息。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT GetColumnInfo(DBORDINAL* pulColumns,  
   DBCOLUMNINFO** ppColumnInfo,  
   LPOLESTR* ppStrings) const;  

HRESULT GetColumnInfo(DBORDINAL* pColumns,  
   DBCOLUMNINFO** ppColumnInfo);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx)中*OLE DB 程序员参考*。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 返回的列信息和字符串缓冲区，用户必须释放。 使用此方法的第二个版本，当你使用[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)和需要重写绑定。  
  
 有关详细信息，请参阅[IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx)中*OLE DB 程序员参考*。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CAccessorRowset 类](../../data/oledb/caccessorrowset-class.md)