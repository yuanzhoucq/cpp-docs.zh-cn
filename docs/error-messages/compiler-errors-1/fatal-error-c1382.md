---
title: "错误 C1382 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1382
dev_langs:
- C++
helpviewer_keywords:
- C1382
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: ddb016e14b01b3bc1dfd45c7d5a8ad1aa489ac3a
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="fatal-error-c1382"></a>错误 C1382
已重新生成 PCH 文件 file 由于在生成时 obj。 请重新生成此对象  
  
 使用时[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)，编译器检测到指向了它 CIL.obj 比新的.pch 文件。 CIL.obj 文件中的信息已过期。 重新生成对象。  
  
 如果使用进行编译也可能发生 C1382 **/Yc**，但还将多个源代码文件传递到编译器。  若要解决，不要使用**/Yc**时将多个源传递给编译器的代码文件。  有关详细信息，请参阅[/Yc （创建预编译标头文件）](../../build/reference/yc-create-precompiled-header-file.md)。
