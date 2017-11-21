---
title: "-GENPROFILE，FASTGENPROFILE （生成经分析检测的生成） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GENPROFILE
- FASTGENPROFILE
- /GENPROFILE
- /FASTGENPROFILE
helpviewer_keywords:
- GENPROFILE
- FASTGENPROFILE
ms.assetid: deff5ce7-46f5-448a-b9cd-a7a83a6864c6
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2e3b0f986d4bc805a3cac1ec49193f3749f31af9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="genprofile-fastgenprofile-generate-profiling-instrumented-build"></a>/GENPROFILE, /FASTGENPROFILE（生成经分析检测的生成）
通过链接器指定 .pgd 文件的生成，以支持按配置优化 (PGO)。  /GENPROFILE 和 /FASTGENPROFILE 使用不同的默认参数。 使用 /GENPROFILE，以在分析期间以精度（而不是速度和内存使用情况）优先。 使用 /FASTGENPROFILE，以更小的内存使用情况和速度（而不是精度）优先。  
  
## <a name="syntax"></a>语法  
  
```  
/{GENPROFILE|FASTGENPROFILE}[:{COUNTER32|COUNTER64|EXACT|MEMMAX=#|MEMMIN=#|NOEXACT|NOPATH|NOTRACKEH|PATH|PGD=filename|TRACKEH}]   
```  
  
## <a name="remarks"></a>备注  
 COUNTER32 &#124;COUNTER64  
 用 COUNTER32 指定使用 32 位探针计数器，用 COUNTER64 指定使用 64 位探针计数器。 指定 /GENPROFILE 时，默认为 COUNTER64。 指定 /FASTGENPROFILE 时，默认为 COUNTER32。  
  
 确切 &#124;NOEXACT  
 使用 EXACT 为探针指定线程安全互锁增量。 NOEXACT 为探针指定未受保护的增量操作。 默认为 NOEXACT。  
  
 MEMMAX=value, MEMMIN=value  
 使用 MEMMAX 和 MEMMIN 指定内存中训练数据的最大和最小预留大小。 该值为要保留的内存量（以字节为单位）。  默认情况下，这些值由内部启发式确定。  
  
 路径 &#124;NOPATH  
 使用 PATH 为函数的每个唯一路径指定一组单独的 PGO 计数器。 使用 NOPATH 为每个函数指定仅一组计数器。   指定 /GENPROFILE 时，默认为 PATH。 指定 /FASTGENPROFILE 时，默认为 NOPATH。  
  
 TRACKEH &#124;NOTRACKEH  
 指定是否使用额外计数器以便在训练期间引发异常时保持准确计数。 使用 TRACKEH 指定额外计数器，以进行确切计数。 使用 NOTRACKEH 为不使用异常处理或在训练方案中不会遇到异常的代码指定单个计数器。  指定 /GENPROFILE 时，默认为 TRACKEH。 指定 /FASTGENPROFILE 时，默认为 NOTRACKEH。  
  
 PGD = 文件名  
 指定 .pgd 文件的基文件名。 默认情况下，链接器使用带 .pgd 扩展名的基本可执行映像文件名。  
  
 /GENPROFILE 和 /FASTGENPROFILE 选项告知链接器生成支持按配置优化 (PGO) 的应用程序训练所需的分析检测文件。 将应用程序训练生成的分析信息用作输入，以在生成期间执行目标全程序优化。   你可以设置其他选项来控制各种性能分析功能，以调整应用训练和生成期间的性能。 /GENPROFILE 指定的默认选项提供最准确的结果，尤其是对于大型的复杂多线程应用。 /FASTGENPROFILE 选项使用不同的默认值，以在训练期间实现更低的内存占用量和更快的性能，代价是牺牲准确性。  
  
 使用 /FASTGENPROFILE 的 /GENPROFILE 进行生成后，将在你运行已检测应用时捕获分析信息。 当你指定 /USEPROFILE 选项时，链接器将使用此信息。 有关训练应用的方法和所收集数据的详细信息，请参阅“按配置优化”。  
  
 指定 /GENPROFILE 或 /FASTGENPROFILE 时，还必须指定 /LTCG。  
  
## <a name="see-also"></a>另请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)   
 [/LTCG （链接时间代码生成）](../../build/reference/ltcg-link-time-code-generation.md)