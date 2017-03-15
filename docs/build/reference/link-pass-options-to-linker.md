---
title: "/link（将选项传递到链接器） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/link"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/link 编译器选项 [C++]"
  - "cl.exe 编译器 [C++], 将选项传递给链接器"
  - "link 编译器选项 [C++]"
  - "-link 编译器选项 [C++]"
  - "链接器 [C++], 将选项传递给"
  - "将选项传递给链接器"
ms.assetid: 16902a94-c094-4328-841f-3ac94ca04848
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# /link（将选项传递到链接器）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将一个或多个链接器选项传递到链接器。  
  
## 语法  
  
```  
/link linkeroptions  
```  
  
## Arguments  
 `linkeroptions`  
 要传递到链接器的链接器选项。  
  
## 备注  
 **\/link** 选项及其链接器选项必须出现在任何文件名和 CL 选项之后。  **\/link** 和 `linkeroptions` 之间需要空格。  有关详细信息，请参阅[设置链接器选项](../../build/reference/setting-linker-options.md)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击链接器属性页。  
  
4.  修改一个或多个属性。  
  
### 以编程方式设置此编译器选项  
  
-   不能以编程方式更改此编译器选项。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)