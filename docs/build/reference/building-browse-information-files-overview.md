---
title: "生成浏览信息文件： 概述 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 51a922e75d0cc7232a7e45472e505440b7b1631c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="building-browse-information-files-overview"></a>生成浏览信息文件：概述
若要创建浏览信息符号浏览的编译器在项目中，然后 BSCMAKE 创建每个源文件的.sbr 文件。EXE 将.sbr 文件串联成一个.bsc 文件。  
  
 生成.sbr 和.bsc 文件需要时间，，因此 Visual c + + 将关闭默认情况下的这些函数。 如果你想要浏览当前信息，必须启用浏览选项，并再次生成你的项目。  
  
 使用[/FR](../../build/reference/fr-fr-create-dot-sbr-file.md)或[/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md)以告知编译器创建.sbr 文件。 若要创建.bsc 文件，你可以调用[BSCMAKE](../../build/reference/bscmake-command-line.md)从命令行。 从命令行使用 BSCMAKE 可更精确地控制浏览信息文件的操作。 请参阅[BSCMAKE 参考](../../build/reference/bscmake-reference.md)有关详细信息。  
  
> [!TIP]
>  你可以打开.sbr 文件生成，但不要关闭.bsc 文件生成。 这提供了快速生成，而且还使您能够快速创建新的.bsc 文件，通过打开.bsc 文件生成和生成项目。  
  
 你可以减少时间、 内存和减少.bsc 文件的大小，从而生成.bsc 文件所需的磁盘空间。  
  
 请参阅[常规属性页 （项目）](../../ide/general-property-page-project.md)有关如何生成在开发环境中的浏览器文件的信息。  
  
### <a name="to-create-a-smaller-bsc-file"></a>若要创建较小的.bsc 文件  
  
1.  使用[BSCMAKE 命令行选项](../../build/reference/bscmake-options.md)禁止浏览信息文件的信息。  
  
2.  省略中一个或多个.sbr 文件编译或汇编时的本地符号。  
  
3.  如果的对象文件不包含所需的调试你当前阶段的信息，请重新生成浏览信息文件时省略 BSCMAKE 命令从其.sbr 文件。  
  
### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>若要将多个项目中为一个浏览器文件 (.bsc) 的浏览信息合并  
  
1.  不生成.bsc 文件，在项目级别，或者使用 /n 开关防止.sbr 文件被截断。  
  
2.  生成所有项目后，作为输入使用所有的.sbr 文件运行 BSCMAKE。 接受通配符。 例如，如果你有项目目录 C:\X、 C:\Y 和 C:\Z 具有中以及你想要将它们组合成一个.bsc 文件所有的.sbr 文件，然后使用 BSCMAKE C:\X\\*.sbr C:\Y\\\*.sbr C:\Z\\\*。sbr /o c:\whatever_directory\combined.bsc 生成组合的.bsc 文件。  
  
## <a name="see-also"></a>另请参阅  
 [C/c + + 生成工具](../../build/reference/c-cpp-build-tools.md)   
 [BSCMAKE 参考](../../build/reference/bscmake-reference.md)