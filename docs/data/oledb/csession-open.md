---
title: "Csession:: Open |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CSession::Open
- CSession::Open
- CSession.Open
- ATL.CSession.Open
dev_langs: C++
helpviewer_keywords: Open method
ms.assetid: c2050c2c-9817-4857-be49-189f346968f6
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b3aa0f6b694bc594ec00511ce39b7887bf26ecae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="csessionopen"></a>CSession::Open
为数据源对象打开新会话。  
  
## <a name="syntax"></a>语法  
  
```  
  
      HRESULT Open(  
   const CDataSource& ds,  
   DBPROPSET *pPropSet = NULL,  
   ULONG ulPropSets = 0  
) throw( );  
```  
  
#### <a name="parameters"></a>参数  
 `ds`  
 [in]数据源为打开会话。  
  
 *pPropSet*  
 [in]指向数组的指针[DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)包含属性和要设置值的结构。 请参阅[属性设置和属性组](https://msdn.microsoft.com/en-us/library/ms713696.aspx)中*OLE DB 程序员参考*Windows SDK 中。  
  
 `ulPropSets`  
 [in]数[DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)结构*pPropSet*自变量。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 你必须打开数据源对象使用[cdatasource:: Open](../../data/oledb/cdatasource-open.md)之前将其传递给`CSession::Open`。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CSession 类](../../data/oledb/csession-class.md)