---
title: 如何：生成免注册 COM 组件
ms.date: 11/04/2016
helpviewer_keywords:
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
ms.openlocfilehash: 783677c97835acc98751fc4a19f9405af752b71a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809595"
---
# <a name="how-to-build-registration-free-com-components"></a>如何：生成免注册 COM 组件

免注册 COM 组件是 COM 组件，具有内置 Dll 的清单。

### <a name="to-build-manifests-into-com-components"></a>若要为 COM 组件生成清单

1. 打开 COM 组件的项目属性页。

1. 展开**配置属性**节点，然后展开**清单工具**节点。

1. 选择**输入和输出**属性页，然后将设置**嵌入清单**属性等于**是**。

1. 单击 **“确定”**。

1. 生成解决方案。

## <a name="see-also"></a>请参阅

[如何：生成独立应用程序以使用 COM 组件](how-to-build-isolated-applications-to-consume-com-components.md)
