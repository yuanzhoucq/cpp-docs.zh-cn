---
title: 编译器错误 C2870
ms.date: 11/04/2016
f1_keywords:
- C2870
helpviewer_keywords:
- C2870
ms.assetid: 80523ee9-1fd3-4dc4-8a77-5083deb99066
ms.openlocfilehash: 3b006592723df1222d05e39b3bc9e5729efc8aa6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755026"
---
# <a name="compiler-error-c2870"></a>编译器错误 C2870

"name"：命名空间定义必须出现在文件范围内或紧跟在另一个命名空间定义中

你定义的命名空间 `name` 错误。 必须在文件范围（在所有块和类的外部）或在另一个命名空间中定义命名空间。

下面的示例生成 C2870：

```cpp
// C2870.cpp
// compile with: /c
int main() {
   namespace A { int i; };   // C2870
}
```
