---
title: C3859
ms.date: 03/08/2019
f1_keywords:
- C3859
helpviewer_keywords:
- C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
ms.openlocfilehash: 9b20224207ba797c6ee93c06404e4d90c3d02525
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391876"
---
# <a name="compiler-error-c3859"></a>C3859

> PCH 超出; 的虚拟内存范围请重新编译使用的命令行选项-Zm*值*或更高版本

为预编译标头分配的虚拟内存是编译器尝试放入其中的数据量太小。 在 Visual Studio 2015 中，启动 **/Zm**使用时，建议仅是重要`#pragma hdrstop`指令。 在其他情况下，它是指示 Windows 虚拟内存不足问题的虚假错误。

如果使用预编译标头`#pragma hdrstop`指令，使用 **/Zm**编译器标志，用于指定预编译的头文件的较大值。 否则，请考虑减少在生成中的并行编译进程数。 有关详细信息，请参阅[/Zm （指定预编译标头内存分配限额）](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)。
