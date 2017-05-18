---
title: "stdext 命名空间 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- stdext
dev_langs:
- C++
helpviewer_keywords:
- _DEFINE_DEPRECATED_HASH_CLASSES symbol
- stdext namespace
ms.assetid: 3e94fc89-0584-424f-bc09-081b73379545
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 213b760a134a645a0b6552e4c3600fc4762b0bb2
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="stdext-namespace"></a>stdext 命名空间
[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员当前不是 ISO C++ 标准的一部分。 因此，这些类型和成员已从 `std` 命名空间移动到命名空间 `stdext`以保持符合 C++ 标准。  
  
 当使用默认的 [/Ze](../build/reference/za-ze-disable-language-extensions.md) 进行编译时，该编译器将针对 <hash_map> 和 <hash_set> 头文件的成员警告 `std` 的使用。 若要禁用该警告，请使用[警告](../preprocessor/warning.md)杂注。  
  
 若要在针对 <hash_map> 和 <hash_set> 头文件的成员使用 `std` 时让编译器生成错误和 **/Ze**，则在包括任何 C++ 标准库头文件之前添加以下指令。  
  
```  
#define _DEFINE_DEPRECATED_HASH_CLASSES 0  
```  
  
 使用 **/Za**进行编译时，该编译器将生成一个错误。  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库概述](../standard-library/cpp-standard-library-overview.md)


