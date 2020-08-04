---
title: 赋值转换
ms.date: 11/04/2016
helpviewer_keywords:
- conversions, assignment
- assignment conversions
ms.assetid: 4ee01013-de32-4aae-b12e-0051d0cde927
ms.openlocfilehash: cc75bdd8227c09247f6d4270f1fc21235de2eb05
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211835"
---
# <a name="assignment-conversions"></a>赋值转换

在赋值操作中，赋值的类型将转换为接受赋值的变量的类型。 即使转换过程中会丢失信息，C 仍然允许在整型和浮点类型之间进行赋值转换。 使用的转换方法取决于赋值涉及的类型，如[常用算术转换](../c-language/usual-arithmetic-conversions.md)和下列各节中所述：

- [从带符号整型的转换](../c-language/conversions-from-signed-integral-types.md)

- [从无符号整型的转换](../c-language/conversions-from-unsigned-integral-types.md)

- [从浮点类型的转换](../c-language/conversions-from-floating-point-types.md)

- [指针类型之间的转换](../c-language/conversions-to-and-from-pointer-types.md)

- [从其他类型的转换](../c-language/conversions-from-other-types.md)

虽然不能在赋值的左侧使用 `const` 左值，但类型限定符不会影响转换的可允许性。

## <a name="see-also"></a>请参阅

[类型转换](../c-language/type-conversions-c.md)
