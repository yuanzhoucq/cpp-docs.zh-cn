---
title: /CLRUNMANAGEDCODECHECK（删除 SuppressUnmanagedCodeSecurityAttribute）
ms.date: 05/16/2019
ms.topic: reference
f1_keywords:
- /CLRUNMANAGEDCODECHECK
helpviewer_keywords:
- -CLRUNMANAGEDCODECHECK linker option
- /CLRUNMANAGEDCODECHECK linker option
ms.assetid: 73abc426-dab0-45e2-be85-0f9a14206cc2
author: corob-msft
ms.author: corob
ms.openlocfilehash: ecc560673a8e98752289ef0e0f89d3abfc1938e4
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837239"
---
# <a name="clrunmanagedcodecheck-remove-suppressunmanagedcodesecurityattribute"></a>/CLRUNMANAGEDCODECHECK（删除 SuppressUnmanagedCodeSecurityAttribute）

“/CLRUNMANAGEDCODECHECK”指定链接器不将 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 应用于从托管代码到本机 DLL 的链接器生成的 `PInvoke` 调用。

## <a name="syntax"></a>语法

> **/CLRUNMANAGEDCODECHECK**[ **:NO**]

## <a name="remarks"></a>备注

默认情况下，链接器将“SuppressUnmanagedCodeSecurityAttribute”应用于链接器生成的 `PInvoke` 调用。 当“/CLRUNMANAGEDCODECHECK”生效时，将删除“SuppressUnmanagedCodeSecurityAttribute”。 若要将“SuppressUnmanagedCodeSecurityAttribute”显式应用于链接器生成的 `PInvoke` 调用，可以使用“/CLRUNMANAGEDCODECHECK:NO”。

链接器仅将属性添加到使用“/clr”或“/clr:pure”编译的对象。 但是，“/clr:pure”编译器选项在 Visual Studio 2015 中已弃用，在 Visual Studio 2017 及更高版本中不受支持。

如果链接器找不到托管符号，无法满足来自托管调用方的引用，但可找到满足该引用的本机符号，链接器将生成 `PInvoke` 调用。 有关 `PInvoke` 的更多信息，请参阅[从托管代码调用本机函数](../../dotnet/calling-native-functions-from-managed-code.md)。

请注意，如果在代码中使用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute>，则应显式设置“/CLRUNMANAGEDCODECHECK”以删除“SuppressUnmanagedCodeSecurity”属性。 如果映像包含“SuppressUnmanagedCodeSecurity”和“AllowPartiallyTrustedCallers”属性，则这是一个潜在的安全漏洞。

有关使用“SuppressUnmanagedCodeSecurityAttribute”的含义的更多信息，请参阅[非托管代码的安全编码指南](/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 展开“配置属性”节点。

1. 展开“链接器”节点。

1. 选择“高级”属性页。

1. 修改“CLR 非托管代码检查”属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

1. 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRUnmanagedCodeCheck%2A>。

## <a name="see-also"></a>请参阅

- [MSVC 链接器参考](linking.md)
- [MSVC 链接器选项](linker-options.md)
