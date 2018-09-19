---
title: 编译器错误 C2430 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2430
dev_langs:
- C++
helpviewer_keywords:
- C2430
ms.assetid: 07c20f76-63e1-4d22-b2a9-98b0d45c5cac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 102e7082a3fc1cfd96db5c38832e3ebb91ee742c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054449"
---
# <a name="compiler-error-c2430"></a>编译器错误 C2430

identifier 中注册多个索引

多个注册进行缩放。 编译器支持扩展索引，但只能缩放一个寄存器。

## <a name="example"></a>示例

下面的示例生成 C2430。

```
// C2430.cpp
// processor: x86
int main() {
   _asm mov eax, [ebx*2+ecx*4] // C2430
}
```