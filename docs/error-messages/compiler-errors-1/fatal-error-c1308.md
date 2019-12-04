---
title: 错误 C1308
ms.date: 11/04/2016
f1_keywords:
- C1308
helpviewer_keywords:
- C1308
ms.assetid: 46177997-069e-433a-8e20-93c846d78ffd
ms.openlocfilehash: 95e13a6914b5e02441f95dd2256532dbd1d718e5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747015"
---
# <a name="fatal-error-c1308"></a>错误 C1308

不支持链接程序集

允许 .netmodule 作为链接器输入，但程序集不能。 当尝试链接使用 `/clr:safe`编译的程序集时，可能会生成此错误。

有关详细信息，请参阅 [用作链接器输入的 .netmodule 文件](../../build/reference/netmodule-files-as-linker-input.md)。

下面的示例生成 C1308：

```cpp
// C1308.cpp
// compile with: /clr:safe /LD
public ref class MyClass {
public:
   int i;
};
```

然后

```cpp
// C1308b.cpp
// compile with: /clr /link C1308b.obj C1308.dll
// C1308 expected
#using "C1308.dll"
int main() {
   MyClass ^ my = gcnew MyClass();
}
```
