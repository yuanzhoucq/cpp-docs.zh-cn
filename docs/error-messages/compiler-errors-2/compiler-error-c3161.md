---
title: 编译器错误 C3161
ms.date: 11/04/2016
f1_keywords:
- C3161
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
ms.openlocfilehash: 22ecc176036308699c3ad7bd8c015836be910073
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174199"
---
# <a name="compiler-error-c3161"></a>编译器错误 C3161

interface： 嵌套类、 结构、 联合或接口中的接口是非法的;类、 结构或联合中的嵌套接口是非法的

[__Interface](../../cpp/interface.md)只能出现在全局范围或命名空间内。 类、 结构或联合不能出现在接口中。

## <a name="example"></a>示例

下面的示例生成 C3161。

```
// C3161.cpp
// compile with: /c
__interface X {
   __interface Y {};   // C3161 A nested interface
};
```