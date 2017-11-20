---
title: "编译器警告 （等级 1） C4153 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4153
dev_langs: C++
helpviewer_keywords: C4153
ms.assetid: 37a15754-9dba-470b-adda-c4b888064b3e
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c46774d944e6a7187a4345f76e1f8e7c7e7c3f87
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4153"></a>编译器警告（等级 1）C4153
表达式中的函数/数据指针转换  
  
 在函数指针与数据指针之间转换。 在 Microsoft 扩展 (/Ze) 下允许此类转换，但在 ANSI C 下则不允许。