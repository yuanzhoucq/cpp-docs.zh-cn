---
title: "/CLRUNMANAGEDCODECHECK（添加 SupressUnmanagedCodeSecurityAttribute） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/CLRUNMANAGEDCODECHECK"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/CLRUNMANAGEDCODECHECK 链接器选项"
  - "-CLRUNMANAGEDCODECHECK 链接器选项"
ms.assetid: 73abc426-dab0-45e2-be85-0f9a14206cc2
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# /CLRUNMANAGEDCODECHECK（添加 SupressUnmanagedCodeSecurityAttribute）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**\/CLRUNMANAGEDCODECHECK** 指定链接器是否将 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 应用于链接器生成的从托管代码到本机 DLL 的 `PInvoke` 调用。  
  
## 语法  
  
```  
/CLRUNMANAGEDCODECHECK[:NO]  
```  
  
## 备注  
 默认情况下，链接器将 SuppressUnmanagedCodeSecurityAttribute 应用于链接器生成的 `PInvoke` 调用。  当 **\/CLRUNMANAGEDCODECHECK** 有效时，不应用 SuppressUnmanagedCodeSecurityAttribute。  
  
 链接器仅将特性添加到用 **\/clr** 或 **\/clr:pure** 编译的对象。  链接器不在用 **\/clr:safe** 编译的对象中生成 `PInvoke` 调用。  有关详细信息，请参阅[\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
 如果链接器找不到一个托管符号来满足托管调用方的引用，但可以找到一个本机符号来满足该引用时，该链接器将生成 `PInvoke` 调用。  有关 `PInvoke`的更多信息，请参见[从托管代码调用本机函数](../../dotnet/calling-native-functions-from-managed-code.md)。  
  
 注意：如果在代码中使用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute>，应显式设置 **\/CLRUNMANAGEDCODECHECK**。  如果映像同时包含 SuppressUnmanagedCodeSecurity 和 AllowPartiallyTrustedCallers 特性，则是一个潜在的安全漏洞。  
  
 有关使用 SuppressUnmanagedCodeSecurityAttribute 的含义的更多信息，请参见[Security Optimizations](http://msdn.microsoft.com/zh-cn/cf255069-d85d-4de3-914a-e4625215a7c0)。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展开**“配置属性”**节点。  
  
3.  展开**“链接器”**节点。  
  
4.  选择**“高级”**属性页。  
  
5.  修改**“CLR 非托管代码检查”**属性。  
  
### 以编程方式设置此链接器选项  
  
1.  请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRUnmanagedCodeCheck%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)