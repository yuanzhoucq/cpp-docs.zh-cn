---
title: __unaligned |Microsoft 文档
ms.custom: ''
ms.date: 03/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __unaligned_cpp
dev_langs:
- C++
helpviewer_keywords:
- __unaligned keyword [C++]
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d73b082b9f41d03eb0b1a8c9fe772351ff4da91f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32420898"
---
# <a name="unaligned"></a>__unaligned

**Microsoft 专用**。 声明带有 `__unaligned` 修饰符的指针时，编译器将假定该指针处理未对齐的数据。 因此，相应平台的代码生成以处理未对齐的读取和写入通过指针。

## <a name="remarks"></a>备注

此修饰符描述该指针; 寻址的数据的对齐方式指针本身被假定对齐。

必要条件`__unaligned`关键字因平台和环境。 未能将相应地标记数据可以导致范围从性能损失到硬件故障的问题。 `__unaligned`修饰符不适合 x86 平台。

有关对齐的详细信息，请参阅：

- [align](../cpp/align-cpp.md)

- [__alignof 运算符](../cpp/alignof-operator.md)

- [pack](../preprocessor/pack.md)

- [/Zp（结构成员对齐）](../build/reference/zp-struct-member-alignment.md)

- [结构对齐示例](../build/examples-of-structure-alignment.md)

## <a name="see-also"></a>请参阅

[关键字](../cpp/keywords-cpp.md)
