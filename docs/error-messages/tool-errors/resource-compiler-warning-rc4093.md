---
title: 资源编译器警告 RC4093
ms.date: 11/04/2016
f1_keywords:
- RC4093
helpviewer_keywords:
- RC4093
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
ms.openlocfilehash: 29d24f1e380f5c531e170e5dc23cf5c77eefb874
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182287"
---
# <a name="resource-compiler-warning-rc4093"></a>资源编译器警告 RC4093

非活动代码的字符常量中的非转义换行符

`#if`、`#elif`、 **#ifdef**或 **#ifndef**预处理器指令的常量表达式的计算结果为零，使得代码处于非活动状态。 在该非活动代码中，换行符出现在一组单引号或双引号内。

所有文本直到下一个双引号被视为在字符常量内。
