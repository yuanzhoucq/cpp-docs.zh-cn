---
title: Intel&#39;s MMX 指令集 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- MMX instruction set
ms.assetid: 705deb2d-c3fd-4696-9e22-8bcf25866daf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95f3cb57fc5c046057a5efa568ce930f13ca3256
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43688348"
---
# <a name="intel39s-mmx-instruction-set"></a>Intel&#39;s MMX 指令集

**Microsoft 专用**

利用 Visual C++ 编译器，您可以在内联汇编程序中使用 Intel 的 MMX（多媒体扩展）指令集。 调试器反汇编也支持 MMX 指令。 如果函数包含 MMX 命令，但不包含清空媒体状态的 EMMS 指令，编译器将生成警告消息。 有关详细信息，请参阅 Intel 网站。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>