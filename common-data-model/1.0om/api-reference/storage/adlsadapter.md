---
title: ADLS Adapter | Microsoft Docs
description: API reference for ADLSAdapter.
author: jinichu
ms.service: common-data-model
ms.reviewer: deonhe 
ms.topic: article
ms.date: 10/18/2019
ms.author: jibyun
---

# ADLS Adapter

The ADLS adapter is the storage adapter that's used to interact with data on Azure Data Lake Storage Gen2.

```csharp
public class ADLSAdapter extends NetworkAdapter, StorageAdapter
```
*ADLSAdapter extends NetworkAdapter, StorageAdapterBase in Python.*

## Constructors
|Name|Description|
|---|---|
|**ADLSAdapter()**|Initializes a new instance of the [ADLSAdapter](adlsadapter.md) class. The user must apply an adapter configuration if this constructor is used. See *UpdateConfig(...)*.|
|**ADLSAdapter(string, string, string, string, string)**<br/>*hostname*: The ADLS hostname.<br/>*root*: The root path of the schema documents.<br/>*tenant*: The tenant.<br/>*clientId*: The client ID of the application accessing ADLS.<br/>*secret*: The secret for the application accessing ADLS.|Initializes a new instance of the [ADLSAdapter](adlsadapter.md) class with client ID/secret authentication.|
|**ADLSAdapter(string, string, string)**<br/>*hostname*: The ADLS hostname.<br/>*root*: The root path of the schema documents.<br/>*sharedKey*: The account/shared key.|Initializes a new instance of the [ADLSAdapter](adlsadapter.md) class with shared key authentication.|
|**ADLSAdapter(string, string, [TokenProvider](../utilities/tokenprovider.md))**<br/>*hostname*: The ADLS hostname.<br/>*root*: The root path of the schema documents.<br/>*tokenProvider*: The user-defined token provider.|Initializes a new instance of the [ADLSAdapter](adlsadapter.md) class with a user-defined implementation of the [TokenProvider](../utilities/tokenprovider.md) interface.|

## Properties
|Name|Type|Description|
|---|---|---|
|Root|string|The root path of the schema documents.|
|Hostname|string|The ADLS hostname.|
|Tenant|string|The tenant.|
|ClientId|string|The client ID of the application accessing ADLS.|
|Secret|string|The secret for the application accessing ADLS.|
|SharedKey|string|The account or shared key.|
|Token Provider|[TokenProvider](../utilities/tokenprovider.md)|The token provider used to dynamically generate the access token.|
|LocationHint|string|The hint given to the reader application about where to find the the adapter implementation (for example, in Nuget, NPM, etc.).|

## Methods
|Name|Description|Return Type|
|---|---|---|
|**CanRead()**|Returns true, since the ADLS adapter can read data.|bool|
|**CanWrite()**|Returns true, since the ADLS adapter can write data to its source.|bool|
|**ReadAsync(string)**|See [StorageAdapter.ReadAsync(...)](storageadapter.md#methods).|Task\<string>|
|**WriteAsync(string, string)**|See [StorageAdapter.WriteAsync(...)](storageadapter.md#methods).|Task|
|**CreateAdapterPath(string)**|See [StorageAdapter.CreateAdapterPath(...)](storageadapter.md#methods).|string|
|**CreateCorpusPath(string)**|See [StorageAdapter.CreateCorpusPath(...)](storageadapter.md#methods).|string|
|**ClearCache()**|See [StorageAdapter.ClearCache()](storageadapter.md#methods). This method doesn't do anything because the ADLS adapter doesn't maintain a cache.|void|
|**ComputeLastModifiedTimeAsync(string)**|See [StorageAdapter.ComputeLastModifiedTimeAsync(...)](storageadapter.md#methods).|Task\<DateTimeOffset?>|
|**FetchAllFilesAsync(string)**|See [StorageAdapter.FetchAllFilesAsync(...)](storageadapter.md#methods).|Task\<List\<string>>|
|**FetchConfig()**|See [StorageAdapter.FetchConfig()](storageadapter.md#methods).|string|
|**UpdateConfig(string)**|See [StorageAdapter.UpdateConfig(...)](storageadapter.md#methods).|void|
