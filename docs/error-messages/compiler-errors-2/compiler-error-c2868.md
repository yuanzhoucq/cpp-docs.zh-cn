---
title: 编译器错误 C2868 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2868
dev_langs:
- C++
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2de22b34f9dc564ef89d7776af86718af70d51eb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037861"
---
# <a name="compiler-error-c2868"></a>编译器错误 C2868

> '*标识符*： 非法的 using 声明语法; 预期的限定名称

一个[using 声明](../../cpp/using-declaration.md)要求*限定的名*，范围运算符 (`::`) 分隔的标识符名称结尾的命名空间、 类或枚举名称的序列。 单个作用域解析运算符可能用于引入与全局命名空间的名称。

## <a name="example"></a>示例

下面的示例生成 C2868，并还显示了正确的使用：

```cpp
// C2868.cpp
class X {
public:
   int i;
};

class Y : X {
public:
   using X::i;   // OK
};

int main() {
   using X;   // C2868
}
```