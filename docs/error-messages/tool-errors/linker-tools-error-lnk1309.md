---
title: "链接器工具错误 LNK1309 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1309"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1309"
ms.assetid: 10146071-883f-4849-97d1-c7468f90efbb
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具错误 LNK1309
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检测到 type1 模块；对 \/CLRIMAGETYPE:type2 开关无效  
  
 使用 **\/CLRIMAGETYPE** 请求了 CLR 映像类型，但是链接器未能生成该类型的映像，因为一个或多个模块与该类型不兼容。  
  
 例如，如果指定 **\/CLRIMAGETYPE:safe** 并传递使用 **\/clr:pure** 生成的模块，将导致 LNK1309。  
  
 如果您尝试使用 ptrustu\[d\].lib 生成部分受信任的 CLR 纯应用程序，也会看到 LNK1309。  有关如何创建部分受信任的应用程序的信息，请参见 [如何：通过移除 CRT 库 DLL 上的依赖项来创建部分受信任的应用程序](../../dotnet/create-a-partially-trusted-application.md)。  
  
 有关更多信息，请参见[\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)和[\/CLRIMAGETYPE（指定 CLR 映像的类型）](../../build/reference/clrimagetype-specify-type-of-clr-image.md)。