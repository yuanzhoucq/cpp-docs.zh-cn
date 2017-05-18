---
title: "&lt;ccomplex&gt; | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <ccomplex>
dev_langs:
- C++
ms.assetid: a9fcb5f0-88e3-464b-a5fd-d1afb8cd7e6f
caps.latest.revision: 15
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
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 63374ad7a56060da78621e9543f38dcfe8a06ae7
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="ltccomplexgt"></a>&lt;ccomplex&gt;
包含 C++ 标准库标头 [\<complex>](../standard-library/complex.md)，它可有效地包含标准 C 库标头 \<complex.h>，并将关联名称添加到 `std` 命名空间。  
  
## <a name="syntax"></a>语法  
  
```cpp  
#include <ccomplex>  
  
```  
  
## <a name="remarks"></a>备注  
 包含该标头还将确保使用标准 C 库标头中的外部链接声明的名称在 `std` 命名空间中声明。  
  
 未在 `std` 命名空间中定义 \<complex.h> 中声明的名称 `clog`，因为这可能会与 [\<iostream>](../standard-library/iostream.md) 中声明的 `clog` 发生冲突。  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 标准库概述](../standard-library/cpp-standard-library-overview.md)




