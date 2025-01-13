---
Arduino IDE 1.8.19,基于 **ESP8266** 的 **本地网页游戏中心服务器**，主要功能是为用户提供一个通过 Wi-Fi 热点访问的网页游戏平台。
Arduino IDE 1.8.19, based on the **ESP8266**, creates a **local web game center server**. Its main functionality is to provide users with a web-based game platform accessible via a Wi-Fi hotspot.


https://github.com/user-attachments/assets/05e5b457-cc3b-47b1-af55-9ce356506980


![_cgi-bin_mmwebwx-bin_webwxgetmsgimg__ MsgID=7455071154444351074 skey=@crypt_1aa0a47_e7a3109856102f4eb19f35727984888b mmweb_appid=wx_webfilehelper](https://github.com/user-attachments/assets/c50c84e4-b75e-4014-ab73-653fae0eb071)

![_cgi-bin_mmwebwx-bin_webwxgetmsgimg__ MsgID=5647126113885545366 skey=@crypt_1aa0a47_e7a3109856102f4eb19f35727984888b mmweb_appid=wx_webfilehelper](https://github.com/user-attachments/assets/c983f6c6-3b0f-4566-ae84-5fc9eb68488a)
![image](https://github.com/user-attachments/assets/830453c1-afed-462f-92e7-4f4e6ee0fbe3)

![image](https://github.com/user-attachments/assets/cc857d7b-797d-4b1f-a9f1-ce7bfb9ef9ec)

![image](https://github.com/user-attachments/assets/52616fa8-cb0a-499c-8934-c5ea42badbac)
![image](https://github.com/user-attachments/assets/913a894b-a321-46e7-a62d-fe9c8ce70988)

### **版权声明 / Copyright Notice**

#### **游戏版权 / Game Copyright**
- **data文件夹里面的网页小游戏，版权归原作者所有，本代码基于演示目的使用。**  
  The web games in the `data` folder are copyrighted by their original authors. This code is used for demonstration purposes only.  
- **由于人数众多，不一一申明列举，一并感谢！**  
  Due to the large number of contributors, we are unable to list everyone individually. We extend our gratitude to all!  
- **游戏来源：https://js13kgames.com/**  
  Game Source: https://js13kgames.com/  

---

#### **代码及衍生数字资产 / Code and Derivative Digital Assets**
- **代码及衍生数字资产使用了本人创意，交由AI撰写。**  
  The code and derivative digital assets are based on my creative ideas and were written by AI.  
- **本人自愿放弃其所有权，任何组织和个人均可无前提条件以任何形式拷贝及使用，本人不保留任何途径和形式的追诉权利。**  
  I voluntarily waive ownership rights. Any organization or individual may copy and use the code in any form without any preconditions. I do not retain any rights to pursue legal action through any means.  

---

#### **代码工具 / Code Tools**
- **代码部分工具：**  
  Tools used for the code:  
  - https://www.deepseek.com/  
  - https://tongyi.aliyun.com/  
  - https://www.doubao.com/chat/  

---

#### **其他资源 / Other Resources**
- **其他部分：**  
  Other resources used:  
  - https://js13kgames.com/  
  - https://www.aconvert.com/cn/audio/extract/  
  - https://www.freeconvert.com/zh/mp3-compressor  
  - https://www.mianfeiziti.com/font_preview-961.htm  
  - https://www.bilibili.com/video/BV17bpJeNEzb/
---

### **声明结束 / End of Notice**

---
### **核心功能与使用说明**

#### **1. Wi-Fi 热点创建**
- **功能**：
  - ESP8266 创建一个名为“瑜神游戏中心服务器”的 Wi-Fi 热点。
- **使用说明**：
  1. 将代码上传到 ESP8266 开发板。
  2. 打开手机或电脑的 Wi-Fi 设置，搜索并连接名为“瑜神游戏中心服务器”的热点。
  3. 连接成功后，打开浏览器，访问 `192.168.4.1`（ESP8266 的默认 IP 地址）。

#### **(2) 文件系统管理**
- **功能**：使用 SPIFFS（SPI Flash File System）存储和管理网页文件（如 HTML、CSS、JS、音频、图片等）。
- **实现**：
  - 初始化 SPIFFS：`SPIFFS.begin()`。
  - 遍历文件系统，查找游戏文件（如 `index.html`），并将文件信息存储在 `fileList` 数组中。

#### **(3) 网页服务**
- **功能**：提供静态文件服务（如 HTML、CSS、JS）和动态接口（如 `/files` 获取文件列表）。
- **实现**：
  - 使用 `ESP8266WebServer` 处理 HTTP 请求。
  - 支持根路径 `/`、文件列表接口 `/files` 和静态文件请求。

#### **(4) 动态文件列表**
- **功能**：动态加载 SPIFFS 中的游戏文件列表，并通过 JSON 格式返回给前端。
- **实现**：
  - 遍历 SPIFFS 文件系统，获取游戏文件路径和名称。
  - 通过 `/files` 接口返回文件列表。

#### **(5) 炫酷加载动画**
- **功能**：前端页面包含复杂的加载动画和交互效果，提升用户体验。
- **实现**：
  - 使用 HTML、CSS 和 JavaScript 实现加载动画。
  - 支持音效播放和全屏模式。

---

### **2. 实现目标**

#### **(1) 本地化游戏中心**
- 提供一个无需互联网的本地游戏平台，用户通过连接 Wi-Fi 热点即可访问。
- 支持多种网页小游戏，点击即可开始。

#### **(2) 动态加载游戏**
- 游戏文件存储在 ESP8266 的 SPIFFS 文件系统中，服务器动态加载并展示游戏列表。
- 支持最多 120 个游戏文件。

#### **(3) 优化用户体验**
- 提供炫酷的加载动画和音效，提升用户参与感。
- 支持全屏模式，增强游戏沉浸感。

#### **(4) 教育与演示**
- 作为物联网（IoT）和网页开发的示例项目，展示 ESP8266 的文件管理和网络服务能力。
- 适合用于教学、演示或个人学习。

---

### **3. 适用场景**

#### **(1) 家庭娱乐**
- 为孩子或朋友提供本地游戏服务，无需互联网即可畅玩。

#### **(2) 教育演示**
- 用于物联网和网页开发的教学，展示 ESP8266 的功能和应用。

### **4. 代码模块概述**

| 模块名称             | 功能描述                                                                 |
|----------------------|--------------------------------------------------------------------------|
| **初始化模块**       | 初始化 SPIFFS、创建 Wi-Fi 热点、启动 HTTP 服务器。                        |
| **文件系统遍历模块** | 递归遍历 SPIFFS 文件系统，获取游戏文件列表。                              |
| **HTTP 请求处理模块**| 处理客户端请求，返回 HTML 页面、JSON 数据或文件内容。                     |
| **前端页面模块**     | 提供炫酷的加载动画、文件列表展示和全屏模式。                              |
| **动态文件列表模块** | 动态加载游戏文件列表，并通过 `/files` 接口返回 JSON 数据。                |

### **详细使用步骤**

#### **1. 硬件准备**
- 准备一块 ESP8266 开发板（如 NodeMCU 或 Wemos D1 Mini）。
- 通过 USB 数据线将开发板连接到电脑。

#### **2. 软件准备**
- 安装 Arduino IDE。
- 安装 ESP8266 开发板支持包。
- 安装 SPIFFS 文件上传工具（ESP8266 Sketch Data Upload）。

#### **3. 上传代码**
1. 打开 Arduino IDE，将代码复制到新项目中。
2. 选择正确的开发板和端口。
3. 点击 **上传**，将代码上传到 ESP8266。

#### **4. 上传文件到 SPIFFS**
1. 在 Arduino IDE 中，点击 **工具** > **ESP8266 Sketch Data Upload**。
2. 将游戏文件（如 HTML、CSS、JS、音频、图片等）放入项目的 `data` 文件夹中。
3. 点击 **上传**，将文件上传到 SPIFFS。

#### **5. 连接与访问**
1. 打开手机或电脑的 Wi-Fi 设置，连接名为“瑜神游戏中心服务器”的热点。
2. 打开浏览器，访问 `192.168.4.1`。
3. 等待加载动画完成后，即可看到游戏列表并开始游戏。

---

### **注意事项**
1. **文件数量限制**：最多支持 120 个游戏文件，确保文件数量不超过限制。
2. **文件命名规范**：每个游戏文件夹中必须包含一个 `index.html` 文件，作为游戏的入口。
3. **SPIFFS 空间限制**：ESP8266 的 SPIFFS 空间有限（通常为 3MB），请合理分配文件大小。
4. **热点范围**：Wi-Fi 热点的覆盖范围有限，建议在近距离使用。

---
---
### **Core Features and Usage Instructions**

#### **1. Wi-Fi Hotspot Creation**
- **Functionality**:
  - The ESP8266 creates a Wi-Fi hotspot named "Yu Shen Game Center Server."
- **Usage Instructions**:
  1. Upload the code to the ESP8266 development board.
  2. Open the Wi-Fi settings on your phone or computer, search for, and connect to the hotspot named "Yu Shen Game Center Server."
  3. After successfully connecting, open a browser and visit `192.168.4.1` (the default IP address of the ESP8266).

#### **(2) File System Management**
- **Functionality**: Use SPIFFS (SPI Flash File System) to store and manage web files (e.g., HTML, CSS, JS, audio, images, etc.).
- **Implementation**:
  - Initialize SPIFFS: `SPIFFS.begin()`.
  - Traverse the file system to locate game files (e.g., `index.html`) and store their information in the `fileList` array.

#### **(3) Web Service**
- **Functionality**: Provide static file services (e.g., HTML, CSS, JS) and dynamic interfaces (e.g., `/files` to retrieve the file list).
- **Implementation**:
  - Use `ESP8266WebServer` to handle HTTP requests.
  - Support for root path `/`, file list interface `/files`, and static file requests.

#### **(4) Dynamic File List**
- **Functionality**: Dynamically load the list of game files from SPIFFS and return it to the front end in JSON format.
- **Implementation**:
  - Traverse the SPIFFS file system to retrieve game file paths and names.
  - Return the file list via the `/files` interface.

#### **(5) Cool Loading Animation**
- **Functionality**: The front-end page includes complex loading animations and interactive effects to enhance user experience.
- **Implementation**:
  - Use HTML, CSS, and JavaScript to implement loading animations.
  - Support audio playback and full-screen mode.

---

### **2. Implementation Goals**

#### **(1) Localized Game Center**
- Provide a local game platform that does not require an internet connection; users can access it by connecting to the Wi-Fi hotspot.
- Support multiple web-based mini-games that can be started with a click.

#### **(2) Dynamic Game Loading**
- Game files are stored in the ESP8266's SPIFFS file system, and the server dynamically loads and displays the game list.
- Support for up to 120 game files.

#### **(3) Optimized User Experience**
- Provide cool loading animations and sound effects to enhance user engagement.
- Support full-screen mode to enhance game immersion.

#### **(4) Education and Demonstration**
- Serve as an example project for IoT and web development, showcasing the file management and network service capabilities of the ESP8266.
- Suitable for teaching, demonstrations, or personal learning.

---

### **3. Applicable Scenarios**

#### **(1) Family Entertainment**
- Provide local game services for children or friends, allowing them to play without an internet connection.

#### **(2) Educational Demonstrations**
- Use for teaching IoT and web development, demonstrating the functionality and applications of the ESP8266.

### **4. Code Module Overview**

| Module Name             | Description                                                                 |
|-------------------------|-----------------------------------------------------------------------------|
| **Initialization Module**       | Initialize SPIFFS, create a Wi-Fi hotspot, and start the HTTP server.       |
| **File System Traversal Module** | Recursively traverse the SPIFFS file system to retrieve the game file list. |
| **HTTP Request Handling Module**| Handle client requests, return HTML pages, JSON data, or file content.      |
| **Front-End Page Module**     | Provide cool loading animations, file list display, and full-screen mode.   |
| **Dynamic File List Module** | Dynamically load the game file list and return JSON data via the `/files` interface. |

### **Detailed Usage Steps**

#### **1. Hardware Preparation**
- Prepare an ESP8266 development board (e.g., NodeMCU or Wemos D1 Mini).
- Connect the development board to your computer via a USB cable.

#### **2. Software Preparation**
- Install Arduino IDE.
- Install the ESP8266 development board support package.
- Install the SPIFFS file upload tool (ESP8266 Sketch Data Upload).

#### **3. Upload the Code**
1. Open Arduino IDE, copy the code into a new project.
2. Select the correct development board and port.
3. Click **Upload** to upload the code to the ESP8266.

#### **4. Upload Files to SPIFFS**
1. In Arduino IDE, click **Tools** > **ESP8266 Sketch Data Upload**.
2. Place game files (e.g., HTML, CSS, JS, audio, images, etc.) into the `data` folder of the project.
3. Click **Upload** to upload the files to SPIFFS.

#### **5. Connect and Access**
1. Open the Wi-Fi settings on your phone or computer, and connect to the hotspot named "Yu Shen Game Center Server."
2. Open a browser and visit `192.168.4.1`.
3. After the loading animation completes, the game list will be displayed, and you can start playing.

---

### **Notes**
1. **File Quantity Limit**: Supports up to 120 game files; ensure the number of files does not exceed this limit.
2. **File Naming Convention**: Each game folder must contain an `index.html` file as the entry point for the game.
3. **SPIFFS Space Limit**: The ESP8266's SPIFFS space is limited (typically 3MB); allocate file sizes appropriately.
4. **Hotspot Range**: The Wi-Fi hotspot has a limited range; it is recommended to use it at close proximity.

---
