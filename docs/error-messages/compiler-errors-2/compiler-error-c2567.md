---
title: "编译器错误 C2567 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2567
dev_langs: C++
helpviewer_keywords: C2567
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 28cd1dc74e15ae3cd63286fc6de9c3508bb1d279
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2567"></a>编译器错误 C2567
无法打开 file 中的元数据，文件可能已删除或移动  
  
 在源中引用的元数据文件 (与`#using`) 未找到位于同一目录中由编译器后端进程按照原样编译器前端进程。 请参阅[#using 指令](../../preprocessor/hash-using-directive-cpp.md)有关详细信息。  
  
 如果使用进行编译则可能导致 C2567 **/c**在某个上计算机，然后尝试在其他计算机上的链接时代码生成。 有关详细信息，请参阅[/LTCG （链接时间代码生成）](../../build/reference/ltcg-link-time-code-generation.md))。  
  
 此外，它也可能表示你的计算机已没有更多内存。  
  
 若要更正此错误，请确保元数据文件位于相同的目录位置为生成过程的所有阶段。