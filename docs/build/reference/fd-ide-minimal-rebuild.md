---
title: "-FD （IDE 最小重新生成） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /FD
dev_langs:
- C++
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c0dfcf34be03204b920e5a4459c6a2d7ea6c506d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fd-ide-minimal-rebuild"></a>/FD（IDE 最小重新生成）
**/FD**不向除中的用户公开[命令行](../../ide/command-line-property-pages.md)c + + 项目的属性页**属性页**对话框中，当且仅当[/Gm （启用最小重新生成）](../../build/reference/gm-enable-minimal-rebuild.md)没有同时选择。 **/FD**不起作用以外的其他开发环境中。 **/FD**不公开的输出中**cl /？**。  
  
 如果你没有启用**/Gm**在开发环境中， **/FD**将使用。 **/FD**可确保.idb 文件有足够的依赖项信息。 **/FD**仅由开发环境中，使用和不应从命令行或生成脚本。  
  
## <a name="see-also"></a>请参阅  
 [输出文件 (/ F) 选项](../../build/reference/output-file-f-options.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)