BLE（Bluetooth Low Energy）低功耗蓝牙，传输速率低，适合用在可穿戴设备或者物联网上。

GATT：通用属性配置文件，建立在ATT协议基础上，对ATT进行进一步的逻辑封装，定义数据的交换方式和含义。GATT按照层级定义了三个概念，服务（Service）、特征\(Characteristic\)、描述（Descriptor）。一个 Service 包含若干个 Characteristic，一个 Characteristic 可以包含若干 Descriptor。而 Characteristic 定义了数值和操作。Characteristic 的操作这几种权限：读、写、通知等权限。

Profile配置文件，把若干个相关的 Service 组合在一起，就成为了一个 Profile，Profile 就是定义了一个实际的应用场景。

UUID：128位，8-4-4-12 hex，Service、Characteristic 还有 Descriptor 都是使用 UUID 唯一标示的。

