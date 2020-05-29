---
title: 编译器错误 C2720
ms.date: 11/04/2016
f1_keywords:
- C2720
helpviewer_keywords:
- C2720
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
ms.openlocfilehash: 24f4329ee631eafc7c2670d9ebf28609c22e7592
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202123"
---
# <a name="compiler-error-c2720"></a>编译器错误 C2720

> "*identifier*"：成员上的 "*说明符*" 存储类说明符非法

存储类无法用于声明外部的类成员。 若要修复此错误，请从类声明外部的成员定义中删除不需要的[存储类](../../cpp/storage-classes-cpp.md)说明符。

## <a name="example"></a>示例

下例生成了 C2720，并介绍了如何修复此错误：

```cpp
// C2720.cpp
struct S {
   static int i;
};
static S::i;   // C2720 - remove the unneeded 'static' to fix it
```
