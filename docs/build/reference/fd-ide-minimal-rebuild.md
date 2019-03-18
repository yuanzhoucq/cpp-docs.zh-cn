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
ms.openlocfilehash: 323a0045ab11f23ab996d5179a135d0eb4184f20
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817434"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD（IDE 最小重新生成）

**/FD**不向除中的用户公开[命令行](command-line-property-pages.md)c + + 项目的属性页**属性页**对话框中，当且仅当[/Gm （启用最小重新生成）](gm-enable-minimal-rebuild.md)也不会选中。 **/FD**以外的其他开发环境中没有影响。 **/FD**的输出中未公开**cl /？**。

如果不启用 **/Gm**开发环境中 **/FD**将使用。 **/FD**可确保.idb 文件有足够的依赖关系信息。 **/FD**仅由开发环境中，并且不应从命令行或生成脚本。

## <a name="see-also"></a>请参阅

[输出文件 (/F) 选项](output-file-f-options.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
