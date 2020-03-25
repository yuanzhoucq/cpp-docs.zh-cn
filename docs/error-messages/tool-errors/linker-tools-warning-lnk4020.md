---
title: 链接器工具警告 LNK4020
ms.date: 05/29/2018
f1_keywords:
- LNK4020
helpviewer_keywords:
- LNK4020
ms.openlocfilehash: e818909cc0b590b0f7727846cfd7b469e8bc0e3f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194221"
---
# <a name="linker-tools-warning-lnk4020"></a>链接器工具警告 LNK4020

> "*filename*" 中的类型记录已损坏;某些符号和类型可能无法从调试器中访问

PDB*文件名的类型记录已损坏*。

此问题通常是其他生成问题的辅助问题;除非这是第一个报告的生成问题，否则请先处理其他错误和警告。 如果这是第一个报告的问题，则可能需要清除生成目录并重新生成项目。 如果使用并行生成过程，请查看序列化生成时错误是否仍然存在。
