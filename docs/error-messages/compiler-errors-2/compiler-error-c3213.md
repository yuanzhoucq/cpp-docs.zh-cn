---
title: 编译器错误 C3213
ms.date: 11/04/2016
f1_keywords:
- C3213
helpviewer_keywords:
- C3213
ms.assetid: 1f079e36-b3e9-40f8-8e95-08eeba3adc82
ms.openlocfilehash: 1b08b0ef5b8fefcfa1dd55ef3a16ee4ef5d027e0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182504"
---
# <a name="compiler-error-c3213"></a>编译器错误 C3213

基类“base_type”的可访问性比“derived_type”低

程序集中可见的类型必须使用公开可见的基类。

以下示例生成 C3213：

```
// C3213.cpp
// compile with: /clr
private ref struct privateG {
public:
   int i;
};

public ref struct publicG {
public:
   int i;
};

public ref struct V : public privateG {   // C3213
public:
   int j;
};

public ref struct W: public publicG {   // OK
public:
   int j;
};
```