---
title: 链接器工具警告 LNK4086 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4086
dev_langs:
- C++
helpviewer_keywords:
- LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b7b3ad3a8ceebf97ccdcf7a1d8079886f54a3984
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4086"></a>链接器工具警告 LNK4086
入口点 function 不是使用的参数，则数字字节的 __stdcall图像可能无法运行  
  
 DLL 的入口点必须是`__stdcall`。 请重新编译具有函数[/Gz](../../build/reference/gd-gr-gv-gz-calling-convention.md)选项或指定`__stdcall`或 WINAPI 时将函数定义。