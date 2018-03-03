---
title: "链接器工具错误 LNK1302 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1302
dev_langs:
- C++
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2a5b9201608d6d457288c7ade9376147da08bcb9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1302"></a>链接器工具错误 LNK1302
只支持链接安全的 .netmodule；无法链接文件 .netmodule  
  
 .Netmodule (使用编译**/LN**) 中进行调用 MSIL 链接的用户尝试传递到链接器。  C + + 模块可用于 MSIL 链接如果进行编译的**/clr: safe**。  
  
 若要更正此错误，编译与**/clr: safe**启用 MSIL 链接，或传递**/clr**或**/clr： 纯**到链接器而不是模块的.obj 文件。  
  
 有关详细信息，请参见  
  
-   [/LN （创建 MSIL 模块）](../../build/reference/ln-create-msil-module.md)  
  
-   [用作链接器输入的 .netmodule 文件](../../build/reference/netmodule-files-as-linker-input.md)