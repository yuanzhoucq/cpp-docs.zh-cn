---
title: 如何：生成独立应用程序以使用 COM 组件
ms.date: 11/04/2016
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
ms.openlocfilehash: 8ae3c51502267f202cbb85ea7be2a81dc3310410
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493237"
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>如何：生成独立应用程序以使用 COM 组件

独立应用程序是清单内置在程序中的应用程序。 可以创建独立应用程序以使用 COM 组件。

### <a name="to-add-com-references-to-manifests-of-isolated-applications"></a>添加对独立应用程序清单的 COM 引用

1. 打开独立应用程序的项目属性页。

1. 展开“配置属性”节点，然后展开“清单工具”节点   。

1. 选择“独立 COM”  属性页，然后将“组件文件名”  属性设置为你希望独立应用程序使用的 COM 组件的名称。

1. 单击 **“确定”** 。

### <a name="to-build-manifests-into-isolated-applications"></a>将清单生成到独立应用程序中

1. 打开独立应用程序的项目属性页。

1. 展开“配置属性”节点，然后展开“清单工具”节点   。

1. 选择“输入和输出”属性页，然后将“嵌入清单”属性设置为“是”    。

1. 单击 **“确定”** 。

1. 生成解决方案。

## <a name="see-also"></a>请参阅

[独立的应用程序](/windows/win32/SbsCs/isolated-applications)<br/>
[关于并行程序集](/windows/win32/SbsCs/about-side-by-side-assemblies-)
