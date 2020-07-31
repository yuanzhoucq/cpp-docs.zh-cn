---
title: 编译器警告（等级 1）C4742
ms.date: 07/22/2020
f1_keywords:
- C4742
helpviewer_keywords:
- C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
ms.openlocfilehash: e6ecd082a9f6d690414761d11d3a0adf101f87c2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233231"
---
# <a name="compiler-warning-level-1-c4742"></a>编译器警告（等级 1）C4742

> "*file1*" 和 "*file2*" 中的 "*variable*" 对齐方式不同：*数字 1*和*数字 2*

在两个文件中引用或定义的外部变量在这些文件中的对齐方式有所不同。

## <a name="remarks"></a>备注

当编译器发现 **`alignof`** *file1*中的变量与 **`alignof`** *file2*中的变量的不同时，将发出此警告。 这可能是由于在不同文件中声明变量时使用了不兼容的类型，或者 `#pragma pack` 在不同的文件中使用了非匹配。

若要解决此警告，请使用相同的类型定义或对变量使用不同的名称。

有关详细信息，请参阅 [`pack`](../../preprocessor/pack.md) 和[ `alignof` 运算符](../../cpp/alignof-operator.md)。

## <a name="example"></a>示例

这是定义该类型的第一个文件。

```c
// C4742a.c
// compile with: /c
struct X {
   char x, y, z, w;
} global;
```

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
