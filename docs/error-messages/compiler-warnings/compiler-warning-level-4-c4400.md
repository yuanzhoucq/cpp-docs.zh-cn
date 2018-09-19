---
title: 编译器警告 （等级 C4400 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4400
dev_langs:
- C++
helpviewer_keywords:
- C4400
ms.assetid: f135fe98-4f92-4e07-9d71-2621b36ee755
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd22db0313d2d0ea6494908259e7d098336f6dbd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016190"
---
# <a name="compiler-warning-level-4-c4400"></a>编译器警告（等级 4）C4400

type： 不支持此类型上的 const/volatile 限定符

[Const](../../cpp/const-cpp.md)并[易失性](../../cpp/volatile-cpp.md)限定符不会使用公共语言运行时类型的变量。

## <a name="example"></a>示例

下面的示例生成 C4400。

```
// C4400.cpp
// compile with: /clr /W4
// C4401 expected
using namespace System;
#pragma warning (disable : 4101)
int main() {
   const String^ str;   // C4400
   volatile String^ str2;   // C4400
}
```