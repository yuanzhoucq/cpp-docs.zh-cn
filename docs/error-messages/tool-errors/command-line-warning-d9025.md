---
title: "命令行警告 D9025 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: D9025
dev_langs: C++
helpviewer_keywords: D9025
ms.assetid: 6edff72c-1508-46c2-99f4-0e4b3c5e60c9
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d95c4c16b472f0e1b37a981df7f73ff573d06447
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="command-line-warning-d9025"></a>命令行警告 D9025
重写"选项 1"与"选项 2"  
  
 *选项 1*选项已指定，但然后由重写*选项 2*。 *选项 2*以前用选项。  
  
 如果两个选项指定矛盾或不兼容的指令，则使用命令行上最右侧选项中指定或隐含的指令。  
  
 如果在从开发环境中，编译时收到此警告，并且不确定的冲突的选项来自何处，考虑以下方面：  
  
-   在代码中或在项目的项目设置，可以指定一个选项。 如果你看一下编译器的[命令行属性页](../../ide/command-line-property-pages.md)并且时看到中的冲突选项**所有选项**字段然后设置了选项在项目的属性页中，否则为选项在源代码中设置。  
  
     如果在项目的属性页中设置的选项，查找在编译器的预处理器属性页上 （包含在解决方案资源管理器中选择的项目节点）。  如果你看不到选项设置存在，检查每个源代码文件 （在解决方案资源管理器） 的预处理器属性页设置以确保它未添加到此处。  
  
     如果在代码中设置的选项可将其设置在代码中，也可在 windows 头文件。  你可以尝试创建一个预处理的文件 ([/P](../../build/reference/p-preprocess-to-a-file.md)) 并在其中搜索符号。