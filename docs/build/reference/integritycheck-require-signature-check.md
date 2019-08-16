---
title: /INTEGRITYCHECK（需要签名检查）
ms.date: 11/04/2016
ms.assetid: 9e738825-2c98-40cd-8ad2-5d0d9c14893e
ms.openlocfilehash: 1732c612501b66753635b272f94764975c555f75
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492847"
---
# <a name="integritycheck-require-signature-check"></a>/INTEGRITYCHECK（需要签名检查）

指定必须在加载时检查二进制文件的数字签名。

```
/INTEGRITYCHECK[:NO]
```

## <a name="remarks"></a>备注

默认情况下, **/INTEGRITYCHECK**为 off。

**/INTEGRITYCHECK**选项会在 DLL 文件或可执行文件的 PE 标头中设置-内存管理器的标志, 用于检查数字签名以便在 Windows 中加载图像。 对于实现某些 Windows 功能加载的内核模式代码的32位和64位 Dll, 此选项必须设置为, 并且建议用于 Windows Vista、Windows 7、Windows 8、Windows Server 2008 和 Windows Server 2012 上的所有设备驱动程序。 Windows Vista 之前的 Windows 版本忽略此标志。 有关详细信息, 请参阅[可移植可执行文件 (PE) 的强制完整性签名](https://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)。

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中设置此链接器选项

1. 打开项目“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 展开“配置属性”节点。

1. 展开“链接器”节点。

1. 选择 "**命令行**" 属性页。

1. 在 "**其他选项**" `/INTEGRITYCHECK`中`/INTEGRITYCHECK:NO`, 输入或。

## <a name="see-also"></a>请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)<br/>
[可移植可执行 (PE) 文件的强制完整性签名](https://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)<br/>
[内核模式代码签名要求](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-)<br/>
[AppInit Dll 和安全启动](/windows/win32/dlls/secure-boot-and-appinit-dlls)
