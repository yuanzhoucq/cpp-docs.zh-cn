---
title: 链接器工具错误 LNK1112 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1112
dev_langs:
- C++
helpviewer_keywords:
- LNK1112
ms.assetid: 425793d8-37e6-4072-9b6e-c3d4e9c12562
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 79ca2afc7270a69c443447d1b294ee7ec8bbe5a7
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704992"
---
# <a name="linker-tools-error-lnk1112"></a>链接器工具错误 LNK1112

> 模块计算机类型*type1*与目标计算机类型的冲突*type2*

## <a name="remarks"></a>备注

指定为输入的对象文件为不同的计算机类型进行了编译。

例如，如果你尝试链接使用 **/clr** 编译的对象文件和使用 **/clr:pure** （计算机类型 CEE）编译的对象文件，则链接器将生成错误 LNK1112。 **/Clr: pure**编译器选项是在 Visual Studio 2015 中已过时，并在 Visual Studio 2017 中不支持。

同样，如果你使用 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 编译器创建一个模块并使用 x86 编译器创建另一个模块，然后尝试链接它们，那么链接器将生成 LNK1112。

此错误的可能原因是你正在开发 64 位应用程序但未安装其中一个 Visual C++ 64 位编译器。 在这种情况下，64 位配置将不可用。 若要解决此问题，运行 Visual Studio 的安装程序并安装缺少的 C++ 组件。

如果你更改，也可能发生此错误**活动解决方案配置**中**Configuration Manager** ，然后尝试生成项目，然后删除中间项目文件。 若要解决此错误，请选择**重新生成解决方案**从**生成**菜单。 你还可以选择**清理解决方案**从**生成**菜单，然后生成解决方案。

## <a name="see-also"></a>请参阅

- [链接器工具错误和警告](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)
