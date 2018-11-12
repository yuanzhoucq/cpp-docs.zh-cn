---
title: IDL 特性，添加方法向导
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.method.idlattrib
helpviewer_keywords:
- Add Method Wizard [C++]
- IDL attributes, Add Method Wizard
ms.assetid: f80c3bc1-b515-4d6c-83ee-98c2c21ba902
ms.openlocfilehash: 073f821d7db0733c89c21ed4b2a85014aa151244
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615782"
---
# <a name="idl-attributes-add-method-wizard"></a>IDL 特性，添加方法向导

使用“添加方法向导”的此页为方法指定任何接口定义语言 (IDL) 设置。

- **id**

   设置标识方法的数字 ID。 请参阅 MIDL 引用中的 [ID](/windows/desktop/Midl/id)。

   此框不可用于自定义接口和 MFC 调度接口。

- **call_as**

   指定此本地方法可映射到的远程方法的名称。 请参阅 MIDL 引用中的 [call_as](/windows/desktop/Midl/call-as)。

   不可用于 MFC 调度接口。

- **helpcontext**

   指定一个上下文 ID，让用户可以在帮助文件中查看此方法的相关信息。 请参阅 MIDL 引用中的 [helpcontext](/windows/desktop/Midl/helpcontext)。

   不可用于 MFC 调度接口。

- **helpstring**

   指定一个字符串，用于描述应用该字符串的元素。 默认情况下，该字符串设置为“method Method name”。 请参阅 MIDL 引用中的 [helpstring](/windows/desktop/Midl/helpstring)。

   不可用于 MFC 调度接口。

- **附加特性**

   不可用于 MFC 调度接口。

   |特性|描述|
   |---------------|-----------------|
   |**hidden**|指示该方法虽然存在，但不应在面向用户的浏览器中显示。 请参阅 MIDL 引用中的 [hidden](/windows/desktop/Midl/hidden)。|
   |**source**|指示方法的一个成员是事件源。 请参阅 MIDL 引用中的 [source](/windows/desktop/Midl/source)。|
   |`local`|向 MIDL 编译器指出该方法不是远程的。 请参阅 MIDL 引用中的 [local](/windows/desktop/Midl/local)。|
   |**restricted**|指定此方法不能任意调用。 请参阅 MIDL 引用中的 [restricted](/windows/desktop/Midl/restricted)。|
   |**vararg**|指定方法采用的参数数目可变。 为了实现这一点，最后一个参数必须是包含所有剩余参数的 VARIANT 类型的安全数组。 请参阅 MIDL 引用中的 [vararg](/windows/desktop/Midl/vararg)。|

## <a name="see-also"></a>请参阅

[添加方法](../ide/adding-a-method-visual-cpp.md)<br>
[添加方法向导](../ide/add-method-wizard.md)