---
title: 编译器警告（等级 3）C4686
ms.date: 08/27/2018
f1_keywords:
- C4686
helpviewer_keywords:
- C4686
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
ms.openlocfilehash: 5e23e6aa69fe8a59e3dfd22af7e33780c223cdd3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584507"
---
# <a name="compiler-warning-level-3-c4686"></a>编译器警告（等级 3）C4686

> '*用户定义类型*： 行为可能有更改，UDT 中的更改返回调用约定

## <a name="remarks"></a>备注

类模板专用化不是之前在返回类型用于定义。 实例化类的任何内容将解决此 C4686 警告;声明一个实例或访问成员 (C\<int >:: 任何内容) 还提供了选项。

默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。

## <a name="example"></a>示例

改为尝试以下：

```cpp
// C4686.cpp
// compile with: /W3
#pragma warning (default : 4686)
template <class T>
class C;

template <class T>
C<T> f(T);

template <class T>
class C {};

int main() {
   f(1);   // C4686
}

template <class T>
C<T> f(T) {
   return C<int>();
}
```