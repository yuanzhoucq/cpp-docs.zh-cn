---
title: "编译器警告 （等级 4） C4233 |Microsoft 文档"
ms.custom: 
ms.date: 10/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4233
dev_langs: C++
helpviewer_keywords: C4233
ms.assetid: 9aa51fc6-8ef3-43b5-bafb-c9333cf60de3
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ad27d2ec3d59df147d8bfc26372a2d25397e651f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4233"></a>编译器警告（等级 4）C4233

> 使用的非标准扩展:*关键字*仅支持在 c + +，不 C 中的关键字

编译器将编译为 C，而不是 c + +，你的源代码，并且你使用仅在 c + + 中有效的关键字。 编译器将源代码文件编译成 C 如果源文件的扩展名是.c 也使用[/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)。

此警告将自动提升为错误。 如果你想要修改此行为，使用[#pragma 警告](../../preprocessor/warning.md)。 例如，若要使 C4233 级别 4 警告问题，可以将此行添加到源代码文件上：

```cpp
#pragma warning(4:4233)
```
