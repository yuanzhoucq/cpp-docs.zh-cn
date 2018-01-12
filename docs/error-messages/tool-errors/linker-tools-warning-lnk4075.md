---
title: "链接器工具警告 LNK4075 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4075
dev_langs: C++
helpviewer_keywords: LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e8c3330e637ae0e0dce5e875fcc349c6deefcf27
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4075"></a>链接器工具警告 LNK4075
忽略由于"选项 2"规范的"选项 1"  
  
 第二个选项优先于第一个。  
  
 指定了互斥链接器选项。  检查链接器选项。  链接器选项指定的位置取决于你如何生成项目。  
  
-   如果你要在开发环境中生成的在你的项目，链接器属性页中查看并了解这两个链接器选项的指定位置。  请参阅[使用项目属性](../../ide/working-with-project-properties.md)有关详细信息。  
  
-   如果你的命令行生成，请查看此处指定的链接器选项。  
  
-   如果生成使用生成脚本时，请查阅你的脚本，了解这些链接器选项的指定位置。  
  
 当你发现的互相排斥的链接器选项指定的位置时，请删除其中一个链接器选项。  
  
 一些特定的示例：  
  
-   如果链接用编译的模块**/ZI**，这意味着一个内部链接器选项调用意味着没有 /EDITANDCONTINUE /EDITANDCONTINUE 和用 /opt: ref、 /opt: icf 或 /incremental: no，编译的模块，你将获取 LNK4075。  请参阅[/Z7、 /Zi、 /ZI （调试信息格式）](../../build/reference/z7-zi-zi-debug-information-format.md)有关详细信息。