## <a name="create-an-iot-hub"></a>创建 IoT 中心

1. 在 [Azure 门户](https://portal.azure.com/)中，依次单击“新建” > “物联网” > “IoT 中心”。

   ![在 Azure 门户中创建 IoT 中心](../articles/iot-hub/media/iot-hub-create-hub-and-device/1_create-azure-iot-hub-portal.png)
2. 在“IoT 中心”窗格中，输入 IoT 中心的以下信息：

     名称：输入 IoT 中心的名称。 如果输入的名称有效，会显示一个绿色复选标记。

     定价和缩放层：选择“F1 - 免费”层。 此选项对于本演示来说已足够。 有关详细信息，请参阅[定价和缩放层](https://azure.microsoft.com/pricing/details/iot-hub/)。

     **资源组**：创建用于托管 IoT 中心的资源组，或使用现有的资源组。 有关详细信息，请参阅[使用资源组管理 Azure 资源](../articles/azure-resource-manager/resource-group-portal.md)。

     **位置**：选择与创建的 IoT 中心最靠近的位置。

     **固定仪表板**：选中此选项可以方便地从仪表板访问 IoT 中心。

   ![输入创建 IoT 中心所需的信息](../articles/iot-hub/media/iot-hub-create-hub-and-device/2_fill-in-fields-for-azure-iot-hub-portal.png)

   [!INCLUDE [iot-hub-pii-note-naming-hub](iot-hub-pii-note-naming-hub.md)]

3. 单击“创建” 。 创建 IoT 中心可能需要数分钟的时间。 可在“通知”窗格中查看进度。

   ![请查看 IoT 中心的进度通知](../articles/iot-hub/media/iot-hub-create-hub-and-device/3_notification-azure-iot-hub-creation-progress-portal.png)

4. 创建 IoT 中心后，请在仪表板中单击它。 记下“主机名”，并单击“共享访问策略”。

   ![获取 IoT 中心的主机名](../articles/iot-hub/media/iot-hub-create-hub-and-device/4_get-azure-iot-hub-hostname-portal.png)

5. 在“共享访问策略”窗格中单击“iothubowner”策略，复制并记下 IoT 中心的**连接字符串**。 有关详细信息，请参阅[控制对 IoT 中心的访问](../articles/iot-hub/iot-hub-devguide-security.md)。

> [!NOTE] 
此设置教程不需要此 iothubowner 连接字符串。 不过，在完成此设置以后，可能需要将其用于某些讲述其他 IoT 方案的教程。

   ![获取 IoT 中心连接字符串](../articles/iot-hub/media/iot-hub-create-hub-and-device/5_get-azure-iot-hub-connection-string-portal.png)

## <a name="register-a-device-in-the-iot-hub-for-your-device"></a>在 IoT 中心为设备进行设备注册

1. 在 [Azure 门户](https://portal.azure.com/)中打开 IoT 中心。

2. 单击“设备资源管理器”。
3. 在“设备资源管理器”窗格中，单击“添加”将设备添加到 IoT 中心。 然后执行以下操作：

   **设备 ID**：输入新设备的 ID。 设备 ID 区分大小写。

   **身份验证类型**：选择“对称密钥”。

   **自动生成密钥**：选中此复选框。

   **将设备连接到 IoT 中心**：单击“启用”。

   ![在 IoT 中心的设备资源管理器中添加设备](../articles/iot-hub/media/iot-hub-create-hub-and-device/6_add-device-in-azure-iot-hub-device-explorer-portal.png)

   [!INCLUDE [iot-hub-pii-note-naming-device](iot-hub-pii-note-naming-device.md)]

4. 单击“保存” 。
5. 创建设备后，在“设备资源管理器”窗格中打开设备。
6. 记下连接字符串的主密钥。

   ![获取设备连接字符串](../articles/iot-hub/media/iot-hub-create-hub-and-device/7_get-device-connection-string-in-device-explorer-portal.png)
