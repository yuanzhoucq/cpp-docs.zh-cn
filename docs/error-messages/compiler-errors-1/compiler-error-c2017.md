---
title: 编译器错误 C2017 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2017
dev_langs:
- C++
helpviewer_keywords:
- C2017
ms.assetid: 1083eed9-9906-4a97-883c-54e52d7e82cd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f547501ab399165fe256f0dc3d0423b3569c05e7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062197"
---
# <a name="compiler-error-c2017"></a>编译器错误 C2017

非法的转义序列

转义序列，如 \t，出现外的字符或字符串常量。

下面的示例生成 C2017:

```
// C2017.cpp
int main() {
   char test1='a'\n;   // C2017
   char test2='a\n';   // ok
}
```

当 stringize 运算符用于包含转义序列的字符串，则会发生 C2017。

下面的示例生成 C2017:

```
// C2017b.cpp
#define TestDfn(x) AfxMessageBox(#x)
TestDfn(CString("\\") + CString(".h\"\n\n"));   // C2017
```