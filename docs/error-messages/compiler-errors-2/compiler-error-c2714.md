---
title: 编译器错误 C2714 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2714
dev_langs:
- C++
helpviewer_keywords:
- C2714
ms.assetid: 401a5a42-660c-4bad-9d63-1a2d092bc489
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a5a8a2157fc574b9a43688bfc8fa9adcbcb676f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108490"
---
# <a name="compiler-error-c2714"></a>编译器错误 C2714

不允许 __alignof(void)

对运算符传递了无效值。

请参阅[__alignof 运算符](../../cpp/alignof-operator.md)有关详细信息。

## <a name="example"></a>示例

下面的示例生成 C2714。

```
// C2714.cpp
int main() {
   return __alignof(void);   // C2714
   return __alignof(char);   // OK
}
```