---
title: 编译器错误 C2873 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2873
dev_langs:
- C++
helpviewer_keywords:
- C2873
ms.assetid: 7a10036b-400e-4364-bd2f-dcd7370c5e28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 94a04d650729bdda949754c5070a6c307d390929
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33244373"
---
# <a name="compiler-error-c2873"></a>编译器错误 C2873
symbol： 符号不能在 using 声明  
  
 A`using`指令是缺少[命名空间](../../cpp/namespaces-cpp.md)关键字。 这将导致编译器错误地解释为代码[using 声明](../../cpp/using-declaration.md)而不是[using 指令](../../cpp/namespaces-cpp.md#using_directives)。