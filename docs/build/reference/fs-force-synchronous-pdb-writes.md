---
title: "/FS（强制同步 PDB 写入） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/FS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "-FS 编译器选项 [C++]"
  - "/FS 编译器选项 [C++]"
ms.assetid: b2caaffe-f6e1-4963-b068-648f06b105e0
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /FS（强制同步 PDB 写入）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

强制写入程序数据库（PDB）由文件创建，用[\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) 或 [\/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)—通过MSPDBSRV.EXE被序列化。  
  
## 语法  
  
```  
/FS  
```  
  
## 备注  
 默认情况下， **\/Zi** 或 **\/ZI**被指定，编译器锁PDB文件写入类型信息和符号调试信息。  如果类型的数目很大时，它采用编译器生成类型信息的这样可以显着减少时。  如果另一个临时进程锁定 PDB 文件 ，例如，由编译器的防病毒程序编写可能失败，并则可能会出现错误。  此问题也可能发生，当 cl.exe 访问的多个副本同一个 PDB 文件 ，例如，如果您的解决方案具有使用相同的中间目录或输出目录和并行生成启用独立的项目。  该**\/FS**编译器选项阻止编译器锁定的PDB文件，并强制写入序列的访问要经过MSPDBSRV.EXE。  这会使生成速度较长，但它无法阻止可能发生在 cl.exe 访问多个实例 PDB 文件同时的任何错误。  建议您更改解决方案，以便独立项目编写分隔中间文件和输出位置，也可以使一项依赖于另一侧来强制序列化的项目生成。  
  
 [\/MP](../../build/reference/mp-build-with-multiple-processes.md)选项能用**\/FS**为默认。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择 **C\/C\+\+** 文件夹。  
  
3.  选择**“命令行”**属性页。  
  
4.  修改“其它选项”属性以包括`/FS`，然后选择“确定”。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)