---
title: 编译器警告（等级 1）C4076
ms.date: 11/04/2016
f1_keywords:
- C4076
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
ms.openlocfilehash: 3a56e58d9bec1034a55f4e588dbddd0dba03f348
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437019"
---
# <a name="compiler-warning-level-1-c4076"></a>编译器警告（等级 1）C4076

> '*的类型修饰符*： 不能使用类型*typename*

## <a name="remarks"></a>备注

类型修饰符，它是否**签名**或**无符号**，不能用于非整数类型。 *类型修饰符*将被忽略。

## <a name="example"></a>示例

下面的示例生成 C4076;若要修复此错误，请删除**无符号**类型修饰符：

```cpp
// C4076.cpp
// compile with: /W1 /LD
unsigned double x;   // C4076
```