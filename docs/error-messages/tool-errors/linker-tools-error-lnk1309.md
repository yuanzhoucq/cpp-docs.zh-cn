---
title: 链接器工具错误 LNK1309 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1309
dev_langs:
- C++
helpviewer_keywords:
- LNK1309
ms.assetid: 10146071-883f-4849-97d1-c7468f90efbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f179a74823be1293bc927afe122c4bf14c0030b9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1309"></a>链接器工具错误 LNK1309
检测到; type1 模块与交换机 /CLRIMAGETYPE:type2 无效  
  
 CLR 映像类型通过请求 **/CLRIMAGETYPE**但链接器无法生成该类型的映像，因为一个或多个模块已与该类型不兼容。  
  
 例如，你将看到 LNK1309，如果你指定 **/CLRIMAGETYPE:safe**并传递与生成的模块 **/clr: pure**。  
  
 如果你尝试生成部分受信任的 CLR 纯使用的应用程序 [d] ptrustu.lib，也会看到 LNK1309。 有关如何创建部分受信任的应用程序的信息，请参阅[如何： 创建部分受信任应用程序删除依赖项由 CRT 库 DLL 上](../../dotnet/create-a-partially-trusted-application.md)。  
  
 有关详细信息，请参阅[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)和[/CLRIMAGETYPE （指定类型的 CLR 映像）](../../build/reference/clrimagetype-specify-type-of-clr-image.md)。