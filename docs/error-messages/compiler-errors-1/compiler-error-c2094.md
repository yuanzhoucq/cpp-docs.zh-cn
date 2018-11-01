---
title: 编译器错误 C2094
ms.date: 11/04/2016
f1_keywords:
- C2094
helpviewer_keywords:
- C2094
ms.assetid: 9e4f8f88-f189-46e7-91c9-481bacc7af87
ms.openlocfilehash: 072c51ca4ae25c6f51b1841ea129a7b4fb495bdf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50529826"
---
# <a name="compiler-error-c2094"></a>编译器错误 C2094

标签“identifier”未定义

通过 [goto](../../cpp/goto-statement-cpp.md) 语句使用的标签在函数中不存在。

## <a name="example"></a>示例

以下示例生成 C2094：

```cpp
// C2094.c
int main() {
   goto test;
}   // C2094
```

可能的解决方法：

```cpp
// C2094b.c
int main() {
   goto test;
   test:
   {
   }
}
```