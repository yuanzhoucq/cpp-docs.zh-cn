---
title: /ALLOWBIND
ms.date: 11/04/2016
f1_keywords:
- /allowbind_bind
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
ms.openlocfilehash: 4f5b662223914cbb4970188595afb52cc2500cd4
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440387"
---
# <a name="allowbind"></a>/ALLOWBIND

指定一个 DLL 是否可以绑定。

```

/ALLOWBIND[:NO]
```

## <a name="remarks"></a>备注

**/ALLOWBIND**选项会在 DLL 的标头中设置一个位，指示绑定允许绑定图像的 .exe。 当加载程序无需为每个引用的 DLL 实现变基并执行地址修正时，绑定可以使图像加载速度更快。 如果 DLL 已进行数字签名，则您可能不希望对其进行绑定，绑定使签名无效。 如果在支持 ASLR 的 Windows 版本上使用 **/DYNAMICBASE**为映像启用了地址空间布局随机化（ASLR），则绑定不起作用。

使用 **/ALLOWBIND： NO**可防止 CMD.EXE 绑定 DLL。

有关详细信息，请参阅[/ALLOWBIND](allowbind-prevent-dll-binding.md)链接器选项。

## <a name="see-also"></a>另请参阅

[EDITBIN 选项](editbin-options.md)
