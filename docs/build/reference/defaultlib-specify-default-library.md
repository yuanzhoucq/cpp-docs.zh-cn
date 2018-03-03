---
title: "-DEFAULTLIB （指定默认库） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.DefaultLibraries
- /defaultlib
dev_langs:
- C++
helpviewer_keywords:
- -DEFAULTLIB linker option
- DEFAULTLIB linker option
- /DEFAULTLIB linker option
- libraries, adding to list of
ms.assetid: 6af7ff49-c170-4a13-97e2-2b9ae2de20c9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 40fe07543dd9dc65d93cc9f79504f5fd324204dd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="defaultlib-specify-default-library"></a>/DEFAULTLIB（指定默认库）
```  
/DEFAULTLIB:library  
```  
  
## <a name="remarks"></a>备注  
 其中：  
  
 *库*  
 在解析外部引用时搜索的库的名称。  
  
## <a name="remarks"></a>备注  
 /DEFAULTLIB 选项添加一个*库*到的链接将在解析引用时搜索的库的列表。 /DEFAULTLIB 使用指定的库搜索后指定命令行上和之前在.obj 文件中命名的默认库的库中。  
  
 [忽略所有默认库](../../build/reference/nodefaultlib-ignore-libraries.md)(/ NODEFAULTLIB) 选项将重写 /DEFAULTLIB:*库*。 [忽略库](../../build/reference/nodefaultlib-ignore-libraries.md)(/ NODEFAULTLIB:*库*) 选项将重写 /DEFAULTLIB:*库*时相同*库*名称中同时指定。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
-   此链接器选项不可用从 Visual Studio 开发环境。 若要将库添加到在链接阶段，使用**附加依赖项**属性从**输入**属性页。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)