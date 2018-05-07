---
title: 'Cdynamicaccessor:: Getcolumninfo |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetColumnInfo
- ATL.CDynamicAccessor.GetColumnInfo
- ATL::CDynamicAccessor::GetColumnInfo
- CDynamicAccessor.GetColumnInfo
- CDynamicAccessor::GetColumnInfo
dev_langs:
- C++
helpviewer_keywords:
- GetColumnInfo method
ms.assetid: 7f2102ea-b7cc-4714-812f-3ca2857f4b9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0c9fe862f08fc9ecfa280dcbb55f48e14427d6ed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicaccessorgetcolumninfo"></a>CDynamicAccessor::GetColumnInfo
返回所需的大多数使用者的列元数据。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT GetColumnInfo(IRowset* pRowset,   
   DBORDINAL* pColumns,   
   DBCOLUMNINFO** ppColumnInfo,   
   OLECHAR** ppStringsBuffer) throw();  
```  
  
#### <a name="parameters"></a>参数  
 `pRowset`  
 [in]指向的指针[IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx)接口。  
  
 *pColumns*  
 [out]指向内存中用于在行集中; 返回的列数的指针此数字包括书签列，如果有一个。  
  
 *ppColumnInfo*  
 [out]指向内存中要返回的数组的指针**DBCOLUMNINFO**结构。 请参阅中的"DBCOLUMNINFO 结构" [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx)中*OLE DB 程序员参考*。  
  
 `ppStringsBuffer`  
 [out]指向要存储的所有字符串值中返回一个指向在其中的内存的指针 (在使用名称*columnid*或*pwszName*) 在单个分配块。  
  
## <a name="return-value"></a>返回值  
 一个标准`HRESULT`值。  
  
## <a name="remarks"></a>备注  
 请参阅[IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx)中*OLE DB 程序员参考*有关数据类型信息**DBORDINAL**， **DBCOLUMNINFO**，和**OLECHAR**。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)