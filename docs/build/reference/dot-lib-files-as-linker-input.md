---
title: "用作链接器输入的 .Lib 文件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.AdditionalDependencies"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".lib 文件"
  - "COFF 文件, 导入库"
  - "默认库 [C++]"
  - "默认库 [C++], 链接器输出"
  - "默认值 [C++], 库"
  - "导入库, 链接器文件"
  - "库 [C++], 用作链接器输入的 .lib 文件"
  - "链接 [C++], OMF 库"
  - "OMF 库"
ms.assetid: dc5d2b1c-2487-41fa-aa71-ad1e0647958b
caps.latest.revision: 15
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 用作链接器输入的 .Lib 文件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

LINK 接受 COFF 标准库和 COFF 导入库，这两者通常都具有扩展名 .lib。  标准库包含对象，并用 LIB 工具创建。  导入库包含有关其他程序中导出的信息。当 LINK 生成包含导出的程序时导入库由 LINK 创建，或由 LIB 工具创建。  有关使用 LIB 创建标准库或导入库的信息，请参见 [LIB 参考](../../build/reference/lib-reference.md)。  有关使用 LINK 创建导入库的详细信息，请参见 [\/DLL](../../build/reference/dll-build-a-dll.md) 选项。  
  
 库可以作为文件名参数或默认库指定给 LINK。  LINK 解析外部引用时，首先在命令行上指定的库中搜索，然后在用 [\/DEFAULTLIB](../../build/reference/defaultlib-specify-default-library.md) 选项指定的默认库中搜索，最后在 .obj 文件中指定的默认库中搜索。  如果路径是用库名指定的，则 LINK 在该目录中查找库。  如果没有指定路径，则 LINK 先在运行 LINK 的目录中查找，然后在 LIB 环境变量中指定的任何目录中查找。  
  
### 在开发环境中添加用作链接器输入的 .lib 文件  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击“输入”属性页。  
  
4.  修改**“附加依赖项”**属性。  
  
### 以编程方式添加用作链接器输入的 .lib 文件  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalDependencies%2A>。  
  
## 示例  
 下面的示例演示如何生成和使用 .lib 文件：  
  
```  
// lib_link_input_1.cpp  
// compile with: /LD  
__declspec(dllexport) int Test() {  
   return 213;  
}  
```  
  
## 示例  
 然后：  
  
```  
// lib_link_input_2.cpp  
// compile with: /EHsc lib_link_input_1.lib  
__declspec(dllimport) int Test();  
#include <iostream>  
int main() {  
   std::cout << Test() << std::endl;  
}  
```  
  
  **213**   
## 请参阅  
 [LINK 输入文件](../../build/reference/link-input-files.md)   
 [链接器选项](../../build/reference/linker-options.md)