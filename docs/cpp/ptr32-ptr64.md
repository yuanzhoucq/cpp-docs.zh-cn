---
title: "__ptr32、 __ptr64 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __ptr32_cpp
- __ptr64_cpp
- __ptr32
- __ptr64
dev_langs:
- C++
helpviewer_keywords:
- __ptr64 keyword [C++]
- _ptr32 keyword [C++]
- ptr32 keyword [C++]
- ptr64 keyword [C++]
- _ptr64 keyword [C++]
- __ptr32 keyword [C++]
ms.assetid: afb563d8-7458-4fe7-9c30-bd4b5385a59f
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: d722f8403efbe1172fefbe8a792c95d4063e893f
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="ptr32-ptr64"></a>__ptr32、__ptr64
## <a name="microsoft-specific"></a>Microsoft 专用  
 `__ptr32` 表示 32 位系统中的本机指针，而 `__ptr64` 表示 64 位系统中的本机指针。  
  
 以下示例演示如何声明所有这些指针类型：  
  
```  
int * __ptr32 p32;  
int * __ptr64 p64;  
```  
  
 在 32 位系统中，使用 `__ptr64` 声明的指针被截断为 32 位指针。 在 64 位系统中, 使用 `__ptr32` 声明的指针被强制转换为 64 位指针。  
  
> [!NOTE]
>  不能使用`__ptr32`或`__ptr64`编译时**/clr: pure**。 否则，将生成 `Compiler Error C2472`。 **/clr:pure** 和 **/clr:safe** 编译器选项在 Visual Studio 2015 中已弃用。  
  
## <a name="example"></a>示例  
 以下示例演示如何使用 `__ptr32` 和 `__ptr64` 关键字声明和分配指针。  
  
```  
#include <cstdlib>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
  
    int * __ptr32 p32;  
    int * __ptr64 p64;  
  
    p32 = (int * __ptr32)malloc(4);  
    *p32 = 32;  
    cout << *p32 << endl;  
  
    p64 = (int * __ptr64)malloc(4);  
    *p64 = 64;  
    cout << *p64 << endl;  
}  
```  
  
```Output  
32  
64  
```  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [基本类型](../cpp/fundamental-types-cpp.md)
