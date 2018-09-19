---
title: 编译器错误 C2951 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2951
dev_langs:
- C++
helpviewer_keywords:
- C2951
ms.assetid: c6f95aa2-c894-425b-a51c-d40d70c8daa1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6757256f08c5c1ed0a35fbf1c2a70776a4f2936
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074664"
---
# <a name="compiler-error-c2951"></a>编译器错误 C2951

类型声明只能在全局、 命名空间或类范围内

不能声明泛型或模板类外部全局或命名空间范围。 如果在包含文件中进行泛型或模板声明，请确保包含文件是在全局范围内。

下面的示例生成 C2951:

```
// C2951.cpp
template <class T>
class A {};

int main() {
   template <class T>   // C2951
   class B {};
}
```

使用泛型时，也可能发生 C2951:

```
// C2951b.cpp
// compile with: /clr /c

// OK
generic <class T>
ref class GC { };

int main() {
   generic <class T> ref class GC2 {};   // C2951
}
```