---
title: "/INTEGRITYCHECK（需要签名检查） | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 9e738825-2c98-40cd-8ad2-5d0d9c14893e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /INTEGRITYCHECK（需要签名检查）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定二进制图像的数字签名在加载时必须进行检查。  
  
```  
/INTEGRITYCHECK[:NO]  
```  
  
## 备注  
 默认情况下，**\/INTEGRITYCHECK** 处于关闭状态。  
  
 **\/INTEGRITYCHECK** 选项在 DLL 文件或可执行文件的 PE 标头中设置标志，让内存管理器检查数字签名以 Windows 中加载图像。  必须为某些实现 Windows功能加载的内核模式代码的32位和64位DLL设置此选项在[!INCLUDE[win7](../../build/includes/win7_md.md)]、[!INCLUDE[win8](../../build/includes/win8_md.md)]、[!INCLUDE[winsvr08](../../build/includes/winsvr08_md.md)]、[!INCLUDE[winserver8](../../build/includes/winserver8_md.md)] 和的所有设备驱动程序中也建议设置此选项。  Windows Vista 之前的各个 Windows 版本忽略此标志。  有关详细信息，请参见 [Forced Integrity Signing of Portable Executable \(PE\)](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)（可移植可执行文件 \(PE\) 的强制完整性签名）。  
  
### 在 Visual Studio 中设置此链接器选项  
  
1.  打开此项目的**“属性页”**对话框。  有关详细信息，请参阅[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展开**“配置属性”**节点。  
  
3.  展开**“链接器”**节点。  
  
4.  选择**“命令行”**属性页。  
  
5.  在“附加选项”，输入 `/INTEGRITYCHECK` 或 `/INTEGRITYCHECK:NO`。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)   
 [Forced Integrity Signing of Portable Executable \(PE\) files](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)   
 [Kernel\-Mode Code Signing Walkthrough](http://msdn.microsoft.com/windows/hardware/gg487328.aspx)   
 [Windows 7 和 Windows Server 2008 中的 AppInit DLL](http://msdn.microsoft.com/windows/hardware/gg463040.aspx)