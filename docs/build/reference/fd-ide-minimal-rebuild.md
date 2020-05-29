---
title: /FD（IDE 最小重新生成）
ms.date: 04/08/2019
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
ms.openlocfilehash: 896adcb97a259e6714cf23241424841456371491
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439815"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD（IDE 最小重新生成）

在C++项目的 "**属性页**" 对话框的 "[命令行](command-line-property-pages.md)" 属性页中， **/fd**仅向用户公开。 当且仅当未选择不推荐使用和非默认的[/gm （启用最小重新生成）](gm-enable-minimal-rebuild.md)选项时，它才可用。 **/Fd**除了从开发环境中没有任何影响。 **/Fd** `cl /?`的输出中未公开。

如果未在开发环境中启用弃用的 **/gm**选项，则使用 **/fd** 。 **/Fd**确保 .idb 文件具有足够的依赖项信息。 **/Fd**仅供开发环境使用，不应从命令行或生成脚本中使用。

## <a name="see-also"></a>另请参阅

[输出文件 (/F) 选项](output-file-f-options.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
