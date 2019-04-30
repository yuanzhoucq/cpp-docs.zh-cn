---
title: 编译器警告（等级 1）C4742
ms.date: 11/04/2016
f1_keywords:
- C4742
helpviewer_keywords:
- C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
ms.openlocfilehash: 00ac67fec3aafa5a259b5222bd6bb8654210fa61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390420"
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