---
title: "Cbulkrowset:: Movetoratio |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CBulkRowset.MoveToRatio
- ATL::CBulkRowset::MoveToRatio
- MoveToRatio
- CBulkRowset::MoveToRatio
- ATL.CBulkRowset<TAccessor>.MoveToRatio
- ATL::CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset.MoveToRatio
- CBulkRowset<TAccessor>::MoveToRatio
dev_langs: C++
helpviewer_keywords: MoveToRatio method
ms.assetid: 86be60f5-9341-44c1-8e1e-9174c082d0d5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 98536344e3282008ace529565e6c8d805b546ef2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cbulkrowsetmovetoratio"></a>CBulkRowset::MoveToRatio
提取行的行集中的小数部分位置 （从开始）。  
  
## <a name="syntax"></a>语法  
  
```  
  
      HRESULT MoveToRatio(  
   DBCOUNTITEM nNumerator,  
   DBCOUNTITEM nDenominator   
) throw( );  
```  
  
#### <a name="parameters"></a>参数  
 `nNumerator`  
 [in]用于确定要从中提取数据的小数部分位置分子。  
  
 `nDenominator`  
 [in]用于确定要从中提取数据的小数部分位置分母。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 `MoveToRatio`提取行大致根据以下公式：  
  
 `( nNumerator *  RowsetSize ) / nDenominator`  
  
 其中`RowsetSize`是行集，以行为单位的大小。 此公式的准确性取决于特定的提供程序。 有关详细信息，请参阅[IRowsetScroll::GetRowsAtRatio](https://msdn.microsoft.com/en-us/library/ms709602.aspx)中*OLE DB 程序员参考*。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CBulkRowset 类](../../data/oledb/cbulkrowset-class.md)