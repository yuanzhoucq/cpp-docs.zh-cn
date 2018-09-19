---
title: 编译器错误 C2665 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2665
dev_langs:
- C++
helpviewer_keywords:
- C2665
ms.assetid: a7f99b61-2eae-4f2b-ba75-ea68fd1e8312
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b442e1de0481ef3d00742ed201575526332decff
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109140"
---
# <a name="compiler-error-c2665"></a>编译器错误 C2665

function: number1 重载没有可以从类型 type 转换参数数字 2

重载函数的参数不能转换为所需的类型。  可能的解决方法：

- 提供转换运算符。

- 使用显式转换。

## <a name="example"></a>示例

下面的示例生成 C2665。

```
// C2665.cpp
void func(short, char*){}
void func(char*, char*){}

int main() {
   func(0, 1);   // C2665
   func((short)0, (char*)1);   // OK
}
```