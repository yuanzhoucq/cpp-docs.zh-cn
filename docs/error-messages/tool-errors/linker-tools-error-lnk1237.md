---
title: 链接器工具错误 LNK1237
ms.date: 11/04/2016
f1_keywords:
- LNK1237
helpviewer_keywords:
- LNK1237
ms.assetid: 8722ffa8-096a-4bb0-85f9-f3aa0e10872a
ms.openlocfilehash: ae1a397cdcc10cd89fd046a94e78c15dd46dceed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581319"
---
# <a name="linker-tools-error-lnk1237"></a>链接器工具错误 LNK1237

代码在生成期间，编译器引入了对符号 symbol 模块 module 使用 /gl 进行编译中定义的引用

在代码生成期间，编译器不应引入更高版本解析为定义编译的符号 **/GL**。 `symbol` 是已引入和更高版本解析为定义使用编译的符号 **/GL**。

有关详细信息，请参阅 [/GL（全程序优化）](../../build/reference/gl-whole-program-optimization.md)。

若要解决 LNK1237，不编译的符号宽度 **/GL**或使用[/INCLUDE （强制符号引用）](../../build/reference/include-force-symbol-references.md)以强制对符号的引用。

## <a name="example"></a>示例

下面的示例生成 LNK1237。 若要解决此错误，请不要未初始化的数组中 LNK1237_a.cpp 并添加 **/include: __chkstk**到链接命令。

```
// LNK1237_a.cpp
int main() {
   char c[5000] = {0};
}
```

```
// LNK1237_b.cpp
// compile with: /GS- /GL /c LNK1237_a.cpp
// processor: x86
// post-build command: (lib LNK1237_b.obj /LTCG & link LNK1237_a.obj LNK1237_b.lib /nodefaultlib /entry:main /LTCG)
extern "C" void _chkstk(size_t s) {}
```