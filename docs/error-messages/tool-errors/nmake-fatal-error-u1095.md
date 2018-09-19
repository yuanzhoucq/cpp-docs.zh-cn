---
title: NMAKE 错误 U1095 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1095
dev_langs:
- C++
helpviewer_keywords:
- U1095
ms.assetid: a392582b-06db-4568-9c13-450293a4fbda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 964ec1d029e56a5d9d78659ad919c71a4e44506d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039876"
---
# <a name="nmake-fatal-error-u1095"></a>NMAKE 错误 U1095

扩展的命令行命令行太长

宏展开之后，给定的命令行超过了操作系统的命令行长度限制。

MS-DOS 命令行上允许最多为 128 个字符。

如果该命令是可以接受命令行输入文件中的程序，更改该命令，并从磁盘上的文件或内联文件提供输入。 例如，链接和 LIB 接受输入的响应文件。