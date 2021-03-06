---
title: "将媒体服务资产下载到计算机 - Azure | Microsoft 文档"
description: "了解如何将资产下载到计算机。 代码示例用 C# 编写且使用适用于 .NET 的媒体服务 SDK。"
services: media-services
documentationcenter: 
author: juliako
manager: erikre
editor: 
ms.assetid: 8908a1dd-3ffb-4f18-955d-4c8e2d82fc5d
ms.service: media-services
ms.workload: media
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 08/09/2017
ms.author: juliako
ms.translationtype: Human Translation
ms.sourcegitcommit: c1cd1450d5921cf51f720017b746ff9498e85537
ms.openlocfilehash: 19f6ea37f892054ee5d7bf793a32364dff264058
ms.contentlocale: zh-cn
ms.lasthandoff: 03/14/2017

---
# <a name="how-to-deliver-an-asset-by-download"></a>如何：通过下载交付资产
本主题介绍已上载到媒体服务的媒体资产的交付选项。 你可以采用众多的应用程序方案来交付媒体服务内容。 你可以下载媒体资产，或使用定位器访问媒体资产。 你可以将媒体内容发送到其他应用程序或其他内容提供商。 为了提高性能和可缩放性，你还可以使用内容传送网络 (CDN) 来传送内容。

此示例演示如何将媒体资产从媒体服务下载到本地计算机。 该代码将按作业 ID 查询与媒体服务帐户关联的作业，并访问其 **OutputMediaAssets** 集合（即运行作业后生成的、包含一个或多个输出媒体资产的集）。 此示例演示如何通过作业下载输出媒体资产，但也可运用相同的方法下载其他资产。

>[!NOTE]
>不同 AMS 策略的策略限制为 1,000,000 个（例如，对于定位器策略或 ContentKeyAuthorizationPolicy）。 如果始终使用相同的日期/访问权限，则应使用相同的策略 ID，例如，用于要长期就地保留的定位符的策略（非上传策略）。 有关详细信息，请参阅[此](media-services-dotnet-manage-entities.md#limit-access-policies)主题。

    // Download the output asset of the specified job to a local folder.
    static IAsset DownloadAssetToLocal( string jobId, string outputFolder)
    {
        // This method illustrates how to download a single asset. 
        // However, you can iterate through the OutputAssets
        // collection, and download all assets if there are many. 

        // Get a reference to the job. 
        IJob job = GetJob(jobId);

        // Get a reference to the first output asset. If there were multiple 
        // output media assets you could iterate and handle each one.
        IAsset outputAsset = job.OutputMediaAssets[0];

        // Create a SAS locator to download the asset
        IAccessPolicy accessPolicy = _context.AccessPolicies.Create("File Download Policy", TimeSpan.FromDays(30), AccessPermissions.Read);
        ILocator locator = _context.Locators.CreateLocator(LocatorType.Sas, outputAsset, accessPolicy);

        BlobTransferClient blobTransfer = new BlobTransferClient
        {
            NumberOfConcurrentTransfers = 20,
            ParallelTransferThreadCount = 20
        };

        var downloadTasks = new List<Task>();
        foreach (IAssetFile outputFile in outputAsset.AssetFiles)
        {
            // Use the following event handler to check download progress.
            outputFile.DownloadProgressChanged += DownloadProgress;

            string localDownloadPath = Path.Combine(outputFolder, outputFile.Name);

            Console.WriteLine("File download path:  " + localDownloadPath);

            downloadTasks.Add(outputFile.DownloadAsync(Path.GetFullPath(localDownloadPath), blobTransfer, locator, CancellationToken.None));

            outputFile.DownloadProgressChanged -= DownloadProgress;
        }

        Task.WaitAll(downloadTasks.ToArray());

        return outputAsset;
    }

    static void DownloadProgress(object sender, DownloadProgressChangedEventArgs e)
    {
        Console.WriteLine(string.Format("{0} % download progress. ", e.Progress));
    }



## <a name="media-services-learning-paths"></a>媒体服务学习路径
[!INCLUDE [media-services-learning-paths-include](../../includes/media-services-learning-paths-include.md)]

## <a name="provide-feedback"></a>提供反馈
[!INCLUDE [media-services-user-voice-include](../../includes/media-services-user-voice-include.md)]

## <a name="see-also"></a>另请参阅
[传送流式处理内容](media-services-deliver-streaming-content.md)


