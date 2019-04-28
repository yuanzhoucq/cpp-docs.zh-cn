---
title: /FD（IDE 最小重新生成）
ms.date: 04/08/2019
f1_keywords:
- /FD
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
ms.openlocfilehash: ac63b021dc0cb9ee5964af7fa2e168f710653979
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292869"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD（IDE 最小重新生成）

**/FD**仅向用户公开[命令行](command-line-property-pages.md)属性页的C++项目的**属性页**对话框。 提供当且仅当它是不推荐使用和关闭： 默认情况下[/Gm （启用最小重新生成）](gm-enable-minimal-rebuild.md)选项未选中。 **/FD**以外的其他开发环境中没有影响。 **/FD**的输出中不公开`cl /?`。

如果未启用已弃用 **/Gm**在开发环境中，选项 **/FD**使用。 **/FD**可确保.idb 文件有足够的依赖关系信息。 **/FD**仅由开发环境中，从命令行或生成脚本不应使用它。

## <a name="see-also"></a>请参阅

[输出文件 (/F) 选项](output-file-f-options.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
