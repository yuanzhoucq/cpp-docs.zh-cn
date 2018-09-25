---
title: 2.7.2.1 专用 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 079b4b84-f2b3-4050-a0ac-289493c36b3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d06650a784b5b59405f446f4701918393b21fa3b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387232"
---
# <a name="2721-private"></a>2.7.2.1 private

`private`子句声明变量的列表是专用于在团队中每个线程中的变量。 语法`private`子句如下所示：

```
private(variable-list)
```

中指定的变量的行为`private`子句如下所示。 具有自动存储持续时间的新对象分配的构造。 大小和新对象的对齐方式取决于变量的类型。 这种分配发生一次为每个线程团队，并默认构造函数调用的类对象，如有必要;否则的初始值是不确定的。  变量所引用的原始对象具有不确定的值输入到构造时、 内动态构造，程度不进行修改和已在从构造退出时不确定的值。

中的指令的构造的词法范围内，变量引用新的专用对象分配的线程。

对限制`private`子句如下所示：

- 中指定的类类型的变量`private`子句必须具有一个可访问的、 明确的默认构造函数。

- 中指定的变量`private`子句不能**const**-限定类型，除非它具有类类型与`mutable`成员。

- 中指定的变量`private`子句不能是不完整类型或引用类型。

- 在出现的变量`reduction`子句**并行**指令不能指定`private`绑定到并行构造的工作共享指令上的子句。