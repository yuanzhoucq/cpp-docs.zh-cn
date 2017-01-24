---
title: "/Zl（省略默认库名） | Microsoft Docs"
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
  - "/zi"
  - "VC.Project.VCCLCompilerTool.OmitDefaultLibName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zl 编译器选项 [C++]"
  - "默认库, 省略名称"
  - "“省略默认库名”编译器选项"
  - "ZI 编译器选项"
  - "-Zl 编译器选项 [C++]"
ms.assetid: b27d39d0-44d6-498c-84ae-27c1326fee59
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Zl（省略默认库名）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

省略 .obj 文件中的默认 C 运行库名称。  默认情况下，编译器将库名放入 .obj 文件中，以便使链接器指向正确的库。  
  
## 语法  
  
```  
/Zl  
```  
  
## 备注  
 有关默认库的更多信息，请参见[使用运行库](../../build/reference/md-mt-ld-use-run-time-library.md)。  
  
 可以使用 **\/Zl** 来编译打算放入库中的 .obj 文件。  虽然省略库名只为单个 .obj 文件节省了少量空间，但在包含许多对象模块的库中节省的总空间是很多的。  
  
 此选项为高级选项。  设置此选项将移除应用程序可能需要的某种 C 运行库支持，如果应用程序依赖于此支持，则将导致链接时错误。  如果使用此选项，则必须以其他某种方式提供所需组件。  
  
 使用[\/NODEFAULTLIB（忽略库）](../../build/reference/nodefaultlib-ignore-libraries.md)使链接器忽略所有 .obj 文件中的库引用。  
  
 有关详细信息，请参阅[CRT 库功能](../../c-runtime-library/crt-library-features.md)。  
  
 使用 **\/Zl** 进行编译时，将定义 `_VC_NODEFAULTLIB`。例如：  
  
```  
// vc_nodefaultlib.cpp  
// compile with: /Zl  
void Test() {  
   #ifdef _VC_NODEFAULTLIB  
      int i;  
   #endif  
  
   int i;   // C2086  
}  
```  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“高级”**属性页。  
  
4.  修改**“省略默认的库名称”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitDefaultLibName%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)