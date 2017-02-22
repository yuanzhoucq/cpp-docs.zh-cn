---
title: "/c（在不链接的情况下进行编译） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/c"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/c 编译器选项 [C++]"
  - "c 编译器选项 [C++]"
  - "-c 编译器选项 [C++]"
  - "cl.exe 编译器, 编译而不链接"
  - "取消链接"
ms.assetid: 8017fc3d-e5dd-4668-a1f7-3120daa95d20
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# /c（在不链接的情况下进行编译）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

禁止自动调用 LINK。  
  
## 语法  
  
```  
/c  
```  
  
## 备注  
 用 **\/c** 编译将只创建 .obj 文件。  必须用正确的文件和选项显式调用 LINK，才能执行生成的链接阶段。  
  
 默认情况下，在开发环境中创建的任何内部项目都使用 **\/c** 选项。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
-   此选项从开发环境内部不可用。  
  
### 以编程方式设置此编译器选项  
  
-   若要以编程方式设置此编译器选项，请参见 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileOnly%2A>。  
  
## 示例  
 下列命令行创建对象文件 FIRST.obj 和 SECOND.obj。  忽略 THIRD.obj。  
  
```  
CL /c FIRST.C SECOND.C THIRD.OBJ  
```  
  
 若要创建可执行文件，必须调用 LINK：  
  
```  
LINK firsti.obj second.obj third.obj /OUT:filename.exe  
```  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)