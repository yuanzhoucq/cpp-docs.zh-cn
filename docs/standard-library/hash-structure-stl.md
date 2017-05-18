---
title: "hash 结构（C++ 标准库）| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- thread/std::hash
dev_langs:
- C++
ms.assetid: 4a8bf5bc-4334-4070-936b-98585f8a073b
caps.latest.revision: 13
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: 1af8dc2f8fef535883088c413827a98a35539980
ms.contentlocale: zh-cn
ms.lasthandoff: 04/19/2017

---
# <a name="hash-structure-c-standard-library"></a>hash 结构（C++ 标准库）
定义一个成员函数，该函数返回一个由 `Val` 唯一决定的值。 此成员函数定义一个 [hash](../standard-library/hash-class.md) 函数，此函数适用于将 `thread::id` 类型的值映射到索引值的分布。  
  
## <a name="syntax"></a>语法  
  
```  
template <>  
struct hash<thread::id> :   
    public unary_function<thread::id, size_t>  
{  
    size_t operator()(thread::id Val) const;

 
};  
```  
  
## <a name="requirements"></a>要求  
 **标头︰** \<线程 >  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<thread>](../standard-library/thread.md)   
 [unary_function 结构](../standard-library/unary-function-struct.md)

