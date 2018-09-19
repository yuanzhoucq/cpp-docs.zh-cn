---
title: 链接器工具错误 LNK1264 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1264
dev_langs:
- C++
helpviewer_keywords:
- LNK1264
ms.assetid: 23b1aad7-d382-42c1-bae8-db68575c57a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8232e83774dc53755b77ad9c8b3bbb2a0bcc6ae6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102733"
---
# <a name="linker-tools-error-lnk1264"></a>链接器工具错误 LNK1264

指定 /ltcg: pginstrument 但没有所需; 的代码生成检测失败

**/Ltcg: pginstrument**已指定，但找到了文件是使用编译任何.obj [/GL](../../build/reference/gl-whole-program-optimization.md)。 检测不能采用的位置，以及失败的链接。 必须在命令行上至少一个使用编译的.obj 文件 **/GL**以便进行检测。

按配置优化 (PGO) 是仅在 64 位编译器中可用。