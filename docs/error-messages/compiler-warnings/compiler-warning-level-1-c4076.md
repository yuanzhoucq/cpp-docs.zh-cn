---
title: 编译器警告（等级 1）C4076
ms.date: 11/04/2016
f1_keywords:
- C4076
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
ms.openlocfilehash: 77efeae27a67ea844759fd9980801d3daf788e89
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200249"
---
# <a name="compiler-warning-level-1-c4076"></a>编译器警告（等级 1）C4076

> "*type 修饰符*"：不能与 "*typename*" 类型一起使用

## <a name="remarks"></a>备注

类型修饰符（无论是**有符号**还是**无符号**）不能用于非整数类型。 已忽略*type 修饰符*。

## <a name="example"></a>示例

下面的示例生成 C4076;若要修复此问题，请删除**无符号**类型修饰符：

```cpp
// C4076.cpp
// compile with: /W1 /LD
unsigned double x;   // C4076
```
