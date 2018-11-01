---
title: /SWAPRUN
ms.date: 11/04/2016
f1_keywords:
- /swaprun
helpviewer_keywords:
- /SWAPRUN editbin option
- -SWAPRUN editbin option
- SWAPRUN editbin option
ms.assetid: 6eefd7f3-ca47-48e3-8509-323d27cf4ae7
ms.openlocfilehash: 0440d268a807e6f3f43beb9f38bd1950dee55ffd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550717"
---
# <a name="swaprun"></a>/SWAPRUN

```
/SWAPRUN:{[!]NET|[!]CD}
```

## <a name="remarks"></a>备注

此选项编辑映像以告诉操作系统要将映像复制到交换文件，并从该处运行它。 使用此选项对于驻留在网络或可移动媒体的映像。

您可以添加或删除的 NET 或 CD 限定符：

- NET 指示图像驻留在网络上。

- CD 指示图像驻留在 CD-ROM 或类似的可移动介质。

- 使用 ！ NET 和 ！若要反转的 NET 和 CD 效果的 CD。

## <a name="see-also"></a>请参阅

[EDITBIN 选项](../../build/reference/editbin-options.md)