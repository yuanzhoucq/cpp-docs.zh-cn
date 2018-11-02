---
title: 链接器工具错误 LNK1112
ms.date: 11/04/2016
f1_keywords:
- LNK1112
helpviewer_keywords:
- LNK1112
ms.assetid: 425793d8-37e6-4072-9b6e-c3d4e9c12562
ms.openlocfilehash: bc01d56fb8144d23b91c82a7f791a70a5dadb7ef
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607085"
---
# <a name="linker-tools-error-lnk1112"></a>链接器工具错误 LNK1112

> 模块计算机类型*type1*冲突与目标计算机类型*type2*

## <a name="remarks"></a>备注

指定为输入的对象文件为不同的计算机类型进行了编译。

例如，如果你尝试链接使用 **/clr** 编译的对象文件和使用 **/clr:pure** （计算机类型 CEE）编译的对象文件，则链接器将生成错误 LNK1112。 **/Clr: pure**编译器选项在 Visual Studio 2015 中弃用并在 Visual Studio 2017 中不受支持。

同样，如果您创建一个模块使用 x64 编译器和另一个模块与 x86 编译器，然后尝试链接，链接器将生成 LNK1112。

此错误的可能原因是你正在开发 64 位应用程序但未安装其中一个 Visual C++ 64 位编译器。 在这种情况下，64 位配置将不可用。 若要解决此问题，运行 Visual Studio 的安装程序并安装缺少的 C++ 组件。

如果更改，也可能发生此错误**活动解决方案配置**中**Configuration Manager** ，然后尝试生成项目，然后删除中间项目文件。 若要解决此错误，请选择**重新生成解决方案**从**生成**菜单。 您还可以选择**清理解决方案**从**生成**菜单，然后生成解决方案。

## <a name="see-also"></a>请参阅

- [链接器工具错误和警告](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)
