---
title: 编译器错误 C3309
ms.date: 11/04/2016
f1_keywords:
- C3309
helpviewer_keywords:
- C3309
ms.assetid: 75ee16e3-7d4e-4c41-b3cb-64e9849c3aab
ms.openlocfilehash: 31849320568e049a794a82c5068ac6aa11c9023e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735978"
---
# <a name="compiler-error-c3309"></a>编译器错误 C3309

“macro_name”：模块名称不能是宏或关键字

将传递给模块特性的 name 属性的值不能为符号而必须是字符串文本，否则预处理器将无法展开。

下面的示例生成 C3309：

```cpp
// C3309.cpp
#define NAME MyModule
[module(name="NAME")];   // C3309
// Try the following line instead
// [module(name="MyModule")];
[coclass]
class MyClass {
public:
   void MyFunc();
};

int main() {
}
```
