---
title: "编译器警告 （等级 1） C4049 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4049
dev_langs: C++
helpviewer_keywords: C4049
ms.assetid: d11c1870-bcfc-4d71-8945-b87ec6ec3514
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6e749571bcf4c0e1547279a857e50556f766c576
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4049"></a>编译器警告 （等级 1） C4049
编译器限制： 显示终止行号  
  
 该文件包含多个 16777215 (2<sup>24</sup>-1) 源行。 编译器停止在 16777215 编号。  
  
 对于在行 16777215 之后的代码：  
  
-   映像将包含没有调试信息的行号。  
  
-   一些诊断可能会报告与错误的行号。  
  
-   .asm 列表 (/ FAs) 可能有不正确的行号。