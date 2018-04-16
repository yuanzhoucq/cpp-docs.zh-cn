---
title: "链接器工具警告 LNK4086 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4086
dev_langs:
- C++
helpviewer_keywords:
- LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fcd701401c798d7126be4f4239ee533b14d90652
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4086"></a>链接器工具警告 LNK4086
入口点 function 不是使用的参数，则数字字节的 __stdcall图像可能无法运行  
  
 DLL 的入口点必须是`__stdcall`。 请重新编译具有函数[/Gz](../../build/reference/gd-gr-gv-gz-calling-convention.md)选项或指定`__stdcall`或 WINAPI 时将函数定义。