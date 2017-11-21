---
title: "-errorReport （报告内部编译器错误） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.ErrorReporting
- /errorreport
dev_langs: C++
helpviewer_keywords:
- /errorReport compiler option [C++]
- -errorReport compiler option [C++]
ms.assetid: 819828f8-b0a5-412c-9c57-bf822f17e667
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b4b532003de90fa036ac5d03fb8e3b40b57c0aac
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="errorreport-report-internal-compiler-errors"></a>/errorReport（报告内部编译器错误）
允许你直接向 Microsoft 提供内部编译器错误 (ICE) 信息。  
  
## <a name="syntax"></a>语法  
  
```  
/errorReport:[ none | prompt | queue | send ]  
```  
  
## <a name="arguments"></a>参数  
 **none**  
 不收集有关内部编译器错误的报告，或不向 Microsoft 发送报告。  
  
 **提示**  
 当您收到内部编译器错误时，提示您发送报告。 **提示符**在开发环境中编译应用程序是默认设置。  
  
 **queue**  
 将错误报告排入队列。 当使用管理员特权登录时，将显示一个窗口，以便您可以记录中被记录的上次报告任何失败 （你不会提示发送故障报告一次以上每隔三天）。 **队列**时在命令提示符下编译的应用程序是默认设置。  
  
 **发送**  
 如果启用报告的 Windows 错误报告系统设置自动向 Microsoft 发送报告内部编译器错误。  
  
## <a name="remarks"></a>备注  
 当编译器无法处理源代码文件时，会导致内部编译器错误 (ICE)。 出现 ICE 时，编译器不会生成可用于修复代码的输出文件或任何有用的诊断。  
  
 在早期版本中，当你 ICE，你仅建议致电 Microsoft 产品支持服务要报告问题。 与**/errorReport**，你可以直接向 Microsoft 提供 ICE 信息。 你的错误报告可以帮助改进未来的编译器版本。  
  
 用户能否发送报告取决于计算机和用户策略权限。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  单击**高级**属性页。  
  
4.  修改**错误报告**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ErrorReporting%2A>。  
  
## <a name="see-also"></a>另请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)