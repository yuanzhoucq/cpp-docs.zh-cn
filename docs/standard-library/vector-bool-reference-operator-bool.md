---
title: vector&lt;bool&gt;::reference::operator bool | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- operatorbool
- vector<bool>::reference::operatorbool
- bool
- std::vector<bool>::reference::operatorbool
dev_langs: C++
helpviewer_keywords:
- BOOL operator
- reference::operator bool
ms.assetid: b0e57869-18cc-4296-9061-da502f30120d
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cbfe1f002c038f5dcc1b3a024891780d56c3572c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="vectorltboolgtreferenceoperator-bool"></a>vector&lt;bool&gt;::reference::operator bool
提供从 `vector<bool>::reference` 到 `bool` 的隐式转换。  
  
## <a name="syntax"></a>语法  
  
```  
operator bool() const;
```  
  
## <a name="return-value"></a>返回值  
 [vector\<bool>](../standard-library/vector-bool-class.md) 对象元素的布尔值。  
  
## <a name="remarks"></a>备注  
 `vector<bool>` 对象无法通过此运算符修改。  
  
## <a name="requirements"></a>惠?  
 **标头：**\<vector>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
 [vector\<bool>::reference 类](../standard-library/vector-bool-reference-class.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)

