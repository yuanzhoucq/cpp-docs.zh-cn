---
title: 编译器错误 C2720 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2720
dev_langs:
- C++
helpviewer_keywords:
- C2720
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2d75c9847016102d4ae8609fb0a0a78726e4c67
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084011"
---
# <a name="compiler-error-c2720"></a>编译器错误 C2720

> '*标识符*':'*说明符*存储类说明符在成员上非法

存储类无法用于声明外部的类成员。 若要修复此错误，删除不需要[存储类](../../cpp/storage-classes-cpp.md)说明符定义中的类声明外部的成员。

## <a name="example"></a>示例

下例生成了 C2720，并介绍了如何修复此错误：

```cpp
// C2720.cpp
struct S {
   static int i;
};
static S::i;   // C2720 - remove the unneeded 'static' to fix it
```