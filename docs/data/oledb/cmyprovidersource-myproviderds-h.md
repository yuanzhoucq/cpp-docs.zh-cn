---
title: CCustomSource (CustomDS.H) |Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- myproviderds.h
- cmyprovidersource
- customds.h
- ccustomsource
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderSource class in MyProviderDS.H
- CCustomSource class in CustomDS.H
ms.assetid: c143d48e-59c8-4f67-9141-3aab51859b92
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bcabecde8f299e878ec6498dada503a894c406b4
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50081126"
---
# <a name="ccustomsource-customdsh"></a>CCustomSource (CustomDS.h)

提供程序类使用多重继承。 下面的代码显示了数据源对象的继承链：

```cpp
/////////////////////////////////////////////////////////////////////////
// CCustomSource
class ATL_NO_VTABLE CCustomSource :
   public CComObjectRootEx<CComSingleThreadModel>,
   public CComCoClass<CCustomSource, &CLSID_Custom>,
   public IDBCreateSessionImpl<CCustomSource, CCustomSession>,
   public IDBInitializeImpl<CCustomSource>,
   public IDBPropertiesImpl<CCustomSource>,
   public IPersistImpl<CCustomSource>,
   public IInternalConnectionImpl<CCustomSource>
```

所有 COM 组件均都派生自`CComObjectRootEx`和`CComCoClass`。 `CComObjectRootEx` 提供所有实现`IUnknown`接口。 它可以处理任何线程模型。 `CComCoClass` 处理所需的任何错误支持。 如果你想要将更丰富的错误信息发送到客户端，则可以使用一些错误 Api 中`CComCoClass`。

数据源对象还从多个 Impl 类继承。 每个类提供了一个接口的实现。 数据源对象实现`IPersist`， `IDBProperties`， `IDBInitialize`，和`IDBCreateSession`接口。 OLE DB 要求每个接口来实现数据源对象。 您可以选择支持或通过继承或不继承自其中一个 Impl 类的支持特定功能。 如果你想要支持`IDBDataSourceAdmin`从继承的接口，`IDBDataSourceAdminImpl`类，以获取所需的功能。

## <a name="com-map"></a>COM 映射

每当客户端调用`QueryInterface`对于数据源上的接口，它将经历以下 COM 映射：

```cpp
BEGIN_COM_MAP(CCustomSource)
   COM_INTERFACE_ENTRY(IDBCreateSession)
   COM_INTERFACE_ENTRY(IDBInitialize)
   COM_INTERFACE_ENTRY(IDBProperties)
   COM_INTERFACE_ENTRY(IPersist)
   COM_INTERFACE_ENTRY(IInternalConnection)
END_COM_MAP()
```

COM_INTERFACE_ENTRY 宏来自 ATL 和告诉的实现`QueryInterface`在`CComObjectRootEx`返回相应的接口。

## <a name="property-map"></a>属性映射

属性映射指定提供程序指定的所有属性：

```cpp
BEGIN_PROPSET_MAP(CCustomSource)
   BEGIN_PROPERTY_SET(DBPROPSET_DATASOURCEINFO)
      PROPERTY_INFO_ENTRY(ACTIVESESSIONS)
      PROPERTY_INFO_ENTRY(ASYNCTXNABORT)
      PROPERTY_INFO_ENTRY(ASYNCTXNCOMMIT)
      PROPERTY_INFO_ENTRY(BYREFACCESSORS)
      PROPERTY_INFO_ENTRY_VALUE(CATALOGLOCATION, DBPROPVAL_CL_START)
      PROPERTY_INFO_ENTRY(CATALOGTERM)
      PROPERTY_INFO_ENTRY(CATALOGUSAGE)
      PROPERTY_INFO_ENTRY(COLUMNDEFINITION)
      PROPERTY_INFO_ENTRY(CONCATNULLBEHAVIOR)
      PROPERTY_INFO_ENTRY(DATASOURCENAME)
      PROPERTY_INFO_ENTRY(DATASOURCEREADONLY)
      PROPERTY_INFO_ENTRY(DBMSNAME)
      PROPERTY_INFO_ENTRY(DBMSVER)
      PROPERTY_INFO_ENTRY_VALUE(DSOTHREADMODEL, DBPROPVAL_RT_FREETHREAD)
      PROPERTY_INFO_ENTRY(GROUPBY)
      PROPERTY_INFO_ENTRY(HETEROGENEOUSTABLES)
      PROPERTY_INFO_ENTRY(IDENTIFIERCASE)
      PROPERTY_INFO_ENTRY(MAXINDEXSIZE)
      PROPERTY_INFO_ENTRY(MAXROWSIZE)
      PROPERTY_INFO_ENTRY(MAXROWSIZEINCLUDESBLOB)
      PROPERTY_INFO_ENTRY(MAXTABLESINSELECT)
      PROPERTY_INFO_ENTRY(MULTIPLEPARAMSETS)
      PROPERTY_INFO_ENTRY(MULTIPLERESULTS)
      PROPERTY_INFO_ENTRY(MULTIPLESTORAGEOBJECTS)
      PROPERTY_INFO_ENTRY(MULTITABLEUPDATE)
      PROPERTY_INFO_ENTRY(NULLCOLLATION)
      PROPERTY_INFO_ENTRY(OLEOBJECTS)
      PROPERTY_INFO_ENTRY(ORDERBYCOLUMNSINSELECT)
      PROPERTY_INFO_ENTRY(OUTPUTPARAMETERAVAILABILITY)
      PROPERTY_INFO_ENTRY(PERSISTENTIDTYPE)
      PROPERTY_INFO_ENTRY(PREPAREABORTBEHAVIOR)
      PROPERTY_INFO_ENTRY(PREPARECOMMITBEHAVIOR)
      PROPERTY_INFO_ENTRY(PROCEDURETERM)
      PROPERTY_INFO_ENTRY(PROVIDERNAME)
      PROPERTY_INFO_ENTRY(PROVIDEROLEDBVER)
      PROPERTY_INFO_ENTRY(PROVIDERVER)
      PROPERTY_INFO_ENTRY(QUOTEDIDENTIFIERCASE)
      PROPERTY_INFO_ENTRY(ROWSETCONVERSIONSONCOMMAND)
      PROPERTY_INFO_ENTRY(SCHEMATERM)
      PROPERTY_INFO_ENTRY(SCHEMAUSAGE)
      PROPERTY_INFO_ENTRY(STRUCTUREDSTORAGE)
      PROPERTY_INFO_ENTRY(SUBQUERIES)
      PROPERTY_INFO_ENTRY(TABLETERM)
      PROPERTY_INFO_ENTRY(USERNAME)
   END_PROPERTY_SET(DBPROPSET_DATASOURCEINFO)
   BEGIN_PROPERTY_SET(DBPROPSET_DBINIT)
      PROPERTY_INFO_ENTRY(AUTH_PASSWORD)
      PROPERTY_INFO_ENTRY(AUTH_PERSIST_SENSITIVE_AUTHINFO)
      PROPERTY_INFO_ENTRY(AUTH_USERID)
      PROPERTY_INFO_ENTRY(INIT_DATASOURCE)
      PROPERTY_INFO_ENTRY(INIT_HWND)
      PROPERTY_INFO_ENTRY(INIT_LCID)
      PROPERTY_INFO_ENTRY(INIT_LOCATION)
      PROPERTY_INFO_ENTRY(INIT_MODE)
      PROPERTY_INFO_ENTRY(INIT_PROMPT)
      PROPERTY_INFO_ENTRY(INIT_PROVIDERSTRING)
      PROPERTY_INFO_ENTRY(INIT_TIMEOUT)
   END_PROPERTY_SET(DBPROPSET_DBINIT)
   BEGIN_PROPERTY_SET(DBPROPSET_DATASOURCE)
      PROPERTY_INFO_ENTRY(CURRENTCATALOG)
   END_PROPERTY_SET(DBPROPSET_DATASOURCE)
   CHAIN_PROPERTY_SET(CCustomSession)
END_PROPSET_MAP()
```

OLE DB 中的属性进行分组。 数据源对象具有两个组的属性： 一个用于 DBPROPSET_DATASOURCEINFO 设置，一个用于 DBPROPSET_DBINIT 设置。 DBPROPSET_DATASOURCEINFO 集对应于提供程序和其数据源有关的属性。 DBPROPSET_DBINIT 集对应于在初始化时使用的属性。 OLE DB 提供程序模板处理 PROPERTY_SET 宏与这些集。 宏还将创建包含的属性数组的块。 每当客户端调用`IDBProperties`接口，该提供程序使用的属性映射。

不需要实现规范中的每个属性。 但是，必须支持所需的属性;请参阅详细信息的级别 0 符合性规范。 如果不想要支持的属性，您可以从映射中将其删除。 如果你想要支持的属性，将其添加到映射使用 PROPERTY_INFO_ENTRY 宏。 该宏对应于`UPROPINFO`结构，如下面的代码中所示：

```cpp
struct UPROPINFO
{
   DBPROPID    dwPropId;
   ULONG       ulIDS;
   VARTYPE     VarType;
   DBPROPFLAGS dwFlags;
   union
   {
      DWORD dwVal;
      LPOLESTR szVal;
   };
   DBPROPOPTIONS dwOption;
};
```

结构中的每个元素表示处理属性的信息。 它包含`DBPROPID`属性确定的 GUID 和 ID。 它还包含项，以确定的类型和属性的值。

如果你想要更改属性 （请注意，使用者可以在任何时候更改可写属性的值） 的默认值，可以使用 PROPERTY_INFO_ENTRY_VALUE 或 PROPERTY_INFO_ENTRY_EX 宏。 这些宏，可以指定相应属性的值。 PROPERTY_INFO_ENTRY_VALUE 宏是速记表示法，您可以更改的值。 PROPERTY_INFO_ENTRY_VALUE 宏将调用 PROPERTY_INFO_ENTRY_EX 宏。 此宏，可添加或更改的属性中的所有`UPROPINFO`结构。

如果你想要定义您自己的属性集，可以添加一个额外的 BEGIN_PROPSET_MAP/END_PROPSET_MAP 组合，从而。 您需要定义属性集的 GUID，然后定义您自己的属性。 如果已将特定于提供程序的属性，则将它们添加到新的属性而不是使用一个现有设置。 这样可避免在更高版本的 OLE DB 中的问题。

## <a name="user-defined-property-sets"></a>用户定义的属性集

Visual c + + 支持用户定义的属性集。 无需重写`GetProperties`或`GetPropertyInfo`。 相反，模板会检测到任何用户定义的属性集，并将其添加到适当的对象。

如果有需要在初始化时是可用的用户定义的属性集 (即，使用者调用之前`IDBInitialize::Initialize`)，可以使用 UPROPSET_USERINIT 标志结合 BEGIN_PROPERTY_SET_EX 宏指定这。 在属性集中必须是为实现此目的 （如 OLE DB 规范要求） 的数据源对象中。 例如：

```cpp
BEGIN_PROPERTY_SET_EX(DBPROPSET_MYPROPSET, UPROPSET_USERINIT)
   PROPERTY_INFO_ENTRY(DBPROP_MYPROP)
END_PROPERTY_SET_EX(DBPROPSET_MYPROPSET)
```

## <a name="see-also"></a>请参阅

[提供程序向导生成的文件](../../data/oledb/provider-wizard-generated-files.md)