---
title: 链接器工具警告 LNK4102 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4102
dev_langs:
- C++
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9daaffc4ddfa9a869c2e60e2c05dc2b7e296d94b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031844"
---
# <a name="linker-tools-warning-lnk4102"></a>链接器工具警告 LNK4102

导出删除的析构函数 name;映像可能无法正确运行

该程序已尝试导出删除的析构函数。 生成删除可能会跨 DLL 边界，以便进程可以释放不拥有的内存。 请确保在.def 文件中，未列出给定的符号和符号未列出的参数 **/导入**或 **/export**链接器命令行中的选项。

如果您正在重新生成的 C 运行时库，可以忽略此消息。