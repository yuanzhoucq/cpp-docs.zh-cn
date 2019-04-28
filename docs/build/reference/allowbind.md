---
title: /ALLOWBIND
ms.date: 11/04/2016
f1_keywords:
- /allowbind
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
ms.openlocfilehash: 4cb7e5a3627d865e2f2193dee096c72cced75f5f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273191"
---
# <a name="allowbind"></a>/ALLOWBIND

指定一个 DLL 是否可以绑定。

```

/ALLOWBIND[:NO]
```

## <a name="remarks"></a>备注

**/ALLOWBIND**选项设置一个位向 Bind.exe 指示允许图像要绑定的 DLL 的标头中。 绑定可以允许加载程序不具有可重定基本值并为每个引用的 DLL 执行地址链接地址信息时更快地加载的图像。 您可能不希望的 DLL，如果已进行数字签名绑定-绑定使签名无效。 如果使用映像启用地址空间布局随机化 (ASLR)，绑定没有任何作用 **/DYNAMICBASE**支持 ASLR 的 Windows 版本上。

使用 **/allowbind: no**以防止 Bind.exe 绑定 DLL。

有关详细信息，请参阅[/ALLOWBIND](allowbind-prevent-dll-binding.md)链接器选项。

## <a name="see-also"></a>请参阅

[EDITBIN 选项](editbin-options.md)
