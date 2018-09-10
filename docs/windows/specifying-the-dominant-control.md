---
title: 指定主导控件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dominant controls
- Dialog Editor [C++], dominant control
- controls [C++], dominant
ms.assetid: 42b523a7-192a-417b-9512-d4af795e002f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a4721cec6ebc11cf2107afe0048da90164c0f47f
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315556"
---
# <a name="specifying-the-dominant-control"></a>指定主导控件

所选控件首先是主导控件。

### <a name="to-specify-the-dominant-control"></a>若要指定主导控件

1. 按住**Ctrl**密钥，然后单击你想要使用影响大小或位置的其他控件的控件*第一个*。

   **请注意**主导控件的大小调整句柄都是可靠的空心下级控件的句柄时。 所有进一步调整大小或对齐方式取决于主导控件。

### <a name="to-change-the-dominant-control"></a>若要更改主导控件

1. 清除所有当前所选控件的外部单击当前所选内容。

2. 重复上一过程，首先选择一个不同的控件。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[选定多个控件](../windows/selecting-multiple-controls.md)  
[“选择”控件](../windows/selecting-controls.md)  
[对话框中的控件](../windows/controls-in-dialog-boxes.md)