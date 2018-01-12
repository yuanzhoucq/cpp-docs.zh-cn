---
title: "Crowset:: Movetoratio |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MoveToRatio
- CRowset<TAccessor>::MoveToRatio
- CRowset::MoveToRatio
- CRowset<TAccessor>.MoveToRatio
- ATL.CRowset.MoveToRatio
- ATL::CRowset::MoveToRatio
- CRowset.MoveToRatio
- ATL.CRowset<TAccessor>.MoveToRatio
- ATL::CRowset<TAccessor>::MoveToRatio
dev_langs: C++
helpviewer_keywords: MoveToRatio method
ms.assetid: 1fa313bd-8fd1-4608-8e85-44993b97dd88
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 70b4d7994bb2175d0d402fdd309a8258f7127dc7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="crowsetmovetoratio"></a>CRowset::MoveToRatio
提取行的行集中的小数部分位置 （从开始）。  
  
## <a name="syntax"></a>语法  
  
```  
  
      HRESULT MoveToRatio(   
   DBCOUNTITEM nNumerator,   
   DBCOUNTITEM nDenominator,   
   bool bForward = true    
) throw( );  
```  
  
#### <a name="parameters"></a>参数  
 `nNumerator`  
 [in]用于确定小数分子从中提取数据的位置。  
  
 `nDenominator`  
 [in]用于确定小数分母从中提取数据的位置。  
  
 `bForward`  
 [in]指示是否将向前或向后移动。 默认值为转发。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 `MoveToRatio`提取行大致按照以下公式：  
  
 `( nNumerator *  RowsetSize ) / nDenominator`  
  
 其中`RowsetSize`是行集，以行为单位的大小。 此公式的准确性取决于特定的提供程序。 有关详细信息，请参阅[IRowsetScroll::GetRowsAtRatio](https://msdn.microsoft.com/en-us/library/ms709602.aspx)。  
  
 此方法要求的可选接口`IRowsetScroll`，这可能不支持对所有提供程序，如果出现这种情况，该方法返回**E_NOINTERFACE**。 你还必须设置**DBPROP_IRowsetScroll**到`VARIANT_TRUE`之前调用**打开**对表或命令，其中包含行集。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)