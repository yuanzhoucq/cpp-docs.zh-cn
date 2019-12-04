---
title: 错误 C1004
ms.date: 11/04/2016
f1_keywords:
- C1004
helpviewer_keywords:
- C1004
ms.assetid: dbe034b0-6eb0-41b4-a50c-2fccf9e78ad4
ms.openlocfilehash: 82a1a3e410505be53d4356e46d5521aebb72763c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756963"
---
# <a name="fatal-error-c1004"></a>错误 C1004

找到意外的文件结尾

编译器在未解析构造的情况下到达了源文件的结尾。 代码可能缺少以下元素之一：

- 右大括号

- 右括号

- 结束注释标记（*/）

- 分号

若要解决此错误，请检查以下各项：

- 默认磁盘驱动器的临时文件空间不足，需要大约两倍于源文件空间。

- 计算结果为 false 的 `#if` 指令缺少关闭 `#endif` 指令。

- 源文件不以回车符和换行符结尾。

下面的示例生成 C1004：

```cpp
// C1004.cpp
#if TEST
int main() {}
// C1004
```

可能的解决方法：

```cpp
// C1004b.cpp
#if TEST
#endif

int main() {}
```
