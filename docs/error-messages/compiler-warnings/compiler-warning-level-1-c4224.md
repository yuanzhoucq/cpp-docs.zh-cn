---
title: 编译器警告（等级1） C4224
ms.date: 11/04/2016
f1_keywords:
- C4224
helpviewer_keywords:
- C4224
ms.assetid: 1531cae0-5040-49fd-b149-005bb5085391
ms.openlocfilehash: 2ac7c49f33c052c895c71ca1dc3ce60be8dd9c8d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627295"
---
# <a name="compiler-warning-level-1-c4224"></a>编译器警告（等级1） C4224

使用了非标准扩展：形参 "identifier" 以前被定义为类型

标识符以前用作 `typedef`。 这会在 ANSI 兼容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下产生警告。

## <a name="example"></a>示例

```cpp
// C4224.cpp
// compile with: /Za /W1 /LD
typedef int I;
void func ( int I );  // C4224
```