---
title: "在内联汇编程序内调用 c + + 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- functions [C++], calling in inline assembly
- function calls, C++ functions
- function calls, in inline assembly
- Visual C++, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: 1f0d1eb3-54cf-45d5-838d-958188616b38
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0c91829eac3247255d8fe3cb966a61fca5319f94
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="calling-c-functions-in-inline-assembly"></a>在内联汇编程序内调用 C++ 函数
## <a name="microsoft-specific"></a>Microsoft 专用  
 `__asm` 块只能调用未重载的全局 C++ 函数。 如果调用重载的全局 C++ 函数或 C++ 成员函数，则编译器会发出错误。  
  
 你还可以调用使用声明的任何函数**extern"C"**链接。 这允许`__asm`调用 C 库函数，因为所有标准标头文件都声明库函数具有 c + + 程序中的块**extern"C"**链接。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [内联汇编程序](../../assembler/inline/inline-assembler.md)