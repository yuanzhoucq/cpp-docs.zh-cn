---
title: "-NXCOMPAT （与数据执行保护兼容） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /NXCOMPAT
dev_langs: C++
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
ms.assetid: 5858e7ff-24d3-4ac3-9046-af2c9e220d9b
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d97b1b84ef6894e4ec161dbcecef47f6b676af23
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT（与数据执行保护兼容）
指示可执行文件已测试可与 Windows 数据执行保护功能兼容。  
  
## <a name="syntax"></a>语法  
  
```  
/NXCOMPAT[:NO]  
```  
  
## <a name="remarks"></a>备注  
 默认情况下， **/NXCOMPAT**上。  
  
 **/NXCOMPAT:NO**可用来显式指定为不与数据执行保护兼容的可执行文件。  
  
 有关数据执行保护的详细信息，请参阅这些文章：  
  
-   [数据执行保护 (DEP) 功能的详细的说明](http://go.microsoft.com/fwlink/?LinkID=157771)Microsoft 帮助和支持网站上  
  
-   [数据执行保护](http://go.microsoft.com/fwlink/?LinkID=157770)MSDN 网站上  
  
-   [数据执行保护 (Windows Embedded)](http://go.microsoft.com/fwlink/?LinkID=157768) MSDN 网站上  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中设置此链接器选项  
  
1.  打开项目“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  点击“命令行”  属性页。  
  
4.  键入中的选项**其他选项**框。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
1.  请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>另请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)