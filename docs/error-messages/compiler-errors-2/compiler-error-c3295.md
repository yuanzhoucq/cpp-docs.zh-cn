---
title: 编译器错误 C3295
ms.date: 11/04/2016
f1_keywords:
- C3295
helpviewer_keywords:
- C3295
ms.assetid: 83f0aa4d-0e0a-4905-9f66-fcf9991fc07a
ms.openlocfilehash: 4ee79e87085b0b939a762fec4c576c393846c2ae
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756859"
---
# <a name="compiler-error-c3295"></a>编译器错误 C3295

“#pragma pragma”只能在全局范围或命名空间范围上使用

部分杂注不能在函数中使用。  有关详细信息，请参阅[Pragma 指令和 __Pragma 关键字](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)。

## <a name="example"></a>示例

以下示例生成 C3295。

```cpp
// C3295.cpp
int main() {
   #pragma managed   // C3295
}
```
