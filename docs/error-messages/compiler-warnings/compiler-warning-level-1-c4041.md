---
title: "编译器警告 （等级 1） C4041 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4041
dev_langs:
- C++
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 42779d33cad8fc867b08b412d2ded294360a0812
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4041"></a>编译器警告（等级 1）C4041
编译器限制 : 正在终止浏览器输出  
  
 浏览器信息超出了编译器限制。  
  
 使用 [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) （浏览器信息包含局部变量）进行编译可能导致该警告。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复  
  
1.  使用 /Fr（浏览器信息不含局部变量）进行编译。  
  
2.  禁用浏览器输出（不使用 /FR 或 /Fr 进行编译）。