---
title: /CLRHEADER
ms.date: 11/04/2016
f1_keywords:
- /CLRHEADER
helpviewer_keywords:
- -CLRHEADER dumpbin option
- /CLRHEADER dumpbin option
- CLRHEADER dumpbin option
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
ms.openlocfilehash: 864ecc0063716ce712e28b063714ce7c17fc294a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50627365"
---
# <a name="clrheader"></a>/CLRHEADER

显示特定于 CLR 的信息。

## <a name="syntax"></a>语法

> /CLRHEADER*文件*

### <a name="arguments"></a>自变量

|||
|-|-|
文件| 使用生成的图像文件[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="remarks"></a>备注

**/CLRHEADER**显示在任何托管程序中使用的.NET 标头有关的信息。 该输出显示的位置和大小，以字节为单位，.NET 标头和标头中的部分。

仅[/HEADERS](../../build/reference/headers.md) DUMPBIN 选项仅适用于使用产生的文件[/GL](../../build/reference/gl-whole-program-optimization.md)编译器选项。

当 **/CLRHEADER**使用在使用 /clr 编译的文件上, 将存在**clr 标头：** dumpbin 输出中的部分。 值**标志**指示使用了哪个 /clr 选项：

- 0-/clr （映像可能包含本机代码）。

以编程方式还可以检查是否为公共语言运行时生成映像。  有关详细信息，请参阅[如何： 确定映像是本机模式或 CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)。

**/Clr: pure**并 **/clr: safe**编译器选项在 Visual Studio 2015 中弃用，在 Visual Studio 2017 中不受支持。 必须为"纯"或"安全"的代码应移植到C#。

## <a name="see-also"></a>请参阅

- [DUMPBIN 选项](../../build/reference/dumpbin-options.md)
