---
title: 调试提供程序
ms.date: 10/29/2018
helpviewer_keywords:
- debugging [C++], providers
- OLE DB providers, debugging
- Visual C++ debugger, debugging providers
- Visual C++ debugger
ms.assetid: 90d4e7db-06ea-4de0-a7f4-4f3751d50d93
ms.openlocfilehash: 15e9df58d4b31a8e69999c9ec7c22af158d08b38
ms.sourcegitcommit: 943c792fdabf01c98c31465f23949a829eab9aad
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2018
ms.locfileid: "51265082"
---
# <a name="debugging-your-provider"></a>调试提供程序

有两种方法来调试您的提供程序：

- 由于提供程序在进程中创建的可以创建一些通常情况下使用 OLE DB 使用者模板和单步执行该提供程序的使用者代码。

- 可以使用 Visual c + + 附带的各种实用程序。

## <a name="to-use-debugging"></a>若要使用调试

1. 打开提供程序项目。

1. 上**项目**菜单上，单击**属性**。

1. 在中**属性页**对话框中，单击**调试**选项卡。

1. 选择选项作为必需的单击**确定**。

1. 设置断点，并像通常那样调试。

## <a name="see-also"></a>请参阅

[使用 OLE DB 提供程序模板](../../data/oledb/working-with-ole-db-provider-templates.md)