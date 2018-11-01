---
title: Microsoft 扩展
ms.date: 11/04/2016
helpviewer_keywords:
- Microsoft extensions to C/C++
ms.assetid: 68654516-24ef-4f33-aae2-175f86cc1979
ms.openlocfilehash: d8104c2df2335e11dcb711108d566e0fdd069762
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50592200"
---
# <a name="microsoft-extensions"></a>Microsoft 扩展

*asm 语句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm***程序集指令* **;**<sub>选择  </sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm {***程序集指令列表***};**<sub>选择    </sub>

*程序集指令列表*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*程序集指令* **;**<sub>选择</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*程序集指令* **;***程序集指令列表* **;**<sub>选择</sub>

*ms 修饰符列表*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ms 修饰符* *ms 修饰符列表*<sub>选择</sub>

*ms 修饰符*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__cdecl**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__fastcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__stdcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__syscall** （为将来的实现保留）<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__oldcall** （为将来的实现保留）<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__unaligned** （为将来的实现保留）<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*基于修饰符*

*基于修饰符*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__based (** *基于类型* **)**

*基于类型*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*名称*