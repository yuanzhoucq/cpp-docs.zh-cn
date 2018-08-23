---
title: 命令行错误 D8016 |Microsoft Docs
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
ms.openlocfilehash: 3c6ba57b7036aae652b9eb6d885f9105d8bf0826
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607598"
---
# <a name="command-line-error-d8016"></a>命令行错误 D8016
"选项 1"和"选项 2"的命令行选项不兼容  
  
 不能一起指定的命令行选项。  
  
 检查环境变量，如 CL，选项规范。  
  
 **/clr**意味着 **/EHa**，且不能指定任何其他 **/EH**编译器选项与 **/clr**。 有关详细信息，请参阅 [/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
 更新 Visual c + + 6.0 项目后，可能会得到 D8016： 项目更新向导进程可能会允许 **/RTC**个项目中每个源代码文件，这会重写 **/RTC**项目设置。  若要解决，更改 **/RTC**设置为默认设置在项目中每个源代码文件，这意味着的项目设置 **/RTC**将生效的每个文件。  
  
 请参阅[/RTC （运行时错误检查）](../../build/reference/rtc-run-time-error-checks.md)有关更改信息 **/RTC**属性设置。