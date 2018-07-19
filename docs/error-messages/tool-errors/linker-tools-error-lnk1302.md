---
title: 链接器工具错误 LNK1302 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1302
dev_langs:
- C++
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6aa84a411f91303c84acb44e2e6c0ab3d975e19f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299414"
---
# <a name="linker-tools-error-lnk1302"></a>链接器工具错误 LNK1302
只支持链接安全的 .netmodule；无法链接文件 .netmodule  
  
 .Netmodule (使用编译 **/LN**) 中进行调用 MSIL 链接的用户尝试传递到链接器。  C + + 模块可用于 MSIL 链接如果进行编译的 **/clr: safe**。  
  
 若要更正此错误，编译与 **/clr: safe**启用 MSIL 链接，或传递 **/clr**或 **/clr： 纯**到链接器而不是模块的.obj 文件。  
  
 有关详细信息，请参见  
  
-   [/LN（创建 MSIL 模块）](../../build/reference/ln-create-msil-module.md)  
  
-   [用作链接器输入的 .netmodule 文件](../../build/reference/netmodule-files-as-linker-input.md)