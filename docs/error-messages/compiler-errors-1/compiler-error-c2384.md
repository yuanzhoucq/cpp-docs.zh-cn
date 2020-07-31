---
title: 编译器错误 C2384
ms.date: 11/04/2016
f1_keywords:
- C2384
helpviewer_keywords:
- C2384
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
ms.openlocfilehash: 321ccd23bc273f5fa548f75fd44bc320bcf4c426
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225509"
---
# <a name="compiler-error-c2384"></a>编译器错误 C2384

“membe”：不能对托管类或 WinRT 类的成员应用 __declspec(thread)

[线程](../../cpp/thread.md) **`__declspec`** 修饰符不能用于托管类或 Windows 运行时类的成员。

托管代码中的静态线程本地存储仅可用于静态加载的 DLL（进程启动时，必须以静态方式加载该 DLL）。 Windows 运行时不支持线程本地存储。

下面的行生成 C2384 并演示如何在 C++/CLI 代码中修复此错误：

```cpp
// C2384.cpp
// compile with: /clr /c
public ref class B {
public:
   __declspec( thread ) static int tls_i = 1;   // C2384

   // OK - declare with attribute instead
   [System::ThreadStaticAttribute]
   static int tls_j;
};
```
