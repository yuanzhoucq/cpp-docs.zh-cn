---
title: "编译器错误 C3382 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
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
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 782e5c4cc61294dbdaecbd63ff5c6031d387f843
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

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
