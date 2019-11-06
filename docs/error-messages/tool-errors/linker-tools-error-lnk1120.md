---
title: 链接器工具错误 LNK1120
description: 描述 LNK1120 链接器错误，该错误报告链接中无法解析的外部符号错误的数目。
ms.date: 10/31/2019
f1_keywords:
- LNK1120
helpviewer_keywords:
- LNK1120
ms.assetid: 56aa7d36-921f-4daf-b44d-cca0d4fb1b51
ms.openlocfilehash: 21a1ede07a69cdc065dd897715e243115529600d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626584"
---
# <a name="linker-tools-error-lnk1120"></a>链接器工具错误 LNK1120

> *无法解析*的外部

错误 LNK1120 报告当前链接中[无法解析的外部符号](linker-tools-error-lnk2001.md#what-is-an-unresolved-external-symbol)错误的数目。

每个无法解析的外部符号首先由[LNK2001](linker-tools-error-lnk2001.md)或[LNK2019](linker-tools-error-lnk2019.md)错误报告。 LNK1120 消息最后出现，并显示无法解析的符号错误计数。

> [!IMPORTANT]
> **不需要修复此错误。** 如果在生成输出中更正了所有 LNK2001 和 LNK2019 链接器错误，则此错误将消失。 始终从报告的第一个错误开始修复问题。 稍后的错误可能是由早期错误引起的，并且在修复了以前的错误时消失。
