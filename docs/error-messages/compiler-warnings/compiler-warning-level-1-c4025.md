---
title: "编译器警告 （等级 1） C4025 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4025
dev_langs: C++
helpviewer_keywords: C4025
ms.assetid: c4f6a651-0641-4446-973e-8290065e49ad
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 07bb6db07baed9ce191ed396177c73cf7d3fa2ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4025"></a>编译器警告（等级 1）C4025
“编号”: 基指针传递给带变量参数的函数: 参数号  
  
 将基指针传递给使用变量参数的函数会导致指针被规范化，结果不可预知。 请勿将基指针传递给带变量参数的函数。