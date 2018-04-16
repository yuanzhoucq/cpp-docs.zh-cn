---
title: -Fm （命名映射文件） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- /fm
dev_langs:
- C++
helpviewer_keywords:
- -Fm compiler option [C++]
- mapfiles [C++], creating linker
- files [C++], creating map
- Fm compiler option [C++]
- /Fm compiler option [C++]
ms.assetid: 8154448a-93a7-4546-8e4c-5c44d0aff45d
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0a5111291ea92b8650896faf3117f0056510e5ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fm-name-mapfile"></a>/Fm（命名映射文件）
通知链接器生成映射文件包含在相应的.exe 文件或 DLL 的显示的顺序中的段的列表。  
  
## <a name="syntax"></a>语法  
  
```  
/Fmpathname  
```  
  
## <a name="remarks"></a>备注  
 默认情况下，映射文件授予的相应 C 或 c + + 源文件的基名称。将扩展名的映射。  
  
 指定**/Fm**具有相同的效果，如同你指定的一样[/MAP （生成映射文件）](../../build/reference/map-generate-mapfile.md)链接器选项。  
  
 如果指定[（编译而无需链接） 的 /c](../../build/reference/c-compile-without-linking.md)以取消链接， **/Fm**不起作用。  
  
 映射文件中的全局符号通常有一个或多个前导下划线，因为编译器会向变量名称添加前导下划线。 出现在映射文件中的许多全局符号是由编译器和标准库内部使用。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  点击“命令行”  属性页。  
  
4.  在 **“附加选项”** 框中键入编译器选项。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>请参阅  
 [输出文件 (/ F) 选项](../../build/reference/output-file-f-options.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [指定路径名](../../build/reference/specifying-the-pathname.md)