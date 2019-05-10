---
title: 编译器错误 C2785
ms.date: 11/04/2016
f1_keywords:
- C2785
helpviewer_keywords:
- C2785
ms.assetid: d8d13360-0d00-4815-8475-b49c7f0dc0f3
ms.openlocfilehash: fcf2bbb01f2aac668ff52884a6ccfb36c66aa89d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395373"
---
# <a name="compiler-error-c2785"></a>编译器错误 C2785

declaration1 和 declaration2 具有不同的返回类型

函数模板特殊化的返回类型不同于主函数模板的返回类型。

### <a name="to-correct-this-error"></a>更正此错误

1. 检查一致性的函数模板的所有专用化。

## <a name="example"></a>示例

下面的示例生成 C2785:

```
// C2785.cpp
// compile with: /c
template<class T> void f(T);

template<> int f(int); // C2785
template<> void f(int); // OK
```