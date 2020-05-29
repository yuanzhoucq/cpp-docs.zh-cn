---
title: 浮点协处理器和调用约定
ms.date: 11/04/2016
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
ms.openlocfilehash: c70dd3b049ca353acc8a504df52b2c61feaf1974
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188603"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>浮点协处理器和调用约定

如果要为浮点协处理器编写程序集例程，则必须保留浮点控制字并清理协处理器堆栈，除非返回**浮点**值或**双精度**值（函数应以 ST （0）返回）。

## <a name="see-also"></a>另请参阅

[调用约定](../cpp/calling-conventions.md)
