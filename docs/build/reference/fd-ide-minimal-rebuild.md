---
title: -FD （IDE 最小重新生成） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /FD
dev_langs:
- C++
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 474602ce51ff9eb84f54d7580104f641d9b5b2a7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396189"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD（IDE 最小重新生成）

**/FD**不向除中的用户公开[命令行](../../ide/command-line-property-pages.md)c + + 项目的属性页**属性页**对话框中，当且仅当[/Gm （启用最小重新生成）](../../build/reference/gm-enable-minimal-rebuild.md)也不会选中。 **/FD**以外的其他开发环境中没有影响。 **/FD**的输出中未公开**cl /？**。

如果不启用 **/Gm**开发环境中 **/FD**将使用。 **/FD**可确保.idb 文件有足够的依赖关系信息。 **/FD**仅由开发环境中，并且不应从命令行或生成脚本。

## <a name="see-also"></a>请参阅

[输出文件 (/F) 选项](../../build/reference/output-file-f-options.md)<br/>
[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)