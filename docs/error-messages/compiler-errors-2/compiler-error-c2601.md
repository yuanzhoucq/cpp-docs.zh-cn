---
title: 编译器错误 C2601
ms.date: 11/04/2016
f1_keywords:
- C2601
helpviewer_keywords:
- C2601
ms.assetid: 88275582-5f37-45d7-807d-05f06ba00965
ms.openlocfilehash: f18819e5f078cb85121160af1d4a3fc24a365a68
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62215576"
---
# <a name="compiler-error-c2601"></a>编译器错误 C2601

function： 本地函数定义是非法的

代码尝试定义函数中的函数。

或者，C2601 错误的位置之前在源代码中可能有一个额外的大括号。

下面的示例生成 C2601:

```
// C2601.cpp
int main() {
   int i = 0;

   void funcname(int j) {   // C2601
      j++;
   }
}
```