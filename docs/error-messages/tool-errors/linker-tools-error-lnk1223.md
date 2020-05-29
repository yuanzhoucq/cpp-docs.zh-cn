---
title: 链接器工具错误 LNK1223
ms.date: 11/04/2016
f1_keywords:
- LNK1223
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
ms.openlocfilehash: 9c9d4c7224a7e65775354a86bd34fa9ea1b074af
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195027"
---
# <a name="linker-tools-error-lnk1223"></a>链接器工具错误 LNK1223

无效或损坏的文件：文件包含无效的 pdata 基值

对于使用 pdata 的 RISC 平台，如果编译器发出具有无序条目的 .pdata 部分，则将发生此错误。

若要解决此问题，请尝试不启用[/gl （全程序优化）](../../error-messages/tool-errors/linker-tools-error-lnk1223.md)进行编译。 在某些情况下，空的函数体也可能导致此错误。
