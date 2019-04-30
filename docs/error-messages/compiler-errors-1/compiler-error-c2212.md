---
title: 编译器错误 C2212
ms.date: 11/04/2016
f1_keywords:
- C2212
helpviewer_keywords:
- C2212
ms.assetid: 3fdab304-272c-4d07-bfd4-fad75170e536
ms.openlocfilehash: a632aaf9809cd306354320a21cb03b993d60a95f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400417"
---
# <a name="compiler-error-c2212"></a>编译器错误 C2212

identifier: __based 不可用于指向函数的指针

不能声明为指向函数的指针`__based`。 如果需要基于代码的数据，请使用`__declspec`关键字或`data_seg`杂注。