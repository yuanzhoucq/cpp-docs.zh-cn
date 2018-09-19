---
title: 编译器错误 C2504 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2504
dev_langs:
- C++
helpviewer_keywords:
- C2504
ms.assetid: c9e002a6-a4ee-4ba7-970e-edf4adb83692
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6fb11774f65454799761913babb428dc6a471743
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054124"
---
# <a name="compiler-error-c2504"></a>编译器错误 C2504

class： 未定义基类

声明类的基类，但是永远不会定义。  可能的原因：

1. 缺少包含文件。

1. 使用未声明外部基类[extern](../../cpp/using-extern-to-specify-linkage.md)。

下面的示例生成 C2504:

```
// C2504.cpp
// compile with: /c
class A;
class B : public A {};   // C2504
```

还行

```
class C{};
class D : public C {};
```