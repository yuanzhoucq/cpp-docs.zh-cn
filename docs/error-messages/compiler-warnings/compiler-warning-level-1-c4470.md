---
title: 编译器警告 （等级 1） C4470 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4470
dev_langs:
- C++
helpviewer_keywords:
- C4470
ms.assetid: f52a3eaa-a235-4747-a47d-9ec4ad4cb0ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a660192b11e98bc34871e1f845c872fe27fb9ee
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076978"
---
# <a name="compiler-warning-level-1-c4470"></a>编译器警告（等级 1）C4470

在 /clr 下忽略了浮点控制 pragma

浮点控制杂注：

- [fenv_access](../../preprocessor/fenv-access.md)

- [float_control](../../preprocessor/float-control.md)

- [fp_contract](../../preprocessor/fp-contract.md)

在不起作用[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。

下面的示例生成 C4470:

```
// C4470.cpp
// compile with: /clr /W1 /LD
#pragma float_control(except, on)   // C4470
```