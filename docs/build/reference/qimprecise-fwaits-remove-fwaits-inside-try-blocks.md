---
title: "-Qimprecise_fwaits （移除 Try 块中的 fwaits） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /Qimprecise_fwaits
dev_langs: C++
helpviewer_keywords:
- -Qimprecise_fwaits compiler option (C++)
- /Qimprecise_fwaits compiler option (C++)
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 06c93e60530d870b05c601be4980308feb627b46
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="qimprecisefwaits-remove-fwaits-inside-try-blocks"></a>/Qimprecise_fwaits（移除 Try 块中的 fwaits）
删除`fwait`命令的内部`try`阻止使用时[/fp： 除](../../build/reference/fp-specify-floating-point-behavior.md)编译器选项。  
  
## <a name="syntax"></a>语法  
  
```  
/Qimprecise_fwaits  
```  
  
## <a name="remarks"></a>备注  
 此选项不起如果**/fp： 除**也未指定。 如果指定**/fp： 除**选项，编译器将插入`fwait`命令的每一行中的代码周围`try`块。 这种方式，编译器可标识产生异常的代码的特定行。 **/Qimprecise_fwaits**删除内部`fwait`说明，离开仅围绕等待`try`块。 这将改善性能，但编译器将仅能够说这`try`块导致异常，不是哪一行。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  点击“命令行”  属性页。  
  
4.  在 **“附加选项”** 框中键入编译器选项。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>请参阅  
 [/Q 选项 （低级别操作）](../../build/reference/q-options-low-level-operations.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)