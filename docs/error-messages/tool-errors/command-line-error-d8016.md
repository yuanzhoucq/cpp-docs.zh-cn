---
title: 命令行错误 D8016
ms.date: 11/04/2016
f1_keywords:
- D8016
helpviewer_keywords:
- D8016
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
ms.openlocfilehash: c1e2e3e28f8556416f58d68f8ef1df4b220bc54c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399962"
---
# <a name="command-line-error-d8016"></a>命令行错误 D8016

"选项 1"和"选项 2"的命令行选项不兼容

不能一起指定的命令行选项。

检查环境变量，如 CL，选项规范。

**/clr**意味着 **/EHa**，且不能指定任何其他 **/EH**编译器选项与 **/clr**。 有关详细信息，请参阅 [/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。

更新视觉对象后，可能会得到 D8016 C++ 6.0 项目： 项目更新向导进程可能会允许 **/RTC**个项目中每个源代码文件，这会重写 **/RTC**设置为项目。  若要解决，更改 **/RTC**设置为默认设置在项目中每个源代码文件，这意味着的项目设置 **/RTC**将生效的每个文件。

请参阅[/RTC （运行时错误检查）](../../build/reference/rtc-run-time-error-checks.md)有关更改信息 **/RTC**属性设置。