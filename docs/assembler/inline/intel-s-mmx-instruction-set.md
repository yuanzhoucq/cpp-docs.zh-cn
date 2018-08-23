---
title: Intel&#39;s MMX 指令集 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: c054c1236fbbc74cfc45834f05aa2be08faa07f6
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
ms.locfileid: "32050732"
---
# <a name="intel39s-mmx-instruction-set"></a>Intel&#39;s MMX 指令集
## <a name="microsoft-specific"></a>Microsoft 专用  
 利用 Visual C++ 编译器，您可以在内联汇编程序中使用 Intel 的 MMX（多媒体扩展）指令集。 调试器反汇编也支持 MMX 指令。 如果函数包含 MMX 命令，但不包含清空媒体状态的 EMMS 指令，编译器将生成警告消息。 有关详细信息，请参阅 Intel 网站。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)