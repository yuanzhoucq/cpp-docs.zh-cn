---
title: "-Fe （命名 EXE 文件） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /fe
dev_langs: C++
helpviewer_keywords:
- -Fe compiler option [C++]
- executable files, renaming
- rename file compiler option [C++]
- /Fe compiler option [C++]
- Fe compiler option [C++]
ms.assetid: 49f594fd-5e94-45fe-a1bf-7c9f2abb6437
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 83965ef2bf64f77dbcb1eb9832e7178c30260d16
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fe-name-exe-file"></a>/Fe（命名 EXE 文件）
指定名称和.exe 文件或 DLL 由编译器创建的目录。  
  
## <a name="syntax"></a>语法  
  
```  
/Fepathname  
```  
  
## <a name="remarks"></a>备注  
 如果不使用此选项，编译器会对该文件使用命令行的扩展名为.exe 或.dll 上指定的第一个源或对象文件的基名称的默认名称。  
  
 如果指定[（编译而无需链接） 的 /c](../../build/reference/c-compile-without-linking.md)、 编译但不链接， **/Fe**不起作用。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  单击**常规**属性页。  
  
4.  修改**输出文件**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>。  
  
## <a name="example"></a>示例  
 下面的命令行编译并链接当前目录中的所有 C 源文件。 生成的可执行文件被命名为 PROCESS.exe 和在 C:\BIN 的目录中创建。  
  
```  
CL /FeC:\BIN\PROCESS *.C  
```  
  
## <a name="example"></a>示例  
 下面的命令行创建中的可执行文件`C:\BIN`具有相同基名称作为第一个源或对象文件：  
  
```  
CL /FeC:\BIN\ *.C  
```  
  
## <a name="see-also"></a>请参阅  
 [输出文件 (/ F) 选项](../../build/reference/output-file-f-options.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [指定路径名](../../build/reference/specifying-the-pathname.md)