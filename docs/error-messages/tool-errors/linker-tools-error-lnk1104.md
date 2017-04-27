---
title: "链接器工具错误 LNK1104 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1104
dev_langs:
- C++
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 4bac7b2942f9d72674b8092dc7bf64174dd3c349
ms.openlocfilehash: 7fce9c60da4bceafb9ee81231a8630acb4397d83
ms.lasthandoff: 04/24/2017

---
# <a name="linker-tools-error-lnk1104"></a>链接器工具错误 LNK1104
无法打开文件*filename*  
  
链接器无法打开指定的文件。  
  
若要解决此错误，请检查以下可能的原因︰  
  
-   文件*filename*不存在。 如果你的项目依赖于另一个项目以生成此文件，请确保你的项目依赖项都正确设置。  
  
-   在指定库项目的属性页对话框中时，必须用空格，而不是逗号分隔库名称。  
  
-   文件名或命令行上指定的路径不正确，或者路径具有无效的驱动器规范。 请检查拼写，并验证文件名和位置。 如果要生成从另一台计算机复制的项目，则检查路径上[VC + + 目录属性页](../../ide/vcpp-directories-property-page.md)并根据需要对其进行更新。  
  
-   未安装的项目配置或平台工具集的库。 验证平台工具集和你的项目的属性页中指定的 Windows SDK 安装，并包括工具集和库所需的配置设置。 单独设置调试和发布配置，因此如果一个 build 的工作原理，但其他会导致错误，请确保设置正确，并为两个配置安装所需的工具。  
  
-   你没有足够的磁盘空间。 不是很少会链接器在链接期间消耗大量的临时磁盘空间。  
  
-   具有访问没有足够的文件权限*filename*。  
  
-   路径*filename*超过 260 个字符。 更改名称或重新排列你的目录结构，如果需要缩短对所需文件的路径。  
  
-   如果*filename*名为 LNK*n*、 即生成链接器为临时文件的文件名、 TMP 环境变量中指定的目录可能不存在，或为 TMP 环境变量可指定多个目录。 只能将一个目录路径应为 TMP 环境变量指定。  
  
-   如果库名称出现错误消息，并且你最近刚从之前的 Microsoft Visual C++ 开发系统中移植了 .mak 文件，库名称可能不再有效。 确保库名称正确无误，且仍存在于指定的位置，或更新为指向新位置的 LIB 路径。  
  
-   另一个程序可能已打开该文件，链接器无法向其写入。 防病毒程序通常暂时阻止对新创建的文件的访问。 请尝试从防病毒扫描程序中排除项目生成目录。  
  
-   具有不正确的 LIB 环境变量。 有关如何更新 LIB 环境变量的信息，请参阅[VC + + 目录属性页](../../ide/vcpp-directories-property-page.md)。 请确保此处列出了所需的所有包含库的目录。  
  
-   链接器在多个用例中使用临时文件。 即使有足够的磁盘空间，一个非常大的链接可以消耗或片段的可用磁盘空间。 请考虑使用[/OPT （优化）](../../build/reference/opt-optimizations.md)选项; 不采取可传递的 comdat 消除读取所有对象文件多次。
