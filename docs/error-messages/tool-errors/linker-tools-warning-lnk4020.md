---
title: 链接器工具警告 LNK4020 |Microsoft 文档
ms.custom: ''
ms.date: 05/29/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4020
dev_langs:
- C++
helpviewer_keywords:
- LNK4020
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e55239b90910f6c151949c53939d4f8ed7c15c5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2018
ms.locfileid: "34570680"
---
# <a name="linker-tools-warning-lnk4020"></a>链接器工具警告 LNK4020

> 中的类型记录*filename*已损坏; 某些符号和类型可能不能从调试器访问

PDB 文件*filename*具有损坏的类型记录。

此问题通常是与其他生成问题; 辅助这是第一个报告的生成问题，除非其他错误和警告处理第一个。 如果这是第一个报告的问题，你可能需要清除生成目录并重新生成你的项目。 如果使用并行生成过程，请参阅如果错误仍然存在，序列化你的生成时。