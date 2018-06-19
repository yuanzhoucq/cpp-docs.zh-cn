---
title: -FD （IDE 最小重新生成） |Microsoft 文档
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
ms.openlocfilehash: 18e31955b131e4ca22d23013565e53f83493275d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373395"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD（IDE 最小重新生成）
**/FD**不向除中的用户公开[命令行](../../ide/command-line-property-pages.md)c + + 项目的属性页**属性页**对话框中，当且仅当[/Gm （启用最小重新生成）](../../build/reference/gm-enable-minimal-rebuild.md)没有同时选择。 **/FD**不起作用以外的其他开发环境中。 **/FD**不公开的输出中**cl /？**。  
  
 如果你没有启用 **/Gm**在开发环境中， **/FD**将使用。 **/FD**可确保.idb 文件有足够的依赖项信息。 **/FD**仅由开发环境中，使用和不应从命令行或生成脚本。  
  
## <a name="see-also"></a>请参阅  
 [输出文件 (/ F) 选项](../../build/reference/output-file-f-options.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)