---
title: 链接器工具警告 LNK4020
ms.date: 05/29/2018
f1_keywords:
- LNK4020
helpviewer_keywords:
- LNK4020
ms.openlocfilehash: 7810fd9a97a8f6e22ad362819a024358a9f4b07c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298576"
---
# <a name="linker-tools-warning-lnk4020"></a>链接器工具警告 LNK4020

> 中的类型记录*文件名*' 已损坏; 某些符号和类型可能不能在调试器中访问

PDB 文件*文件名*已损坏的类型记录。

此问题通常是次要的其他生成问题;这是第一个报告的生成问题，除非出现其他错误和警告处理第一个。 如果这是第一个报告的问题，可能需要清除生成目录并重新生成你的项目。 如果使用并行生成过程，请参阅此错误仍然存在时序列化您的生成。