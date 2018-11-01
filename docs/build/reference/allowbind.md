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
ms.openlocfilehash: 3d38b2a70fc3510b2c26942dc3e5e6fdd76a28e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550522"
---
# <a name="allowbind"></a>/ALLOWBIND

指定一个 DLL 是否可以绑定。

```

/ALLOWBIND[:NO]
```

## <a name="remarks"></a>备注

**/ALLOWBIND**选项设置一个位向 Bind.exe 指示允许图像要绑定的 DLL 的标头中。 绑定可以允许加载程序不具有可重定基本值并为每个引用的 DLL 执行地址链接地址信息时更快地加载的图像。 您可能不希望的 DLL，如果已进行数字签名绑定-绑定使签名无效。 如果使用映像启用地址空间布局随机化 (ASLR)，绑定没有任何作用 **/DYNAMICBASE**支持 ASLR 的 Windows 版本上。

使用 **/allowbind: no**以防止 Bind.exe 绑定 DLL。

有关详细信息，请参阅[/ALLOWBIND](../../build/reference/allowbind-prevent-dll-binding.md)链接器选项。

## <a name="see-also"></a>请参阅

[EDITBIN 选项](../../build/reference/editbin-options.md)