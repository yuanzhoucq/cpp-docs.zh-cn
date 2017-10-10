---
title: "错误 C1852 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1852
dev_langs:
- C++
helpviewer_keywords:
- C1852
ms.assetid: fa011004-b8d6-46f1-ba80-4785e4ce137f
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: cd7168c6ffa653af54404bf81cdc4d308a76783a
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="fatal-error-c1852"></a>错误 C1852
“filename”不是有效的预编译头文件  
  
 文件不是预编译头文件。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  使用 **/Yu** 或 **#pragma hdrstop**指定的无效文件。  
  
2.  如果未另行指定，编译器将假定 .pch 为文件扩展名。
