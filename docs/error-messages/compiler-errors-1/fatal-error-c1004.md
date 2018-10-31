---
title: 错误 C1004
ms.date: 11/04/2016
f1_keywords:
- C1004
helpviewer_keywords:
- C1004
ms.assetid: dbe034b0-6eb0-41b4-a50c-2fccf9e78ad4
ms.openlocfilehash: 13fb8963b33569facf62ccedfe9ce8b7bbbbfdc3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428114"
---
# <a name="fatal-error-c1004"></a>错误 C1004

意外的文件结束

编译器未解析为构造到达源文件的末尾。 代码可能缺少一个下列元素：

- 右大括号

- 右括号

- 结束注释标记 (* /)

- 分号

若要解决此错误，请检查以下：

- 默认磁盘驱动器没有足够的空间用于临时文件，需要大约两倍空间与源文件。

- `#if`指令的计算结果为 false 缺少右`#endif`指令。

- 源文件不以回车符和换行符结尾。

下面的示例生成 C1004:

```
// C1004.cpp
#if TEST
int main() {}
// C1004
```

可能的解决方法：

```
// C1004b.cpp
#if TEST
#endif

int main() {}
```