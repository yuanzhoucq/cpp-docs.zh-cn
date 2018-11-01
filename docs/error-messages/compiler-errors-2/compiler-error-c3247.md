---
title: 编译器错误 C3247
ms.date: 11/04/2016
f1_keywords:
- C3247
helpviewer_keywords:
- C3247
ms.assetid: f9a2bbb5-3fce-40bf-9fd3-835a5f164dbb
ms.openlocfilehash: 7ca84b4f054852aefa75a9c4547286137b436c63
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569153"
---
# <a name="compiler-error-c3247"></a>编译器错误 C3247

“class1”：组件类不能继承自另一个组件类“class2”

[coclass](../../windows/coclass.md) 特性标记的类不能继承自 `coclass` 特性标记的另一个类。

以下示例生成 C3247：

```
// C3247.cpp
[module(name="MyLib")];
[coclass]
class a {
};

[coclass]
class b : public a {   // C3247
};
int main() {
}
```