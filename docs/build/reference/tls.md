---
title: /TLS
ms.date: 11/04/2016
f1_keywords:
- /TLS
helpviewer_keywords:
- /TLS dumpbin option
- -TLS dumpbin option
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
ms.openlocfilehash: 751c212398f3d309b1d31d204291fe3a0503cf06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317258"
---
# <a name="tls"></a>/TLS

显示从可执行文件的 IMAGE_TLS_DIRECTORY 结构。

## <a name="remarks"></a>备注

/ TLS 显示 TLS 结构的字段以及 TLS 回调函数的地址。

如果程序不使用线程本地存储区，其映像将不包含 TLS 结构。  请参阅[线程](../../cpp/thread.md)有关详细信息。

IMAGE_TLS_DIRECTORY winnt.h 中定义。

## <a name="see-also"></a>请参阅

[DUMPBIN 选项](dumpbin-options.md)
