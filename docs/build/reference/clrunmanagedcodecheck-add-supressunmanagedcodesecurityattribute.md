---
title: -CLRUNMANAGEDCODECHECK （添加 SupressUnmanagedCodeSecurityAttribute） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLRUNMANAGEDCODECHECK
dev_langs:
- C++
helpviewer_keywords:
- -CLRUNMANAGEDCODECHECK linker option
- /CLRUNMANAGEDCODECHECK linker option
ms.assetid: 73abc426-dab0-45e2-be85-0f9a14206cc2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a00563460519225b38b1c5e745679da943d890cd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="clrunmanagedcodecheck-add-supressunmanagedcodesecurityattribute"></a>/CLRUNMANAGEDCODECHECK（添加 SupressUnmanagedCodeSecurityAttribute）
**/CLRUNMANAGEDCODECHECK**指定链接器是否将应用<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>到链接器生成`PInvoke`从托管代码调用到本机 Dll。  
  
## <a name="syntax"></a>语法  
  
```  
/CLRUNMANAGEDCODECHECK[:NO]  
```  
  
## <a name="remarks"></a>备注  
 默认情况下，链接器 SuppressUnmanagedCodeSecurityAttribute 适用于链接器生成`PInvoke`调用。 当 **/CLRUNMANAGEDCODECHECK**实际上，是 SuppressUnmanagedCodeSecurityAttribute 则不会应用。  
  
 链接器仅将属性添加到使用编译的对象 **/clr**或 **/clr: pure**。 但是， **/clr: pure**和 **/clr: safe**编译器选项在 Visual Studio 2015 中弃用，并将编译器的未来版本中删除。  
  
 A`PInvoke`链接器找不到一个托管的符号来满足中托管的调用方的引用，但可以查找本机符号来满足该引用时，调用将生成链接器。 有关详细信息`PInvoke`，请参阅[从托管代码调用本机函数](../../dotnet/calling-native-functions-from-managed-code.md)。  
  
 请注意，如果你使用<xref:System.Security.AllowPartiallyTrustedCallersAttribute>在代码中，你应显式设置 **/CLRUNMANAGEDCODECHECK**。 如果映像包含 SuppressUnmanagedCodeSecurity 和 AllowPartiallyTrustedCallers 属性，则会潜在的安全漏洞。  
  
 请参阅[非托管代码的安全编码准则](/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code)有关使用 SuppressUnmanagedCodeSecurityAttribute 的影响的详细信息。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  展开**配置属性**节点。  
  
3.  展开**链接器**节点。  
  
4.  选择**高级**属性页。  
  
5.  修改**CLR 非托管代码检查**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
1.  请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRUnmanagedCodeCheck%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)