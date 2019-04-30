---
title: 编译器警告（等级 4）C4220
ms.date: 11/04/2016
f1_keywords:
- C4220
helpviewer_keywords:
- C4220
ms.assetid: aba18868-825f-4763-9af6-3296406a80e4
ms.openlocfilehash: 177fb01ba4181f72740724d107fe08e6680ed492
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401106"
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