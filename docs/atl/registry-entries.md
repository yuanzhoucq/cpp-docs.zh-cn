---
title: 注册表项 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- registry, ATL services entries
- registry, application IDs
ms.assetid: 881989b7-61bb-459a-a13e-3bfcb33e184e
ms.openlocfilehash: 7a89bc5d510d493f557b7ea74b8eabe5dfd87ac1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261930"
---
# <a name="registry-entries"></a>注册表项

DCOM 引入了应用程序 Id (Appid) 分组到一个集中位置在注册表中的一个或多个 DCOM 对象配置选项的概念。 通过它在名为值对象的 CLSID 下 AppID 的值，该值指示指定一个应用程序 Id。

默认情况下，ATL 生成的服务使用的 CLSID 为其应用程序标识的 guid。 下`HKEY_CLASSES_ROOT\AppID`，可以指定特定于 DCOM 的条目。 最初，存在两个项：

- `LocalService`其值等于服务的名称。 如果此值存在，则使用而不是`LocalServer32`CLSID 下的键。

- `ServiceParameters`其值等于`-Service`。 此值指定在启动时传递给服务的参数。 请注意，这些参数传递给服务的`ServiceMain`函数，未`WinMain`。

任何 DCOM 服务还需要创建另一个密钥下的`HKEY_CLASSES_ROOT\AppID`。 此密钥与的 EXE 的名称相同且充当交叉引用，因为它包含重新指向应用程序标识条目的 AppID 值。

## <a name="see-also"></a>请参阅

[服务](../atl/atl-services.md)
