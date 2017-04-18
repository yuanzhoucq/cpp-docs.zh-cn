---
title: "编译器错误 C3382 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3382
dev_langs:
- C++
helpviewer_keywords:
- C3382
ms.assetid: a7603abd-ac4e-4ae6-a02b-3bdc6d1908a6
caps.latest.revision: 3
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
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 2cb6ac6aa2409defea2d31591b348b2f2aae403b
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3382"></a>编译器错误 C3382
不支持将“sizeof”与 /clr:safe 一同使用  
  
 **/clr:safe** 编译的输出文件是可验证类型安全的文件，不支持 sizeof ，因为 sizeof 运算符的返回值是 size_t，其大小因操作系统而异。  
  
 有关详细信息，请参阅  
  
-   [sizeof 运算符](../../cpp/sizeof-operator.md)  
  
-   [/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Visual C++ 64 位迁移的常见问题](../../build/common-visual-cpp-64-bit-migration-issues.md)  
  
## <a name="example"></a>示例  
 下面的示例生成 C3382。  
  
```  
// C3382.cpp  
// compile with: /clr:safe  
int main() {  
   sizeof( char );   // C3382  
}  
```
