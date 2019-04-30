---
title: 编译器错误 C2130
ms.date: 11/04/2016
f1_keywords:
- C2130
helpviewer_keywords:
- C2130
ms.assetid: c6fd5a7e-8f28-4f67-99d1-95a13b0dff90
ms.openlocfilehash: aee0931926cad2ac30631c152aeb94bfd24befd2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397596"
---
# <a name="compiler-error-c2130"></a>编译器错误 C2130

\#行应为包含文件名，却找到 token 字符串

在 [#line](../../preprocessor/hash-line-directive-c-cpp.md) `linenumber` 后面的可选文件名标记必须是字符串。

以下示例生成 C2130:

```
// C2130.cpp
int main() {
   #line 1000 test   // C2130
   #line 1000 "test"   // OK
}
```