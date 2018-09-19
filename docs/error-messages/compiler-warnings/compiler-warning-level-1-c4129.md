---
title: 编译器警告 （等级 1） C4129 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4129
dev_langs:
- C++
helpviewer_keywords:
- C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e02f38044180c45e221099d2874b7f8ff48d62f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098440"
---
# <a name="compiler-warning-level-1-c4129"></a>编译器警告 （等级 1） C4129

character： 无法识别的字符转义序列

`character`反斜杠 (\\) 中的字符或字符串常量未识别为有效的转义序列。 反斜杠被忽略，不打印。 打印对反斜杠后面的字符。

若要打印单个反斜杠，请指定双反斜杠 (\\\\)。

C + + 标准，2.13.2 节中的讨论了转义序列。

下面的示例生成 C4129:

```
// C4129.cpp
// compile with: /W1
int main() {
   char array1[] = "\/709";   // C4129
   char array2[] = "\n709";   // OK
}
```