---
title: "编译器警告 （等级 1） C4182 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4182
dev_langs: C++
helpviewer_keywords: C4182
ms.assetid: 8970f3c6-e2dd-407e-b2ec-964360eb8b43
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dfd94e5c98e1ca6e19e3e34c3028c93148871cf4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4182"></a>编译器警告（等级 1）C4182
\#包括嵌套级别为 number 层;可能的无限递归  
  
 由于嵌套的包含文件数量过多，编译器用尽了堆上的空间。 当包含文件包含在另一个包含文件中时，它就是嵌套的。  
  
 此消息是信息性消息，出现在错误 [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md)之前。