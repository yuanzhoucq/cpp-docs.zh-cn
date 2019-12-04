---
title: 编译器错误 C3161
ms.date: 11/04/2016
f1_keywords:
- C3161
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
ms.openlocfilehash: 7315dad7959cdd3b950ed814b13be3867399d332
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761811"
---
# <a name="compiler-error-c3161"></a>编译器错误 C3161

"interface"：接口中的嵌套类、结构、联合或接口是非法的;类、结构或联合中的嵌套接口是非法的

[__Interface](../../cpp/interface.md)只能出现在全局范围或命名空间中。 类、结构或联合不能出现在接口中。

## <a name="example"></a>示例

下面的示例生成 C3161。

```cpp
// C3161.cpp
// compile with: /c
__interface X {
   __interface Y {};   // C3161 A nested interface
};
```
