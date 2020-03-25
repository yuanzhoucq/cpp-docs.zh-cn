---
title: 编译器警告（等级 1）C4224
ms.date: 11/04/2016
f1_keywords:
- C4224
helpviewer_keywords:
- C4224
ms.assetid: 1531cae0-5040-49fd-b149-005bb5085391
ms.openlocfilehash: e2e6cde3cc3c6d3032bfbf4e81959ae791a91981
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199779"
---
# <a name="compiler-warning-level-1-c4224"></a>编译器警告（等级 1）C4224

使用了非标准扩展：形参 "identifier" 以前被定义为类型

标识符以前用作 `typedef`。 这会在 ANSI 兼容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下产生警告。

## <a name="example"></a>示例

```cpp
// C4224.cpp
// compile with: /Za /W1 /LD
typedef int I;
void func ( int I );  // C4224
```
