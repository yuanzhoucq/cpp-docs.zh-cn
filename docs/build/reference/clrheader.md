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
ms.openlocfilehash: 5896e12d5e3b3b3984884388d11c6380e900d73d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="clrheader"></a>/CLRHEADER
```  
/CLRHEADER file  
```  
  
## <a name="remarks"></a>备注  
 其中：  
  
 `file`  
 使用生成的图像文件[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
## <a name="remarks"></a>备注  
 CLRHEADER 显示有关在任何托管程序中使用的.NET 标头信息。 该输出显示的位置和大小，以字节为单位，.NET 标头和标头中的部分。  
  
 仅[/HEADERS](../../build/reference/headers.md) DUMPBIN 选项是可供产生的文件的使用[/GL](../../build/reference/gl-whole-program-optimization.md)编译器选项。  
  
 当对使用 /clr 编译的文件使用 /CLRHEADER 时，将有**clr 标头：** dumpbin 输出中的部分。  值**标志**指示使用哪个 /clr 选项：  
  
-   0-/clr （映像可能包含本机代码）。  
  
 以编程方式还可以检查是否为公共语言运行时生成映像。  有关详细信息，请参阅[如何： 确定映像是否本机或 CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)。  
  
 **/Clr: pure**和 **/clr: safe**编译器选项在 Visual Studio 2015 中弃用，并将编译器的未来版本中删除。 必须为"纯"或"安全"的代码应移植到 C#。 
  
## <a name="see-also"></a>请参阅  
 [DUMPBIN 选项](../../build/reference/dumpbin-options.md)