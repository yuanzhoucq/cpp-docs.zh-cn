---
title: 编译器错误 C2220 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2220
dev_langs:
- C++
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d23476de35e0af45b46a775683ba8673b4959346
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2220"></a>编译器错误 C2220
警告视为错误-没有生成的对象文件  
  
 [/WX](../../build/reference/compiler-option-warning-level.md)告知编译器将所有警告视为错误。 由于发生了错误，未生成对象或可执行文件。  
  
 时，此错误仅出现 **/WX**设置标志，并且在编译期间出现警告。 若要纠正此错误，必须消除项目中的每个警告。  
  
### <a name="to-fix-use-one-of-the-following-techniques"></a>若要纠正错误，请使用以下方法之一  
  
-   解决导致项目中出现警告的问题。  
  
-   在较低警告等级进行编译-例如，使用 **/W3**而不是 **/W4**。  
  
-   使用[警告](../../preprocessor/warning.md)杂注来禁用还是禁止在某个具体的警告。  
  
-   不要使用 **/WX**进行编译。