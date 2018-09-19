---
title: 编译器警告 （等级等级 1)c4742 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4742
dev_langs:
- C++
helpviewer_keywords:
- C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 622a1b1cd62024da58191ce1312c391dd39e0d28
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088587"
---
# <a name="compiler-warning-level-1-c4742"></a>编译器警告（等级 1）C4742

var 具有 file1 和 file2 中的不同对齐方式： 数字和数字

外部变量的引用或两个文件中定义这些文件中具有不同的对齐方式。 当编译器发现时，发出此警告`__alignof`中的变量*file1*不同于`__alignof`中的变量*file2*。 这可能在不同文件中声明变量时使用的类型不兼容，或使用不匹配导致`#pragma pack`不同文件中。

若要解决此警告，请使用相同的类型定义或使用不同的变量的名称。

有关详细信息，请参阅[pack](../../preprocessor/pack.md)并[__alignof 运算符](../../cpp/alignof-operator.md)。

## <a name="example"></a>示例

这是定义的类型的第一个文件。

```
// C4742a.c
// compile with: /c
struct X {
   char x, y, z, w;
} global;
```

## <a name="example"></a>示例

下面的示例生成 C4742。

```
// C4742b.c
// compile with: C4742a.c /W1 /GL
// C4742 expected
extern struct X {
   int a;
} global;

int main() {
   global.a = 0;
}
```