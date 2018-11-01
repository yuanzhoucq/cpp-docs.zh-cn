---
title: 编译器错误 C2567
ms.date: 11/04/2016
f1_keywords:
- C2567
helpviewer_keywords:
- C2567
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
ms.openlocfilehash: eec529f43e23810843651888ef5722c5d0a0b2c9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651940"
---
# <a name="compiler-error-c2567"></a>编译器错误 C2567

无法打开 file 中的元数据，文件可能已删除或移动

在源中引用的元数据文件 (与`#using`) 未找到相同的目录中由编译器后端进程当时编译器前端进程。 请参阅[#using 指令](../../preprocessor/hash-using-directive-cpp.md)有关详细信息。

如果使用进行编译可能导致 C2567 **/c**上一个计算机，然后尝试在另一台计算机上的链接时间代码生成。 有关详细信息，请参阅[/LTCG （链接时间代码生成）](../../build/reference/ltcg-link-time-code-generation.md))。

它还可能指示您的计算机有没有更多的内存。

若要更正此错误，请确保元数据文件在相同的目录位置为生成过程的所有阶段。