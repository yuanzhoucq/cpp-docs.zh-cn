---
title: "编译器错误 C2812 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2812
dev_langs:
- C++
helpviewer_keywords:
- C2812
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
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
ms.openlocfilehash: 358d0d3a5c7f0129d74be70c3309337542807d1d
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2812"></a>编译器错误 C2812
\#导入不支持使用 /clr: pure 和 /clr: safe  
  
 **/Clr: pure**和**/clr: safe**编译器选项不推荐使用 Visual Studio 2015 中。  
  
 [#import 指令](../../preprocessor/hash-import-directive-cpp.md)不支持**/clr: pure**和**/clr: safe**因为`#import`需要本机编译器支持库使用。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2812。  
  
```  
// C2812.cpp  
// compile with: /clr:pure /c  
#import "importlib.tlb"   // C2812  
```
