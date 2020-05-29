---
title: 链接器工具警告 LNK4086
ms.date: 11/04/2016
f1_keywords:
- LNK4086
helpviewer_keywords:
- LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
ms.openlocfilehash: 6e012ceb5e20855353c69bbcde85fb78afad2011
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183418"
---
# <a name="linker-tools-warning-lnk4086"></a>链接器工具警告 LNK4086

入口点 "function" 与参数的 "number" 个字节不 __stdcall;映像可能无法运行

DLL 的入口点必须 `__stdcall`。 可以用[/Gz](../../build/reference/gd-gr-gv-gz-calling-convention.md)选项重新编译该函数，也可以在定义函数时指定 `__stdcall` 或 WINAPI。
