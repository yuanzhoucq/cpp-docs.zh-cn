---
title: 编译器警告 （等级 3） C4686 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4686
dev_langs:
- C++
helpviewer_keywords:
- C4686
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 32a44cd929eb7629ef317ce9847950b613bde52c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43202075"
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