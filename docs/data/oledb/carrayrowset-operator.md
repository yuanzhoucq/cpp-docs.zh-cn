---
title: "Carrayrowset:: Operator |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CArrayRowset::operator[]
- CArrayRowset.operator[]
dev_langs: C++
helpviewer_keywords:
- operator [], arrays
- '[] operator'
- operator[], arrays
ms.assetid: 3bb8c310-cc1e-46e8-9711-9b565488acaa
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 61929df340fb12afc5c2abdc6bd9f4e8bd899108
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="carrayrowsetoperator"></a>CArrayRowset::operator
提供用于访问行集中的行的类似数组的语法。  
  
## <a name="syntax"></a>语法  
  
```  
  
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