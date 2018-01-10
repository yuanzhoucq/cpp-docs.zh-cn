---
title: "-Q 选项 （低级别操作） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /q
dev_langs: C++
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.assetid: 9fa738b9-630a-4bde-bc87-bdfa30552be4
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d970c2de5e34840ab2ed77f229c329db3c6f72fd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="q-options-low-level-operations"></a>/Q 选项（低级别操作）
你可以使用**/Q**编译器选项执行以下低级别编译器操作：  
  
-   [/Qfast_transcendentals （强制快速先验）](../../build/reference/qfast-transcendentals-force-fast-transcendentals.md)： 生成快速先验。  
  
-   [/Qifist (取消 _ftol)](../../build/reference/qifist-suppress-ftol.md)： 取消`_ftol`从浮点类型转换为整型时必需 (仅限 x86)。  
  
-   [/Qimprecise_fwaits （移除 Try 块中的 fwaits）](../../build/reference/qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)： 删除`fwait`内的命令`try`块。  
  
-   [/Qpar （自动并行化）](../../build/reference/qpar-auto-parallelizer.md)： 启用自动并行化的循环标记有[#pragma loop （)](../../preprocessor/loop.md)指令。  
  
-   [/Qpar-report （自动并行化程序报告等级）](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)： 启用自动并行化的报告级别。  
  
-   [/ Qsafe_fp_loads](../../build/reference/qsafe-fp-loads.md)： 取消优化，为浮点寄存器加载并为内存和 MMX 之间移动注册。  
  
-   [/Qvec-report （自动向量化报告等级）](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md)： 启用自动矢量化的报告级别。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)