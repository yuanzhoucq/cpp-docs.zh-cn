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
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: bbd890a7506059f939ca6d8957f71e20cba771f8
ms.contentlocale: zh-cn
ms.lasthandoff: 04/12/2017

---
# <a name="fatal-error-c1383"></a>错误 C1383
编译器选项 /GL 与安装的公共语言运行时版本不兼容  
  
 将以前版本的公共语言运行时与较新编译器结合使用时，以及使用 **/clr** 和 **/GL.**进行编译时，会发生 C1383。  
  
 要进行解决，请勿将 **/GL** 与 **/clr** 结合使用，或是安装随你的编译器附带的公共语言运行时版本。  
  
 有关详细信息，请参阅[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)和[/GL （全程序优化）](../../build/reference/gl-whole-program-optimization.md)。
