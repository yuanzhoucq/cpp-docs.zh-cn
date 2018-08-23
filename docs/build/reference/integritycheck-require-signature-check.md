---
title: -INTEGRITYCHECK （需要签名检查） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9e738825-2c98-40cd-8ad2-5d0d9c14893e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a10594391b0f3be490608f7dfa006b0c32aa2e0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609275"
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
  
1.  打开项目“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  展开“配置属性”节点。  
  
3.  展开**链接器**节点。  
  
4.  选择**命令行**属性页。  
  
5.  在中**其他选项**，输入`/INTEGRITYCHECK`或`/INTEGRITYCHECK:NO`。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)   
 [强制的完整性签名的可移植可执行文件 (PE) 文件](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)   
 [内核模式代码签名演练](http://msdn.microsoft.com/windows/hardware/gg487328.aspx)   
 [Windows 7 和 Windows Server 2008 中的 AppInit Dll](http://msdn.microsoft.com/windows/hardware/gg463040.aspx)