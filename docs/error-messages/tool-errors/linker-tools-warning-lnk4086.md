---
title: 链接器工具警告 LNK4086
ms.date: 11/04/2016
f1_keywords:
- LNK4086
helpviewer_keywords:
- LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
ms.openlocfilehash: f692f848825cd3d8e5e1fc042cb94d7cce8ea6bf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87195806"
---
# <a name="linker-tools-warning-lnk4086"></a>链接器工具警告 LNK4086

入口点 "function" 与参数的 "number" 个字节不 __stdcall;映像可能无法运行

DLL 的入口点必须是 **`__stdcall`** 。 在定义函数时，可以用[/Gz](../../build/reference/gd-gr-gv-gz-calling-convention.md)选项重新编译该函数，也可以指定 **`__stdcall`** 或 WINAPI。
