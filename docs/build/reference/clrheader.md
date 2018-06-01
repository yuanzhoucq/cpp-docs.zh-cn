---
title: -CLRHEADER | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLRHEADER
dev_langs:
- C++
helpviewer_keywords:
- -CLRHEADER dumpbin option
- /CLRHEADER dumpbin option
- CLRHEADER dumpbin option
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6cda2f03e8a0473d2c45f54c96ca97b043d80d5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704436"
---
# <a name="clrheader"></a>/CLRHEADER

显示特定于 CLR 的信息。

## <a name="syntax"></a>语法

> / CLRHEADER*文件*

### <a name="arguments"></a>自变量

|||
|-|-|
文件| 使用生成的图像文件[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="remarks"></a>备注

**/ CLRHEADER**显示有关在任何托管程序中使用的.NET 标头信息。 该输出显示的位置和大小，以字节为单位，.NET 标头和标头中的部分。

仅[/HEADERS](../../build/reference/headers.md) DUMPBIN 选项是可供产生的文件的使用[/GL](../../build/reference/gl-whole-program-optimization.md)编译器选项。

当 **/CLRHEADER**使用对使用 /clr 编译的文件，将有**clr 标头：** dumpbin 输出中的部分。 值**标志**指示使用哪个 /clr 选项：

- 0-/clr （映像可能包含本机代码）。

以编程方式还可以检查是否为公共语言运行时生成映像。  有关详细信息，请参阅[如何： 确定映像是否本机或 CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)。

**/Clr: pure**和 **/clr: safe**编译器选项是在 Visual Studio 2015 中已过时，在 Visual Studio 2017 中不支持。 必须为"纯"或"安全"的代码应移植到 C#。

## <a name="see-also"></a>请参阅

- [DUMPBIN 选项](../../build/reference/dumpbin-options.md)
