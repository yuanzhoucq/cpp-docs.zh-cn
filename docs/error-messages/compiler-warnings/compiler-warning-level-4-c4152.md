---
title: "编译器警告 （等级 4） C4152 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4152
dev_langs: C++
helpviewer_keywords: C4152
ms.assetid: 6025ab70-d7cf-4730-913a-3ca0b1186a3a
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1958ae2c14b9e8de7c17060419f20064da24eec1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4152"></a>编译器警告（等级 4）C4152
非标准扩展, 表达式中的函数/数据指针转换  
  
 在函数指针与数据指针之间转换。 在 Microsoft 扩展 (/Ze) 下允许此类转换，但在 ANSI C 下则不允许。