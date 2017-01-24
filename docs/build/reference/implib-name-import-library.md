---
title: "/IMPLIB（命名导入库） | Microsoft Docs"
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
  - "/implib"
  - "VC.Project.VCLinkerTool.ImportLIbrary"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/IMPLIB 链接器选项"
  - "IMPLIB 链接器选项"
  - "-IMPLIB 链接器选项"
  - "导入库, 重写默认名称"
ms.assetid: fe8f71ab-7055-41b5-8ef8-2b97cfa4a432
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /IMPLIB（命名导入库）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/IMPLIB:filename  
```  
  
## 备注  
 其中：  
  
 *filename*  
 用户指定的导入库名称。  该名称将会替换默认名称。  
  
## 备注  
 \/IMPLIB 选项重写 LINK 在生成包含导出的程序时所创建的导入库的默认名称。  默认名称由主输出文件的基名称和扩展名 .lib 组成。  如果指定了下列一项或多项内容，则程序包含导出：  
  
-   源代码中的 [\_\_declspec\(dllexport\)](../../cpp/dllexport-dllimport.md) 关键字  
  
-   .def 文件中的 [EXPORTS](../../build/reference/exports.md) 语句  
  
-   LINK 命令中的 [\/EXPORT](../../build/reference/export-exports-a-function.md) 规范  
  
 当导入库未被创建时，LINK 忽略 \/IMPLIB。  如果未指定导出，则 LINK 不创建导入库。  如果在生成中使用导出文件，则 LINK 假定导入库已经存在并且不再创建。  有关导入库和导出文件的信息，请参见 [LIB 参考](../../build/reference/lib-reference.md)。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击“高级”属性页。  
  
4.  修改“导入库”属性。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ImportLibrary%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)