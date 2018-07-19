---
title: 编译器错误 C2097 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2097
dev_langs:
- C++
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa4b867c7f043d796f208fdc7100509893147daf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33168355"
---
# <a name="compiler-error-c2097"></a>编译器错误 C2097
初始化非法  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  使用一个非常量值变量的初始化。  
  
2.  使用长地址短地址初始化。  
  
3.  初始化的局部结构、 联合或数组时，用非常量表达式使用编译 **/Za**。  
  
4.  初始化包含逗号运算符的表达式。  
  
5.  既不常量，也不符号的表达式初始化。