---
title: 命令行错误 D8016
ms.date: 11/04/2016
f1_keywords:
- D8016
helpviewer_keywords:
- D8016
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
ms.openlocfilehash: 1bdef16b14488be86aff880db7c049f4bcddcdb5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196958"
---
# <a name="command-line-error-d8016"></a>命令行错误 D8016

"选项 1" 和 "选项 2" 命令行选项不兼容

不能同时指定命令行选项。

检查环境变量（如 CL）以了解选项规范。

**/clr**暗含 **/eha**，不能通过 **/clr**指定任何其他 **/EH**编译器选项。 有关详细信息，请参阅 [/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。

更新 Visual C++ 6.0 项目后，你可能会收到 D8016：项目更新向导进程可能会为项目中的每个源代码文件启用 **/rtc** ，这会重写项目的 **/rtc**设置。  若要解决此问题，请将项目中每个源代码文件的 **/rtc**设置更改为默认设置，这意味着 **/rtc**的项目设置对每个文件都有效。

有关更改 **/rtc**属性设置的信息，请参阅[/Rtc （运行时错误检查）](../../build/reference/rtc-run-time-error-checks.md) 。
