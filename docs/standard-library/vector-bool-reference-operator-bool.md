---
title: vector&lt;bool&gt;::reference::operator bool | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- operatorbool
- vector<bool>::reference::operatorbool
- bool
- std::vector<bool>::reference::operatorbool
dev_langs:
- C++
helpviewer_keywords:
- BOOL operator
- reference::operator bool
ms.assetid: b0e57869-18cc-4296-9061-da502f30120d
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: acc0ecd4edaf1e58977dcbdeb483d497a72bc4c8
ms.openlocfilehash: f79b54237aa3a3b53000aaa47ef6a8e198ed6725
ms.lasthandoff: 02/24/2017

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
  
## <a name="requirements"></a>要求  
 **标头：**\<vector>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [vector\<bool>::reference 类](../standard-library/vector-bool-reference-class.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)


