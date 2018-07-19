---
title: 命令行错误 D8016 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8016
dev_langs:
- C++
helpviewer_keywords:
- D8016
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6f9709da189403f2594d76751430d30554bffe5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300613"
---
# <a name="command-line-error-d8016"></a>命令行错误 D8016
"选项 1"和"选项 2"的命令行选项不兼容  
  
 命令行选项不能一起指定。  
  
 检查环境变量，例如 CL，针对选项规范。  
  
 **/clr**意味着 **/EHa**，并且不能指定任何其他 **/EH**编译器选项与 **/clr**。 有关详细信息，请参阅 [/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
 更新后，可能会得到 D8016 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 6.0 项目： 项目更新向导过程可实现 **/RTC**个项目中每个源代码文件，这会重写 **/RTC**设置项目。  若要解决，更改 **/RTC**为项目中每个源代码文件设置为默认设置，这意味着的项目设置 **/RTC**将生效的每个文件。  
  
 请参阅[/RTC （运行时错误检查）](../../build/reference/rtc-run-time-error-checks.md)有关更改信息 **/RTC**属性设置。