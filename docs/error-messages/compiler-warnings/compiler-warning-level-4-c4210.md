---
title: 编译器警告（等级 4）C4210
ms.date: 11/04/2016
f1_keywords:
- C4210
helpviewer_keywords:
- C4210
ms.assetid: f8600adf-dfe2-4022-a37a-3d4997641dfd
ms.openlocfilehash: 3435e18f60568cad390dcb0ef7900658a21ea959
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401184"
---
# <a name="compiler-warning-level-4-c4210"></a>编译器警告（等级 4）C4210

使用了非标准扩展： 函数给定文件范围

与默认 Microsoft 扩展 ([/Ze](../../build/reference/za-ze-disable-language-extensions.md))，函数声明具有文件范围。

```
// C4210.c
// compile with: /W4 /c
void func1()
{
   extern int func2( double );   // C4210 expected
}

int main()
{
   func2( 4 );   //  /Ze passes 4 as type double
}                //  /Za passes 4 as type int
```

此扩展可以防止您的代码移植到其他编译器。