---
title: 编译器错误 C2434
ms.date: 11/04/2016
f1_keywords:
- C2434
helpviewer_keywords:
- C2434
ms.assetid: 01329e26-7c74-4219-b74f-69e3a40c9738
ms.openlocfilehash: 869db3b49075fa477860e045e59306e22a381ca4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205457"
---
# <a name="compiler-error-c2434"></a>编译器错误 C2434

> "*symbol*"：使用 __declspec （process）声明的符号无法在/clr： pure 模式下动态初始化

## <a name="remarks"></a>备注

**/Clr： pure**和 **/clr： safe**编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。

不能在 **/clr： pure**下动态初始化每个进程变量。 有关详细信息，请参阅[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)和[处理](../../cpp/process.md)。

## <a name="example"></a>示例

下面的示例生成 C2434。 若要解决此问题，请使用常量初始化 `process` 变量。

```cpp
// C2434.cpp
// compile with: /clr:pure /c
int f() { return 0; }
__declspec(process) int i = f();   // C2434
__declspec(process) int i2 = 0;   // OK
```
