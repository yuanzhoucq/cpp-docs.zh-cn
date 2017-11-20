---
title: "编译器错误 C2170 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2170
dev_langs: C++
helpviewer_keywords: C2170
ms.assetid: d5c663f0-2459-4e11-a8bf-a52b62f3c71d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8520e9ea71d90e7f97c6296d4326abb1fd4c7609
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2170"></a>编译器错误 C2170
identifier： 未声明为函数，不能为内部函数  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  杂注`intrinsic`用于与函数之外的项。  
  
2.  杂注`intrinsic`用于没有内部形式的函数。