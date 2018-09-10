---
title: 编辑版本信息资源 （c + +） 中的字符串 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.version
dev_langs:
- C++
helpviewer_keywords:
- version information resources [C++]
- resources [C++], editing version information
ms.assetid: d3a7d4e4-7d31-47c2-902c-f50b8404ba4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c5cc7da4629ba00bbb1c48d764b836897c0b3748
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316973"
---
# <a name="editing-a-string-in-a-version-information-resource-c"></a>编辑版本信息资源 （c + +） 中的字符串

### <a name="to-edit-a-string-in-a-version-information-resource"></a>编辑版本信息资源中的字符串

1. 单击相应项目一次以选择它，然后再次开始编辑它。 使所做的更改直接在**版本信息**表中或在[属性窗口](/visualstudio/ide/reference/properties-window)。 进行的更改会在这两个位置得到反映。

   > [!NOTE] 
   > 编辑时`FILEFLAGS`中的键**版本信息**编辑器中，您会注意到，不能设置**调试**， **Private Build**，或**特殊构建**属性 (在**属性**窗口) 为.rc 文件：

   - **版本信息**编辑器集**调试**具有属性`#ifdef`在资源脚本中，基于`_DEBUG`生成标志。

   - 如果`Private Build`密钥都有**值**中设置**版本信息**表中，相应**Private Build**属性 (在**属性**窗口) 的`FILEFLAGS`键将为**True**。 如果 **Value** 为空，则该属性为 **False**。 同样， **Special Build**密钥 (在**版本信息**表) 绑定到**Special Build**属性`FILEFLAGS`密钥。

可以通过单击键或值列标题来对字符串块的信息序列进行排序。 这些标题会自动将信息重新排列为所选顺序。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[版本信息编辑器](../windows/version-information-editor.md)  
[版本信息 (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)