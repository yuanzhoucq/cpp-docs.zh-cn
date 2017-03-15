---
title: "编译器错误 C2434 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2434
dev_langs:
- C++
helpviewer_keywords:
- C2434
ms.assetid: 01329e26-7c74-4219-b74f-69e3a40c9738
caps.latest.revision: 6
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
translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 65aac590a3282f2fd71c460d14927f5695fcdc5a
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2434"></a>编译器错误 C2434
symbol︰ 不能在 /clr 中动态初始化 __declspec(process) 用声明的符号︰ 纯模式  
  
 **/Clr: pure**和**/clr: safe**编译器选项不推荐使用 Visual Studio 2015 中。  
  
 不能动态初始化每个进程变量在下的**/clr: pure**。 有关详细信息，请参阅[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)和[过程](../../cpp/process.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2434。  
  
```  
// C2434.cpp  
// compile with: /clr:pure /c  
int f() { return 0; }  
__declspec(process) int i = f();   // C2434  
__declspec(process) int i2 = 0;   // OK  
```
