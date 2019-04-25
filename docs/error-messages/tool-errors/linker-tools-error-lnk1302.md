---
title: 链接器工具错误 LNK1302
ms.date: 11/04/2016
f1_keywords:
- LNK1302
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
ms.openlocfilehash: c3b1117b31db4759b385943323a581da7a58f0c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160440"
---
# <a name="linker-tools-error-lnk1302"></a>链接器工具错误 LNK1302

只支持链接安全的 .netmodule；无法链接文件 .netmodule

.Netmodule (使用编译 **/LN**) 传递给链接器中的用户尝试调用 MSIL 链接。  一个C++模块是有效的 MSIL 链接如果用编译 **/clr: safe**。

若要更正此错误，编译与 **/clr: safe**来启用 MSIL 链接，或传递 **/clr**或 **/clr: pure** .obj 文件中的而不是模块链接器。

有关详细信息，请参见

- [/LN（创建 MSIL 模块）](../../build/reference/ln-create-msil-module.md)

- [用作链接器输入的 .netmodule 文件](../../build/reference/netmodule-files-as-linker-input.md)