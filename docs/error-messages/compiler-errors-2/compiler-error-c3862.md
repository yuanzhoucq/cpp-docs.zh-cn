---
title: "编译器错误 C3862 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3862
dev_langs:
- C++
helpviewer_keywords:
- C3862
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: af959252ce5b404d8646ad61e02c5e480b41ed83
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3862"></a>编译器错误 C3862
function： 无法编译非托管的函数使用 /clr: pure 或 /clr: safe  
  
 **/clr:pure** 和 **/clr:safe** 编译器选项在 Visual Studio 2015 中已弃用。  
  
 使用编译**/clr: pure**或**/clr: safe**将生成仅 MSIL 映像，不包含本机 （非托管） 代码的映像。  因此，不能使用`unmanaged`中的杂注**/clr: pure**或**/clr: safe**编译。  
  
 有关详细信息，请参阅[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)和[managed、 unmanaged](../../preprocessor/managed-unmanaged.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3862:  
  
```  
// C3862.cpp  
// compile with: /clr:pure /c  
#pragma unmanaged  
void f() {}   // C3862  
```
