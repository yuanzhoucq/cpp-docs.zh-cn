---
title: main 函数限制
ms.date: 11/04/2016
f1_keywords:
- Main
helpviewer_keywords:
- main function, restrictions on using
ms.assetid: 7b3df731-344b-44a8-850c-11cbcbfbfa83
ms.openlocfilehash: 9ccea987b05c7854e78ba1621fd6c0a065d73d5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301833"
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