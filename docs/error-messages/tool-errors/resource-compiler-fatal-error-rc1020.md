---
title: 资源编译器错误 RC1020 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1020
dev_langs:
- C++
helpviewer_keywords:
- RC1020
ms.assetid: 3e073ebf-9136-4bf8-ac6a-3c642ed64594
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fe19b079a0407f07796bd8141db2cbedaf02cbbb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032960"
---
# <a name="resource-compiler-fatal-error-rc1020"></a>资源编译器错误 RC1020

意外的 #endif

`#endif`指令没有匹配出现`#if`， **#ifdef**，或 **#ifndef**指令。

请确保是否有匹配`#endif`为每个`#if`， **#ifdef**，并 **#ifndef**语句。