---
title: 链接器工具错误 LNK1302
ms.date: 11/04/2016
f1_keywords:
- LNK1302
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
ms.openlocfilehash: 8323fa234851ce3ba12083adb74d5ee0fba0ac69
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194923"
---
# <a name="linker-tools-error-lnk1302"></a>链接器工具错误 LNK1302

只支持链接安全的 .netmodule；无法链接文件 .netmodule

将 .netmodule （使用 **/LN**编译）传递给链接器，用户尝试调用 MSIL 链接。  如果C++用于 MSIL 链接的模块是使用 **/clr： safe**编译的，则该模块对其有效。

若要更正此错误，请使用 **/clr： safe**进行编译，以启用 MSIL 链接，或将 **/clr**或 **/clr： pure**文件传递到链接器而不是模块。

有关详细信息，请参阅

- [/LN（创建 MSIL 模块）](../../build/reference/ln-create-msil-module.md)

- [用作链接器输入的 .netmodule 文件](../../build/reference/netmodule-files-as-linker-input.md)
