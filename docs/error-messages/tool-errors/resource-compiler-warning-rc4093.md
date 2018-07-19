---
title: 资源编译器警告 RC4093 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC4093
dev_langs:
- C++
helpviewer_keywords:
- RC4093
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9cca3c2a139e1109746f3a690cfb3f31509a9fe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322427"
---
# <a name="resource-compiler-warning-rc4093"></a>资源编译器警告 RC4093
非活动代码中的字符常量中的非转义换行  
  
 常量表达式的`#if`， `#elif`， **#ifdef**，或 **#ifndef**计算结果为零，使代码的预处理器指令跟处于非活动状态。 在此非活动代码中换行字符出现在单引号或双引号括起来的一组。  
  
 直到下一步双引号被认为是字符常量内的所有文本。