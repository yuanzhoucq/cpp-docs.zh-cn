---
title: 编译器警告 （等级 1） C4920 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4920
dev_langs:
- C++
helpviewer_keywords:
- C4920
ms.assetid: 1e501f2e-93c1-4d27-a4fa-54fc86271ae7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4873fcb1e5bb6d712e44b86d6f60589d6c8ddf4d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091733"
---
# <a name="compiler-warning-level-1-c4920"></a>编译器警告（等级 1）C4920

enum enum member member=value 在 enum enum 中被视为 member=value

如果传递到 #import 的 .tlb 具有在两个或更多的枚举中定义的相同符号，则此警告指示后续的相同符号被忽略，且会在 .tlh 文件中被注释掉。

假定 .tlb 包含：

```
library MyLib
{
    typedef enum {
        enumMember = 512
    } AProblem;

    typedef enum {
        enumMember = 1024
    } BProblem;
};
```

以下示例生成 C4920，

```
// C4920.cpp
// compile with: /W1
#import "t4920.tlb"   // C4920

int main() {
}
```