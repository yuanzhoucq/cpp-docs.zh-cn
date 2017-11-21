---
title: "-CLRHEADER |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /CLRHEADER
dev_langs: C++
helpviewer_keywords:
- -CLRHEADER dumpbin option
- /CLRHEADER dumpbin option
- CLRHEADER dumpbin option
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 699fa0e97236b1c5cf207e73dcbb39156bfbb130
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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
  
-   1-/clr: safe （图为唯一，能够在 CLR 任何平台上，运行和可能是可验证的 MSIL）。  
  
-   3-/clr: pure (图像 MSIL 仅是，但仅能够在 x86 上运行的平台)。  
  
 以编程方式还可以检查是否为公共语言运行时生成映像。  有关详细信息，请参阅[如何： 确定映像是否本机或 CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)。  
  
 **/clr:pure** 和 **/clr:safe** 编译器选项在 Visual Studio 2015 中已弃用。  
  
## <a name="see-also"></a>另请参阅  
 [DUMPBIN 选项](../../build/reference/dumpbin-options.md)