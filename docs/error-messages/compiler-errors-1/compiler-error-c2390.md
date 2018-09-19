---
title: 编译器错误 C2390 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2390
dev_langs:
- C++
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5de5a9af8f8aa04219f0a7d61162336745fd4bfa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098207"
---
# <a name="compiler-error-c2390"></a>编译器错误 C2390

identifier： 不正确的存储类 specifier

存储类无效，不能为全局作用域标识符。 默认的存储类将代替类无效。

可能的解决方法：

- 如果该标识符是一个函数，将其与声明`extern`存储。

- 如果该标识符是形参或局部变量，将其声明使用自动存储。

- 如果该标识符是一个全局变量，它不使用存储类声明 （自动存储）。

## <a name="example"></a>示例

- 下面的示例生成 C2390:

```
// C2390.cpp
register int i;   // C2390

int main() {
   register int j;   // OK
}
```