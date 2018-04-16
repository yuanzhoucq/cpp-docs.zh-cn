---
title: "MIDL 属性页： 高级 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCMidlTool.ErrorCheckBounds
- VC.Project.VCMidlTool.ErrorCheckStubData
- VC.Project.VCMidlTool.ErrorCheckAllocations
- VC.Project.VCMidlTool.CPreprocessOptions
- VC.Project.VCMidlTool.UndefinePreprocessorDefinitions
- VC.Project.VCMidlTool.EnableErrorChecks
- VC.Project.VCMidlTool.RedirectOutputAndErrors
- VC.Project.VCMidlTool.ErrorCheckEnumRange
- VC.Project.VCMidlTool.StructMemberAlignment
- VC.Project.VCMidlTool.ErrorCheckRefPointers
- VC.Project.VCMidlTool.ValidateParameters
dev_langs:
- C++
helpviewer_keywords:
- MIDL, property pages
ms.assetid: d1c92e01-f403-4ed6-ab45-4043a3c9c6bb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d6e7dde047c3311c6fd694a91c7a63fcfbcc95d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="midl-property-pages-advanced"></a>MIDL 属性页：高级
**高级**中的属性页**MIDL**文件夹指定以下 MIDL 编译器选项：  
  
-   启用错误检查 ([/error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   检查分配 ([/error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   检查界限 ([/error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   检查枚举范围 ([/error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   检查引用指针 ([/error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   检查存根 （stub） 数据 ([/error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   验证参数 ([/ 可靠](http://msdn.microsoft.com/library/windows/desktop/aa367363)) *  
  
-   结构成员对齐 ([/Zp](http://msdn.microsoft.com/library/windows/desktop/aa367388))  
  
-   将输出重定向 ([/o](http://msdn.microsoft.com/library/windows/desktop/aa367351))  
  
-   C 预处理选项 ([/cpp_opt](http://msdn.microsoft.com/library/windows/desktop/aa367318))  
  
-   取消定义预处理器定义 ([/U](http://msdn.microsoft.com/library/windows/desktop/aa367373))  
  
 \*/ 可靠只能用于为 Windows 2000 或更高版本的计算机进行生成时。 如果你生成 ATL 项目，并想要使用 / 可靠，将此行 dlldatax.c 文件中的更改：  
  
```  
#define _WIN32_WINNT 0x0400   //for Windows NT 4.0 or Windows 95 with DCOM  
to   
#define _WIN32_WINNT 0x0500   //for Windows NT 4.0 or Windows 95 with DCOM  
```  
  
 有关如何访问信息**高级**中的属性页**MIDL**文件夹，请参阅[使用项目属性](../ide/working-with-project-properties.md)。  
  
 有关如何以编程方式访问 c + + 项目的 MIDL 选项的信息，请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool>。  
  
## <a name="see-also"></a>请参阅  
 [“MIDL”属性页](../ide/midl-property-pages.md)