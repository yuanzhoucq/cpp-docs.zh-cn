---
title: "/F（设置堆栈大小） | Microsoft Docs"
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
  - "/f"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/F 编译器选项 [C++]"
  - "F 编译器选项 [C++]"
  - "-F 编译器选项 [C++]"
  - "设置堆栈大小编译器选项"
  - "堆栈, 设置大小"
ms.assetid: 17320b6f-8305-445b-9ec2-75833f4b29e0
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /F（设置堆栈大小）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

设置程序堆栈大小（以字节为单位）。  
  
## 语法  
  
```  
/F number  
```  
  
## Arguments  
 `number`  
 堆栈大小（以字节为单位）。  
  
## 备注  
 如果不使用此选项，堆栈大小默认为 1 MB。  `number` 参数可以用十进制或 C 语言表示法表示。  参数的范围可以在 1 到链接器接受的最大堆栈大小之间。  链接器将指定值向上舍入为最接近的 4 个字节。  **\/F** 和 `number` 之间的空格可选的。  
  
 如果程序获得堆栈溢出消息，则可能需要增加堆栈大小。  
  
 也可通过下列内容设置堆栈大小：  
  
-   使用 **\/STACK** 链接器选项。  有关详细信息，请参阅[\/STACK](../../build/reference/stack.md)。  
  
-   对 .exe 文件使用 EDITBIN。  有关详细信息，请参阅[EDITBIN 参考](../../build/reference/editbin-reference.md)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“命令行”**属性页。  
  
4.  在**“附加选项”**框中键入编译器选项。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)