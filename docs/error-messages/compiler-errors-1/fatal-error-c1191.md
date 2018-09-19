---
title: 错误 C1191 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1191
dev_langs:
- C++
helpviewer_keywords:
- C1191
ms.assetid: 2888c6c4-b4e6-449e-8ee0-7917f31086df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: daefec7c89fc98d056963c4f761b7298d6e491cc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062964"
---
# <a name="fatal-error-c1191"></a>错误 C1191

只能在全局范围内导入 dll

指令将 mscorlib.dll 导入使用 /clr 编程的程序不能出现在命名空间或函数，但必须出现在全局范围内。

下面的示例生成 C1191:

```
// C1191.cpp
// compile with: /clr
namespace sample {
   #using <mscorlib.dll>   // C1191 not at global scope
}
```

可能的解决方法：

```
// C1191b.cpp
// compile with: /clr /c
#using <mscorlib.dll>
namespace sample {}
```