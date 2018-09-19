---
title: 编译器警告 （等级 C4220 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4220
dev_langs:
- C++
helpviewer_keywords:
- C4220
ms.assetid: aba18868-825f-4763-9af6-3296406a80e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70c6b104c924a09570d4bd77191f1df715726370
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118773"
---
# <a name="compiler-warning-level-4-c4220"></a>编译器警告（等级 4）C4220

varargs 与剩余的参数相匹配

在默认的 Microsoft 扩展 (/Ze) 中，指向函数的匹配到具有相似，但变量、 参数的函数的指针。

## <a name="example"></a>示例

```
// C4220.c
// compile with: /W4

int ( *pFunc1) ( int a, ... );
int ( *pFunc2) ( int a, int b);

int main()
{
   if ( pFunc1 != pFunc2 ) {};  // C4220
}
```

此类指针不匹配在 ANSI 兼容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。