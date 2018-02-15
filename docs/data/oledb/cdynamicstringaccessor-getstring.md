---
title: CDynamicStringAccessor::GetString | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicStringAccessor.GetString
- CDynamicStringAccessor::GetString
dev_langs:
- C++
helpviewer_keywords:
- GetString method
ms.assetid: 4af27f27-7589-49f5-93d8-6ef05c023c8a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9c3ccef4046928be7ce62c845c99538f894bd1b3
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="cdynamicstringaccessorgetstring"></a>CDynamicStringAccessor::GetString
将指定列数据作为字符串检索。  
  
## <a name="syntax"></a>语法  
  
```cpp
      BaseType* GetString(DBORDINAL nColumn) const throw();  

BaseType* GetString(const CHAR* pColumnName) const throw();  

BaseType* GetString(const WCHAR* pColumnName) const throw();  
```  
  
#### <a name="parameters"></a>参数  
 `nColumn`  
 [in] 列号。 列编号从 1 开始。 值为 0 引用的书签列中，如果有的话。  
  
 `pColumnName`  
 [in]指向包含列名的字符串的指针。  
  
## <a name="return-value"></a>返回值  
 从指定的列检索到的字符串值的指针。 值的类型是***BaseType***，这将是**CHAR**或**WCHAR**具体取决于是否定义了是否的 _UNICODE。 如果找不到指定的列，返回 NULL。  
  
## <a name="remarks"></a>备注  
 第二个重写窗体采用的列名称为 ANSI 字符串。 第三个重写窗体采用的列名称为 Unicode 字符串。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDynamicStringAccessor 类](../../data/oledb/cdynamicstringaccessor-class.md)