---
title: 链接器工具警告 LNK4086
ms.date: 11/04/2016
f1_keywords:
- LNK4086
helpviewer_keywords:
- LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
ms.openlocfilehash: c6a5a0714e070e6cf3aee8efcdfbdfa07fa9ee69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399924"
---
# <a name="linker-tools-warning-lnk4086"></a>链接器工具警告 LNK4086

入口点 function 不是使用的参数，则 number 个字节的 __stdcall映像可能无法运行

DLL 的入口点必须是`__stdcall`。 请重新编译的函数[/Gz](../../build/reference/gd-gr-gv-gz-calling-convention.md)选项，或指定`__stdcall`或 WINAPI 时定义的函数。