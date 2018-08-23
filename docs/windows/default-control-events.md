---
title: 默认控件事件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Dialog editor, default control events
- controls [C++], default control events
- events [C++], controls
- dialog box controls, events
ms.assetid: 75556b23-18f5-4390-97a4-2ecad3309741
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1a208e85418f362bfa698055ba6b3b403c21bce0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610865"
---
# <a name="default-control-events"></a>默认控件事件

以下控件名称具有随附的默认事件：

|控件名称|默认事件|
|------------------|-------------------|
|动画|ACN_START|
|复选框|BN_CLICKED|
|组合框|CBN_SELCHANGE|
|自定义|TTN_GETDISPINFO|
|日期时间选取器|DTN_DATETIMECHANGE|
|编辑框|EN_CHANGE|
|分组框|（不适用于）|
|热键|NM_OUTOFMEMORY|
|IP 地址|IPN_FIELDCHANGED|
|列表|LVN_ITEMCHANGE|
|列表框|LBN_SELCHANGE|
|月历|MCN_SELCHANGE|
|图片控件|（不适用于）|
|进度|NM_CUSTOMDRAW|
|下压按钮|BN_CLICKED|
|单选按钮|BN_CLICKED|
|格式文本编辑|EN_CHANGE|
|滚动条|NM_THEMECHANGED|
|Slider|NM_CUSTOMDRAW|
|数值调节钮|UDN_DELTAPOS|
|静态文本|（不适用于）|
|Tab|TCN_SELCHANGE|
|树|TVN_SELCHANGE|

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[定义对话框控件的成员变量](../windows/defining-member-variables-for-dialog-controls.md)  
[与用户界面对象关联的消息类型](../mfc/reference/message-types-associated-with-user-interface-objects.md)  
[编辑消息处理程序](../mfc/reference/editing-a-message-handler.md)  
[为反射消息定义消息处理程序](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)  
[声明基于新控件类的变量](../mfc/reference/declaring-a-variable-based-on-your-new-control-class.md)  
[重写虚函数](../ide/overriding-a-virtual-function-visual-cpp.md)