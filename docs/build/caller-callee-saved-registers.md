---
title: 调用方-被调用方保存的寄存器
ms.date: 11/04/2016
ms.assetid: 0533bd4b-d6bb-4ce1-8201-495e16870cbb
ms.openlocfilehash: f34fbfff8e6c61b5d568c073f6b7da2a12e34535
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654696"
---
# <a name="callercallee-saved-registers"></a>由调用方或被调用方保存的寄存器

注册到 RAX、 RCX、 RDX、 R8，R9、 R10、 R11 被视为易失性并必须考虑销毁函数调用上 (除非否则为安全-进行可证明以通过分析如全程序优化)。

注册 RBX、 RBP、 RDI、 RSI、 RSP、 R12、 R13、 R14，并 R15 被视为非易失性，必须保存并还原函数使用它们。

## <a name="see-also"></a>请参阅

[调用约定](../build/calling-convention.md)