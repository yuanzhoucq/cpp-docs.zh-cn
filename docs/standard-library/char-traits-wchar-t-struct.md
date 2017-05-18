---
title: "char_traits&lt;wchar_t&gt; 结构 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- char_traits<wchar_t>
- string/std::char_traits<wchar_t>
dev_langs:
- C++
helpviewer_keywords:
- char_traits<wchar_t> class
ms.assetid: 31f34072-04d6-4871-88fe-48e17d473484
caps.latest.revision: 21
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
ms.openlocfilehash: 8816f9cadccdb1c8b52733c079668f1b07ea54da
ms.contentlocale: zh-cn
ms.lasthandoff: 04/19/2017

---
# <a name="chartraitsltwchartgt-struct"></a>char_traits&lt;wchar_t&gt; 结构
此类是模板结构 **char_traits\<CharType>** 对 `wchar_t` 类型的一个元素的专用化。  
  
## <a name="syntax"></a>语法  
  
```
template <>  
struct char_traits<wchar_t>;
```  
  
## <a name="remarks"></a>备注  
 专用化允许结构利用库函数处理此 `wchar_t` 类型的对象。  
  
## <a name="requirements"></a>要求  
 **标头：** \<string>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [char_traits 结构](../standard-library/char-traits-struct.md)   
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




