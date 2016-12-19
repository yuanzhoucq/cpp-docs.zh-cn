---
title: "/HIGHENTROPYVA（支持 64 位 ASLR） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: fe35f9f7-d28e-4694-9aeb-a79db06168e0
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /HIGHENTROPYVA（支持 64 位 ASLR）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定可执行图像支持高熵（64 位）地址空间布局随机化 \(ASLR\)。  
  
## 语法  
  
```  
/HIGHENTROPYVA[:NO]  
```  
  
## 备注  
 默认情况下，为 64 位可执行图打开 \/HIGHENTROPYVA。  它不适用于 32 位可执行图像。  若要启用此选项，\/DYNAMICBASE 也必须处于打开状态。  
  
 \/HIGHENTROPYVA 修改 .dll 文件或 .exe 文件的标头，以指示是否支持 64 位地址的 ASLR。  当在可执行文件和所有依赖的模块上执行此选项时，支持 64 位 ASLR 的操作系统可在加载时通过使用 64 位虚拟地址空间来重新设定可执行图像段。  更大的地址空间使攻击者更难猜到特定内存区域的位置。  
  
### 在 Visual Studio 中设置此链接器选项  
  
1.  打开项目“属性页”对话框。  有关详细信息，请参阅 [如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展开“配置属性”节点。  
  
3.  展开“链接器”节点。  
  
4.  选择“命令行”属性页。  
  
5.  在“附加选项”中，输入 `/HIGHENTROPYVA` 或 `/HIGHENTROPYVA:NO`。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)