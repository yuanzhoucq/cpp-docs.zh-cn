---
title: "编译器错误 C3859 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3859
dev_langs:
- C++
helpviewer_keywords:
- C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d3a240771c0b2e104ef7c51b187d4040500edaae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3859"></a>C3859
超过了 PCH 的虚拟内存范围；请使用“-Zmvalue”或更大的命令行选项重新编译  
  
 预编译标头对于编译器尝试放入其中的数据量太小。 使用**/Zm**编译器标志可指定预编译标头文件的更大值。 有关详细信息，请参阅[/Zm （指定预编译头内存分配限制）](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)。