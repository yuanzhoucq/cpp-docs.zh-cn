---
title: /CLRUNMANAGEDCODECHECK (Remove SuppressUnmanagedCodeSecurityAttribute)
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- /CLRUNMANAGEDCODECHECK
helpviewer_keywords:
- -CLRUNMANAGEDCODECHECK linker option
- /CLRUNMANAGEDCODECHECK linker option
ms.assetid: 73abc426-dab0-45e2-be85-0f9a14206cc2
author: corob-msft
ms.author: corob
ms.openlocfilehash: cb23106648e3325755a857d0b962112e9bdcfac4
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822595"
---
# <a name="clrunmanagedcodecheck-remove-suppressunmanagedcodesecurityattribute"></a>/CLRUNMANAGEDCODECHECK (Remove SuppressUnmanagedCodeSecurityAttribute)

**/CLRUNMANAGEDCODECHECK**指定链接器不适用于<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>到链接器生成`PInvoke`从托管代码到本机 Dll 的调用。

## <a name="syntax"></a>语法

> **/CLRUNMANAGEDCODECHECK**[**:NO**]

## <a name="remarks"></a>备注

默认情况下，链接器适用**SuppressUnmanagedCodeSecurityAttribute**到链接器生成`PInvoke`调用。 当 **/clrunmanagedcodecheck 有效，则**有效时， **SuppressUnmanagedCodeSecurityAttribute**中删除。 若要显式应用**SuppressUnmanagedCodeSecurityAttribute**到链接器生成`PInvoke`调用，可以使用 **/CLRUNMANAGEDCODECHECK:NO**。

链接器仅将属性添加到使用编译的对象 **/clr**或 **/clr: pure**。 但是， **/clr: pure**编译器选项在 Visual Studio 2015 中弃用并在 Visual Studio 2017 中不受支持。

一个`PInvoke`链接器找不到一个托管的符号来满足托管调用方的引用，但可以找到本机符号来满足该引用时，链接器将生成调用。 有关详细信息`PInvoke`，请参阅[从托管代码调用本机函数](../../dotnet/calling-native-functions-from-managed-code.md)。

请注意，如果您使用<xref:System.Security.AllowPartiallyTrustedCallersAttribute>在代码中，您应显式设置 **/clrunmanagedcodecheck 有效，则**若要删除**SuppressUnmanagedCodeSecurity**属性。 如果映像包含是潜在的安全漏洞**SuppressUnmanagedCodeSecurity**并**AllowPartiallyTrustedCallers**属性。

请参阅[用于非托管代码安全编码准则](/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code)有关详细信息的使用含义**SuppressUnmanagedCodeSecurityAttribute**。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 展开“配置属性”节点。

1. 展开**链接器**节点。

1. 选择**高级**属性页。

1. 修改**CLR 非托管代码检查**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

1. 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRUnmanagedCodeCheck%2A>。

## <a name="see-also"></a>请参阅

- [MSVC 链接器引用](linking.md)
- [MSVC 链接器选项](linker-options.md)
