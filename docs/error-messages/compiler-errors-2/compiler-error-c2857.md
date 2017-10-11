---
title: "编译器错误 C2857 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2857
dev_langs:
- C++
helpviewer_keywords:
- C2857
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: ca0f2b8847600096c9e39de24c58e6a0021fa83f
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2857"></a>编译器错误 C2857
#include 源文件中找不到与 /Ycfilename 命令行选项指定的语句  
  
 [/Yc](../../build/reference/yc-create-precompiled-header-file.md)选项指定不包括正在编译的源文件中的包含文件的名称。  
  
 此错误可能由`#include`未编译的条件编译块中的语句。
