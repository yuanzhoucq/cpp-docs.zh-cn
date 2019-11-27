---
title: 编译器警告（等级 4）C4220
ms.date: 11/04/2016
f1_keywords:
- C4220
helpviewer_keywords:
- C4220
ms.assetid: aba18868-825f-4763-9af6-3296406a80e4
ms.openlocfilehash: 781626e20f787bf582605ebd2d4943a7d5f2aa0c
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541917"
---
# <a name="compiler-warning-level-4-c4220"></a>编译器警告（等级 4）C4220

varargs 与剩余的参数匹配

在默认的 Microsoft 扩展（/Ze）下，指向函数的指针与指向具有类似但可变参数的函数的指针匹配。

## <a name="example"></a>示例

```c
// C4220.c
// compile with: /W4

int ( *pFunc1) ( int a, ... );
int ( *pFunc2) ( int a, int b);

int main()
{
   if ( pFunc1 != pFunc2 ) {};  // C4220
}
```

此类指针在 ANSI 兼容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下不匹配。