---
title: 编译器警告 C4962 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4962
dev_langs:
- C++
helpviewer_keywords:
- C4962
ms.assetid: 62b156fe-04e5-4a6e-9339-6ab148185f87
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 74878342e153a78c6149ae3b177eff8c49e4a261
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272095"
---
# <a name="compiler-warning-c4962"></a>编译器警告 C4962
“function”：已禁用按配置文件优化，原因在于优化导致了配置数据文件不一致  
  
 函数不是使用 /LTCG:PGO 编译的，因为该函数的计数（分析）数据不可靠。 重做分析以重新生成包含该函数不可靠分析数据的 .pgc 文件。  
  
 默认情况下，此警告处于关闭状态。 有关详细信息，请参阅 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。