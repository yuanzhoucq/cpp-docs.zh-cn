---
title: 编译器错误 C3166
ms.date: 11/04/2016
f1_keywords:
- C3166
helpviewer_keywords:
- C3166
ms.assetid: ec3e330d-c15d-4158-8268-09101486c566
ms.openlocfilehash: 17efd401314e93ff710be2c1e6f187a938e388b9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648365"
---
# <a name="compiler-error-c3166"></a>编译器错误 C3166

指针： 不能将指向内部 __gc 指针的指针声明为 type 的成员

编译器找到了无效的指针声明 (`__nogc`指针，指向`__gc`指针。)。

C3166 才可访问使用已过时的编译器选项 **/clr: oldsyntax**。
