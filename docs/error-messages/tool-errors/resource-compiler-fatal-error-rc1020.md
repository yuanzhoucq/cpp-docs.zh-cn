---
title: 资源编译器错误 RC1020
ms.date: 11/04/2016
f1_keywords:
- RC1020
helpviewer_keywords:
- RC1020
ms.assetid: 3e073ebf-9136-4bf8-ac6a-3c642ed64594
ms.openlocfilehash: ff4cc5564f59d0adf74ae86149130dd5d017a9ae
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182677"
---
# <a name="resource-compiler-fatal-error-rc1020"></a>资源编译器错误 RC1020

意外的 "#endif"

出现 `#endif` 指令，但没有匹配的 `#if`、 **#ifdef**或 **#ifndef**指令。

请确保每个 `#if`、 **#ifdef**和 **#ifndef**语句的 `#endif` 都匹配。
