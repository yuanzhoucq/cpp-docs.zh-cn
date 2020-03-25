---
title: 链接器工具警告 LNK4102
ms.date: 11/04/2016
f1_keywords:
- LNK4102
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
ms.openlocfilehash: fda1fdb03a7629894f846bb20ed84df519239327
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183301"
---
# <a name="linker-tools-warning-lnk4102"></a>链接器工具警告 LNK4102

导出删除的析构函数 "name";图像可能无法正确运行

该程序已尝试导出删除的析构函数。 生成的删除可能会在 DLL 边界内发生，以便进程可以释放不拥有的内存。 请确保 .def 文件中未列出给定的符号，并且该符号未在链接器命令行中作为 **/IMPORT**或 **/export**选项的参数列出。

如果要重新生成 C 运行时库，可以忽略此消息。
