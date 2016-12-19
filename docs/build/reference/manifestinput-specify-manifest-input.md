---
title: "/MANIFESTINPUT（指定清单输入） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /MANIFESTINPUT（指定清单输入）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定一个清单输入文件加入嵌入在图像中的清单中。  
  
## 语法  
  
```c#  
/MANIFESTINPUT:filename  
```  
  
#### 参数  
 `filename`  
 要包含在内嵌清单中的清单文件。  
  
## 备注  
 **\/MANIFESTINPUT** 选项指定了用来在可执行图像中创建嵌入清单的输入文件的路径。  如果您有多个清单输入文件，请多次使用切换——针对每个输入文件使用一次。  清单输入文件经过合并以创建嵌入清单。  此选项需要 **\/MANIFEST:EMBED** 选项。  
  
 此选项不能直接在 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 中设置。  相反，请使用项目的“附加清单文件”属性来指定要包括的附加清单文件。  有关详细信息，请参阅[“\<项目名\> 属性页”对话框 \-\>“配置属性”\-\>“清单工具”\-\>“输入和输出”](../../ide/input-and-output-manifest-tool.md)。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)