---
title: 编译器错误 C3383 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3383
dev_langs:
- C++
helpviewer_keywords:
- C3383
ms.assetid: ceb7f725-f417-4dc3-8496-0f413bb76687
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b54eda0e29a9876da83b9e3da384a39b9345d5d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33251155"
---
# <a name="compiler-error-c3383"></a>编译器错误 C3383
不支持将“operator new”与 /clr:safe 一起使用  
  
 **/clr:safe** 编译的输出文件可确保是类型安全的，且不支持指针。  
  
 有关详细信息，请参阅  
  
-   [/cgthreads（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)  
  
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