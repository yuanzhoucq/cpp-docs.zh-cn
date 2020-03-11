---
title: 运行时对象模型服务
ms.date: 03/27/2019
helpviewer_keywords:
- run-time object model services macros
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
ms.openlocfilehash: f8b891467d91d0c945b6c59c90dbc49fd7cbcb30
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855253"
---
# <a name="run-time-object-model-services"></a>运行时对象模型服务

类[CObject](../../mfc/reference/cobject-class.md)和[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)封装了多个对象服务，包括访问运行时类信息、序列化和动态对象创建。 所有派生自 `CObject` 的类都继承此功能。

能够访问运行时类信息可让您在运行时确定有关对象的类的信息。 当需要对函数参数进行额外的类型检查以及必须基于对象的类编写专用代码时很有用，能够在运行时确定对象的类很有用。 C++ 语言不直接支持运行时类信息。

序列化是在文件中写入或读取对象内容的过程。 当应用程序退出后，可以使用序列化来存储对象的内容。 对象随后可在应用程序重新启动时从文件中读取。 此类数据对象被称为“永久对象”。

动态对象创建支持在运行时创建指定类的对象。 例如，文档、视图和框架对象必须支持动态创建，因为框架需要以动态方式创建这些内容。

下表列出了支持运行时类信息、序列化和动态创建的 MFC 宏。

有关这些运行时对象服务和序列化的详细信息，请参阅[CObject 类：访问运行时类信息一](../../mfc/accessing-run-time-class-information.md)文。

### <a name="run-time-object-model-services-macros"></a>运行时对象模型服务宏

|||
|-|-|
|[DECLARE_DYNAMIC](#declare_dynamic)|支持访问运行时类信息（必须在类声明中使用）。|
|[DECLARE_DYNCREATE](#declare_dyncreate)|支持动态创建和访问运行时类信息（必须在类声明中使用）。|
|[DECLARE_SERIAL](#declare_serial)|支持序列化和访问运行时类信息（必须在类声明中使用）。|
|[IMPLEMENT_DYNAMIC](#implement_dynamic)|支持访问运行时类信息（必须在类实现中使用）。|
|[IMPLEMENT_DYNCREATE](#implement_dyncreate)|支持动态创建和访问运行时类信息（必须在类实现中使用）。|
|[IMPLEMENT_SERIAL](#implement_serial)|允许序列化和访问运行时类信息（必须在类实现中使用）。|
|[RUNTIME_CLASS](#runtime_class)|返回与命名类对应的 `CRuntimeClass` 结构。|

OLE 通常要求在运行时动态创建对象。 例如，OLE 服务器应用程序必须能够动态创建 OLE 项以响应来自客户端的请求。 同样，自动化服务器必须能够创建项以响应来自自动化客户端的请求。

Microsoft 基础类库提供了两个特定于 OLE 的宏。

### <a name="dynamic-creation-of-ole-objects"></a>OLE 对象的动态创建

|||
|-|-|
|[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)|确定公共控件库是否实现了指定的 API。|
|[AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)|确定公共控件库是否实现了指定的 API。|
|[DECLARE_OLECREATE](#declare_olecreate)|支持通过 OLE 自动化创建对象。|
|[DECLARE_OLECTLTYPE](#declare_olectltype)|声明控件类的 `GetUserTypeNameID` 和 `GetMiscStatus` 成员函数。|
|[DECLARE_PROPPAGEIDS](#declare_proppageids)|声明 OLE 控件提供了一个属性页列表以显示其属性。|
|[IMPLEMENT_OLECREATE](#implement_olecreate)|支持由 OLE 系统创建对象。|
|[IMPLEMENT_OLECTLTYPE](#implement_olectltype)|实现控件类的 `GetUserTypeNameID` 和 `GetMiscStatus` 成员函数。|
|[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)|此宏或[IMPLEMENT_OLECREATE](#implement_olecreate)必须出现在使用 `DECLARE_OLECREATE`的任何类的实现文件中。 |

## <a name="afx_comctl32_if_exists"></a>AFX_COMCTL32_IF_EXISTS

确定公共控件库是否实现了指定的 API。

### <a name="syntax"></a>语法

```
AFX_COMCTL32_IF_EXISTS(  proc );
```

### <a name="parameters"></a>parameters

*proc*<br/>
指向包含函数名的以 null 结尾的字符串的指针，或者指定函数的序号值。 如果此参数是序号值，则它必须在低序位字中；高序位字必须为零。 此参数必须采用 Unicode。

### <a name="remarks"></a>备注

使用此宏确定公共控件库是否为*进程*指定的函数（而不是调用[GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress)）。

### <a name="requirements"></a>要求

afxcomctl32.h，afxcomctl32.inl

## <a name="afx_comctl32_if_exists2"></a>AFX_COMCTL32_IF_EXISTS2

确定公共控件库是否实现指定的 API （这是[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)的 Unicode 版本）。

### <a name="syntax"></a>语法

```
AFX_COMCTL32_IF_EXISTS2( proc );
```

### <a name="parameters"></a>parameters

*proc*<br/>
指向包含函数名的以 null 结尾的字符串的指针，或者指定函数的序号值。 如果此参数是序号值，则它必须在低序位字中；高序位字必须为零。 此参数必须采用 Unicode。

### <a name="remarks"></a>备注

使用此宏确定公共控件库是否为*进程*指定的函数（而不是调用[GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress)）。 此宏是 AFX_COMCTL32_IF_EXISTS 的 Unicode 版本。

### <a name="requirements"></a>要求

afxcomctl32.h，afxcomctl32.inl

##  <a name="declare_dynamic"></a>DECLARE_DYNAMIC

在从 `CObject`派生类时，添加了访问对象类的运行时信息的功能。

```
DECLARE_DYNAMIC(class_name)
```

### <a name="parameters"></a>parameters

*class_name*<br/>
类的实际名称。

### <a name="remarks"></a>备注

将 DECLARE_DYNAMIC 宏添加到类的标头（.h）模块，然后将该模块包含在需要访问此类的对象的所有 .cpp 模块中。

如果使用 DECLARE_ 的动态和 IMPLEMENT_DYNAMIC 宏，则可以使用 RUNTIME_CLASS 宏和 `CObject::IsKindOf` 函数在运行时确定对象的类。

如果 DECLARE_DYNAMIC 包含在类声明中，则 IMPLEMENT_DYNAMIC 必须包含在类实现中。

有关 DECLARE_DYNAMIC 宏的详细信息，请参阅[CObject 类主题](../../mfc/using-cobject.md)。

### <a name="example"></a>示例

请参阅[IMPLEMENT_DYNAMIC](#implement_dynamic)的示例。

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="declare_dyncreate"></a>DECLARE_DYNCREATE

允许在运行时动态创建 `CObject`派生类的对象。

```
DECLARE_DYNCREATE(class_name)
```

### <a name="parameters"></a>parameters

*class_name*<br/>
类的实际名称。

### <a name="remarks"></a>备注

框架使用此功能来动态创建新对象。 例如，打开新文档时创建的新视图。 文档、视图和框架类应支持动态创建，因为框架需要动态创建它们。

在类的 .h 模块中添加 DECLARE_DYNCREATE 宏，然后将该模块包含在需要访问此类的对象的所有 .cpp 模块中。

如果 DECLARE_DYNCREATE 包含在类声明中，则 IMPLEMENT_DYNCREATE 必须包含在类实现中。

有关 DECLARE_DYNCREATE 宏的详细信息，请参阅[CObject 类主题](../../mfc/using-cobject.md)。

> [!NOTE]
>  DECLARE_DYNCREATE 宏包含 DECLARE_DYNAMIC 的所有功能。

### <a name="example"></a>示例

请参阅[IMPLEMENT_DYNCREATE](#implement_dyncreate)的示例。

### <a name="requirements"></a>要求

**标头：** afx.h

## <a name="declare_olectltype"></a>DECLARE_OLECTLTYPE

声明控件类的 `GetUserTypeNameID` 和 `GetMiscStatus` 成员函数。

### <a name="syntax"></a>语法

```
DECLARE_OLECTLTYPE( class_name )
```

### <a name="parameters"></a>parameters

*class_name*<br/>
控件类的名称。

### <a name="remarks"></a>备注

`GetUserTypeNameID` 和 `GetMiscStatus` 是 `COleControl`中声明的纯虚函数。 由于这些函数是纯虚函数，因此必须在控件类中进行重写。 除了 DECLARE_OLECTLTYPE 之外，还必须将 IMPLEMENT_OLECTLTYPE 宏添加到控件类声明中。

### <a name="requirements"></a>要求

**标头：** afxctl。h

## <a name="declare_proppageids"></a>DECLARE_PROPPAGEIDS

声明 OLE 控件提供了一个属性页列表以显示其属性。

### <a name="syntax"></a>语法

```
DECLARE_PROPPAGEIDS( class_name )
```

### <a name="parameters"></a>parameters

*class_name*<br/>
拥有属性页的控件类的名称。

### <a name="remarks"></a>备注

在类声明的末尾使用 `DECLARE_PROPPAGEIDS` 宏。 然后，在定义类的成员函数的 .cpp 文件中，使用 `BEGIN_PROPPAGEIDS` 宏、控件的每个属性页的宏项和 `END_PROPPAGEIDS` 宏来声明属性页列表的末尾。

有关属性页的详细信息，请参阅文章[ActiveX 控件：属性页](../mfc-activex-controls-property-pages.md)。

### <a name="requirements"></a>要求

**标头：** afxctl。h

##  <a name="declare_serial"></a>DECLARE_SERIAL

生成可C++序列化的 `CObject`派生类所必需的标头代码。

```
DECLARE_SERIAL(class_name)
```

### <a name="parameters"></a>parameters

*class_name*<br/>
类的实际名称。

### <a name="remarks"></a>备注

序列化是指将对象的内容写入文件或从文件中读取对象的过程。

使用 .h 模块中的 DECLARE_SERIAL 宏，然后将该模块包含在需要访问此类的对象的所有 .cpp 模块中。

如果 DECLARE_SERIAL 包含在类声明中，则 IMPLEMENT_SERIAL 必须包含在类实现中。

DECLARE_SERIAL 宏包含 DECLARE_DYNAMIC 和 DECLARE_DYNCREATE 的所有功能。

您可以使用 AFX_API 宏为使用 DECLARE_SERIAL 和 IMPLEMENT_SERIAL 宏的类自动导出 `CArchive` 提取运算符。 用下面的代码将类声明（位于 .h 文件中）括起来：

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

有关 DECLARE_SERIAL 宏的详细信息，请参阅[CObject 类主题](../../mfc/using-cobject.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCObjectSample#21](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="implement_dynamic"></a>IMPLEMENT_DYNAMIC

使用对C++类名称和层次结构内位置的运行时访问，生成动态 `CObject`派生的类所需的代码。

```
IMPLEMENT_DYNAMIC(class_name, base_class_name)
```

### <a name="parameters"></a>parameters

*class_name*<br/>
类的实际名称。

*base_class_name*<br/>
基类的名称。

### <a name="remarks"></a>备注

在 .cpp 模块中使用 IMPLEMENT_DYNAMIC 宏，然后仅将生成的对象代码链接一次。

有关详细信息，请参阅[CObject 类主题](../../mfc/using-cobject.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCObjectSample#2](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]

[!code-cpp[NVC_MFCCObjectSample#3](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="implement_dyncreate"></a>IMPLEMENT_DYNCREATE

当与 DECLARE_DYNCREATE 宏一起使用时，允许在运行时动态创建 `CObject`派生类的对象。

```
IMPLEMENT_DYNCREATE(class_name, base_class_name)
```

### <a name="parameters"></a>parameters

*class_name*<br/>
类的实际名称。

*base_class_name*<br/>
基类的实际名称。

### <a name="remarks"></a>备注

此框架使用此功能来动态创建新对象，例如，在序列化期间从磁盘读取对象时。 将 IMPLEMENT_DYNCREATE 宏添加到类实现文件中。 有关详细信息，请参阅[CObject 类主题](../../mfc/using-cobject.md)。

如果使用 DECLARE_DYNCREATE 和 IMPLEMENT_DYNCREATE 宏，则可以使用 RUNTIME_CLASS 宏和 `CObject::IsKindOf` 成员函数在运行时确定对象的类。

如果 DECLARE_DYNCREATE 包含在类声明中，则 IMPLEMENT_DYNCREATE 必须包含在类实现中。

请注意，此宏定义将调用类的默认构造函数。 如果类显式实现了一个非常简单的构造函数，则它也必须显式实现默认构造函数。 可以将默认构造函数添加到类的**私有**或**受保护**成员节中，以防止在类实现外部调用它。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCObjectSample#22](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]

[!code-cpp[NVC_MFCCObjectSample#23](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]

### <a name="requirements"></a>要求

**标头：** afx.h

## <a name="implement_olecreate_flags"></a>IMPLEMENT_OLECREATE_FLAGS

此宏或[IMPLEMENT_OLECREATE](#implement_olecreate)必须出现在使用 DECLARE_OLECREATE 的任何类的实现文件中。

### <a name="syntax"></a>语法

```
IMPLEMENT_OLECREATE_FLAGS( class_name, external_name, nFlags,
    l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>parameters

*class_name*<br/>
类的实际名称。

*external_name*<br/>
向其他应用程序公开的对象名称（用引号引起来）。

*nFlags*<br/>
包含一个或多个以下标志：

   - `afxRegInsertable` 允许控件显示在 OLE 对象的 "插入对象" 对话框中。
   - `afxRegApartmentThreading` 将注册表中的线程模型设置为 ThreadingModel = 单元。
   - `afxRegFreeThreading` 将注册表中的线程模型设置为 ThreadingModel = Free。

         You can combine the two flags `afxRegApartmentThreading` and `afxRegFreeThreading` to set ThreadingModel=Both. See [InprocServer32](/windows/win32/com/inprocserver32) in the Windows SDK for more information on threading model registration.

*l*， *w1*， *w2*， *b1*， *b2*， *b3*， *b4*， *b5*， *b6*， *b7*， *b8* Components 类的 CLSID。

### <a name="remarks"></a>备注

> [!NOTE]
>  如果使用 IMPLEMENT_OLECREATE_FLAGS，则可以使用*nFlags*参数指定对象支持的线程模型。 如果只想支持单一 treading 模型，请使用 IMPLEMENT_OLECREATE。

外部名称是向其他应用程序公开的标识符。 客户端应用程序使用外部名称从自动化服务器请求此类的对象。

OLE 类 ID 是对象的唯一128位标识符。 它由 "语法说明" 中的 " *l*"、 **"** *w1*"、" *w2*" 和 " *b1*到*b8* " 表示 应用程序向导和代码向导会根据需要为您创建唯一的 OLE 类 Id。

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="implement_olectltype"></a>IMPLEMENT_OLECTLTYPE

实现控件类的 `GetUserTypeNameID` 和 `GetMiscStatus` 成员函数。

### <a name="syntax"></a>语法

```
DECLARE_OLECTLTYPE( class_name, idsUserTypeName, dwOleMisc )
```

### <a name="parameters"></a>parameters

*class_name*<br/>
控件类的名称。

*idsUserTypeName*<br/>
包含控件外部名称的字符串的资源 ID。

*dwOleMisc*<br/>
包含一个或多个标志的枚举。 有关此枚举的详细信息，请参阅 Windows SDK 中的[OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) 。

### <a name="remarks"></a>备注

除了 IMPLEMENT_OLECTLTYPE 之外，还必须将 DECLARE_OLECTLTYPE 宏添加到控件类声明中。

`GetUserTypeNameID` 成员函数返回标识控件类的资源字符串。 `GetMiscStatus` 返回控件的 OLEMISC 位。 此枚举指定描述控件的其他特征的设置集合。 有关 OLEMISC 设置的完整说明，请参阅 "Windows SDK 中的" [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) "。

> [!NOTE]
>  ActiveX ControlWizard 使用的默认设置是： OLEMISC_ACTIVATEWHENVISIBLE、OLEMISC_SETCLIENTSITEFIRST、OLEMISC_INSIDEOUT、OLEMISC_CANTLINKINSIDE 和 OLEMISC_RECOMPOSEONRESIZE。

### <a name="requirements"></a>要求

**标头：** afxctl。h

##  <a name="implement_serial"></a>IMPLEMENT_SERIAL

使用对C++类名称和层次结构内位置的运行时访问，生成动态 `CObject`派生的类所需的代码。

```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)
```

### <a name="parameters"></a>parameters

*class_name*<br/>
类的实际名称。

*base_class_name*<br/>
基类的名称。

*wSchema*<br/>
UINT "版本号"，将在存档中进行编码，以使反序列化程序能够识别和处理早期程序版本创建的数据。 类架构编号不得为-1。

### <a name="remarks"></a>备注

在 .cpp 模块中使用 IMPLEMENT_SERIAL 宏;然后，仅将生成的对象代码链接一次。

您可以使用 AFX_API 宏为使用 DECLARE_SERIAL 和 IMPLEMENT_SERIAL 宏的类自动导出 `CArchive` 提取运算符。 用下面的代码将类声明（位于 .h 文件中）括起来：

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

有关详细信息，请参阅[CObject 类主题](../../mfc/using-cobject.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCObjectSample#24](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="runtime_class"></a>RUNTIME_CLASS

从C++类的名称获取运行时类结构。

```
RUNTIME_CLASS(class_name)
```

### <a name="parameters"></a>parameters

*class_name*<br/>
类的实际名称（不用引号引起来）。

### <a name="remarks"></a>备注

RUNTIME_CLASS 返回指向*class_name*指定的类的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)结构的指针。 仅 `CObject`使用 DECLARE_DYNAMIC、DECLARE_DYNCREATE 或 DECLARE_SERIAL 声明的派生类将返回指向 `CRuntimeClass` 结构的指针。

有关详细信息，请参阅[CObject 类主题](../../mfc/using-cobject.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCObjectSample#25](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="declare_olecreate"></a>DECLARE_OLECREATE

启用通过 OLE 自动化创建 `CCmdTarget`派生类的对象。

```
DECLARE_OLECREATE(class_name)
```

### <a name="parameters"></a>parameters

*class_name*<br/>
类的实际名称。

### <a name="remarks"></a>备注

此宏使其他启用 OLE 的应用程序能够创建此类型的对象。

在类的 .h 模块中添加 DECLARE_OLECREATE 宏，然后将该模块包含在需要访问此类的对象的所有 .cpp 模块中。

如果 DECLARE_OLECREATE 包含在类声明中，则 IMPLEMENT_OLECREATE 必须包含在类实现中。 使用 DECLARE_OLECREATE 的类声明还必须使用 DECLARE_DYNCREATE 或 DECLARE_SERIAL。

### <a name="requirements"></a>要求

**标头**： afxdisp.h&gt

##  <a name="implement_olecreate"></a>IMPLEMENT_OLECREATE

此宏或[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)必须出现在使用 `DECLARE_OLECREATE`的任何类的实现文件中。

```
IMPLEMENT_OLECREATE(class_name, external_name, l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>parameters

*class_name*<br/>
类的实际名称。

*external_name*<br/>
向其他应用程序公开的对象名称（用引号引起来）。

*l*， *w1*， *w2*， *b1*， *b2*， *b3*， *b4*， *b5*， *b6*， *b7*， *b8* Components 类的 CLSID。

### <a name="remarks"></a>备注

> [!NOTE]
>  如果使用 IMPLEMENT_OLECREATE，则默认情况下仅支持单线程模型。 如果使用 IMPLEMENT_OLECREATE_FLAGS，则可以使用*nFlags*参数指定对象支持的线程模型。

外部名称是向其他应用程序公开的标识符。 客户端应用程序使用外部名称从自动化服务器请求此类的对象。

OLE 类 ID 是对象的唯一128位标识符。 它由 "语法说明" 中的 " *l*"、 **"** *w1*"、" *w2*" 和 " *b1*到*b8* " 表示 应用程序向导和代码向导会根据需要为您创建唯一的 OLE 类 Id。

### <a name="requirements"></a>要求

**标头**： afxdisp.h&gt

## <a name="see-also"></a>另请参阅

[宏和全局](mfc-macros-and-globals.md)<br/>
[隔离 MFC 公用控件库](../isolation-of-the-mfc-common-controls-library.md)<br/>
[CLSID 密钥](/windows/win32/com/clsid-key-hklm)
