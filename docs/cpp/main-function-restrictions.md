---
title: main 函数限制 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Main
dev_langs:
- C++
helpviewer_keywords:
- main function, restrictions on using
ms.assetid: 7b3df731-344b-44a8-850c-11cbcbfbfa83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93f5cce15d4db9f7f6d4e3361d22028fccd676f2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117356"
---
# <a name="main-function-restrictions"></a>main 函数限制

几个限制适用于**主要**并不适用于任何其他 C++ 函数的函数。 **主要**函数：

- 不能重载 (请参阅[函数重载](function-overloading.md))。

- 不能声明为**内联**。

- 不能声明为**静态**。

- 不能提取其地址。

- 无法被调用。

## <a name="see-also"></a>请参阅

[main：程序启动](../cpp/main-program-startup.md)