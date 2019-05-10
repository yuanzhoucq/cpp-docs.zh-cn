---
title: 编译器警告（等级 4）C4131
ms.date: 11/04/2016
f1_keywords:
- C4131
helpviewer_keywords:
- C4131
ms.assetid: 7903b3e1-454f-4be2-aa9b-230992f96a2d
ms.openlocfilehash: 24872bb0b42de77dde358dc29f99826b41638628
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401340"
---
# <a name="compiler-warning-level-4-c4131"></a>编译器警告（等级 4）C4131

“函数”：使用旧样式的声明符

指定的函数声明不是原型形式。

旧样式的函数声明应转换为原型形式。

下面的示例展示一个旧样式的函数声明：

```
// C4131.c
// compile with: /W4 /c
void addrec( name, id ) // C4131 expected
char *name;
int id;
{ }
```

下面的示例展示一个原型形式：

```
void addrec( char *name, int id )
{ }
```