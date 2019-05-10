---
title: 链接器工具错误 LNK1223
ms.date: 11/04/2016
f1_keywords:
- LNK1223
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
ms.openlocfilehash: 331521c357389c2f7c1aa786969154a2b747ffe5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242815"
---
# <a name="linker-tools-error-lnk1223"></a>链接器工具错误 LNK1223

无效或损坏的文件： 文件包含无效的.pdata 基值

对于使用 pdata 的 RISC 平台，如果编译器发出具有无序条目的 .pdata 部分，则将发生此错误。

若要解决此问题，请尝试编译但不[/GL （全程序优化）](../../error-messages/tool-errors/linker-tools-error-lnk1223.md)启用。 在某些情况下，空的函数体也可能导致此错误。