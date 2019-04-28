---
title: 链接器工具警告 LNK4102
ms.date: 11/04/2016
f1_keywords:
- LNK4102
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
ms.openlocfilehash: 0f9c8649988dd3056e98730ac4b02022a8c9dd51
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327257"
---
# <a name="linker-tools-warning-lnk4102"></a>链接器工具警告 LNK4102

导出删除的析构函数 name;映像可能无法正确运行

该程序已尝试导出删除的析构函数。 生成删除可能会跨 DLL 边界，以便进程可以释放不拥有的内存。 请确保在.def 文件中，未列出给定的符号和符号未列出的参数 **/导入**或 **/export**链接器命令行中的选项。

如果您正在重新生成的 C 运行时库，可以忽略此消息。