---
title: 编译器错误 C2002 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2002
dev_langs:
- C++
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01124fc839d6e788ff2dccae325f01f7d4337f5d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2002"></a>编译器错误 C2002
无效的宽字符常量  
  
 多字节字符常量无效。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  宽字符常量包含比预期更多字节。  
  
2.  标准标头 STDDEF.h 不包括。  
  
3.  不能与普通字符串文本串联宽字符。  
  
4.  宽字符常量的前面必须是字符 L:  
  
    ```  
    L'mbconst'  
    ```  
  
5.  Microsoft c + + 预处理器指令的文本参数必须为 ASCII。 例如，该指令， `#pragma message(L"string")`，而无效。