---
title: 如何：生成独立应用程序以使用 COM 组件
ms.date: 11/04/2016
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
ms.openlocfilehash: ba35c016996604e2b433083c2de7b9ddc807d52c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587533"
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>如何：生成独立应用程序以使用 COM 组件

独立应用程序是具有内置于程序的清单的应用程序。 您可以创建独立应用程序以使用 COM 组件。

### <a name="to-add-com-references-to-manifests-of-isolated-applications"></a>若要添加到独立的应用程序的清单中的 COM 引用

1. 打开独立的应用程序的项目属性页。

1. 展开**配置属性**节点，然后展开**清单工具**节点。

1. 选择**独立 COM**属性页，然后将设置**组件文件名**属性设置为你想要使用的独立应用程序的 COM 组件的名称。

1. 单击 **“确定”**。

### <a name="to-build-manifests-into-isolated-applications"></a>若要构建到独立的应用程序的清单

1. 打开独立的应用程序的项目属性页。

1. 展开**配置属性**节点，然后展开**清单工具**节点。

1. 选择**输入和输出**属性页，然后将设置**嵌入清单**属性等于**是**。

1. 单击 **“确定”**。

1. 生成解决方案。

## <a name="see-also"></a>请参阅

[独立的应用程序](/windows/desktop/SbsCs/isolated-applications)<br/>
[有关通过并行程序集](/windows/desktop/SbsCs/about-side-by-side-assemblies-)