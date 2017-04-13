---
title: "编译器警告 （等级 4） C4985 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- C4985
ms.assetid: 832f001c-afe7-403d-a8b4-02334724c79e
caps.latest.revision: 6
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
ms.openlocfilehash: 4a36692420ea9d5547f236c1e5dfeaa269afbb67
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-4-c4985"></a>编译器警告（等级 4）C4985
“symbol name”: 先前声明中不存在特性。  
  
 当前方法声明或定义上的 Microsoft 源代码注释语言 (SAL) 注释与早期声明上的注释不同。 方法的定义和声明中必须使用相同的 SAL 注释。  
  
 SAL 提供一组可用于描述函数如何使用参数的注释、其关于参数的假设，以及就完成所作的保证。 注释是在 sal.h 头文件中定义的。  
  
 请注意，除非项目具有，否则 SAL 宏将不会展开[/ 分析](../../build/reference/analyze-code-analysis.md)指定的标志。 在指定 **/analyze**时，即使警告和错误均显示有 **/analyze**，编译器也会引发 C4985。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
1.  在方法的定义及其所有声明上使用相同的 SAL 注释。  
  
## <a name="see-also"></a>另请参阅  
 [SAL 批注](../../c-runtime-library/sal-annotations.md)
