---
title: _SCL_SECURE_NO_WARNINGS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
dev_langs:
- C++
helpviewer_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
caps.latest.revision: 5
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
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 92cc02c47d4a423cce70a1289a1ce54587a92c2f
ms.contentlocale: zh-cn
ms.lasthandoff: 10/03/2017

---
# <a name="sclsecurenowarnings"></a>_SCL_SECURE_NO_WARNINGS
在 C++ 标准库中，若调用任何一种存在安全威胁的方法，将导致[编译器警告（等级 3）C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 若要禁用此警告，可在代码中将宏定义为 **_SCL_SECURE_NO_WARNINGS**：  
  
```  
#define _SCL_SECURE_NO_WARNINGS  
```  
  
## <a name="remarks"></a>备注  
 禁用 C4996 警告的其他方式包括：  
  
-   使用 [/D（预处理器定义）](../build/reference/d-preprocessor-definitions.md)编译器选项：  
  
 ```  
    cl /D_SCL_SECURE_NO_WARNINGS [other compiler options] myfile.cpp  
```  
  
-   使用 [/w](../build/reference/compiler-option-warning-level.md) 编译器选项：  
  
 ```  
    cl /wd4996 [other compiler options] myfile.cpp  
```  
  
-   使用 [#pragma warning](../preprocessor/warning.md) 指令：  
  
 ```  
 #pragma warning(disable:4996)  
```  
  
 此外，你可以手动更改警告 C4996，其中包含的级别**/w\<l >\< n>** 编译器选项。 例如，可将警告 C4996 设置为级别 4：  
  
```  
cl /w44996 [other compiler options] myfile.cpp  
```  
  
 有关详细信息，请参阅 [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX（警告级别）](../build/reference/compiler-option-warning-level.md)。  
  
## <a name="see-also"></a>另请参阅  
 [安全库：C++ 标准库](../standard-library/safe-libraries-cpp-standard-library.md)


