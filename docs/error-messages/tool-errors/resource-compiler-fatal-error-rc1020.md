---
title: 资源编译器错误 RC1020
ms.date: 11/04/2016
f1_keywords:
- RC1020
helpviewer_keywords:
- RC1020
ms.assetid: 3e073ebf-9136-4bf8-ac6a-3c642ed64594
ms.openlocfilehash: ac4a9d521728b22966f6d8824479d13cc7394601
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297330"
---
# <a name="resource-compiler-fatal-error-rc1020"></a>资源编译器错误 RC1020

意外的 #endif

`#endif`指令没有匹配出现`#if`， **#ifdef**，或 **#ifndef**指令。

请确保是否有匹配`#endif`为每个`#if`， **#ifdef**，并 **#ifndef**语句。