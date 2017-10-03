---
title: "is_move_constructible 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- type_traits/std::is_move_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 9498029f431b287312583f78effc5197fc097fd6
ms.contentlocale: zh-cn
ms.lasthandoff: 10/03/2017

---
# <a name="ismoveconstructible-class"></a>is_move_constructible 类
测试类型是否具有移动构造函数。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>  
struct is_move_constructible;
```  
  
#### <a name="parameters"></a>参数  
 T  
 要计算的类型  
  
## <a name="remarks"></a>备注  
 如果类型 `T` 可通过使用移动操作构造，则类型谓词的计算结果为 true。 此谓词等效于 `is_constructible<T, T&&>`。  
  
## <a name="requirements"></a>要求  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [<type_traits>](../standard-library/type-traits.md)




