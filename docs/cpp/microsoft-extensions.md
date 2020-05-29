---
title: Microsoft 扩展
ms.date: 11/04/2016
helpviewer_keywords:
- Microsoft extensions to C/C++
ms.assetid: 68654516-24ef-4f33-aae2-175f86cc1979
ms.openlocfilehash: a2d0846e55122f177b4868c2e80c4f1d27267f5e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179401"
---
# <a name="microsoft-extensions"></a>Microsoft 扩展

*asm 语句*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__asm***程序集指令* **;** <sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__asm {** *assembly* **;** <sub>opt</sub>

*程序集指令列表*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*程序集指令* **;** <sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*程序集指令* **;** *程序集指令列表* **;** <sub>opt</sub>

*ms 修饰符-列表*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ms 修饰符* *ms 修饰符-列表*<sub>opt</sub>

*ms 修饰符*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__cdecl**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__fastcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__stdcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__syscall** （为将来的实现保留）<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__oldcall** （为将来的实现保留）<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__unaligned** （为将来的实现保留）<br/>
*基于*&nbsp;&nbsp;&nbsp;&nbsp;

*基于修饰符*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__based （** *基于类型* **）**

*基于类型*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*名称*
