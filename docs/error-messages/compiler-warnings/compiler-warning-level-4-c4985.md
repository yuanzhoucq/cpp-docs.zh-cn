---
title: "编译器警告 （等级 4） C4985 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: C4985
ms.assetid: 832f001c-afe7-403d-a8b4-02334724c79e
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cb2b95e10a5a5e2b6fcaf67ab41880580267ec7a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4985"></a>编译器警告（等级 4）C4985
“symbol name”: 先前声明中不存在特性。  
  
 当前方法声明或定义上的 Microsoft 源代码注释语言 (SAL) 注释与早期声明上的注释不同。 方法的定义和声明中必须使用相同的 SAL 注释。  
  
 SAL 提供一组可用于描述函数如何使用参数的注释、其关于参数的假设，以及就完成所作的保证。 注释是在 sal.h 头文件中定义的。  
  
 请注意，除非项目具有指定的 [/analyze](../../build/reference/analyze-code-analysis.md) 标志，否则 SAL 宏将不会展开。 在指定 **/analyze**时，即使警告和错误均显示有 **/analyze**，编译器也会引发 C4985。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
1.  在方法的定义及其所有声明上使用相同的 SAL 注释。  
  
## <a name="see-also"></a>请参阅  
 [SAL 批注](../../c-runtime-library/sal-annotations.md)