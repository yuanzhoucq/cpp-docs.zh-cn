---
title: 链接器工具错误 LNK1120 |Microsoft Docs
ms.custom: ''
ms.date: 05/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1120
dev_langs:
- C++
helpviewer_keywords:
- LNK1120
ms.assetid: 56aa7d36-921f-4daf-b44d-cca0d4fb1b51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f1d2a55d683e9c8b9d6a0da2b3e5fa78d5a39933
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725564"
---
# <a name="linker-tools-error-lnk1120"></a>链接器工具错误 LNK1120

> *数字*无法解析的外部对象  
  
错误 LNK1120 报告计数 (*数*) 的此链接操作的未解析的外部符号错误。 大多数无法解析的单独的报告的外部符号错误[链接器工具错误 LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)并[链接器工具错误 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)，其中前加上此错误消息，一次为每个无法解析的外部符号时出错。  
  
若要修复此错误，更正所有其他的未解析的外部错误或其他生成输出中在其之前的链接器错误。 当不再有任何未解析的外部错误时，不报告此错误。  
