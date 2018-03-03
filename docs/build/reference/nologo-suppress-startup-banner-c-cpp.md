---
title: "-nologo （取消显示启动版权标志） （C/c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.SuppressStartupBanner
- VC.Project.VCCLCompilerTool.SuppressStartupBanner
dev_langs:
- C++
helpviewer_keywords:
- -nologo compiler option [C++]
- /nologo compiler option [C++]
- nologo compiler option [C++]
- banners, suppressing startup
ms.assetid: 75930d8b-b11c-4db8-99e5-b52f97da0693
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a36ba1cc206e23d51ecc6d790b2b32dca22c5963
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="nologo-suppress-startup-banner-cc"></a>/nologo（取消显示启动版权标志）(C/C++)
取消显示版权标志编译器启动时和在编译期间显示信息性消息。  
  
## <a name="syntax"></a>语法  
  
```  
/nologo  
```  
  
## <a name="remarks"></a>备注  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  单击**常规**属性页。  
  
4.  修改**取消显示启动版权标志**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SuppressStartupBanner%2A>。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)