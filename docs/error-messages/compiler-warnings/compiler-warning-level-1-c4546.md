---
title: 编译器警告 （等级 1） C4546 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4546
dev_langs:
- C++
helpviewer_keywords:
- C4546
ms.assetid: 071e1709-3841-46c1-8e71-96109cd22041
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0973e657793fe002a3fb6555ec0b0b95aa06e5bf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024791"
---
# <a name="compiler-warning-level-1-c4546"></a>编译器警告（等级 1）C4546

逗号前的函数调用缺少自变量列表

编译器检测到的格式不正确的逗号表达式。

默认情况下，此警告处于关闭状态。 有关详细信息，请参阅 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。

## <a name="example"></a>示例

下面的示例生成 C4546:

```
// C4546.cpp
// compile with: /W1
#pragma warning (default : 4546)
void f(int i) {
   i++;
}

int main() {
   int i = 0, k = 0;

   if ( f, k )   // C4546
   // try the following line instead
   // if ( f(i), k )
      i++;
}
```