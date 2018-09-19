---
title: 编译器错误 C2847 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2847
dev_langs:
- C++
helpviewer_keywords:
- C2847
ms.assetid: 9ad9a0e0-8b16-49d9-a5be-f8eda2372aa9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 41e3b49c509240fd0d782aacaa9fae836b62702a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054436"
---
# <a name="compiler-error-c2847"></a>编译器错误 C2847

无法将 sizeof 应用到托管或 WinRT 类型“类”

[Sizeof](../../cpp/sizeof-operator.md)运算符在编译时获取对象的值。 由于托管或 WinRT 类的大小、接口或值类型是动态的，因此在编译时无法得知。

例如，以下示例生成 C2847：

```
// C2847.cpp
// compile with: /clr
ref class A {};

int main() {
   A ^ xA = gcnew A;
   sizeof(*xA);   // C2847 cannot use sizeof on managed object
}
```
