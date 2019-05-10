---
title: 编译器错误 C2492
ms.date: 11/04/2016
f1_keywords:
- C2492
helpviewer_keywords:
- C2492
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
ms.openlocfilehash: e2b08ef3e46681147c4efd77cbffadb096bbfc16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360705"
---
# <a name="compiler-error-c2492"></a>编译器错误 C2492

'*变量*： 具有线程存储持续时间的数据可能没有 dll 接口

与声明该变量[线程](../../cpp/thread.md)属性，并使用的 DLL 接口。 地址`thread`变量之前未知运行时，因此它不能链接到 DLL 导入或导出。

下面的示例生成 C2492:

```
// C2492.cpp
// compile with: /c
class C {
public:
   char   ch;
};

__declspec(dllexport) __declspec(thread) C c_1;   // C2492
__declspec(thread) C c_1;   // OK
```