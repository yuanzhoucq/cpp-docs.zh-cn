---
title: __unaligned |Microsoft Docs
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
ms.openlocfilehash: 2a7a9de35e225dabadbf9f4a3731f6d57fd9e99a
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940408"
---
# <a name="unaligned"></a>__unaligned

**特定于 Microsoft**。 当声明的指针 **__unaligned**修饰符，编译器将假定该指针处理未对齐的数据。 因此，相应平台的代码生成，以处理未对齐的读取和写入通过指针。

## <a name="remarks"></a>备注

此修饰符描述所处理的指针; 的数据的对齐方式指针本身被假定对齐。

偶尔 **__unaligned**关键字因平台和环境。 未能将适当地标记数据可能会导致性能损失范围到硬件故障的问题。 **__Unaligned**修饰符不能用于 x86 平台。

有关对齐的详细信息，请参阅：

- [align](../cpp/align-cpp.md)

- [__alignof 运算符](../cpp/alignof-operator.md)

- [pack](../preprocessor/pack.md)

- [/Zp（结构成员对齐）](../build/reference/zp-struct-member-alignment.md)

- [结构对齐示例](../build/examples-of-structure-alignment.md)

## <a name="see-also"></a>请参阅

[关键字](../cpp/keywords-cpp.md)
