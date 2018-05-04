---
title: .Res 文件作为链接器输入 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- RES files as linker input
- .res files as linker input
- linking [C++], resource files
- resource files, linking
ms.assetid: 9c37ab00-97df-4d9a-91cd-6bf132970683
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 71344bb752ff7a328ddd5f718a5de1c1f42b65be
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="res-files-as-linker-input"></a>用作链接器输入的 .Res 文件
链接程序时，你可以指定一个.res 文件。 .Res 文件是由资源编译器 (RC) 创建的。 链接将.res 文件自动转换为 COFF。 CVTRES.exe 工具必须 LINK.exe 同一目录中或在指定的目录中的 PATH 环境变量中。  
  
## <a name="see-also"></a>请参阅  
 [LINK 输入的文件](../../build/reference/link-input-files.md)   
 [链接器选项](../../build/reference/linker-options.md)