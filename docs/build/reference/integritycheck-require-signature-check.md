---
title: /INTEGRITYCHECK（需要签名检查）
ms.date: 11/04/2016
ms.assetid: 9e738825-2c98-40cd-8ad2-5d0d9c14893e
ms.openlocfilehash: 8530175cd5bc0ed5dced7f92e5f67a1576bb43e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578342"
---
# <a name="integritycheck-require-signature-check"></a>/INTEGRITYCHECK（需要签名检查）

指定必须在加载时检查数字签名的二进制图像。

```
/INTEGRITYCHECK[:NO]
```

## <a name="remarks"></a>备注

默认情况下 **/INTEGRITYCHECK**处于关闭状态。

**/INTEGRITYCHECK**选项集 — DLL 文件或可执行文件的 PE 标头中，内存管理器检查数字签名才能加载 Windows 中的图像的标志。 此选项必须为实现某些 Windows 功能，加载的内核模式代码的 32 位和 64 位 Dll 设置，适用于 Windows Vista、 Windows 7、 Windows 8、 Windows Server 2008 和 Windows Server 2012 上的所有设备驱动程序。 在 Windows Vista 之前的 Windows 版本忽略此标志。 有关详细信息，请参阅[强制完整性签名的可移植可执行文件 (PE) 文件](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)。

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中设置此链接器选项

1. 打开项目“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 展开“配置属性”节点。

1. 展开**链接器**节点。

1. 选择**命令行**属性页。

1. 在中**其他选项**，输入`/INTEGRITYCHECK`或`/INTEGRITYCHECK:NO`。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)<br/>
[强制的完整性签名的可移植可执行文件 (PE) 文件](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)<br/>
[内核模式代码签名演练](https://msdn.microsoft.com/windows/hardware/gg487328.aspx)<br/>
[Windows 7 和 Windows Server 2008 中的 AppInit Dll](https://msdn.microsoft.com/windows/hardware/gg463040.aspx)