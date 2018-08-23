---
title: 编译器错误 C3859 |Microsoft 文档
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
ms.openlocfilehash: d2f8c51f25c09881e10e980276fc2035a6a70aed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272299"
---
# <a name="compiler-error-c3859"></a>C3859
超过了 PCH 的虚拟内存范围；请使用“-Zmvalue”或更大的命令行选项重新编译  
  
 预编译标头对于编译器尝试放入其中的数据量太小。 使用 **/Zm**编译器标志可指定预编译标头文件的更大值。 有关详细信息，请参阅[/Zm （指定预编译头内存分配限制）](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)。