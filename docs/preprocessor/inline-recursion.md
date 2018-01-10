---
title: "inline_recursion |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- inline_recursion_CPP
- vc-pragma.inline_recursion
dev_langs: C++
helpviewer_keywords:
- pragmas, inline_recursion
- inline_recursion pragma
ms.assetid: cfef5791-63b7-45ac-9574-623747b9b9c9
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d749753e7eaf81284de72314f5f940fd2790962c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="inlinerecursion"></a>inline_recursion
控制直接或相互递归函数调用的内联扩展。  
  
## <a name="syntax"></a>语法  
  
```  
  
#pragma inline_recursion( [{on | off}] )  
```  
  
## <a name="remarks"></a>备注  
 使用此杂注对控件函数标记为[内联](../cpp/inline-functions-cpp.md)和[__inline](../cpp/inline-functions-cpp.md)或编译器在 /Ob2 选项下自动扩展的函数。 使用此杂注要求[/Ob](../build/reference/ob-inline-function-expansion.md)编译器选项设置为 1 或 2。 `inline_recursion` 的默认状态为关闭。 此杂注在出现后在第一个函数调用处生效，并且不会影响函数的定义。  
  
 `inline_recursion` 杂注控制如何扩展递归函数。 如果 `inline_recursion` 处于关闭状态，并且内联函数调用自身（直接或间接），则该函数仅扩展一次。 如果`inline_recursion`处于打开状态，该函数将扩展多次，直到它达到与设置的值[inline_depth](../preprocessor/inline-depth.md)杂注定义的递归函数的默认值`inline_depth`杂注或容量限制.  
  
## <a name="see-also"></a>请参阅  
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [inline_depth](../preprocessor/inline-depth.md)   
 [/Ob （内联函数扩展）](../build/reference/ob-inline-function-expansion.md)