---
title: 链接器工具错误 LNK1223 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1223
dev_langs:
- C++
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8639919c74559829367108b36d62594e2a83a91a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067971"
---
# <a name="linker-tools-error-lnk1223"></a>链接器工具错误 LNK1223

无效或损坏的文件： 文件包含无效的.pdata 基值

对于使用 pdata 的 RISC 平台，如果编译器发出具有无序条目的 .pdata 部分，则将发生此错误。

若要解决此问题，请尝试编译但不[/GL （全程序优化）](../../error-messages/tool-errors/linker-tools-error-lnk1223.md)启用。 在某些情况下，空的函数体也可能导致此错误。