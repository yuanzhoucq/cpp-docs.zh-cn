---
title: "COLUMN_NAME_PS_STATUS |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: COLUMN_NAME_PS_STATUS
dev_langs: C++
helpviewer_keywords: COLUMN_NAME_PS_STATUS macro
ms.assetid: 134e1bfe-abfa-4b64-9159-e492f31de44b
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a773891e7a3a0a623d10e8eb55069bf46fc10f21
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="columnnamepsstatus"></a>COLUMN_NAME_PS_STATUS
在行集中的特定列表示行集上的绑定。 类似于[COLUMN_NAME](../../data/oledb/column-name.md)，只不过此宏还采用精度、 小数位数和列的状态。  
  
## <a name="syntax"></a>语法  
  
```  
  
COLUMN_NAME_PS_STATUS(  
pszName  
,   
nPrecision  
,   
nScale  
,   
data  
,   
status )  
```  
  
#### <a name="parameters"></a>参数  
 `pszName`  
 [in]指向的列名称的指针。 名称必须是 Unicode 字符串。 你可以完成此操作通过将放在 L 的所有引用，例如： `L"MyColumn"`。  
  
 `nPrecision`  
 [in] 要绑定的列的最大精度。  
  
 `nScale`  
 [in] 要绑定的列的小数位数。  
  
 `data`  
 [in] 用户记录中的对应数据成员。  
  
 *status*  
 [in] 要绑定到列变量的状态。  
  
## <a name="remarks"></a>备注  
 请参阅[COLUMN_NAME](../../data/oledb/column-name.md)有关在何处信息**COLUMN_NAME_\*** 使用宏，则。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [宏和全局函数 OLE DB 使用者模板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN_NAME](../../data/oledb/column-name.md)   
 [COLUMN_NAME_EX](../../data/oledb/column-name-ex.md)   
 [COLUMN_NAME_LENGTH](../../data/oledb/column-name-length.md)   
 [COLUMN_NAME_LENGTH_STATUS](../../data/oledb/column-name-length-status.md)   
 [COLUMN_NAME_STATUS](../../data/oledb/column-name-status.md)   
 [COLUMN_NAME_PS](../../data/oledb/column-name-ps.md)   
 [COLUMN_NAME_PS_LENGTH](../../data/oledb/column-name-ps-length.md)   
 [COLUMN_NAME_PS_LENGTH_STATUS](../../data/oledb/column-name-ps-length-status.md)   
 [COLUMN_NAME_TYPE](../../data/oledb/column-name-type.md)   
 [COLUMN_NAME_TYPE_PS](../../data/oledb/column-name-type-ps.md)   
 [COLUMN_NAME_TYPE_SIZE](../../data/oledb/column-name-type-size.md)   
 [COLUMN_NAME_TYPE_STATUS](../../data/oledb/column-name-type-status.md)