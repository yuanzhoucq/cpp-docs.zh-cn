---
title: "错误 C1853 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1853
dev_langs: C++
helpviewer_keywords: C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 05c29c266aad095517734fdcac776e12467d34ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1853"></a>错误 C1853
  
> *filename*预编译标头文件从早期版本的编译器，或者预编译标头为 c + +，在你使用它从 C （或相反）  
  
可能的原因：  
  
-   预编译标头是与以前的编译器版本编译的。 尝试重新编译使用当前编译器的标头。  
  
-   预编译标头为 c + + 和 c。 请尝试重新与 C 一起使用的标头编译通过指定之一从使用[/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)编译器选项，或更改的源文件的后缀为"c"。 有关详细信息，请参阅[预编译代码的两种方法](../../build/reference/creating-precompiled-header-files.md#two-choices-for-precompiling-code)。