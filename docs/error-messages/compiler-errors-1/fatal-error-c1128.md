---
title: 错误 C1128 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1128
dev_langs:
- C++
helpviewer_keywords:
- C1128
ms.assetid: 6f9580fd-ecef-48be-9780-dcf666704279
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1d2604b17b656efab3a3575469eff6a02df960c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1128"></a>错误 C1128
节数超过对象文件格式限制： 请使用 /bigobj 进行编译  
  
 .Obj 文件超出允许的节，COFF 对象文件格式限制的数目。  
  
 达到此部分限制可能是由于使用[/Gy](../../build/reference/gy-enable-function-level-linking.md)和调试版本;**/Gy**导致函数进入自己 COMDAT 节。 在调试版本中，没有用于每个 COMDAT 函数的调试信息节。  
  
 有太多的内联函数时，还可能导致 C1128。  
  
 若要更正此错误，将源文件划分为多个源代码文件，而无需编译 **/Gy**，或使用编译[/bigobj （增加的节数中。Obj 文件）](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md)。  如果您不编译与 **/Gy**，你将需要单独，指定优化由于 **/O2**和 **/O1**均暗指 **/Gy**。  
  
 如果可能，编译不使用调试信息。  
  
 你可能还需要在单独的源的代码文件，具有特定的模板实例，而不是让编译器发出。  
  
 当移植代码，C1128 可能时将出现第一次使用 x64 编译器和很多更高版本与 x86 编译器。 x64 将具有与编译每个函数相关联的至少 4 个节 **/Gy**或内联从模板或类内联： 编码，pdata，和调试信息以及可能 xdata。  X86 无 pdata。