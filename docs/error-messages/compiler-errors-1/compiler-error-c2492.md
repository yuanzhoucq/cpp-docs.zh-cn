---
title: 编译器错误 C2492
ms.date: 11/04/2016
f1_keywords:
- C2492
helpviewer_keywords:
- C2492
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
ms.openlocfilehash: fd52b434f86bdc93124c6005bbf7fadad3cb56b2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757054"
---
# <a name="compiler-error-c2492"></a>编译器错误 C2492

"*variable*"：具有线程存储持续时间的数据可能没有 dll 接口

变量是用[thread](../../cpp/thread.md)特性和 DLL 接口声明的。 在运行时之前，`thread` 变量的地址是未知的，因此不能将其链接到 DLL 导入或导出。

下面的示例生成 C2492：

```cpp
// C2492.cpp
// compile with: /c
class C {
public:
   char   ch;
};

__declspec(dllexport) __declspec(thread) C c_1;   // C2492
__declspec(thread) C c_1;   // OK
```
