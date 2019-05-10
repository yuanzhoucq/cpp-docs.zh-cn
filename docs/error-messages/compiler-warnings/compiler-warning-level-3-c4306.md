---
title: 编译器警告（等级 3）C4306
ms.date: 08/27/2018
f1_keywords:
- C4306
helpviewer_keywords:
- C4306
ms.assetid: 5b2192d7-402d-4b6d-8619-08105e7dcac7
ms.openlocfilehash: 78ec291b555838b1af63287e3d24fdb809afd7c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402055"
---
# <a name="compiler-warning-level-3-c4306"></a>编译器警告（等级 3）C4306

> '*标识符*： 从转换*type1*to*type2*更大的

标识符的类型强制转换为更大的指针。 未填充的新类型高位将用零填充。

此警告可能表示不需要的转换。 在生成的指针可能无效。