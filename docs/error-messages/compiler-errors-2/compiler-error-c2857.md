---
title: 编译器错误 C2857 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2857
dev_langs:
- C++
helpviewer_keywords:
- C2857
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4bb2ec5047646bea420bf109f18a72d87a8f7c44
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246342"
---
# <a name="compiler-error-c2857"></a>编译器错误 C2857
#include 源文件中找不到与 /Ycfilename 命令行选项指定的语句  
  
 [/Yc](../../build/reference/yc-create-precompiled-header-file.md)选项指定不包括正在编译的源文件中的包含文件的名称。  
  
 此错误可能由`#include`未编译的条件编译块中的语句。