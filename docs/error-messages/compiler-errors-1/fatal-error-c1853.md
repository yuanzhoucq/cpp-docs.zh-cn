---
title: 错误 C1853 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- devlang-cpp
ms.topic: error-reference
f1_keywords:
- C1853
dev_langs:
- C++
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9aa6a67c13f76b0bf43159b9e9de95068102a2b1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1853"></a>错误 C1853
  
> *filename*预编译标头文件从早期版本的编译器，或者预编译标头为 c + +，在你使用它从 C （或相反）  
  
可能的原因：  
  
-   预编译标头是与以前的编译器版本编译的。 尝试重新编译使用当前编译器的标头。  
  
-   预编译标头为 c + + 和 c。 请尝试重新与 C 一起使用的标头编译通过指定之一从使用[/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)编译器选项，或更改的源文件的后缀为"c"。 有关详细信息，请参阅[预编译代码的两种方法](../../build/reference/creating-precompiled-header-files.md#two-choices-for-precompiling-code)。