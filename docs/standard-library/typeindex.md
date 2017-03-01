---
title: '&lt;typeindex&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <typeindex>
dev_langs:
- C++
ms.assetid: a9551137-f74b-4f02-af64-ff00214cea1f
caps.latest.revision: 14
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
ms.sourcegitcommit: 2d05749ba2837a3879c91886b9266de47dd2ece6
ms.openlocfilehash: 4279c10994de9247819e58a06276ef9690b39bb8
ms.lasthandoff: 02/24/2017

---
# <a name="lttypeindexgt"></a>&lt;typeindex&gt;
包括标准标头 \<typeindex>，以定义支持类 [type_info](../cpp/type-info-class.md) 的对象索引的类和函数。  
  
## <a name="syntax"></a>语法  
  
```cpp  
#include <typeindex>  
```  
  
## <a name="remarks"></a>备注  
 [hash 结构](../standard-library/hash-structure.md)可定义适合将 [type_index](../standard-library/type-index-class.md) 类型的值映射到索引值的分布的 `hash function`。  
  
 `type_index` 类包装指向 `type_info` 对象的指针，以便辅助编写索引。  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)




