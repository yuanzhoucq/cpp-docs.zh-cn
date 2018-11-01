---
title: 如何：生成免注册 COM 组件
ms.date: 11/04/2016
helpviewer_keywords:
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
ms.openlocfilehash: 4f4ebf121b761c37969fa3f9788bda52d913f340
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463526"
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

[独立的应用程序](/windows/desktop/SbsCs/isolated-applications)<br/>
[有关通过并行程序集](/windows/desktop/SbsCs/about-side-by-side-assemblies-)<br/>
[如何：生成独立应用程序以使用 COM 组件](../build/how-to-build-isolated-applications-to-consume-com-components.md)