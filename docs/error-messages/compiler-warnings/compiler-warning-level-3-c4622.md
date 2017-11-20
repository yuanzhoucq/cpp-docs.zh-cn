---
title: "编译器警告 （等级 3） C4622 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4622
dev_langs: C++
helpviewer_keywords: C4622
ms.assetid: d3c879f0-4492-4f4b-b26d-230993f3a933
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 03c6edd3732caad4285848a1acd0176ae8e343ac
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4622"></a>编译器警告（等级 3）C4622
覆盖创建对象文件的预编译头期间生成的调试信息：“file”  
  
 当使用 [/Yu](../../build/reference/yu-use-precompiled-header-file.md) （使用预编译头）选项编译时，指定文件中的 CodeView 信息丢失。  
  
 当创建或使用预编译头文件时（使用 [/Fo](../../build/reference/fo-object-file-name.md)）重命名对象文件，并使用新对象文件进行链接。