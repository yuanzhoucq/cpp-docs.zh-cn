---
title: 'Carrayrowset:: Operator |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CArrayRowset::operator[]
- CArrayRowset.operator[]
dev_langs:
- C++
helpviewer_keywords:
- operator [], arrays
- '[] operator'
- operator[], arrays
ms.assetid: 3bb8c310-cc1e-46e8-9711-9b565488acaa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 755e484f430f47eb072e3c590bfbee8471984bb6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="carrayrowsetoperator"></a>CArrayRowset::operator
提供用于访问行集中的行的类似数组的语法。  
  
## <a name="syntax"></a>语法  
  
```cpp
      TAccessor  
      & operator[](int nrow);  
```  
  
#### <a name="parameters"></a>参数  
 `TAccessor`  
 一个指定存储在行集中的访问器类型的模板化参数。  
  
 `nRow`  
 [in] 要访问的行号（数组元素）。  
  
## <a name="return-value"></a>返回值  
 请求行的内容。  
  
## <a name="remarks"></a>备注  
 如果 `nRow` 超过行集中的行数，则会引发异常。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CArrayRowset 类](../../data/oledb/carrayrowset-class.md)