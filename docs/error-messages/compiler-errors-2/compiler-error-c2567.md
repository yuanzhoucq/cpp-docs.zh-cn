---
title: 编译器错误 C2567
ms.date: 11/04/2016
f1_keywords:
- C2567
helpviewer_keywords:
- C2567
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
ms.openlocfilehash: 921992c678c1de0b74f99f544173478ebe809b2c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177451"
---
# <a name="compiler-error-c2567"></a>编译器错误 C2567

无法打开 "file" 中的元数据，文件可能已被删除或移动

编译器后端进程在同一目录中找不到在源中引用的元数据文件（具有 `#using`）。 有关详细信息，请参阅[#using 指令](../../preprocessor/hash-using-directive-cpp.md)。

如果在一台计算机上使用 **/c**进行编译，然后在另一台计算机上尝试使用链接时间代码生成，则可能导致 C2567。 有关详细信息，请参阅[/ltcg （链接时间代码生成）](../../build/reference/ltcg-link-time-code-generation.md)。

它也可能表示您的计算机没有更多的内存。

若要更正此错误，请确保元数据文件在生成过程的所有阶段都处于相同的目录位置。
