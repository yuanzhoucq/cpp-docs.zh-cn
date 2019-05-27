---
title: /CLRHEADER
ms.date: 05/16/2019
f1_keywords:
- /CLRHEADER
helpviewer_keywords:
- -CLRHEADER dumpbin option
- /CLRHEADER dumpbin option
- CLRHEADER dumpbin option
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
ms.openlocfilehash: 5974606448dad103c8f12a126b8d17c688927c88
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837154"
---
# <a name="clrheader"></a>/CLRHEADER

显示特定于 CLR 的信息。

## <a name="syntax"></a>语法

> /CLRHEADER file

### <a name="arguments"></a>自变量

文件<br/>
使用 [/clr](clr-common-language-runtime-compilation.md) 生成的映像文件。

## <a name="remarks"></a>备注

/CLRHEADER 显示关于任何托管程序中使用的 .NET 标头的信息。 输出显示 .NET 标头和标头中各部分的位置和大小（字节）。

只有 [/HEADERS](headers.md) DUMPBIN 选项可用于由 [/GL](gl-whole-program-optimization.md) 编译器选项产生的文件。

如果在由 /clr 编译的文件上使用 /CLRHEADER，则在 DUMPBIN 输出中会有一个“clr Header:”部分。 标志的值指示使用的是哪个 /clr 选项：

- 0  -- /clr（可能包含本机代码的映像）。

还能以编程方式检查映像是否是针对公共语言运行时生成的。  有关详细信息，请参阅[如何：确定是本机映像还是 CLR 映像](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)。

“/clr:pure”和“/clr:safe”编译器选项在 Visual Studio 2015 中已弃用，并且在 Visual Studio 2017 和更高版本中不受支持。 “纯”代码或“安全”代码应移植到 C#。

## <a name="see-also"></a>请参阅

- [DUMPBIN 选项](dumpbin-options.md)
