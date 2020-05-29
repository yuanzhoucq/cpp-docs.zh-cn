---
title: 编译器警告（等级 2）C4653
ms.date: 11/04/2016
f1_keywords:
- C4653
helpviewer_keywords:
- C4653
ms.assetid: 90ec3317-3d39-4b4c-bcd1-97e7c799e1b6
ms.openlocfilehash: 994e9a4963e7e10af2313b3dcea5bb8b2b93426e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161732"
---
# <a name="compiler-warning-level-2-c4653"></a>编译器警告（等级 2）C4653

编译器选项 "option" 与预编译头不一致;已忽略当前命令行选项

使用 "使用预编译头（[/yu](../../build/reference/yu-use-precompiled-header-file.md)）" 选项指定的选项与创建预编译标头时指定的选项不一致。 此编译使用创建预编译标头时指定的选项。

在编译预编译标头期间指定了不同的 Pack 结构选项（[/Zp](../../build/reference/zp-struct-member-alignment.md)）值时，会出现此警告。
