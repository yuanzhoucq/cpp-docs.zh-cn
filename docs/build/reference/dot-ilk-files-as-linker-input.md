---
title: 用作链接器输入的 .Ilk 文件
ms.date: 11/04/2016
helpviewer_keywords:
- ILK files
- .ilk files
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
ms.openlocfilehash: 6c0eb5627d7dd1b414351dc65685c0c5071d249e
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422502"
---
# <a name="ilk-files-as-linker-input"></a>用作链接器输入的 .Ilk 文件

时以增量方式链接，链接将更新第一个增量链接期间创建的.ilk 状态文件。 此文件具有相同的基名称为.exe 文件或.dll 文件中，并具有扩展名.ilk。 在后面的增量链接，链接更新的.ilk 文件。 如果缺少.ilk 文件，请链接执行完全链接并创建一个新的.ilk 文件。 如果.ilk 文件不可用，则 LINK 执行非增量链接。 有关增量链接的详细信息，请参阅[增量链接 (/incremental)](../../build/reference/incremental-link-incrementally.md)选项。

## <a name="see-also"></a>请参阅

[LINK 输入文件](../../build/reference/link-input-files.md)<br/>
[链接器选项](../../build/reference/linker-options.md)
