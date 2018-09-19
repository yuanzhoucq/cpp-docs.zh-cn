---
title: 编译器错误 C3859 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3859
dev_langs:
- C++
helpviewer_keywords:
- C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ac06a09a6ad66384fd2b5423e3df046771f7653
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053383"
---
# <a name="compiler-error-c3859"></a>C3859

超过了 PCH 的虚拟内存范围；请使用“-Zmvalue”或更大的命令行选项重新编译

预编译标头对于编译器尝试放入其中的数据量太小。 使用 **/Zm**编译器标志，用于指定预编译的头文件的较大值。 有关详细信息，请参阅[/Zm （指定预编译标头内存分配限额）](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)。