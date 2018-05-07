---
title: 资源编译器错误 RC1018 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1018
dev_langs:
- C++
helpviewer_keywords:
- RC1018
ms.assetid: bb1d2efd-6898-412f-bb03-9ff94c54e4dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc54586d03aaf84882120cee0428990caa8cae97
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-fatal-error-rc1018"></a>资源编译器错误 RC1018
意外的 #elif  
  
 `#elif`指令未出现在`#if`， **#ifdef**，或 **#ifndef**构造。  
  
 请确保有`#if`， **#ifdef**，或 **#ifndef**实际上此语句前的语句。