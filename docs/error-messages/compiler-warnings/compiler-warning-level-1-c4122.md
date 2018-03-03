---
title: "编译器警告 （等级 1） C4122 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4122
dev_langs:
- C++
helpviewer_keywords:
- C4122
ms.assetid: 9a83eb0d-8708-42f7-988a-b0b6f2f646a0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b78c0f3589d40f18e96f52e9bfb642c8550becb5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4122"></a>编译器警告（等级 1）C4122
“function”: alloc_text 仅适用于带 C 链接的函数  
  
 **alloc_text** 杂注仅适用于使用 **extern c**声明的函数。 它不能与外部 C++ 函数一起使用。  
  
 将忽略杂注。