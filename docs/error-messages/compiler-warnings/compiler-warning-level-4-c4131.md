---
title: 编译器警告 （等级 C4131 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4131
dev_langs:
- C++
helpviewer_keywords:
- C4131
ms.assetid: 7903b3e1-454f-4be2-aa9b-230992f96a2d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 43de917b2a6aff38602a6118e599c0d9df262a70
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033181"
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