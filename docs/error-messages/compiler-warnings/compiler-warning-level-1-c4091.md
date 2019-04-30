---
title: 编译器警告 （等级 1） C4091
ms.date: 11/04/2016
f1_keywords:
- C4091
helpviewer_keywords:
- C4091
ms.assetid: 3a404967-ab42-49b0-b324-fd7ba1859d78
ms.openlocfilehash: 87432a74dfe7c09a52f436d4e91b3f70eb66856b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410442"
---
# <a name="compiler-warning-level-1-c4091"></a>编译器警告 （等级 1） C4091

keyword： 没有声明变量时忽略角的 type

编译器检测到用户可能预期的变量声明，但编译器无法声明变量的情况。

## <a name="example"></a>示例

一个`__declspec`用户定义类型声明的开始处的特性应用于该类型的变量。 C4091 指示没有声明变量。 下面的示例生成 C4091。

```
// C4091.cpp
// compile with: /W1 /c
__declspec(dllimport) class X {}; // C4091

// __declspec attribute applies to varX
__declspec(dllimport) class X2 {} varX;

// __declspec attribute after the class or struct keyword
// applies to user defined type
class __declspec(dllimport) X3 {};
```

## <a name="example"></a>示例

如果标识符是一个 typedef，它也不能为变量的名称。 下面的示例生成 C4091。

```
// C4091_b.cpp
// compile with: /c /W1 /WX
#define LIST 4
typedef struct _LIST {} LIST;   // C4091
```