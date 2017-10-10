---
title: "错误 C1383 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1383
dev_langs:
- C++
helpviewer_keywords:
- C1383
ms.assetid: ca224d14-d687-4fd6-80c2-8b82f28924ea
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: ff620211470e82cd53a893bdee94fb1ca5d405c9
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="fatal-error-c1383"></a>错误 C1383
编译器选项 /GL 与安装的公共语言运行时版本不兼容  
  
 将以前版本的公共语言运行时与较新编译器结合使用时，以及使用 **/clr** 和 **/GL.**进行编译时，会发生 C1383。  
  
 要进行解决，请勿将 **/GL** 与 **/clr** 结合使用，或是安装随你的编译器附带的公共语言运行时版本。  
  
 有关详细信息，请参阅 [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) 和 [/GL (Whole Program Optimization)](../../build/reference/gl-whole-program-optimization.md)。
