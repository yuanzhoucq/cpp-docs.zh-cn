---
title: 链接器工具警告 LNK4022
ms.date: 11/04/2016
f1_keywords:
- LNK4022
helpviewer_keywords:
- LNK4022
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
ms.openlocfilehash: 9b9ce09a7133c0bdc18957f6ade213583e9540eb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194182"
---
# <a name="linker-tools-warning-lnk4022"></a>链接器工具警告 LNK4022

找不到符号 "symbol" 的唯一匹配项

LINK 或 LIB 找到了给定未修饰符号的多个匹配项，但它未能解析多义性。 不生成输出文件（.exe、.dll、.exp 或 .lib）。 对于每个重复符号，此警告后跟一个警告[LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md) ，最后跟有严重错误[LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md)。

若要防止出现此警告，请指定修饰形式的符号。 对对象运行[DUMPBIN](../../build/reference/dumpbin-options.md)以查看修饰名。
