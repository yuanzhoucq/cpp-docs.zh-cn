---
title: C3859
ms.date: 11/04/2016
f1_keywords:
- C3859
helpviewer_keywords:
- C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
ms.openlocfilehash: be6ccaab49cb329e862fb6068af1337eddbaac8f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490268"
---
# <a name="compiler-error-c3859"></a>C3859

超过了 PCH 的虚拟内存范围；请使用“-Zmvalue”或更大的命令行选项重新编译

预编译标头对于编译器尝试放入其中的数据量太小。 使用 **/Zm**编译器标志，用于指定预编译的头文件的较大值。 有关详细信息，请参阅[/Zm （指定预编译标头内存分配限额）](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)。