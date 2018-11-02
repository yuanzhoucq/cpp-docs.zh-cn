---
title: 编译器错误 C2390
ms.date: 11/04/2016
f1_keywords:
- C2390
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
ms.openlocfilehash: 89f6ebb02326413e8dca67d333e555321da4e645
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595866"
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