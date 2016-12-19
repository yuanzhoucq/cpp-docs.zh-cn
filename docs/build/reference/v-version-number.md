---
title: "/V（版本号） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/v"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/V 编译器选项 [C++]"
  - "嵌入版本字符串"
  - "V 编译器选项 [C++]"
  - "-V 编译器选项 [C++]"
  - "版本号, 为 .obj 指定"
ms.assetid: 3e93fb7a-5dfd-49a6-bd49-3dca8052e0f3
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /V（版本号）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选项将一个文本字符串嵌入到 .obj 文件中。  已否决。  
  
## 语法  
  
```  
/Vstring  
```  
  
## Arguments  
 `string`  
 字符串，指定要嵌入 .obj 文件的版本号或版权声明。  
  
## 备注  
 该字符串可以用版本号或版权声明标记 .obj 文件。  如果该字符串包含任何空格或制表符，则必须将它们括入双引号（“”）中。  如果该字符串包含任何双引号，则其前面必须有一个反斜杠 \(\\\)。  **\/V** 和 `string` 之间的空格是可选的。  
  
 也可以使用带有编译器注释类型参数的 [注释](../../preprocessor/comment-c-cpp.md) 将编译器的名称和版本号放在 .obj 文件中。  
  
 已弃用 **\/V**；**\/V** 原来主要用于支持生成虚拟设备驱动程序 \(VxD\)，而 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 工具集不再支持生成 VxD。  有关详细信息，请参阅[Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/zh-cn/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce)。  
  
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