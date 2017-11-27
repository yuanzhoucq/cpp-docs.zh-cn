---
title: "编译器警告 （等级 1） C4810 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4810
dev_langs: C++
helpviewer_keywords: C4810
ms.assetid: 39e2cae0-9c1c-4ac1-aaa0-5f661d06085b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 65c9c51a7672bea5d6aec81d8b1ee2363519e488
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4810"></a>编译器警告（等级 1）C4810
杂注 pack(show) 的值 == n  
  
 当你使用 **pack** 杂注的[“显示”](../../preprocessor/pack.md) 选项时，将发出此警告。 *n* 是当前的 pack 值。  
  
 例如，下面的代码演示 C4810 警告如何处理 pack 杂注：  
  
```  
// C4810.cpp  
// compile with: /W1 /LD  
// C4810 expected  
#pragma pack(show)  
#pragma pack(4)  
#pragma pack(show)  
```