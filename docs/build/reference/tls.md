---
title: /TLS
ms.date: 11/04/2016
f1_keywords:
- /TLS
helpviewer_keywords:
- /TLS dumpbin option
- -TLS dumpbin option
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
ms.openlocfilehash: c125a6439e6cda2159a8bde2317528e667eaf310
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532620"
---
# <a name="tls"></a>/TLS

显示从可执行文件的 IMAGE_TLS_DIRECTORY 结构。

## <a name="remarks"></a>备注

/ TLS 显示 TLS 结构的字段以及 TLS 回调函数的地址。

如果程序不使用线程本地存储区，其映像将不包含 TLS 结构。  请参阅[线程](../../cpp/thread.md)有关详细信息。

IMAGE_TLS_DIRECTORY winnt.h 中定义。

## <a name="see-also"></a>请参阅

[DUMPBIN 选项](../../build/reference/dumpbin-options.md)