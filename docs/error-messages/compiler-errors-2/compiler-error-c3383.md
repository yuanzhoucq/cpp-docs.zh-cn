---
title: "编译器错误 C3383 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3383
dev_langs:
- C++
helpviewer_keywords:
- C3383
ms.assetid: ceb7f725-f417-4dc3-8496-0f413bb76687
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 2a97cd1348bc927b633e683bed80a6b907f88a58
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3383"></a>编译器错误 C3383
不支持将“operator new”与 /clr:safe 一起使用  
  
 **/clr:safe** 编译的输出文件可确保是类型安全的，且不支持指针。  
  
 有关详细信息，请参阅  
  
-   [/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Visual C++ 64 位迁移的常见问题](../../build/common-visual-cpp-64-bit-migration-issues.md)  
  
## <a name="example"></a>示例  
 下面的示例生成 C3383。  
  
```  
// C3383.cpp  
// compile with: /clr:safe  
int main() {  
   char* pCharArray = new char[256];  // C3383  
}  
```
