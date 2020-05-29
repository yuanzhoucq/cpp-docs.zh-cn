---
title: 编译器警告（等级 1）C4742
ms.date: 11/04/2016
f1_keywords:
- C4742
helpviewer_keywords:
- C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
ms.openlocfilehash: af97c72f496177d2e94cf18f9685ac33c5e62404
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185654"
---
# <a name="compiler-warning-level-1-c4742"></a>编译器警告（等级 1）C4742

"var" 在 "file1" 和 "file2" 中具有不同的对齐方式： number 和 number

在两个文件中引用或定义的外部变量在这些文件中的对齐方式有所不同。 当编译器发现*file1*中的变量 `__alignof` 与*file2*中的变量 `__alignof` 不同时，将发出此警告。 这可能是由于在不同文件中声明变量时使用了不兼容的类型，或者使用了不同文件中的非匹配 `#pragma pack`。

若要解决此警告，请使用相同的类型定义或对变量使用不同的名称。

有关详细信息，请参阅[pack](../../preprocessor/pack.md)和[__alignof 运算符](../../cpp/alignof-operator.md)。

## <a name="example"></a>示例

这是定义该类型的第一个文件。

```c
// C4742a.c
// compile with: /c
struct X {
   char x, y, z, w;
} global;
```

## <a name="example"></a>示例

下面的示例生成 C4742。

```c
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
