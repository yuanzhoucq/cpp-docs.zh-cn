---
title: 编译器警告 （等级 1） C4377 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4377
dev_langs:
- C++
helpviewer_keywords:
- C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 613ebe183b61c6b9894ed3b726f90061e2b24ef6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047169"
---
# <a name="compiler-warning-level-1-c4377"></a>编译器警告（等级 1）C4377

本机类型是私有默认设置。-d1PrivateNativeTypes 已被否决

在早期版本中，在程序集的本机类型是公共的默认值，并且将内部、 未记录的编译器选项 (**/d1PrivateNativeTypes**) 可将其变为专用。

所有类型，本机和 CLR，现在是私有程序集，默认情况下使 **/d1PrivateNativeTypes**不再需要。

## <a name="example"></a>示例

下面的示例生成 C4377。

```
// C4377.cpp
// compile with: /clr /d1PrivateNativeTypes /W1
// C4377 warning expected
int main() {}
```