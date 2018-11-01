---
title: Varargs
ms.date: 11/04/2016
ms.assetid: aac0c54b-0a2d-4a22-b1de-ee41381a3eb1
ms.openlocfilehash: 42647949fbc69f7c4f1140352d0be0bb6bd9018c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487992"
---
# <a name="varargs"></a>Varargs

如果通过 varargs （例如，省略号参数） 传递的参数，实质上是正常的参数传递应用包括溢出的第五个和后续参数。 负责再次被调用方的转储采用其地址的参数。 对于浮点值，包括整数和浮点寄存器将包含 float 值在被调用方需要采用整数寄存器的值的情况下。

## <a name="see-also"></a>请参阅

[调用约定](../build/calling-convention.md)