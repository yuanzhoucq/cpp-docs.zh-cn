---
title: "/DELAY（延迟加载导入设置） | Microsoft Docs"
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
  - "/delay"
  - "VC.Project.VCLinkerTool.DelayNoBind"
  - "VC.Project.VCLinkerTool.SupportUnloadOfDelayLoadedDLL"
  - "VC.Project.VCLinkerTool.DelayUnload"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DELAY 链接器选项"
  - "DELAY 链接器选项"
  - "-DELAY 链接器选项"
  - "DLL 的延迟加载, /DELAY 选项"
ms.assetid: 9334b332-cc58-4dae-b10f-a4c75972d50c
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /DELAY（延迟加载导入设置）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/DELAY:UNLOAD  
/DELAY:NOBIND  
```  
  
## 备注  
 \/DELAY 选项控制 DLL 的[延迟加载](../../build/reference/linker-support-for-delay-loaded-dlls.md)：  
  
-   UNLOAD 限定符通知延迟加载 Helper 函数支持 DLL 的显式卸载。  导入地址表 \(IAT\) 被重置为其原始形式，从而使 IAT 指针无效并导致它们被覆盖。  
  
     如果不选择 UNLOAD，任何对 [FUnloadDelayLoadedDLL](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md) 调用都将失败。  
  
-   NOBIND 限定符通知链接器不要在最终图像中包含可绑定的 IAT。  默认值是为延迟加载的 DLL 创建可绑定的 IAT。  无法静态绑定生成的图像。  （可以在执行之前静态绑定包含可绑定 IAT 的图像。）请参阅 [\/BIND](../../build/reference/bind.md)。  
  
     如果绑定了 DLL，则 Helper 函数将尝试使用绑定信息，而不是对每个引用的导入调用 [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212.aspx)。  如果时间戳或首选地址与加载的 DLL 的时间戳或首选地址不匹配，则 Helper 函数将假定绑定的 IAT 已经过期并继续执行，就像绑定的 IAT 不存在一样。  
  
     NOBIND 导致程序图像比较大，但是可以加快 DLL 的加载时间。  如果从不打算绑定 DLL，则 NOBIND 将禁止生成绑定的 IAT。  
  
 若要指定 DLL 延迟加载，请使用 [\/DELAYLOAD](../../build/reference/delayload-delay-load-import.md) 选项。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关信息，请参见[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  依次展开**“配置属性”**、**“链接器”**，然后选择**“高级”**。  
  
3.  修改**“延迟加载的 DLL”**属性。  
  
### 以编程方式设置此链接器选项  
  
-   请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)