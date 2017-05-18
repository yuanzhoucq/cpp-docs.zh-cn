---
title: "链接器工具警告 LNK4075 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4075
dev_langs:
- C++
helpviewer_keywords:
- LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9dee257bec0f09bd729bf10c4a1468ecb20dfa61
ms.openlocfilehash: 84dea754a1d2268c92e703dd04b0169ccc258ab3
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="linker-tools-warning-lnk4075"></a>链接器工具警告 LNK4075
忽略由于"option2"规范"选项&1;"  
  
 第二个选项将覆盖第一个。  
  
 指定了互斥链接器选项。  检查链接器选项。  指定链接器选项的位置取决于您构建您的项目的方式。  
  
-   如果您正在构建在开发环境中，您的项目，链接器属性页中查看并了解这两个链接器选项的指定位置。  请参阅[使用项目属性](../../ide/working-with-project-properties.md)有关详细信息。  
  
-   如果您的命令行生成，请查看此处指定的链接器选项。  
  
-   如果生成使用生成脚本时，请查阅您的脚本，请参见这些链接器选项指定的位置。  
  
 当您发现其中指定互斥链接器选项时，删除其中一个链接器选项。  
  
 一些特定的示例如下︰  
  
-   如果链接编译时所用的模块**/ZI**，这表明一个称为 /EDITANDCONTINUE 和一个模块，编译时所用 /opt: ref 和 /opt: icf，/incremental: no，表示没有 /EDITANDCONTINUE 的内部链接器选项，你将收到 LNK4075。  请参阅[/Z7、 /Zi、 /ZI （调试信息格式）](../../build/reference/z7-zi-zi-debug-information-format.md)有关详细信息。
