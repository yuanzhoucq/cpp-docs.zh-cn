---
title: “添加属性向导”->“名称”| Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.prop.overview
dev_langs:
- C++
ms.assetid: 0453b7ea-89cb-41a1-80a2-d45f61589c0a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 17c3fd5cfc86f76fcdc1c301bd92bb1fdfac3b9c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339561"
---
# <a name="names-add-property-wizard"></a>“添加属性向导”->“名称”
使用此向导将属性添加到接口。  
  
 **属性类型**  
 设置要添加的属性类型。 对于 MFC 调度接口，请提供自己的类型或从预定义列表中进行选择。 如果提供属性的常用实现，则“属性类型”设为常用类型且不可更改。  
  
 **属性名称**  
 设置属性的名称。 对于与 ActiveX 控件关联的 MFC 调度接口，可以提供自己的名称，也可以从预定义列表中选择常用属性名称。 如果提供自己的属性名称，则常用实现类型不可用。 请参阅[常用属性](../ide/stock-properties.md)了解列表中的属性。  
  
|接口类型|描述|  
|--------------------|-----------------|  
|ATL 双重接口、自定义接口和本地自定义接口|提供属性名称。|  
|MFC 调度接口，MFC ActiveX 控件调度接口|提供属性名称或从列表中选择常用属性。 如果从列表中选择属性，则相应的值出现在“属性类型”框中。 可以更改此类型，具体取决于在“实现类型”下的选择。|  
  
 **返回类型**  
 仅 ATL 接口。 设置属性的返回类型。 对于双重接口，`HRESULT` 始终为返回类型，并且此框不可用。 对于自定义接口，可以从列表中选择返回类型。 仍建议使用 `HRESULT`，因为它提供返回错误的标准方式。  
  
 **变量名**  
 仅 MFC 调度接口。 仅当在“实现类型”下指定了“成员变量”时才可用。 设置与属性关联的成员变量的名称。 默认情况下，变量名称设置为 m_PropertyName。 可以编辑此名称。  
  
 **通知函数**  
 仅 MFC 调度接口。 仅当在“实现类型”下指定了“成员变量”时才可用。 如果属性更改，请设置调用的通知函数的名称。 默认情况下，如果更改则将通知函数的名称设置为 OnPropertyNameChanged。 可以编辑此名称。  
  
 **Get 函数**  
 对于 MFC 调度接口。 仅当在“实现类型”下指定了“Get/Set 方法”时才可用。 设置函数名称以获取属性。 默认情况下，Get 函数的名称设置为 GetPropertyName。 可以编辑此名称。 如果删除此名称，则函数 [GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported) 插入接口调度映射。 Get PropertyName 函数将属性指定为可读。  
  
 **设置函数**  
 仅 MFC 调度接口。 仅当在“实现类型”下指定了“Get/Set 方法”时才可用。 设置函数名称以设置属性。 默认情况下，Set 函数的名称设置为 SetPropertyName。 可以编辑此名称。 如果删除此名称，则函数 [SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported) 插入接口调度映射。 SetPropertyName 函数指定属性可写入。  
  
 **实现类型**  
 仅 MFC 调度接口。 指定如何实现要添加的属性。  
  
|实现类型|描述|  
|-------------------------|-----------------|  
|**常用**|指定在属性名称中选择的属性的常用实现。 默认值。 有关详细信息，请参阅[常用属性](../ide/stock-properties.md)。<br /><br /> 如果指定“常用”，则“属性类型”、“参数类型”和“参数名称”都会变暗。|  
|**成员变量**|指定属性添加为成员变量。 可以将自定义属性或大多数常用属性添加为成员变量。 无法为 Caption、hWnd 和 Text 属性 指定成员变量。<br /><br /> 在变量名称和通知函数下提供默认名称。 可以编辑此名称。|  
|**Get/Set 方法**|指定属性默认添加为 GetPropertyName 和 SetPropertyName 函数。 这些名称显示在 Get 函数和 Set 函数下。<br /><br /> 可以更改用于传递 Get 函数值的默认属性类型。 可以指定 Get 和 `Set` 函数的参数。|  
  
 **Get 函数**  
 对于 ATL 接口。 将属性设置为可读；也就是说，它会创建 Get 方法，以便从对象中检索此属性。 必须选择“Get”和/或“`Put`”。  
  
 **Put 函数**  
 仅 ATL 接口。 将此属性设为可写入，也就是说，它会创建 `Put` 方法，以便设置或“放置”对象的此属性。 必须选择“Get”和/或“`Put`”。 如果选择此选项，则可以从以下两种方式中进行选择，以实现此方法：  
  
|选项|描述|  
|------------|-----------------|  
|**PropPut**|[PropPut](../windows/propput.md) 函数返回对象的一个副本。 这是使属性可写入的默认方法，也是最常用的方法。|  
|**PropPutRef**|[PropPutRef](../windows/propputref.md) 函数返回对对象的引用，而不是返回对象本身的副本。 考虑将这个选项用于可能具有初始化开销的对象，如大型结构或数组。|  
  
 **参数属性**  
 仅 ATL 接口。 设置参数名称指定的参数设置是“in”、“out”、两者都是，还是两者都不是。  
  
|选项|描述|  
|------------|-----------------|  
|**in**|指示参数将从调用过程传递到被调用过程。|  
|**out**|指示从被调用过程返回到调用过程（从服务器到客户端）的指针参数。|  
  
 **参数类型**  
 设置参数的数据类型。 从列表中选择类型。  
  
 **参数名称**  
 如果属性具有参数，则设置要为属性添加的参数的名称。 单击“添加”后，参数名称随即显示在“参数列表”中。  
  
 **参数列表**  
 显示要添加到属性的特性列表。 列表中的每个项都包含参数名称、参数类型和属性。 可使用“添加”和“删除”更新此列表。  
  
 **添加**  
 将在“参数名称”和“参数类型”中指定的参数添加到“参数列表”。 必须单击“添加”才能将参数添加到列表中。  
  
 **移除**  
 删除在“参数列表”中选择的参数。  
  
 **默认属性**  
 仅 MFC 调度接口。 将此属性设置为接口的默认属性。 一个接口只能有一个默认属性；指定了默认属性后，对于添加到接口的任何其他属性，此框均不可用。  
  
## <a name="see-also"></a>请参阅  
 [添加属性](../ide/adding-a-property-visual-cpp.md)   
 [“添加属性向导”->“IDL 特性”](../ide/idl-attributes-add-property-wizard.md)   
 [实现接口](../ide/implementing-an-interface-visual-cpp.md)