---
title: "Carrayrowset:: Operator |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b2dd001dc3946a3eb22b793874ba1f4b16affb72
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
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
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CArrayRowset 类](../../data/oledb/carrayrowset-class.md)