---
title: 编译器警告（等级 1）C4068
ms.date: 11/04/2016
f1_keywords:
- C4068
helpviewer_keywords:
- C4068
ms.assetid: 96a7397a-4eab-44ab-b3bb-36747503f7e5
ms.openlocfilehash: ba6e57fb954e0331e8eede5e7859fbeed5ce6424
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626928"
---
# <a name="compiler-warning-level-1-c4068"></a>编译器警告（等级 1）C4068

未知的杂注

编译器忽略了无法识别的 [杂注](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)。 请确保所使用的的编译器允许使用该 **杂注** 。 下面的示例生成 C4068：

```cpp
// C4068.cpp
// compile with: /W1
#pragma NotAValidPragmaName   // C4068, use valid name to resolve
int main()
{
}
```