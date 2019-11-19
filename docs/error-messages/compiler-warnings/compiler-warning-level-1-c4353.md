---
title: 编译器警告（等级1） C4353
ms.date: 11/04/2016
f1_keywords:
- C4353
helpviewer_keywords:
- C4353
ms.assetid: 6e79f186-ed82-4c95-9923-0ad5bb9c4db1
ms.openlocfilehash: f04bc78e1ff6183208f888d9072bfe90b3aca083
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966551"
---
# <a name="compiler-warning-level-1-c4353"></a>编译器警告（等级1） C4353

使用了非标准扩展：常量0作为函数表达式。 改用 "__noop" 函数内部函数

不能将常量零（0）用作函数表达式。 有关详细信息，请参阅[__noop](../../intrinsics/noop.md)。

下面的示例生成 C4353：

```cpp
// C4353.cpp
// compile with: /W1
void MyPrintf(void){};
#define X 0
#if X
   #define DBPRINT MyPrint
#else
   #define DBPRINT 0   // C4353 expected
#endif
int main(){
DBPRINT();
}
```