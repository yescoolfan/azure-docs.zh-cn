---
title: "使用 AES-128 动态加密和密钥传送服务 | Microsoft Docs"
description: "借助 Microsoft Azure 媒体服务，你可以传送使用 AES 128 位加密密钥加密的内容。 媒体服务还提供密钥传送服务，将加密密钥传送给已授权的用户。 本主题说明如何使用 AES-128 动态加密以及如何使用密钥传送服务。"
services: media-services
documentationcenter: 
author: Juliako
manager: erikre
editor: 
ms.assetid: 4d2c10af-9ee0-408f-899b-33fa4c1d89b9
ms.service: media-services
ms.workload: media
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 07/18/2017
ms.author: juliako
ms.translationtype: HT
ms.sourcegitcommit: 26c07d30f9166e0e52cb396cdd0576530939e442
ms.openlocfilehash: 4996df4623a706e51ab00538c17590ebf2d71fc4
ms.contentlocale: zh-cn
ms.lasthandoff: 07/19/2017

---
# <a name="using-aes-128-dynamic-encryption-and-key-delivery-service"></a>使用 AES-128 动态加密和密钥传送服务
> [!div class="op_single_selector"]
> * [.NET](media-services-protect-with-aes128.md)
> * [Java](https://github.com/southworkscom/azure-sdk-for-media-services-java-samples)
> * [PHP](https://github.com/Azure/azure-sdk-for-php/tree/master/examples/MediaServices)
> 
> 

## <a name="overview"></a>概述
> [!NOTE]
> 请参阅[此](https://channel9.msdn.com/Shows/Azure-Friday/Azure-Media-Services-Protecting-your-Media-Content-with-AES-Encryption)视频，获取有关如何使用 AES 加密保护媒体内容的概述。
> 
> 

借助 Microsoft Azure 媒体服务，你能够传送使用高级加密标准 (AES) 加密的 Http 实时流式处理 (HLS) 和平滑流（使用 128 位加密密钥）。 媒体服务还提供密钥传送服务，将加密密钥传送给已授权的用户。 如果你需要媒体服务来加密资产，则需要将加密密钥与资产相关联，并配置密钥的授权策略。 当播放器请求流时，媒体服务将使用指定的密钥通过 AES 加密来动态加密你的内容。 为了解密流，播放器将从密钥传送服务请求密钥。 为了确定用户是否被授权获取密钥，服务将评估你为密钥指定的授权策略。

媒体服务支持通过多种方式对发出密钥请求的用户进行身份验证。 内容密钥授权策略可能受到一种或多种授权限制：开放或令牌限制。 令牌限制策略必须附带由安全令牌服务 (STS) 颁发的令牌。 媒体服务支持采用[简单 Web 令牌](https://msdn.microsoft.com/library/gg185950.aspx#BKMK_2) (SWT) 格式和 [JSON Web 令牌](https://msdn.microsoft.com/library/gg185950.aspx#BKMK_3) (JWT) 格式的令牌。 有关详细信息，请参阅[配置内容密钥授权策略](media-services-protect-with-aes128.md#configure_key_auth_policy)。

为了充分利用动态加密，你的资产必须包含一组多码率 MP4 文件或多码率平滑流源文件。 你还需要为资产配置传送策略（在本主题后面部分介绍）。 然后，根据你在流 URL 中指定的格式，按需流式处理服务器将确保使用你选定的协议来传送流。 因此，你只需以单一存储格式存储文件并为其付费，然后媒体服务服务就会基于客户端的请求构建并提供相应响应。

本主题适合开发受保护媒体传送应用程序的开发人员。 本主题介绍如何使用授权策略来配置密钥传送服务，确保只有经过授权的客户端才能接收加密密钥。 此外还将介绍如何使用动态加密。


## <a name="aes-128-dynamic-encryption-and-key-delivery-service-workflow"></a>AES-128 动态加密和密钥传送服务工作流

下面是使用 AES 加密资产时需要执行的常规步骤，这些步骤使用媒体服务密钥传送服务，也使用动态加密。

1. [创建资产并将文件上传到资产](media-services-protect-with-aes128.md#create_asset)。
2. [将包含文件的资产编码为自适应比特率 MP4 集](media-services-protect-with-aes128.md#encode_asset)。
3. [创建内容密钥并将其与编码资产相关联](media-services-protect-with-aes128.md#create_contentkey)。 在媒体服务中，内容密钥包含资产的加密密钥。
4. [配置内容密钥授权策略](media-services-protect-with-aes128.md#configure_key_auth_policy)。 你必须配置内容密钥授权策略，客户端必须遵守该策略，才能将内容密钥传送到客户端。
5. [为资产配置传送策略](media-services-protect-with-aes128.md#configure_asset_delivery_policy)。 传送策略配置包括：密钥获取 URL 和初始化向量 (IV)（进行加密和解密时，AES 128 要求提供同一个初始化向量）、传送协议（例如 MPEG DASH、HLS、平滑流式处理或全部）、动态加密类型（例如信封或无动态加密）。

    你可以将不同的策略应用到同一资产上的每个协议。 例如，可以将 PlayReady 加密应用到平滑流/DASH，将 AES 信封应用到 HLS。 将阻止流式处理传送策略中未定义的任何协议（例如，添加仅将 HLS 指定为协议的单个策略）。 如果你根本没有定义任何传送策略，则情况不是这样。 此时，将允许所有明文形式的协议。

6. [创建 OnDemand 定位符](media-services-protect-with-aes128.md#create_locator)以获取流式处理 URL。

本主题还说明了[客户端应用程序如何从密钥传送服务请求密钥](media-services-protect-with-aes128.md#client_request)。

可以在主题末尾找到完整的 .NET [示例](media-services-protect-with-aes128.md#example)。

下图演示了上述工作流。 在图中，使用令牌进行了身份验证。

![使用 AES-128 提供保护](./media/media-services-content-protection-overview/media-services-content-protection-with-aes.png)

本主题的余下部分提供了详细说明、代码示例和主题链接，向你演示如何完成上述任务。

## <a name="current-limitations"></a>当前限制
如果你添加或更新资产的传送策略，则必须删除现有定位符（如果有）并创建新定位符。

## <a id="create_asset"></a>创建资产并将文件上传到资产
为了对视频进行管理、编码和流式处理，必须首先将内容上传到 Microsoft Azure 媒体服务中。 上传完成后，相关内容即安全地存储在云中供后续处理和流式处理。 

有关详细信息，请参阅 [将文件上传到媒体服务帐户](media-services-dotnet-upload-files.md)。

## <a id="encode_asset"></a>将包含文件的资产编码为自适应比特率 MP4 集
使用动态加密时，你只需创建包含一组多码率 MP4 文件或多码率平滑流源文件的资产。 然后，点播流服务器会确保你以选定的协议按清单或分段请求中的指定格式接收流。 因此，你只需以单一存储格式存储文件并为其付费，然后媒体服务服务就会基于客户端的请求构建并提供相应响应。 有关详细信息，请参阅 [动态打包概述](media-services-dynamic-packaging-overview.md) 主题。

>[!NOTE]
>创建 AMS 帐户后，会将一个处于“已停止”状态的**默认**流式处理终结点添加到帐户。 若要开始流式传输内容并利用动态打包和动态加密，要从中流式传输内容的流式处理终结点必须处于“正在运行”状态。 
>
>此外，若要使用动态打包和动态加密，你的资产必须包含一组自适应比特率 MP4 或自适应比特率平滑流式处理文件。

有关如何编码的说明，请参阅 [如何使用 Media Encoder Standard 对资产进行编码](media-services-dotnet-encode-with-media-encoder-standard.md)。

## <a id="create_contentkey"></a>创建内容密钥并将其与编码资产相关联
在媒体服务中，内容密钥包含用于加密资产的密钥。

有关详细信息，请参阅 [创建内容密钥](media-services-dotnet-create-contentkey.md)。

## <a id="configure_key_auth_policy"></a>配置内容密钥授权策略
媒体服务支持通过多种方式对发出密钥请求的用户进行身份验证。 你必须配置内容密钥授权策略，客户端（播放器）必须遵守该策略，才能将密钥传送到客户端。 内容密钥授权策略可能受到一种或多种授权限制：开放、令牌限制或 IP 限制。

有关详细信息，请参阅[配置内容密钥授权策略](media-services-dotnet-configure-content-key-auth-policy.md)。

## <a id="configure_asset_delivery_policy"></a>配置资产传送策略
为资产配置传送策略。 资产传送策略配置包括：

* 密钥获取 URL。 
* 用于信封加密的初始化向量 (IV)。 进行加密和解密时，AES - 128 要求提供同一个 IV。 
* 资产传送协议（例如 MPEG DASH、HLS、平滑流式处理或全部）。
* 动态加密类型（例如 AES 信封）或无动态加密。 

有关详细信息，请参阅 [配置资产传送策略 ](media-services-rest-configure-asset-delivery-policy.md)。

## <a id="create_locator"></a>创建 OnDemand 流定位符以获取流 URL
需要为用户提供平滑流、DASH 或 HLS 的流 URL。

> [!NOTE]
> 如果你添加或更新资产的传送策略，则必须删除现有定位符（如果有）并创建新定位符。
> 
> 

有关如何发布资产和生成流 URL 的说明，请参阅 [生成流 URL](media-services-deliver-streaming-content.md)。

## <a name="get-a-test-token"></a>获取测试令牌
获取用于密钥授权策略的基于令牌限制的测试令牌。

    // Deserializes a string containing an Xml representation of a TokenRestrictionTemplate
    // back into a TokenRestrictionTemplate class instance.
    TokenRestrictionTemplate tokenTemplate = 
        TokenRestrictionTemplateSerializer.Deserialize(tokenTemplateString);

    // Generate a test token based on the data in the given TokenRestrictionTemplate.
    //The GenerateTestToken method returns the token without the word “Bearer” in front
    //so you have to add it in front of the token string. 
    string testToken = TokenRestrictionTemplateSerializer.GenerateTestToken(tokenTemplate);
    Console.WriteLine("The authorization token is:\nBearer {0}", testToken);

你可以使用 [AMS Player](http://amsplayer.azurewebsites.net/azuremediaplayer.html) 来测试你的流。

## <a id="client_request"></a>你的客户端如何从密钥传送服务请求密钥？
在上一步骤中，你构造了指向清单文件的 URL。 你的客户端需要从流清单文件提取必要的信息，以便向密钥传送服务发出请求。

### <a name="manifest-files"></a>清单文件
客户端需要从清单文件提取 URL（也包含内容密钥 ID (kid)）值。 然后，客户端将尝试从密钥传送服务获取加密密钥。 客户端还需要提取 IV 值，并使用该值来解密流。以下代码段显示了平滑流清单的 <Protection> 元素。

    <Protection>
      <ProtectionHeader SystemID="B47B251A-2409-4B42-958E-08DBAE7B4EE9">
        <ContentProtection xmlns:sea="urn:mpeg:dash:schema:sea:2012" schemeIdUri="urn:mpeg:dash:sea:2012">
          <sea:SegmentEncryption schemeIdUri="urn:mpeg:dash:sea:aes128-cbc:2013"/>
          <sea:KeySystem keySystemUri="urn:mpeg:dash:sea:keysys:http:2013"/>
          <sea:CryptoPeriod IV="0xD7D7D7D7D7D7D7D7D7D7D7D7D7D7D7D7" 
                            keyUriTemplate="https://wamsbayclus001kd-hs.cloudapp.net/HlsHandler.ashx?
                                            kid=da3813af-55e6-48e7-aa9f-a4d6031f7b4d"/>
        </ContentProtection>
      </ProtectionHeader>
    </Protection>

对于 HLS，根清单将划分成段文件。 

例如，根清单为 http://test001.origin.mediaservices.windows.net/8bfe7d6f-34e3-4d1a-b289-3e48a8762490/BigBuckBunny.ism/manifest(format=m3u8-aapl) 并且包含段文件名的列表。

    . . . 
    #EXT-X-STREAM-INF:PROGRAM-ID=1,BANDWIDTH=630133,RESOLUTION=424x240,CODECS="avc1.4d4015,mp4a.40.2",AUDIO="audio"
    QualityLevels(514369)/Manifest(video,format=m3u8-aapl)
    #EXT-X-STREAM-INF:PROGRAM-ID=1,BANDWIDTH=965441,RESOLUTION=636x356,CODECS="avc1.4d401e,mp4a.40.2",AUDIO="audio"
    QualityLevels(842459)/Manifest(video,format=m3u8-aapl)
    …

如果在文本编辑器中打开其中一个段文件（例如，http://test001.origin.mediaservices.windows.net/8bfe7d6f-34e3-4d1a-b289-3e48a8762490/BigBuckBunny.ism/QualityLevels(514369)/Manifest(video,format=m3u8-aapl)），则应包含 #EXT-X-KEY，表示文件已加密。

    #EXTM3U
    #EXT-X-VERSION:4
    #EXT-X-ALLOW-CACHE:NO
    #EXT-X-MEDIA-SEQUENCE:0
    #EXT-X-TARGETDURATION:9
    #EXT-X-KEY:METHOD=AES-128,
    URI="https://wamsbayclus001kd-hs.cloudapp.net/HlsHandler.ashx?
         kid=da3813af-55e6-48e7-aa9f-a4d6031f7b4d",
            IV=0XD7D7D7D7D7D7D7D7D7D7D7D7D7D7D7D7
    #EXT-X-PROGRAM-DATE-TIME:1970-01-01T00:00:00.000+00:00
    #EXTINF:8.425708,no-desc
    Fragments(video=0,format=m3u8-aapl)
    #EXT-X-ENDLIST

### <a name="request-the-key-from-the-key-delivery-service"></a>从密钥传送服务请求密钥
以下代码演示如何使用密钥传送 Uri（从清单提取）和令牌（本主题不讨论如何从安全令牌服务获取简单 Web 令牌），向媒体服务密钥传送服务发送请求。

    private byte[] GetDeliveryKey(Uri keyDeliveryUri, string token)
    {
        HttpWebRequest request = (HttpWebRequest)WebRequest.Create(keyDeliveryUri);

        request.Method = "POST";
        request.ContentType = "text/xml";
        if (!string.IsNullOrEmpty(token))
        {
            request.Headers[AuthorizationHeader] = token;
        }
        request.ContentLength = 0;

        var response = request.GetResponse();

        var stream = response.GetResponseStream();
        if (stream == null)
        {
            throw new NullReferenceException("Response stream is null");
        }

        var buffer = new byte[256];
        var length = 0;
        while (stream.CanRead && length <= buffer.Length)
        {
            var nexByte = stream.ReadByte();
            if (nexByte == -1)
            {
                break;
            }
            buffer[length] = (byte)nexByte;
            length++;
        }
        response.Close();

        // AES keys must be exactly 16 bytes (128 bits).
        var key = new byte[length];
        Array.Copy(buffer, key, length);
        return key;
    }

## <a name="create-and-configure-a-visual-studio-project"></a>创建和配置 Visual Studio 项目

1. 设置开发环境，并根据[使用 .NET 进行媒体服务开发](media-services-dotnet-how-to-use.md)中所述，在 app.config 文件中填充连接信息。 
2. 将以下元素添加到 app.config 文件中定义的 **appSettings**：

        <add key="Issuer" value="http://testacs.com"/>
        <add key="Audience" value="urn:test"/>

## <a id="example"></a>示例

使用本部分中所示的代码覆盖 Program.cs 文件中的代码。
 
>[!NOTE]
>不同 AMS 策略的策略限制为 1,000,000 个（例如，对于定位器策略或 ContentKeyAuthorizationPolicy）。 如果始终使用相同的日期/访问权限，则应使用相同的策略 ID，例如，用于要长期就地保留的定位符的策略（非上传策略）。 有关详细信息，请参阅[此](media-services-dotnet-manage-entities.md#limit-access-policies)主题。

请务必将变量更新为指向输入文件所在的文件夹。

    using System;
    using System.Collections.Generic;
    using System.Configuration;
    using System.IO;
    using System.Linq;
    using System.Security.Cryptography;
    using Microsoft.WindowsAzure.MediaServices.Client;
    using System.Threading;
    using Microsoft.WindowsAzure.MediaServices.Client.ContentKeyAuthorization;
    using Microsoft.WindowsAzure.MediaServices.Client.DynamicEncryption;

    namespace AESDynamicEncryptionAndKeyDeliverySvc
    {
        class Program
        {
        // Read values from the App.config file.
        private static readonly string _AADTenantDomain =
        ConfigurationManager.AppSettings["AADTenantDomain"];
        private static readonly string _RESTAPIEndpoint =
        ConfigurationManager.AppSettings["MediaServiceRESTAPIEndpoint"];

        // A Uri describing the issuer of the token.  
        // Must match the value in the token for the token to be considered valid.
        private static readonly Uri _sampleIssuer =
            new Uri(ConfigurationManager.AppSettings["Issuer"]);
        // The Audience or Scope of the token.  
        // Must match the value in the token for the token to be considered valid.
        private static readonly Uri _sampleAudience =
            new Uri(ConfigurationManager.AppSettings["Audience"]);

        // Field for service context.
        private static CloudMediaContext _context = null;

        private static readonly string _mediaFiles =
            Path.GetFullPath(@"../..\Media");

        private static readonly string _singleMP4File =
            Path.Combine(_mediaFiles, @"BigBuckBunny.mp4");

        static void Main(string[] args)
        {
            var tokenCredentials = new AzureAdTokenCredentials(_AADTenantDomain, AzureEnvironments.AzureCloudEnvironment);
            var tokenProvider = new AzureAdTokenProvider(tokenCredentials);

            _context = new CloudMediaContext(new Uri(_RESTAPIEndpoint), tokenProvider);

            bool tokenRestriction = false;
            string tokenTemplateString = null;

            IAsset asset = UploadFileAndCreateAsset(_singleMP4File);
            Console.WriteLine("Uploaded asset: {0}", asset.Id);

            IAsset encodedAsset = EncodeToAdaptiveBitrateMP4Set(asset);
            Console.WriteLine("Encoded asset: {0}", encodedAsset.Id);

            IContentKey key = CreateEnvelopeTypeContentKey(encodedAsset);
            Console.WriteLine("Created key {0} for the asset {1} ", key.Id, encodedAsset.Id);
            Console.WriteLine();

            if (tokenRestriction)
            tokenTemplateString = AddTokenRestrictedAuthorizationPolicy(key);
            else
            AddOpenAuthorizationPolicy(key);

            Console.WriteLine("Added authorization policy: {0}", key.AuthorizationPolicyId);
            Console.WriteLine();

            CreateAssetDeliveryPolicy(encodedAsset, key);
            Console.WriteLine("Created asset delivery policy. \n");
            Console.WriteLine();

            if (tokenRestriction && !String.IsNullOrEmpty(tokenTemplateString))
            {
            // Deserializes a string containing an Xml representation of a TokenRestrictionTemplate
            // back into a TokenRestrictionTemplate class instance.
            TokenRestrictionTemplate tokenTemplate =
                TokenRestrictionTemplateSerializer.Deserialize(tokenTemplateString);

            // Generate a test token based on the data in the given TokenRestrictionTemplate.
            // Note, you need to pass the key id Guid because we specified 
            // TokenClaim.ContentKeyIdentifierClaim in during the creation of TokenRestrictionTemplate.
            Guid rawkey = EncryptionUtils.GetKeyIdAsGuid(key.Id);

            //The GenerateTestToken method returns the token without the word “Bearer” in front
            //so you have to add it in front of the token string. 
            string testToken = TokenRestrictionTemplateSerializer.GenerateTestToken(tokenTemplate, null, rawkey);
            Console.WriteLine("The authorization token is:\nBearer {0}", testToken);
            Console.WriteLine();
            }

            // You can use the bit.ly/aesplayer Flash player to test the URL 
            // (with open authorization policy). 
            // Paste the URL and click the Update button to play the video. 
            //
            string URL = GetStreamingOriginLocator(encodedAsset);
            Console.WriteLine("Smooth Streaming Url: {0}/manifest", URL);
            Console.WriteLine();
            Console.WriteLine("HLS Url: {0}/manifest(format=m3u8-aapl)", URL);
            Console.WriteLine();

            Console.ReadLine();
        }

        static public IAsset UploadFileAndCreateAsset(string singleFilePath)
        {
            if (!File.Exists(singleFilePath))
            {
            Console.WriteLine("File does not exist.");
            return null;
            }

            var assetName = Path.GetFileNameWithoutExtension(singleFilePath);
            IAsset inputAsset = _context.Assets.Create(assetName, AssetCreationOptions.StorageEncrypted);

            var assetFile = inputAsset.AssetFiles.Create(Path.GetFileName(singleFilePath));

            Console.WriteLine("Created assetFile {0}", assetFile.Name);


            Console.WriteLine("Upload {0}", assetFile.Name);

            assetFile.Upload(singleFilePath);
            Console.WriteLine("Done uploading {0}", assetFile.Name);

            return inputAsset;
        }

        static public IAsset EncodeToAdaptiveBitrateMP4Set(IAsset asset)
        {
            // Declare a new job.
            IJob job = _context.Jobs.Create("Media Encoder Standard Job");
            // Get a media processor reference, and pass to it the name of the 
            // processor to use for the specific task.
            IMediaProcessor processor = GetLatestMediaProcessorByName("Media Encoder Standard");

            // Create a task with the encoding details, using a string preset.
            // In this case "Adaptive Streaming" preset is used.
            ITask task = job.Tasks.AddNew("My encoding task",
            processor,
            "Adaptive Streaming",
            TaskOptions.None);

            // Specify the input asset to be encoded.
            task.InputAssets.Add(asset);
            // Add an output asset to contain the results of the job. 
            // This output is specified as AssetCreationOptions.None, which 
            // means the output asset is not encrypted. 
            task.OutputAssets.AddNew("Output asset",
            AssetCreationOptions.StorageEncrypted);

            job.StateChanged += new EventHandler<JobStateChangedEventArgs>(JobStateChanged);
            job.Submit();
            job.GetExecutionProgressTask(CancellationToken.None).Wait();

            return job.OutputMediaAssets[0];
        }

        private static IMediaProcessor GetLatestMediaProcessorByName(string mediaProcessorName)
        {
            var processor = _context.MediaProcessors.Where(p => p.Name == mediaProcessorName).
            ToList().OrderBy(p => new Version(p.Version)).LastOrDefault();

            if (processor == null)
            throw new ArgumentException(string.Format("Unknown media processor", mediaProcessorName));

            return processor;
        }

        static public IContentKey CreateEnvelopeTypeContentKey(IAsset asset)
        {
            // Create envelope encryption content key
            Guid keyId = Guid.NewGuid();
            byte[] contentKey = GetRandomBuffer(16);

            IContentKey key = _context.ContentKeys.Create(
                keyId,
                contentKey,
                "ContentKey",
                ContentKeyType.EnvelopeEncryption);

            // Associate the key with the asset.
            asset.ContentKeys.Add(key);

            return key;
        }

        static public void AddOpenAuthorizationPolicy(IContentKey contentKey)
        {
            // Create ContentKeyAuthorizationPolicy with Open restrictions 
            // and create authorization policy             
            IContentKeyAuthorizationPolicy policy = _context.
                ContentKeyAuthorizationPolicies.
                CreateAsync("Open Authorization Policy").Result;

            List<ContentKeyAuthorizationPolicyRestriction> restrictions =
            new List<ContentKeyAuthorizationPolicyRestriction>();

            ContentKeyAuthorizationPolicyRestriction restriction =
            new ContentKeyAuthorizationPolicyRestriction
            {
            Name = "HLS Open Authorization Policy",
            KeyRestrictionType = (int)ContentKeyRestrictionType.Open,
            Requirements = null // no requirements needed for HLS
        };

            restrictions.Add(restriction);

            IContentKeyAuthorizationPolicyOption policyOption =
            _context.ContentKeyAuthorizationPolicyOptions.Create(
            "policy",
            ContentKeyDeliveryType.BaselineHttp,
            restrictions,
            "");

            policy.Options.Add(policyOption);

            // Add ContentKeyAutorizationPolicy to ContentKey
            contentKey.AuthorizationPolicyId = policy.Id;
            IContentKey updatedKey = contentKey.UpdateAsync().Result;
            Console.WriteLine("Adding Key to Asset: Key ID is " + updatedKey.Id);
        }

        public static string AddTokenRestrictedAuthorizationPolicy(IContentKey contentKey)
        {
            string tokenTemplateString = GenerateTokenRequirements();

            IContentKeyAuthorizationPolicy policy = _context.
                ContentKeyAuthorizationPolicies.
                CreateAsync("HLS token restricted authorization policy").Result;

            List<ContentKeyAuthorizationPolicyRestriction> restrictions =
            new List<ContentKeyAuthorizationPolicyRestriction>();

            ContentKeyAuthorizationPolicyRestriction restriction =
            new ContentKeyAuthorizationPolicyRestriction
            {
                Name = "Token Authorization Policy",
                KeyRestrictionType = (int)ContentKeyRestrictionType.TokenRestricted,
                Requirements = tokenTemplateString
            };

            restrictions.Add(restriction);

            //You could have multiple options 
            IContentKeyAuthorizationPolicyOption policyOption =
            _context.ContentKeyAuthorizationPolicyOptions.Create(
            "Token option for HLS",
            ContentKeyDeliveryType.BaselineHttp,
            restrictions,
            null  // no key delivery data is needed for HLS
            );

            policy.Options.Add(policyOption);

            // Add ContentKeyAutorizationPolicy to ContentKey
            contentKey.AuthorizationPolicyId = policy.Id;
            IContentKey updatedKey = contentKey.UpdateAsync().Result;
            Console.WriteLine("Adding Key to Asset: Key ID is " + updatedKey.Id);

            return tokenTemplateString;
        }

        static public void CreateAssetDeliveryPolicy(IAsset asset, IContentKey key)
        {
            Uri keyAcquisitionUri = key.GetKeyDeliveryUrl(ContentKeyDeliveryType.BaselineHttp);

            string envelopeEncryptionIV = Convert.ToBase64String(GetRandomBuffer(16));

            // When configuring delivery policy, you can choose to associate it
            // with a key acquisition URL that has a KID appended or
            // or a key acquisition URL that does not have a KID appended  
            // in which case a content key can be reused. 

            // EnvelopeKeyAcquisitionUrl:  contains a key ID in the key URL.
            // EnvelopeBaseKeyAcquisitionUrl:  the URL does not contains a key ID

            // The following policy configuration specifies: 
            // key url that will have KID=<Guid> appended to the envelope and
            // the Initialization Vector (IV) to use for the envelope encryption.

            Dictionary<AssetDeliveryPolicyConfigurationKey, string> assetDeliveryPolicyConfiguration =
            new Dictionary<AssetDeliveryPolicyConfigurationKey, string>
            {
            {AssetDeliveryPolicyConfigurationKey.EnvelopeKeyAcquisitionUrl, keyAcquisitionUri.ToString()}
            };

            IAssetDeliveryPolicy assetDeliveryPolicy =
            _context.AssetDeliveryPolicies.Create(
                "AssetDeliveryPolicy",
                AssetDeliveryPolicyType.DynamicEnvelopeEncryption,
                AssetDeliveryProtocol.SmoothStreaming | AssetDeliveryProtocol.HLS | AssetDeliveryProtocol.Dash,
                assetDeliveryPolicyConfiguration);

            // Add AssetDelivery Policy to the asset
            asset.DeliveryPolicies.Add(assetDeliveryPolicy);
            Console.WriteLine();
            Console.WriteLine("Adding Asset Delivery Policy: " +
            assetDeliveryPolicy.AssetDeliveryPolicyType);
        }

        static public string GetStreamingOriginLocator(IAsset asset)
        {

            // Get a reference to the streaming manifest file from the  
            // collection of files in the asset. 

            var assetFile = asset.AssetFiles.Where(f => f.Name.ToLower().
                EndsWith(".ism")).
                FirstOrDefault();

            // Create a 30-day readonly access policy. 
            // You cannot create a streaming locator using an AccessPolicy that includes write or delete permissions.            
            IAccessPolicy policy = _context.AccessPolicies.Create("Streaming policy",
            TimeSpan.FromDays(30),
            AccessPermissions.Read);

            // Create a locator to the streaming content on an origin. 
            ILocator originLocator = _context.Locators.CreateLocator(LocatorType.OnDemandOrigin, asset,
            policy,
            DateTime.UtcNow.AddMinutes(-5));

            // Create a URL to the manifest file. 
            return originLocator.Path + assetFile.Name;
        }

        static private string GenerateTokenRequirements()
        {
            TokenRestrictionTemplate template = new TokenRestrictionTemplate(TokenType.SWT);

            template.PrimaryVerificationKey = new SymmetricVerificationKey();
            template.AlternateVerificationKeys.Add(new SymmetricVerificationKey());
            template.Audience = _sampleAudience.ToString();
            template.Issuer = _sampleIssuer.ToString();

            template.RequiredClaims.Add(TokenClaim.ContentKeyIdentifierClaim);

            return TokenRestrictionTemplateSerializer.Serialize(template);
        }

        static private void JobStateChanged(object sender, JobStateChangedEventArgs e)
        {
            Console.WriteLine(string.Format("{0}\n  State: {1}\n  Time: {2}\n\n",
            ((IJob)sender).Name,
            e.CurrentState,
            DateTime.UtcNow.ToString(@"yyyy_M_d__hh_mm_ss")));
        }

        static private byte[] GetRandomBuffer(int size)
        {
            byte[] randomBytes = new byte[size];
            using (RNGCryptoServiceProvider rng = new RNGCryptoServiceProvider())
            {
            rng.GetBytes(randomBytes);
            }

            return randomBytes;
        }
        }
    }


## <a name="media-services-learning-paths"></a>媒体服务学习路径
[!INCLUDE [media-services-learning-paths-include](../../includes/media-services-learning-paths-include.md)]

## <a name="provide-feedback"></a>提供反馈
[!INCLUDE [media-services-user-voice-include](../../includes/media-services-user-voice-include.md)]


