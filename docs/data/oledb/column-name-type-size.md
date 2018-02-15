---
title: COLUMN_NAME_TYPE_SIZE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- COLUMN_NAME_TYPE_SIZE
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_NAME_TYPE_SIZE macro
ms.assetid: b10f8ef9-78ce-4ec9-b4cc-4278271a46dd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d771a505aeabbf7096ad4bdafa967025927fa8ab
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="columnnametypesize"></a>COLUMN_NAME_TYPE_SIZE
在行集中的特定列表示行集上的绑定。 类似于[COLUMN_NAME](../../data/oledb/column-name.md)，只不过此宏还采用数据类型和大小。  
  
## <a name="syntax"></a>语法  
  
```cpp
COLUMN_NAME_TYPE_SIZE(pszName, wType, nLength, data)  
  
```  
  
#### <a name="parameters"></a>参数  
 `pszName`  
 [in]指向的列名称的指针。 名称必须是 Unicode 字符串。 你可以完成此操作通过将放在 L 的所有引用，例如： `L"MyColumn"`。  
  
 `wType`  
 [in]数据类型。  
  
 `nLength`  
 [in]数据大小 （字节）。  
  
 `data`  
 [in] 用户记录中的对应数据成员。  
  
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
 [COLUMN_NAME_PS_STATUS](../../data/oledb/column-name-ps-status.md)   
 [COLUMN_NAME_PS_LENGTH_STATUS](../../data/oledb/column-name-ps-length-status.md)   
 [COLUMN_NAME_TYPE](../../data/oledb/column-name-type.md)   
 [COLUMN_NAME_TYPE_PS](../../data/oledb/column-name-type-ps.md)   
 [COLUMN_NAME_TYPE_STATUS](../../data/oledb/column-name-type-status.md)