---
title: "assert 函数输出的诊断 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 50a41f3b25a616718cffd4dcd8bce0a1ca4e0932
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="diagnostic-printed-by-the-assert-function"></a>assert 函数输出的诊断
**ANSI 4.2** assert 函数输出的诊断和终止行为  
  
 如果表达式为 false (0)，则 assert 函数将输出诊断消息并调用 abort 例程。 诊断消息具有以下形式  
  
 **Assertion failed**: expression**, file** filename**, line** linenumber  
  
 其中，filename 是源文件的名称，linenumber 是源文件中失败的断言的行号。 如果表达式为 true（非零），则不执行任何操作。  
  
## <a name="see-also"></a>另请参阅  
 [库函数](../c-language/library-functions.md)
