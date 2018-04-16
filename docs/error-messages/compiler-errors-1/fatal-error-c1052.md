---
title: "错误 C1052 |Microsoft 文档"
ms.custom: 
ms.date: 05/08/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1052
dev_langs:
- C++
helpviewer_keywords:
- C1052
ms.assetid: f2c09a2f-d3c1-4420-9501-ffcb65caf87b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6b9d7cc04fa863d30829c5484b328effc55125e6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1052"></a>错误 C1052  
  
> 程序数据库文件*filename*，通过使用 /debug: fastlink; 链接器生成的编译器无法更新此类 PDB 文件; 请删除它或使用 /Fd 来指定不同的 PDB 文件名  
  
编译器不能更新相同的程序数据库 (PDB) 文件链接器生成时[/debug: fastlink](../../build/reference/debug-generate-debug-info.md)指定选项。 通常，编译器生成的 PDB 文件和链接器生成的 PDB 文件具有不同的名称。 但是，如果它们都设置为使用相同的名称，可以导致此错误。  
  
若要解决此问题，可以显式删除 PDB 文件然后重新编译或可以创建不同的编译器生成和链接器生成 PDB 文件的名称。  
  
若要在命令行上指定的编译器生成 PDB 文件名称，使用[/Fd](../../build/reference/fd-program-database-file-name.md)编译器选项。 若要在 IDE 中指定的编译器生成 PDB 文件名称，打开**属性页**对话框为你的项目，并在**配置属性**， **C/c + +**， **输出文件**页上，设置**程序数据库文件名**属性。 默认情况下，此属性是`$(IntDir)vc$(PlatformToolsetVersion).pdb`。  
  
或者，你可以设置的链接器生成 PDB 文件名称。 若要在命令行上指定链接器生成 PDB 文件的名称，使用[/PDB](../../build/reference/pdb-use-program-database.md)链接器选项。 若要在 IDE 中指定链接器生成 PDB 文件的名称，打开**属性页**对话框为你的项目，并在**配置属性**，**链接器**， **调试**页上，设置**生成程序数据库文件**属性。 默认情况下，此属性设置为`$(OutDir)$(TargetName).pdb`。  
