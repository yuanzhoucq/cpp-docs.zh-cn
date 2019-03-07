---
title: /FD（IDE 最小重新生成）
ms.date: 11/04/2016
f1_keywords:
- /FD
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
ms.openlocfilehash: 0685df0baf14685bd24b8390dd58b382ae5ac506
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422047"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD（IDE 最小重新生成）

**/FD**不向除中的用户公开[命令行](../../ide/command-line-property-pages.md)c + + 项目的属性页**属性页**对话框中，当且仅当[/Gm （启用最小重新生成）](../../build/reference/gm-enable-minimal-rebuild.md)也不会选中。 **/FD**以外的其他开发环境中没有影响。 **/FD**的输出中未公开**cl /？**。

如果不启用 **/Gm**开发环境中 **/FD**将使用。 **/FD**可确保.idb 文件有足够的依赖关系信息。 **/FD**仅由开发环境中，并且不应从命令行或生成脚本。

## <a name="see-also"></a>请参阅

[输出文件 (/F) 选项](../../build/reference/output-file-f-options.md)<br/>
[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)
