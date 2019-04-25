---
title: 链接器工具错误 LNK1309
ms.date: 11/04/2016
f1_keywords:
- LNK1309
helpviewer_keywords:
- LNK1309
ms.assetid: 10146071-883f-4849-97d1-c7468f90efbb
ms.openlocfilehash: ea675ca835dfc3fe4881e5fabbea746a4442b10a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187438"
---
# <a name="linker-tools-error-lnk1309"></a>链接器工具错误 LNK1309

> *type1*模块检测到; 具有无效开关 /CLRIMAGETYPE:*y p e 2*

## <a name="remarks"></a>备注

CLR 映像类型通过请求 **/CLRIMAGETYPE**但链接器无法生成该类型的映像，因为一个或多个模块已与该类型不兼容。

例如，你将看到 LNK1309，如果指定 **/CLRIMAGETYPE:safe** ，并将传递使用生成的模块 **/clr: pure**。

**/Clr: pure**并 **/clr: safe**编译器选项和支持库在 Visual Studio 2015 中弃用，并在 Visual Studio 2017 中不受支持。

如果你尝试生成部分受信任的 CLR 纯应用程序使用 ptrustu [d].lib，也会看到 LNK1309。 有关如何创建部分受信任的应用程序的信息，请参阅[如何：通过移除 CRT 库 DLL 上的依赖项来创建部分受信任的应用程序](../../dotnet/create-a-partially-trusted-application.md)。

有关详细信息，请参阅[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)并[/CLRIMAGETYPE （指定 CLR 映像的类型）](../../build/reference/clrimagetype-specify-type-of-clr-image.md)。