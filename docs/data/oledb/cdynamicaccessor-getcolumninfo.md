---
title: CDynamicAccessor::GetColumnInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a9f311e9fc5330a68edba4fd5029e97b75033406
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
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
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)