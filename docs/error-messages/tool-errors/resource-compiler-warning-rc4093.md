---
title: 资源编译器警告 RC4093
ms.date: 11/04/2016
f1_keywords:
- RC4093
helpviewer_keywords:
- RC4093
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
ms.openlocfilehash: 23bf436e6e8338f89bc576564181c84715028332
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541877"
---
# <a name="resource-compiler-warning-rc4093"></a>资源编译器警告 RC4093

非活动代码中的字符常量中的非转义有换行符

常数表达式`#if`， `#elif`， **#ifdef**，或 **#ifndef**计算结果为零，从而使代码的预处理器指令遵循处于非活动状态。 此非活动代码中换行字符出现在一组单引号或双引号括起来。

直到下一步双引号被认为是在字符常数中的所有文本。