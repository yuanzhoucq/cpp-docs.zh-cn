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
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 8a132eb7dbf09421ad5c99249b0208e5f901156b
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3859"></a>C3859
超过了 PCH 的虚拟内存范围；请使用“-Zmvalue”或更大的命令行选项重新编译  
  
 预编译标头对于编译器尝试放入其中的数据量太小。 使用**/Zm**编译器标志可指定预编译标头文件的更大值。 有关详细信息，请参阅[/Zm （指定预编译头内存分配限制）](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)。
