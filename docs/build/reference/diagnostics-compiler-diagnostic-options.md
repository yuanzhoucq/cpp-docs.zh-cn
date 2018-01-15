---
title: "-诊断 （编译器诊断选项） |Microsoft 文档"
ms.custom: 
ms.date: 11/11/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /diagnostics
- VC.Project.VCCLCompilerTool.DiagnosticsFormat
dev_langs: C++
helpviewer_keywords:
- /diagnostics compiler diagnostic options [C++]
- -diagnostics compiler diagnostic options [C++]
- diagnostics compiler diagnostic options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1a1c893b530bfa895e5ec127bd0aea2fb0df4ff3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="diagnostics-compiler-diagnostic-options"></a>/diagnostics （编译器诊断选项）  
  
使用**/diagnostics**编译器选项来指定所显示的错误和警告的位置信息。  
  
## <a name="syntax"></a>语法  
  
```  
/diagnostics:{caret|classic|column}
```  

## <a name="remarks"></a>备注  
**/Diagnostics**编译器选项控制显示的错误和警告信息。  
  
**/Diagnostics:classic**选项是默认情况下，报告仅发现此问题的行数。  
  
**/Diagnostics:column**选项还包括在其中找到问题的列。 这可以帮助你标识特定的语言构造或导致问题的字符。  
  
**/Diagnostics:caret**选项包括其中问题找并将插入符号 (^) 放在其中检测到问题中的代码行的位置下的列。  
  
请注意，在某些情况下，编译器不会检测它发生的问题。 例如，缺少分号可能不会检测到之前遇到了其他、 意外的符号。 报告列和脱字号位于其中编译器检测到出现了问题，它并不总是需要进行你更正。  
  
**/Diagnostics**选项是在 Visual Studio 2017 中开始提供。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1. 打开你的项目的**属性页**对话框。   
  
2. 下**配置属性**，展开**C/c + +**文件夹，然后选择**常规**属性页。  
  
3. 使用中的下拉列表控件**诊断格式**字段来选择诊断显示选项。 选择**确定**或**应用**以保存所做的更改。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)