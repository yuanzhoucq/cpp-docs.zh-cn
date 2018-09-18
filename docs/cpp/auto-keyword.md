---
title: auto 关键字 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 744a41c0-2510-4140-a1be-96257e722908
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 10952e6360fc8170c59e9a67fe3027622cbea4bc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055517"
---
# <a name="auto-keyword"></a>auto 关键字

**自动**关键字是声明说明符。 但是，C++ 标准为此关键字定义了初始和修订的含义。 Visual c + + 2010 之前,**自动**关键字声明中的变量*自动*存储类; 即，具有本地生存期的变量。 从 Visual c + + 2010，开始**自动**关键字声明其类型从其声明中的初始化表达式推导出的变量。 [/Zc: auto&#91;-&#93; ](../build/reference/zc-auto-deduce-variable-type.md)编译器选项控制的含义**自动**关键字。

## <a name="syntax"></a>语法

```cpp
auto declarator ;
auto declarator initializer;
```

## <a name="remarks"></a>备注

定义**自动**关键字进行的更改在 c + + 编程语言中，但不是以 C 编程语言。

下面的主题介绍**自动**关键字和对应的编译器选项：

- [自动](../cpp/auto-cpp.md)介绍的新定义**自动**关键字。

- [/Zc: auto （推导变量类型）](../build/reference/zc-auto-deduce-variable-type.md)介绍了告知编译器哪一定义的编译器选项**自动**关键字来使用。

## <a name="see-also"></a>请参阅

[关键字](../cpp/keywords-cpp.md)