---
title: 编译器错误 C3393
ms.date: 11/04/2016
f1_keywords:
- C3393
helpviewer_keywords:
- C3393
ms.assetid: d57f7c69-0a02-4fe3-9e45-bc62644fd77c
ms.openlocfilehash: 5147e3e406fde73a05b7069e2a9336f27b3db622
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58767127"
---
# <a name="compiler-error-c3393"></a>编译器错误 C3393

constraint 子句有语法错误：“identifier”不是一个类型

传递给约束的标识符必须是一种类型，但该标识符不是一种类型。  有关详细信息，请参阅[泛型类型参数的约束 (C + + CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)。

## <a name="example"></a>示例

以下示例生成 C3393：

```
// C3393.cpp
// compile with: /clr /c
void MyInterface() {}
interface class MyInterface2 {};

generic<typename T>
where T : MyInterface   // C3393
// try the following line instead
// where T : MyInterface2
ref class R {};
```