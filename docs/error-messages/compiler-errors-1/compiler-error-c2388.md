---
title: 编译器错误 C2388 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2388
dev_langs:
- C++
helpviewer_keywords:
- C2388
ms.assetid: 764ad2d7-cb04-425f-ba30-70989488c4a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b6bcec4f5f218a52981a7770f5fa6e600494d9a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114145"
---
# <a name="compiler-error-c2388"></a>编译器错误 C2388

symbol： 不能使用这两个 __declspec 声明一个符号和\__declspec(process)

`appdomain` 和 `process` `__declspec` 修饰符不能用于相同的符号。 变量的存储空间按进程或按应用程序域存在。

有关详细信息，请参见 [应用程序域](../../cpp/appdomain.md) 和 [过程](../../cpp/process.md)。

以下示例生成 C2388：

```
// C2388.cpp
// compile with: /clr /c
__declspec(process) __declspec(appdomain) int i;   // C2388
__declspec(appdomain) int i;   // OK
```