---
title: 添加属性
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.prop.overview
- vc.codewiz.prop.idlattributes
helpviewer_keywords:
- interfaces, adding properties
- properties [C++], adding to interfaces
- names, add property wizard
- IDL attributes, add property wizard
- stock properties, about stock properties
- stock properties
ms.assetid: 37bd4db7-efd3-4faa-87ad-64902ed16a36
ms.openlocfilehash: 5c472b74fee690c0cf33f78eca9e2e8462930eb8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509526"
---
# <a name="add-a-property"></a>添加属性

可以使用[添加属性向导](#names-add-property-wizard)，向项目中的接口添加方法。

**向对象添加属性：**

1. 在[类视图](/visualstudio/ide/viewing-the-structure-of-code)中单击要向其添加属性的接口的名称。

   > [!NOTE]
   > 也可以将属性添加到调度接口，它嵌套在库节点中（除非该项目已特性化）。

1. 从快捷菜单中，选择“添加”，然后选择“添加属性”   。

1. 在[添加属性向导](#names-add-property-wizard)中，提供创建属性的信息。

1. 在向导的 [IDL 特性](#idl-attributes-add-property-wizard)页中，为此属性指定任何接口定义语言 (IDL) 设置。

1. 选择“完成”以添加属性  。

属性的 `Get` 和 `Put` 方法在类视图中定义该属性的接口下显示为两个图标。 可以双击其中任一图标，查看 .idl 文件中的属性声明。

- 对于 ATL 接口，`Get` 和 `Put` 函数已添加到 .cpp 文件，并且对这些函数的引用已添加到 .h 文件。

- 对于 MFC 调度接口，如果选择“成员变量”作为实现类型，则方法和变量将添加到实现它的类中  。 如果选择 Get/Set 方法作为实现类型，则两个方法将添加到实现它的类中  。

## <a name="in-this-section"></a>本节内容

- [名称，添加属性向导](#names-add-property-wizard)
- [IDL 特性，添加属性向导](#idl-attributes-add-property-wizard)
- [常用属性](#stock-properties)

## <a name="names-add-property-wizard"></a>名称，添加属性向导

使用此向导将属性添加到接口。

- **属性类型**

  设置要添加的属性类型。 对于 MFC 调度接口，请提供自己的类型或从预定义列表中进行选择。 如果提供属性的常用实现，则“属性类型”设为常用类型且不可更改  。

- **属性名称**

  设置属性的名称。 对于与 ActiveX 控件关联的 MFC 调度接口，可以提供自己的名称，也可以从预定义列表中选择常用属性名称。 如果提供自己的属性名称，则常用实现类型不可用  。 请参阅[常用属性](#stock-properties)获取列表中属性的说明。

  |接口类型|说明|
  |--------------------|-----------------|
  |ATL 双重接口、自定义接口和本地自定义接口|提供属性名称。|
  |MFC 调度接口，MFC ActiveX 控件调度接口|提供属性名称或从列表中选择常用属性。 如果从列表中选择属性，则相应的值出现在“属性类型”框中  。 可以更改此类型，具体取决于在“实现类型”下的选择  。|

- **返回类型**

  仅 ATL 接口。 设置属性的返回类型。 对于双重接口，`HRESULT` 始终为返回类型，并且此框不可用。 对于自定义接口，可以从列表中选择返回类型。 仍建议使用 `HRESULT`，因为它提供返回错误的标准方式。

- **变量名**

  仅 MFC 调度接口。 仅当在“实现类型”下指定了“成员变量”时才可用   。 设置与属性关联的成员变量的名称。 默认情况下，变量名称设置为 `m_`PropertyName  。 可以编辑此名称。

- **通知函数**

  仅 MFC 调度接口。 仅当在“实现类型”下指定了“成员变量”时才可用   。 如果属性更改，请设置调用的通知函数的名称。 默认情况下，通知函数的名称设置为 `On`PropertyName`Changed`  。 可以编辑此名称。

- **Get 函数**

  对于 MFC 调度接口。 仅当在“实现类型”下指定了“Get/Set 方法”时才可用   。 设置函数名称以获取属性。 默认情况下，`Get` 函数的名称设置为 `Get`PropertyName  。 可以编辑此名称。 如果删除此名称，则函数 [GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported) 插入接口调度映射。 `Get`PropertyName 函数指定该属性可读  。

- **设置函数**

  仅 MFC 调度接口。 仅当在“实现类型”下指定了“Get/Set 方法”时才可用   。 设置函数名称以设置属性。 默认情况下，`Set` 函数的名称设置为 `Set`PropertyName  。 可以编辑此名称。 如果删除此名称，则函数 [SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported) 插入接口调度映射。 `Set`PropertyName 函数指定该属性可写入  。

- **实现类型**

  仅 MFC 调度接口。 指定如何实现要添加的属性。

  |实现类型|说明|
  |-------------------------|-----------------|
  |**常用**|指定在属性名称中选择的属性的常用实现  。 默认值。 有关详细信息，请参阅[常用属性](#stock-properties)。<br /><br /> 如果指定“常用”，则“属性类型”、“参数类型”和“参数名称”都会变暗     。|
  |**成员变量**|指定属性添加为成员变量。 可以将自定义属性或大多数常用属性添加为成员变量。 无法为 `Caption`、`hWnd` 和 `Text` 属性指定成员变量  。<br /><br /> 在变量名称和通知函数下提供默认名称   。 可以编辑此名称。|
  |**Get/Set 方法**|指定该属性默认添加为 `Get`PropertyName 和 `Set`PropertyName 函数   。 这些名称显示在 Get 函数和 Set 函数下   。<br /><br /> 可以更改用于传递 Get 函数值的默认属性类型  。 可为 `Get` 和 `Set` 函数指定参数。|

- **Get 函数**

  对于 ATL 接口。 将属性设置为可读；也就是说，它会创建 `Get` 方法，以便从对象中检索此属性。 选择“Get”、“Put”或同时选择两者   。

- **Put 函数**

  仅 ATL 接口。 将此属性设为可写入，也就是说，它会创建 `Put` 方法，以便设置或“放置”对象的此属性。 选择“Get”、“Put”或同时选择两者   。 如果选择此选项，则可以从以下两种方式中进行选择，以实现此方法：

  |选项|说明|
  |------------|-----------------|
  |**PropPut**|[PropPut](../windows/propput.md) 函数返回对象的一个副本。 这是使属性可写入的默认方法，也是最常用的方法。|
  |**PropPutRef**|[PropPutRef](../windows/propputref.md) 函数返回对对象的引用，而不是返回对象本身的副本。 考虑将这个选项用于可能具有初始化开销的对象，如大型结构或数组。|

- **参数属性**

  仅 ATL 接口。 设置“参数名称”指定的参数是 `in`、`out`、两者都是或两者都不是  。

  |选项|说明|
  |------------|-----------------|
  |`in`|指示参数将从调用过程传递到被调用过程。|
  |`out`|指示从被调用过程返回到调用过程（从服务器到客户端）的指针参数。|

- **参数类型**

  设置参数的数据类型。 从列表中选择类型。

- **参数名称**

  如果属性具有参数，则设置要为属性添加的参数的名称。 选择“添加”后，参数名称随即显示在“参数列表”中   。

- **参数列表**

  显示要添加到属性的特性列表。 列表中的每个项都包含参数名称、参数类型和属性。 可使用“添加”和“删除”更新此列表   。

- **添加**

  将在“参数名称”和“参数类型”中指定的参数添加到“参数列表”    。 选择“添加”可向列表添加参数  。

- **移除**

  删除在“参数列表”中选择的参数  。

- **默认属性**

  仅 MFC 调度接口。 将此属性设置为接口的默认属性。 一个接口只能有一个默认属性；指定了默认属性后，对于添加到接口的任何其他属性，此框均不可用。

## <a name="idl-attributes-add-property-wizard"></a>IDL 特性，添加属性向导

使用“添加属性向导”的此页面来指定属性的任何接口定义语言 (IDL) 设置。

- `id`

  设置标识属性的数字 ID。 此选项不适用于自定义接口的属性。 请参阅 MIDL 引用中的 [ID](/windows/win32/Midl/id)  。

- `helpcontext`

  指定一个上下文 ID，使用户在帮助文件中查看关于此属性的信息。 请参阅 MIDL 引用中的 [helpcontext](/windows/win32/Midl/helpcontext)  。

- `helpstring`

  指定一个字符串，用于描述该字符串适用的元素。 默认情况下，会将它设置为 `property`&nbsp; 属性 &nbsp; 名称  。 请参阅 MIDL 引用中的 [helpstring](/windows/win32/Midl/helpstring)  。

### <a name="other-options"></a>其他选项

并非所有选项都适用于所有属性类型。

|选项|说明|
|------------|-----------------|
|`bindable`|指示该属性支持数据绑定。 请参阅 MIDL 引用中的 [bindable](/windows/win32/Midl/bindable)  。 对于该属性的常用实现，此选项已默认设置，且不可更改。|
|`defaultbind`|指示此单一、可绑定属性最好地表示了该对象。 请参阅 MIDL 引用中的 [defaultbind](/windows/win32/Midl/defaultbind)  。|
|`displaybind`|指示应作为可绑定属性显示给用户的属性。 请参阅 MIDL 引用中的 [displaybind](/windows/win32/Midl/displaybind)  。|
|`immediatebind`|指示将立即通知数据库对数据绑定对象的此属性所做的所有更改。 请参阅 MIDL 引用中的 [immediatebind](/windows/win32/Midl/immediatebind)  。|
|`defaultcollelem`|指示该属性是默认集合的某个元素的访问器函数。 请参阅 MIDL 引用中的 [defaultcollelem](/windows/win32/Midl/defaultcollelem)  。|
|`nonbrowsable`|标记不应显示在属性浏览器中的接口或调度接口成员。 请参阅 MIDL 引用中的 [nonbrowsable](/windows/win32/Midl/nonbrowsable)  。|
|`requestedit`|指示该属性支持 `OnRequestEdit` 通知。 请参阅 MIDL 参考中的 [requestedit](/windows/win32/Midl/requestedit)  。 对于该属性的常用实现，此选项已默认设置，且不可更改。|
|`source`|指示该属性的成员是事件的源。 请参阅 MIDL 引用中的 [source](/windows/win32/Midl/source)  。|
|`hidden`|指示该属性存在，但不应在面向用户的浏览器中显示。 请参阅 MIDL 引用中的 [hidden](/windows/win32/Midl/hidden)  。|
|`restricted`|指定此属性不能任意调用。 请参阅 MIDL 引用中的 [restricted](/windows/win32/Midl/restricted)  。|
|`local`|向 MIDL 编译器指出该属性不是远程的。 请参阅 MIDL 引用中的 [local](/windows/win32/Midl/local)  。|

## <a name="stock-properties"></a>常用属性

如果使用[添加属性向导](#idl-attributes-add-property-wizard)将属性添加到 MFC 调度接口，则可从向导[名称](../ide/names-add-property-wizard.md)页的“属性名”列表中选择常用属性  。 这些属性如下所示：

|属性名称|说明|
|-------------------|-----------------|
|`Appearance`|退回或设置确定控件外观的值。 控件的 `Appearance` 属性可以包含或省略三维显示效果。 此属性是环境读取/写入属性。|
|`BackColor`|返回控件的环境 `BackColor` 属性，或将其设置为调色板 (RGB) 颜色或预定义的系统颜色。 默认情况下，其值对应于控件容器的前景色。 此属性是环境读取/写入属性。|
|`BorderStyle`|返回或设置控件的边框样式。 此属性是读取/写入属性。|
|`Caption`|返回或设置控件的 `Caption` 属性。 标题是窗口的标题。 `Caption` 未包含“成员变量”实现类型  。|
|`Enabled`|返回或设置控件的 `Enabled` 属性。 已启用的控件可响应用户生成的事件。|
|`Font`|返回或设置控件的环境字体。 如果控件没有字体，则为 NULL。|
|`ForeColor`|返回或设置控件的环境 `ForeColor` 属性。|
|`hWnd`|返回或设置控件的 `hWnd` 属性。 `hWnd` 未包含“成员变量”实现类型  。|
|`ReadyState`|返回或设置控件的 `ReadyState` 属性。 控件可以取消初始化或进行初始化，也可以是正在加载，或者是交互的或完整的。 有关详细信息，请参阅 Internet SDK 中的 [READYSTATE](/previous-versions//aa768362\(v=vs.85\))  。|
|`Text`|返回或设置控件中包含的文本。 `Text` 未包含“成员变量”实现类型  。|
