---
title: 编译器警告（等级 4）C4204
ms.date: 11/04/2016
f1_keywords:
- C4204
helpviewer_keywords:
- C4204
ms.assetid: 298d2880-6737-448e-b711-15572d540200
ms.openlocfilehash: e16cb9fb59ee6ec24bb9b68dad1be9432d9eee3f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401236"
---
# <a name="compiler-warning-level-4-c4204"></a>编译器警告（等级 4）C4204

使用了非标准扩展： 非常量聚合初始值设定项

通过 Microsoft 扩展 (/Ze)，可以初始化聚合类型 （数组、 结构、 联合和类） 就不是常量的值。

## <a name="example"></a>示例

```
// C4204.c
// compile with: /W4
int func1()
{
   return 0;
}
struct S1
{
   int i;
};

int main()
{
   struct S1 s1 = { func1() };   // C4204
   return s1.i;
}
```

此类初始化将是无效 ANSI 兼容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。