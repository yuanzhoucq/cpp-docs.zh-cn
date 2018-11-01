---
title: 编译器错误 C2870
ms.date: 11/04/2016
f1_keywords:
- C2870
helpviewer_keywords:
- C2870
ms.assetid: 80523ee9-1fd3-4dc4-8a77-5083deb99066
ms.openlocfilehash: f61281da23e46236e7fce496a4d89086e5d6c0ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546362"
---
# <a name="compiler-error-c2870"></a>编译器错误 C2870

name： 命名空间定义必须出现在文件范围内或在另一个命名空间定义立即出现

定义命名空间`name`不正确。 必须在文件范围内 （之外的所有块和类） 定义的命名空间或立即在另一个命名空间内。

下面的示例生成 C2870:

```
// C2870.cpp
// compile with: /c
int main() {
   namespace A { int i; };   // C2870
}
```