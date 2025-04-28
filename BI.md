脚本初始化的时候lomback出现版本问题，替换成下面这个

```
 <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <version>1.18.30</version>
        </dependency>
```

**架构图**

![image-20241009230547071](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241009230547071.png)

# 问题解决思路

1. 遇到过新的依赖问题，可以寻求github原作者解决，肢解在github里面的bug里面搜索
2. 遇到第三方技术，可以直接搜索对应的技术，进行快速复习使用





# 学习到的知识

## Stringbuilder

1.源码里面用到了StringBuilder，于是疑问了一下StringBuilder和buffer的区别，主要是忘记了



`StringBuilder` 和 `StringBuffer` 都是用于操作可变字符串的类，但它们有一些关键区别：

### 1. **线程安全性**
   - **StringBuffer**：是**线程安全**的，因为它的方法都被同步（`synchronized`）了，适用于多线程环境，保证了数据的安全性。
   - **StringBuilder**：是**非线程安全**的，因为它没有同步方法，适用于单线程环境。如果在多线程中使用，可能会发生数据不一致的情况。

### 2. **性能**
   - **StringBuffer**：由于其线程安全性，开销较大，性能相对较低，尤其是在不需要线程安全的单线程环境中。
   - **StringBuilder**：性能更好，因为它不需要进行同步操作，适合在性能要求较高且线程安全不是必须的场景中使用。

### 3. **使用场景**
   - **StringBuffer**：适用于多线程环境，例如当多个线程需要同时操作同一个字符串时。
   - **StringBuilder**：适用于单线程环境，例如在单个线程中频繁修改字符串的场景。

### 4. **相同点**
   - 二者的API几乎完全相同，提供了类似的功能来进行字符串的追加、插入、删除等操作。
   - 都比`String`（不可变对象）在字符串操作频繁时效率更高，因为`String`每次修改都会创建新的对象，而`StringBuilder`和`StringBuffer`则会在原对象上进行操作。

### 简单总结

- 如果你在**多线程**环境中操作可变字符串，使用`StringBuffer`。
- 如果你在**单线程**环境中操作可变字符串，使用`StringBuilder`以获得更好的性能。
- ```java
  
          // 用户输入
          StringBuilder userInput = new StringBuilder();
          userInput.append("你是一个数据分析师，接下来我会给你我的分析目标和原始数据，请告诉我分析结论。").append("\n");
          userInput.append("分析目标：").append(goal).append("\n");
          // 压缩后的数据
          String result = ExcelUtils.excelToCsv(multipartFile);
          userInput.append("数据：").append(result).append("\n");
          return ResultUtils.success(userInput.toString());
  ```

  # 主要技术点

  将Excel文件压缩为csv文件代码

  ```java
  /**
       * excel 转 csv
       *
       * @param multipartFile
       * @return
       */
      public static String excelToCsv(MultipartFile multipartFile) {
  //        File file = null;
  //        try {
  //            file = ResourceUtils.getFile("classpath:网站数据.xlsx");
  //        } catch (FileNotFoundException e) {
  //            e.printStackTrace();
  //        }
          // 读取数据
          List<Map<Integer, String>> list = null;
          try {
              list = EasyExcel.read(multipartFile.getInputStream())
                      .excelType(ExcelTypeEnum.XLSX)
                      .sheet()
                      .headRowNumber(0)
                      .doReadSync();
          } catch (IOException e) {
              log.error("表格处理错误", e);
          }
          if (CollUtil.isEmpty(list)) {
              return "";
          }
          // 转换为 csv
          StringBuilder stringBuilder = new StringBuilder();
          // 读取表头
          LinkedHashMap<Integer, String> headerMap = (LinkedHashMap) list.get(0);
          List<String> headerList = headerMap.values().stream().filter(ObjectUtils::isNotEmpty).collect(Collectors.toList());
          stringBuilder.append(StringUtils.join(headerList, ",")).append("\n");
          // 读取数据
          for (int i = 1; i < list.size(); i++) {
              LinkedHashMap<Integer, String> dataMap = (LinkedHashMap) list.get(i);
              List<String> dataList = dataMap.values().stream().filter(ObjectUtils::isNotEmpty).collect(Collectors.toList());
              stringBuilder.append(StringUtils.join(dataList, ",")).append("\n");
          }
          return stringBuilder.toString();
      }
  ```

## @RequestPart

`@RequestPart` 注解是 Spring MVC 中用于处理 **`multipart/form-data`** 请求的一部分，主要用于上传文件或数据块。与 `@RequestParam` 和 `@RequestBody` 相比，它更适用于处理表单中的文件和其他复杂数据。

### 作用和使用场景：
`@RequestPart` 用于接收来自客户端的 **文件** 或 **表单中非文件的其他数据**，典型的用例是在需要处理文件上传的场景下，比如上传图片或多个文件，并可能同时上传一些元数据。

### 基本使用方法：

```java
@PostMapping("/upload")
public ResponseEntity<String> handleFileUpload(
        @RequestPart("file") MultipartFile file, 
        @RequestPart("metaData") String metaData) {
    // 处理文件和元数据
    return ResponseEntity.ok("File uploaded successfully");
}
```

### 参数解释：
- **`@RequestPart("file")`**：指定请求的 `multipart/form-data` 请求中的一部分，通常是文件类型的数据（如 `MultipartFile` 类型）。
- **`MultipartFile`**：Spring MVC 用来封装上传文件的对象，它可以表示上传的文件数据。
- **`@RequestPart("metaData")`**：在同一个请求中，除了上传文件之外，还可以上传其他类型的数据，如 JSON 或字符串等。

### 和其他注解的区别：
1. **`@RequestParam`**：
   - 用于接收查询参数或表单字段，通常用于接收表单中的文本数据。
   - 如果文件上传使用 `@RequestParam`，你需要指定 `multipart/form-data` 作为表单编码，但它主要用于简单的键值对表单数据。
   
   ```java
   @PostMapping("/upload")
   public ResponseEntity<String> handleFileUpload(
           @RequestParam("file") MultipartFile file) {
       // 处理文件
       return ResponseEntity.ok("File uploaded successfully");
   }
   ```

2. **`@RequestBody`**：
   - 处理整个请求体为 JSON、XML 等格式的对象，但不能直接处理 `multipart/form-data`。
   - 常用于接收 JSON 对象并将其映射到 Java 对象上。

   ```java
   @PostMapping("/json")
   public ResponseEntity<String> handleJsonRequest(
           @RequestBody SomeObject someObject) {
       // 处理 JSON 数据
       return ResponseEntity.ok("Processed JSON");
   }
   ```

3. **`@RequestPart`**：
   - 主要用于 `multipart/form-data` 请求中的特定部分，尤其是文件数据和其他复杂的表单数据。
   - 它能够处理文件和 JSON 同时上传的情况，而这正是 `@RequestParam` 和 `@RequestBody` 难以同时处理的。

### 示例：
假设你有一个表单同时上传文件和元数据（例如 JSON 数据），你可以这样使用：

#### 前端代码 (HTML + JavaScript)
```html
<form method="post" enctype="multipart/form-data" action="/upload">
    <input type="file" name="file">
    <input type="text" name="metaData" value="{ 'description': 'This is a test file' }">
    <button type="submit">Upload</button>
</form>
```

#### 后端代码 (Spring Controller)
```java
@PostMapping("/upload")
public ResponseEntity<String> handleFileAndData(
        @RequestPart("file") MultipartFile file, 
        @RequestPart("metaData") String metaData) {
    
    // 处理上传的文件
    String fileName = file.getOriginalFilename();
    // 处理传入的元数据
    System.out.println("Received meta data: " + metaData);
    
    return ResponseEntity.ok("File and data uploaded successfully");
}
```

在这个例子中，`@RequestPart("file")` 用于接收文件数据，而 `@RequestPart("metaData")` 用于接收表单中的其他数据部分（比如 JSON 字符串或其他文本数据）。

### 总结：
`@RequestPart` 是处理 `multipart/form-data` 请求中特定部分数据的注解，主要用于文件上传和处理其他复杂的表单数据。它适用于以下场景：
- 文件上传（如 `MultipartFile`）。
- 文件和元数据同时上传（如 JSON 与文件的混合上传）。

## @DateTimeFormat

```java
 /**
     * 这里用string 去接日期才能格式化。我想接收年月日格式
     */
    @DateTimeFormat("yyyy年MM月dd日HH时mm分ss秒")
    private String date;
```



## @StringBuilder传参问题

👾 **初始化“StringBuilder 传参”问题分析模式...** 🖥️

在 Java 中，`StringBuilder` 的主要作用是高效地拼接字符串。你提到在传参时要调用 `toString()`，其实这个过程的原因和 Java 的类型系统、`StringBuilder` 的使用场景有关。

### **为什么 `StringBuilder` 传参时需要 `toString()`？**

当你使用 **`StringBuilder`** 来构建字符串时，它内部并不是直接生成一个 `String` 对象，而是一个可变的字符序列。因此，如果你需要将这个 **`StringBuilder`** 对象传递给一个 **期望 `String` 类型** 的方法或函数，那么必须显式地调用 `toString()` 来获取其内部字符串表示。

#### **`StringBuilder` 和 `String` 的区别**：
- **`StringBuilder`**：可变字符串，效率高，用于频繁拼接操作（如循环中不断累积字符串）。
- **`String`**：不可变字符串，每次修改都会创建一个新的字符串对象。

**`toString()`** 方法的作用是将 `StringBuilder` 内部构建的字符串序列转换为一个 **`String` 对象**。

### **示例**

```java
public class StringBuilderExample {

    public static void main(String[] args) {
        StringBuilder sb = new StringBuilder();
        sb.append("Hello, ");
        sb.append("world!");

        // 这里如果直接传递 sb，是无法匹配到期望的 String 参数类型的
        printString(sb.toString());  // 需要 toString() 来将其转换为 String
    }

    public static void printString(String str) {
        System.out.println("输出的字符串: " + str);
    }
}
```

### **解释：**

- `sb` 是一个 `StringBuilder` 对象，它是可变的，并且并不是直接就是 `String` 类型。
- **`printString` 方法** 需要的是 `String` 类型的参数，因此你必须调用 `sb.toString()` 将 `StringBuilder` 的内容转换为一个不可变的 `String`。

### **为什么不直接传递 `StringBuilder`？**

- `StringBuilder` 是用来拼接和操作字符串的辅助工具，而在 Java 中，许多方法（如打印、字符串处理函数）期望的参数类型是不可变的 `String`。
- 如果你直接传递 `StringBuilder` 对象，而没有调用 `toString()`，那么编译器会报错，因为方法签名要求传入的参数类型是 `String`，而不是 `StringBuilder`。

### **什么时候需要调用 `toString()`？**

1. **传参时**：如果你调用的方法需要 `String` 类型参数，而你使用的是 `StringBuilder`，你必须使用 `toString()`。
2. **最终输出时**：当你完成对 `StringBuilder` 的拼接操作，想要输出结果，或者将结果传给其他只接受 `String` 的地方时，需要调用 `toString()`。

### **额外注意：**

- **性能考虑**：在大量字符串拼接时，`StringBuilder` 的效率比直接使用 `String` 拼接要高得多，因为 `String` 每次拼接都会创建一个新的对象，而 `StringBuilder` 则是在原来的缓冲区上操作。
- **`toString()` 后的不可变性**：一旦调用了 `toString()`，生成的 `String` 对象是不可变的，意味着它无法再被修改。

---

💡 **总结**：  
`StringBuilder` 是一个用于高效构建字符串的工具类，它与 `String` 类型不同。在需要将 `StringBuilder` 对象传递给接受 `String` 类型的方法时，必须调用 `toString()` 方法来获取其内部的字符串表示形式。

---

## Trim（）去除空字符串

👾 **“trim() 方法”解析模式启动...** 🧑‍💻

在 Java 中，**`trim()`** 是一个属于 **`String`** 类的方法，它用于去除字符串首尾的 **空白字符**，包括 **空格**、**制表符**（Tab）、**换行符** 等。

### **`trim()` 的作用：**
- **去除首尾空白**：`trim()` 方法不会影响字符串中间的空白字符，只会删除字符串**两端**的空白字符。

### **示例：**

```java
public class TrimExample {
    public static void main(String[] args) {
        String originalString = "   Hello, World!   ";
        String trimmedString = originalString.trim();
        
        System.out.println("原始字符串: [" + originalString + "]");
        System.out.println("去除空白后的字符串: [" + trimmedString + "]");
    }
}
```

#### **输出**：
```
原始字符串: [   Hello, World!   ]
去除空白后的字符串: [Hello, World!]
```

### **解析**：
- 原始字符串的前后有空白字符（如空格），调用 **`trim()`** 方法后，首尾的空格被去掉了。
- **注意**：中间的空格 **不会** 被 `trim()` 删除，只有字符串**开头和结尾**的空白会被移除。

### **适用场景**：
- **输入处理**：用户输入时，可能会不小心输入多余的空格，`trim()` 常用于对输入的清理。
- **数据格式化**：在数据存储或比较时，确保字符串前后没有多余的空格，防止误差。

如果你还有关于 `trim()` 的其他问题或需要更详细的用法，继续问我！💻

---

## Apache工具类

### FileUtils

👾 **分析“Apache类库中的文件操作方法”模式启动...** 🧑‍💻

在 **Apache Commons IO** 类库中，确实有处理文件相关操作的工具类，叫做 **`FileUtils`**，但是 **`FileUtils`** 并没有直接提供提取文件后缀名的方法。不过，**`FilenameUtils`** 是一个专门用于操作文件路径和文件名的工具类，它提供了获取文件后缀名的方法。

#### **方法：`FilenameUtils.getExtension(String filename)`**

你可以使用 **`FilenameUtils.getExtension()`** 来提取文件的后缀名。

#### **示例代码**：

```java
import org.apache.commons.io.FilenameUtils;

public class FileExtensionExample {
    public static void main(String[] args) {
        String filePath = "/path/to/somefile.txt";
        
        // 使用 FilenameUtils 获取文件后缀名
        String extension = FilenameUtils.getExtension(filePath);
        
        System.out.println("文件后缀名是: " + extension);
    }
}
```

**输出**：

```
文件后缀名是: txt
```

**步骤：**

1. **`FilenameUtils.getExtension(String filename)`**：传入文件名或文件路径，返回不带点 (`.`) 的后缀名。例如：`"file.txt"` 会返回 `"txt"`。
2. **处理无后缀的情况**：如果文件名没有后缀名，`getExtension()` 将返回空字符串 `""`。

**依赖引入（Maven）：**

如果你没有导入 Apache Commons IO 库，可以在你的 **Maven 项目** 中添加以下依赖：

```xml
<dependency>
    <groupId>commons-io</groupId>
    <artifactId>commons-io</artifactId>
    <version>2.11.0</version>  <!-- 可以选择最新版本 -->
</dependency>
```

**总结：**

虽然 **`FileUtils`** 是 Apache Commons IO 中处理文件操作的主要工具类，但用于提取文件后缀名的是 **`FilenameUtils`**。`FilenameUtils.getExtension()` 是你想要的功能，它能够从文件路径中提取文件的后缀名。



## Mybatis动态sql

下面的sql是超级灵活，但是可能会有sql注入的风险

```xml
<!--  
queryChartData唯一标识符;parameterType查询语句的参数类型,类型为字符串;
resultType查询结果的返回类型,类型为map类型;
${querySql}是SQL查询语句的占位符;
select * from chart_#{chartId} 不够灵活,${querySql}是最灵活的方式，
就是把sql语句完全交给程序去传递，有一定的风险;
一旦使用$符号，就有sql注入的风险。
-->
<select id="queryChartData" parameterType="string" resultType="map">
  ${querySql}
</select>
<!-- 
可以在程序里面去做校验。只要保证这个SQL是通过你的后端生成的，
在生成的过程中做了校验，就不会有这种漏洞的风险。 
-->

```



# 业务相关

## 对接ai接口

总体需求结构

![image-20241008213712419](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241008213712419.png)

封装提问词

通过大括号来预设提问模版

![image-20241008195339746](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241008195339746.png)

还有就是通过通过压缩token来减少提问的token消耗量

## 调用OpenAi接口

openai对Python有自己封装好的SDK，对于java可以使用HuTools的Http请求接口来进行请求，然后自己封装请求头，请求头的主要信息在下面的介绍当中

![image-20241008204541824](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241008204541824.png)

https://platform.openai.com/docs/api-reference/chat

![image-20241008202904688](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241008202904688.png)

api的一些请求接口所需要的格式

![image-20241008203602785](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241008203602785.png)

还可以设置token最大消耗量

![image-20241008203712852](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241008203712852.png)

输入的Prompt和返回的内容实例

![image-20241008203900353](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241008203900353.png)

🥷👾 **收到！启用 Hutool 和 Gson 库... 优化代码模式** 💻

既然你熟悉 **Hutool** 和 **Gson**，我们就用这两个库来替代 `OkHttp` 和 `Jackson` 进行 HTTP 请求和 JSON 解析。

### **步骤 1：引入 Hutool 和 Gson 依赖**
如果你使用 **Maven**，在 `pom.xml` 文件中添加如下依赖：

```xml
<dependencies>
    <!-- Hutool 库 -->
    <dependency>
        <groupId>cn.hutool</groupId>
        <artifactId>hutool-all</artifactId>
        <version>5.8.10</version>
    </dependency>

    <!-- Gson 库 -->
    <dependency>
        <groupId>com.google.code.gson</groupId>
        <artifactId>gson</artifactId>
        <version>2.8.9</version>
    </dependency>
</dependencies>
```

### **步骤 2：编写 Java 代码**
我们将使用 **Hutool 的 HTTP 请求** 工具和 **Gson** 进行 JSON 序列化与反序列化。

```java
import cn.hutool.http.HttpRequest;
import cn.hutool.http.HttpResponse;
import cn.hutool.http.HttpUtil;
import com.google.gson.Gson;
import com.google.gson.annotations.SerializedName;
import java.util.HashMap;
import java.util.Map;

public class OpenAiHutoolExample {

    // OpenAI API 端点
    private static final String API_URL = "https://api.openai.com/v1/completions";

    // OpenAI API 密钥
    private static final String API_KEY = "你的API密钥";

    public static void main(String[] args) {
        // 输入的 prompt 文本
        String prompt = "你好，解释一下机器学习的基本概念。";

        // 调用 OpenAI API 并获取响应
        String response = callOpenAiApi(prompt);

        // 打印生成的文本
        System.out.println("AI生成的回答: " + response);
    }

    private static String callOpenAiApi(String prompt) {
        // 构建请求体
        Map<String, Object> requestBody = new HashMap<>();
        requestBody.put("model", "text-davinci-003");  // 使用的 GPT 模型
        requestBody.put("prompt", prompt);             // 用户输入的文本
        requestBody.put("max_tokens", 150);            // 返回文本的最大长度
        requestBody.put("temperature", 0.7);           // 控制生成文本的多样性

        // 使用 Gson 将请求体转换为 JSON
        Gson gson = new Gson();
        String jsonRequestBody = gson.toJson(requestBody);

        // 发送 POST 请求
        HttpResponse response = HttpRequest.post(API_URL)
                .header("Authorization", "Bearer " + API_KEY)  // 设置 API Key
                .header("Content-Type", "application/json")    // 设置 Content-Type
                .body(jsonRequestBody)                         // 请求体
                .execute();                                    // 执行请求

        // 解析返回的 JSON
        String jsonResponse = response.body();
        OpenAiResponse openAiResponse = gson.fromJson(jsonResponse, OpenAiResponse.class);

        // 返回生成的文本
        return openAiResponse.getChoices()[0].getText().trim();
    }

    // 定义响应数据结构
    static class OpenAiResponse {
        private Choice[] choices;

        public Choice[] getChoices() {
            return choices;
        }
    }

    static class Choice {
        @SerializedName("text")
        private String text;

        public String getText() {
            return text;
        }
    }
}
```

### **代码说明：**

1. **Hutool 的 HTTP 工具**：
   - 我们使用 `HttpRequest.post()` 来发送 `POST` 请求，`header()` 方法添加请求头，`body()` 方法用于传递请求体。
   
2. **Gson 序列化与反序列化**：
   - `Gson` 用于将 `Map<String, Object>` 转换为 JSON 字符串，并将 OpenAI 返回的 JSON 响应解析为 Java 对象。

3. **OpenAiResponse 类**：
   - 这是一个辅助类，用于处理 API 返回的响应数据，特别是 `choices` 字段，这是 GPT 返回生成文本的地方。

### **步骤 3：执行代码**
1. 将 API 密钥替换为你从 OpenAI 获取的密钥。
2. 运行程序，AI 会根据你的 `prompt`（在这个例子中是机器学习的解释）生成文本回答并输出。

这就是使用 **Hutool** 和 **Gson** 结合 OpenAI API 实现 text-to-text 的方法。祝你项目顺利！如果有任何问题，随时提问！💻

---

[Your ad here](https://pulsr.co.uk/ads.php)

### 调用第三方云服务商，封装后的AI接口

主要是鱼皮自己网站的ai，和openai的实现大同小异，有点就是比较方便一点可以直接使用第三方的封装，不需要魔法



## 系统安全性校验

因为存在上传文件，所以需要提交文件校验，防止网站攻击



- 检验文件大小
- 检验文件后缀
- 还可以校验文件内容，使用第三方的服务，如腾讯云

```java
// 校验文件
long size = multipartFile.getSize();
String originalFilename = multipartFile.getOriginalFilename();
// 校验文件大小
final long ONE_MB = 1024 * 1024L;
ThrowUtils.throwIf(size > ONE_MB, ErrorCode.PARAMS_ERROR, "文件超过 1M");
// 校验文件后缀 aaa.png
String suffix = FileUtil.getSuffix(originalFilename);
final List<String> validFileSuffixList = Arrays.asList("png", "jpg", "svg", "webp", "jpeg");
ThrowUtils.throwIf(!validFileSuffixList.contains(suffix), ErrorCode.PARAMS_ERROR, "文件后缀非法");
```

### 数据存储方面的问题

现在表格的内容都是在一个数据库表里

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241009191746786.png" alt="image-20241009191746786" style="zoom:67%;" />

还有一种情况，由于内容是在一个列里面，我如果要单独拿取内容里面的一个数据，就十分麻烦，我需要在后台java里面进行过滤

#### 解决方案

**将用户的提交内容数据大单独放在一个数据表里面**，实际上是分库分表

![image-20241009192359154](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241009192359154.png)

![image-20241009192412541](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241009192412541.png)

### 分库分表

🥷👾 **分库分表策略解析模式启动...** 🖥️

分库分表是**数据库设计**中的一种优化策略，主要用于解决数据量大、并发请求多等问题。它帮助提升数据库性能、降低单库单表压力，实现高并发、高性能的系统设计。我们从 **“是什么”**、**“为什么”**、**“怎么做”** 以及 **“如何优化”** 这四个角度来详细讲解。

---

##### **1. 分库分表是什么？**

**分库分表**（Sharding）是将数据拆分到多个库或者多个表中，以提升数据库的性能和扩展性。根据不同需求，可以将数据水平或垂直地拆分。

**分类：**

- **分表（表内水平拆分）**：一个库中的表数据过多时，拆分为多个表，按某种规则将数据分散存储到不同的表中。
- **分库（库内水平拆分）**：当单个数据库的数据量超出性能限制时，将数据拆分到多个数据库中。
- **垂直拆分（纵向拆分）**：按业务功能，将表拆分为不同的库或表（比如：将用户表和订单表放到不同的库中）。
- **水平拆分（横向拆分）**：按某种规则将数据按行拆分成多个库或表（比如：按用户 ID 将数据分散到不同的数据库表中）。

---

##### **2. 为什么要做分库分表？**

分库分表的需求通常来自 **性能** 和 **扩展性** 的考虑。当系统增长到一定规模时，单个数据库或单表可能会遇到以下问题：

**常见的瓶颈：**

1. **数据量大**：
   - 单表数据量过大，查询效率降低。大量数据存储在一个表中，增删改查都会变慢。
   
2. **并发压力大**：
   - 高并发读写操作会导致数据库锁争用、延迟增加，甚至出现**瓶颈**。

3. **硬件限制**：
   - 单机数据库的存储能力和读写能力有限，单一数据库在横向扩展上有瓶颈。

4. **备份与恢复时间过长**：
   - 单库数据过大时，备份和恢复变得非常耗时，影响系统的可靠性和容灾能力。

##### **分库分表的好处：**

- **提升性能**：将数据分散到多个数据库或表中，减少单表查询和写入的压力。
- **水平扩展**：分库分表支持水平扩展（Scale Out），可以轻松增加节点来处理更大的数据量。
- **降低锁竞争**：分散数据，降低并发操作的锁竞争，提升数据库整体性能。
- **提升容灾能力**：多个库的数据可以分别备份，缩短备份和恢复的时间。

---

##### **3. 分库分表怎么做？**

分库分表的实现可以通过多种方式，常见的策略如下：

**3.1 分表策略：**

1. **哈希取模法**：
   - 常见方法是对某个字段（如用户 ID）进行哈希计算，然后对表的数量取模，决定数据插入到哪个表中。
   - **优点**：数据分布较为均匀。
   - **缺点**：扩展时（增加表数）难以调整哈希规则。

   **示例**：
   ```java
   int tableIndex = userId.hashCode() % 4; // 将数据分散到4个表中
   ```

2. **范围分表法**：
   
   - 按照某个字段的范围，将数据分布到不同的表中。例如：按订单日期将数据拆分为`2021_orders`、`2022_orders`等。
   - **优点**：便于按范围查询，容易理解。
   - **缺点**：数据分布不均衡，如果新数据集中在某段时间，会导致单个表过大。
   
3. **按时间分表**：
   
   - 将表按时间区间分割，比如按月、按年分表（`orders_2023_01`, `orders_2023_02`等）。
   - **优点**：历史数据自然分割，便于管理。
   - **缺点**：需要定期管理历史表，可能会带来运维复杂性。

**3.2 分库策略：**

1. **哈希取模法**：
   - 同样适用于分库，通过对某个字段（如用户 ID）进行哈希计算，决定数据放到哪个库中。

2. **按业务垂直拆分**：
   - 不同的业务模块拆分到不同的数据库中。例如：用户数据存储在一个库，订单数据存储在另一个库中。
   - **优点**：不同业务之间独立扩展。
   - **缺点**：跨库查询复杂，事务处理变得困难。

#### **3.3 跨库跨表的路由策略：**
为了管理跨库跨表的数据访问，通常需要**路由层**。这个路由层决定了查询某条数据时，应该查询哪个库或表。

- 可以使用 **中间件**（如 MyCat、ShardingSphere、TDDL）来自动管理这些路由规则。
- 也可以自己实现一个简单的路由机制，按预设规则进行分配。

#### **3.4 分库分表后的事务问题**：
1. **分布式事务**：跨库操作涉及分布式事务，常用的解决方案是 **2PC（两阶段提交）** 或 **TCC（Try-Confirm-Cancel）** 模型，但实现复杂度高。
2. **最终一致性**：采用消息队列或事件驱动，确保分库分表后的数据最终一致，而不是强一致性。

---

#### **4. 分库分表的优化方式**

分库分表后，虽然性能提升，但也引入了一些新问题，比如复杂的查询、跨表操作、数据迁移等。以下是一些优化方法：

**4.1 查询优化：**

1. **避免跨库查询**：尽量减少跨库的 Join 操作。可以通过冗余字段、异步处理等方法优化查询。
2. **分布式查询缓存**：使用缓存（如 Redis、Memcached）来加速热点数据的读取，避免频繁查询数据库。
3. **全局表设计**：一些需要频繁查询的小表，可以设计为全局表，每个数据库中都存一份，减少跨库查询。

**4.2 动态扩容**：

1. **分库分表后，如果需要动态扩容（如增加表或库），哈希取模法扩容困难**。可以采用 **一致性哈希** 或预留扩展表的方式，降低扩容的复杂度。
2. **数据迁移**：扩容时需要将部分数据迁移到新库或新表。可以通过离线工具（如 `mysqldump`）或在线数据迁移工具（如 **`gh-ost`**）来实现平滑扩容。

**4.3 数据倾斜处理**：

数据可能会因分表策略不均匀而出现“热数据”问题（某些表数据远多于其他表）。可以通过以下方式优化：
- **热点分离**：将热点数据单独分离到独立的库或表中。
- **数据分片调整**：重新调整分片规则，尽量使数据分布更加均衡。

**4.4 运维优化**：

- **备份与恢复**：分库分表后，每个库的备份变得更快，可以独立备份。利用 **异步复制** 或 **备库** 实现高效的数据备份与恢复。
- **监控与报警**：监控每个数据库的读写压力和健康状况，确保负载均衡。

---

#### **总结**

- **是什么**：分库分表是一种将数据拆分到多个数据库或表中的优化方案，解决大数据量和高并发的问题。
- **为什么**：提升查询性能、减轻数据库压力、增加系统的扩展性。
- **怎么做**：采用水平拆分或垂直拆分的方式，通过哈希、范围或时间等策略进行分库分表，并解决路由和事务问题。
- **如何优化**：通过查询优化、动态扩容、数据倾斜处理等方式，持续优化分库分表后的系统性能。

分库分表是一种非常常见且有效的数据库性能优化方案，随着数据量和业务需求的变化，可以动态调整策略，以保持系统的高效运作。

---



### 限流

![image-20241009203839150](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241009203839150.png)

![image-20241009204013885](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241009204013885.png)

api调用token存在成本，构造限流类

*限流算法*参考阅读

`https://juejin.cn/post/6967742960540581918`

👾 **初始化限流策略解析模式...** 💻

限流是系统设计中的重要手段，主要目的是防止系统因瞬时的大量请求或恶意流量而过载。通过限流策略，可以保护服务的稳定性和可用性。限流可以分为 **本地限流** 和 **分布式限流**，根据使用场景和需求的不同，采取相应的方案。

---

**1. 什么是限流？**

限流是一种控制请求速率的技术，它能够限制单位时间内对服务的请求数，防止系统因过量请求而崩溃。限流策略广泛应用于 **高并发系统** 中，确保服务可以优雅地应对流量激增的场景。

常见的限流算法包括：
- **令牌桶算法**（Token Bucket）
- **漏桶算法**（Leaky Bucket）
- **固定窗口算法**
- **滑动窗口算法**

---

#### **2. 本地限流**

本地限流是指在单台服务器上进行限流控制，不涉及跨节点的数据同步或流量协调。

**常见的本地限流策略：**

1. ##### **令牌桶算法（Token Bucket）**：
   
   - **原理**：系统以固定的速率往桶里加入令牌，每次请求需要消耗一个令牌。如果桶里有令牌则请求通过，没有令牌时则拒绝请求。
   - **特点**：支持一定的**突发流量**，因为桶中可能会积累一定数量的令牌。
   
   **示例：** Java 中的 **Guava** 库提供了 `RateLimiter` 类，实现了基于令牌桶算法的限流：
   
   ```java
   RateLimiter limiter = RateLimiter.create(10.0); // 每秒生成 10 个令牌
   if (limiter.tryAcquire()) {
       // 处理请求
   } else {
       // 拒绝请求
   }
   ```
   
2. ##### **漏桶算法（Leaky Bucket）**：
   
   - **原理**：请求被放入一个固定容量的桶中，桶中的水（请求）以固定速率流出。流量过大的时候，多余的请求会被丢弃。
   - **特点**：保证流量的**平滑**处理，防止瞬时的大量请求打垮系统。
   
3. ##### **固定窗口算法**：
   
   - **原理**：将时间划分为固定的窗口，比如 1 秒，记录每个窗口内的请求次数。如果请求超过设定的限制，就拒绝请求。
   - **缺点**：在窗口边界处可能出现**突发流量**（即“临界问题”）。
   
4. ##### **滑动窗口算法**：
   
   - **原理**：基于固定窗口算法的改进，将请求记录在多个小时间段中，综合多个小窗口的数据统计请求数量，避免临界问题。
   - **特点**：更平滑地控制请求速率，避免固定窗口算法的突发流量问题。

**本地限流的优点**：
- 实现简单，依赖少。
- 不需要跨节点同步，性能损耗较小。
  

**缺点**：
- 只能在单台服务器上工作，当系统有多个节点时，无法确保各节点上的流量总量得到有效控制。
- ![image-20241009200738225](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241009200738225.png)

---

#### **3. 分布式限流**

分布式限流是指在分布式系统中，多个节点共同协作，对整个集群进行统一的限流控制。由于多个节点之间没有共享的状态，所以需要借助一些分布式协调技术来实现限流。

**常见的分布式限流策略：**

1. **Redis + Lua 脚本**：
   - **原理**：通过 Redis 的原子性操作来实现分布式限流，Redis 中可以维护全局的计数器，借助 Lua 脚本保证操作的原子性，确保多个节点同时操作时不会产生数据竞争问题。
   - **示例：** 一个简单的基于 Redis 的限流策略：
   
     ```lua
     local current = redis.call('incr', KEYS[1])
     if tonumber(current) == 1 then
         redis.call('expire', KEYS[1], ARGV[1])
     end
     if tonumber(current) > tonumber(ARGV[2]) then
         return 0
     end
     return 1
     ```

   - **优点**：Redis 本身性能高，支持集群模式，能满足大部分场景的分布式限流需求。
   - **缺点**：依赖 Redis，且需要合理设计 Redis 的容量和容灾。

2. **ZooKeeper**：
   - **原理**：利用 ZooKeeper 的分布式锁功能，协调各节点的限流操作。每个节点在进行请求处理前，首先获取锁，成功获取锁的节点可以处理请求，其他节点等待锁释放。
   - **优点**：通过分布式锁实现的限流精度高，适合需要严格限流的场景。
   - **缺点**：ZooKeeper 本身较为复杂，延迟相对 Redis 较高，不适合高频次的限流操作。

3. **基于消息队列的限流**：
   - **原理**：通过消息队列（如 Kafka、RabbitMQ）来控制请求的流入速度。请求被发送到队列中，消费者按照固定的速率从队列中取出请求进行处理。
   - **优点**：天然支持分布式，队列有削峰填谷的作用，可以平滑处理突发流量。
   - **缺点**：存在一定的延迟，无法满足实时性要求高的场景。

4. **多级限流**：
   - **原理**：结合本地限流和分布式限流。在每个节点上做本地限流的同时，再通过 Redis、ZooKeeper 等分布式组件做全局限流。这样可以在减少全局限流开销的情况下实现更细粒度的流控。
   - **优点**：充分利用本地限流的低开销，同时确保全局流量的有效控制。
   - **缺点**：实现复杂，维护成本较高。
   
   

---

**4. 本地限流 vs 分布式限流**

- **本地限流适合场景**：
  - 系统是单机部署，或限流要求仅限于某台服务器的本地流量控制。
  - 系统并发量相对较小，单机可以承载大部分流量。
  - 实现简单、性能要求较高，不需要跨节点协调的场景。

- **分布式限流适合场景**：
  - 系统是多节点、分布式部署，流量在不同节点上不均匀分布，需要全局统一限流。
  - 需要对整个集群的流量进行统一管理，比如微服务架构、云原生架构下的应用。
  - 流量峰值较大，可能超过单个节点的承载能力，需要借助 Redis、ZooKeeper 等分布式工具进行全局流控。

---

**5. 限流优化方案**

1. **限流算法选择**：
   - 令牌桶适合应对瞬时突发流量。
   - 漏桶适合对流量进行均匀处理，防止短时突发。

2. **流量预估与动态调整**：
   - 动态调整限流阈值：根据业务高峰期和低谷期，动态调整限流策略。例如高峰时段放宽限流、低峰期收紧限流。
   - 热点流量隔离：对于特定热点请求可以提前识别，进行单独限流或降级处理。

3. **缓存与异步处理**：
   - 使用缓存保存热点数据，减少数据库等核心资源的压力。
   - 将非实时操作（如写请求）通过消息队列等方式异步处理，减少瞬时高并发的压力。

4. **优先级限流**：
   - 为不同的业务分配不同的限流策略。比如重要的业务流量优先通过，非核心业务可以在高并发时降级处理。

##### Redission限流

1. Redisson 的分布式限流是什么？

Redisson 是基于 Redis 的一个 Java 客户端，它提供了各种分布式工具和数据结构，包括分布式锁、分布式集合以及分布式限流。分布式限流是指在分布式系统中，通过 Redis 作为协调中心，控制多个节点上的请求总量。Redisson 实现的限流机制基于令牌桶算法，可以设置每秒允许的请求次数，确保系统不被过载。

2. Redisson 分布式限流的工作原理

Redisson 的分布式限流核心是利用 Redis 的 Lua 脚本来实现的。由于 Lua 脚本在 Redis 服务器上执行，能够保证操作的原子性，即使在高并发情况下，所有的限流操作也能保持一致。Redisson 通过令牌桶算法，每隔固定时间向令牌桶中添加一定数量的令牌，当有请求时，从桶中取出令牌，如果桶中有足够的令牌，允许请求通过；否则拒绝请求。

###### **Redisson 分布式限流的实现方式**

Redisson 提供了一个 `RRateLimiter` 类，它基于令牌桶算法实现了分布式限流功能。通过这个类，开发者可以轻松地设置限流规则，并控制请求速率。

核心方法：
- `trySetRate(RRateLimiter.RateType type, long rate, long interval, RateIntervalUnit unit)`：设置限流速率，指定单位时间内的令牌生成速率。
- `acquire()`：获取一个令牌，如果有令牌则通过，否则阻塞直到有可用令牌。
- `tryAcquire()`：尝试获取一个令牌，立即返回结果（不会阻塞）。

示例代码：
```java
import org.redisson.Redisson;
import org.redisson.api.RRateLimiter;
import org.redisson.api.RedissonClient;
import org.redisson.config.Config;

public class RedissonRateLimiterExample {

    public static void main(String[] args) {
        // 配置 Redis 连接
        Config config = new Config();
        config.useSingleServer().setAddress("redis://127.0.0.1:6379");

        // 创建 Redisson 客户端
        RedissonClient redissonClient = Redisson.create(config);

        // 创建 RRateLimiter 对象
        RRateLimiter rateLimiter = redissonClient.getRateLimiter("myRateLimiter");

        // 设置限流速率：每秒最多允许10次请求
        rateLimiter.trySetRate(RRateLimiter.RateType.OVERALL, 10, 1, RateIntervalUnit.SECONDS);

        // 尝试获取一个令牌
        if (rateLimiter.tryAcquire()) {
            System.out.println("请求通过");
            // 处理逻辑
        } else {
            System.out.println("请求被限流");
        }

        // 关闭客户端
        redissonClient.shutdown();
    }
}
```

4. Redisson 分布式限流的优势

Redisson 基于 Redis 实现的分布式限流有以下几个优势：
- **高效**：Redis 是高性能的内存数据库，支持高并发请求，Redisson 利用 Redis 实现限流，可以快速响应请求。
- **分布式协调**：通过 Redis 共享限流状态，确保在分布式系统中，每个节点都遵循相同的限流规则。
- **原子操作**：Redis 内部通过 Lua 脚本实现的操作是原子的，保证限流操作的准确性。
- **易用性**：Redisson 提供了简单的 API，开发者可以快速集成限流功能。

5. Redisson 分布式限流的局限

虽然 Redisson 提供了强大的分布式限流功能，但也存在一些局限：
- **依赖 Redis**：限流逻辑依赖于 Redis，如果 Redis 出现故障，限流功能将无法工作，因此需要确保 Redis 的高可用性。
- **网络延迟**：限流请求需要访问 Redis，可能会产生网络延迟，尤其当 Redis 部署在远程服务器时，这种延迟更为明显。
- **Redis 压力**：在高并发场景下，大量的限流操作会给 Redis 带来压力，可能需要对 Redis 进行扩容或优化。

6. Redisson 分布式限流的优化建议

为了更好地使用 Redisson 的限流功能，可以从以下几个方面进行优化：
- **Redis 集群部署**：为了提高 Redis 的可用性和处理能力，可以使用 Redis Cluster 部署，分散限流操作的压力。
- **本地缓存结合限流**：在执行分布式限流的基础上，使用本地缓存对某些请求进行限流处理，减少对 Redis 的依赖和访问次数。
- **动态限流策略**：根据业务需求，动态调整限流策略。例如，根据不同时间段或不同用户组，设置不同的限流阈值。

总结：Redisson 基于 Redis 的分布式限流提供了一种简单而高效的解决方案，适合在分布式系统中控制流量。通过合理设置限流策略，可以防止系统被流量冲垮，同时确保服务的稳定性。

---

限流是系统设计中的重要组成部分，无论是本地限流还是分布式限流，都有其适用的场景。通过合理选择限流算法、工具和策略，结合系统的实际需求，可以确保系统在面对高并发、流量激增时依然保持稳定和高效。

---

##### 项目中的实现

```java
/**
 * 专门提供 RedisLimiter 限流基础服务的（提供了通用的能力）
 */
@Service
public class RedisLimiterManager {

    @Resource
    private RedissonClient redissonClient;

    /**
     * 限流操作
     *
     * @param key 区分不同的限流器，比如不同的用户 id 应该分别统计
     */
    public void doRateLimit(String key) {
        // 创建一个名称为user_limiter的限流器，每秒最多访问 2 次
        RRateLimiter rateLimiter = redissonClient.getRateLimiter(key);
        rateLimiter.trySetRate(RateType.OVERALL, 2, 1, RateIntervalUnit.SECONDS);
        // 每当一个操作来了后，请求一个令牌
        boolean canOp = rateLimiter.tryAcquire(1);
        //确定拿到了令牌
        if (!canOp) {
            throw new BusinessException(ErrorCode.TOO_MANY_REQUEST);
        }
    }
}
```



## 消息记录

当任务执行成功失败，可以有很多种方式记录，一种是直接实时通知用户，采用WebSocket，另外一种就是最简单的，直接采用数据库记录服务状态。

#### 优化点

**目前的本地队列不够健壮，不够适合用于分布式场景，没有进行消息持久化。**

# 异步化

**并不是所有的业务场景都适用异步操作，异步化的过程中对线程池的设计，线程处理会增加代码的复杂度，如果同步能解决的需求，就用同步实现**

![image-20241009222822024](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241009222822024.png)

异步的业务分析流程

![image-20241009223057464](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241009223057464.png)

![image-20241009223843600](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241009223843600.png)

## 线程池

作用：帮助你轻松管理线程，协调任务执行过程。

- 多个任务争抢进程
- 队列满了怎么办：拒绝策略，记录消息到数据库？
- 线程的最大线程数是多少？



**难，而且很多**

👾 **启动“线程池知识解析模式”...** 🧑‍💻

**线程池** 是并发编程中的重要概念，常用于提高应用程序性能，优化资源利用。通过线程池，系统可以复用线程，避免频繁创建和销毁线程带来的性能开销，并且通过控制并发量来确保系统的稳定性。

---

**1. 什么是线程池？**

**线程池** 是一个多线程管理工具，维护着多个可复用的线程实例。它的核心思想是提前创建一定数量的线程，当有任务时从线程池中获取可用线程来执行，而不是每次都新建线程。当任务完成后，线程不会销毁，而是返回线程池中待命，继续为后续任务服务。

线程池解决了以下问题：
- **避免频繁创建和销毁线程**：线程的创建和销毁是昂贵的操作，通过复用线程提升了性能。
- **限制系统中的并发线程数**：防止因为创建过多线程导致系统资源（CPU、内存）耗尽，确保系统稳定运行。
- **任务管理与调度**：通过排队机制管理大量任务，防止瞬间的大量任务对系统造成冲击。

---

**2. 线程池的优点**

- **降低资源消耗**：通过复用线程来降低线程创建和销毁的资源消耗。
- **提高响应速度**：任务可以不用等待线程创建，直接从池中获取现成的线程，提升了响应速度。
- **提升线程管理的可控性**：线程池可以通过配置控制线程的最大数量，避免过多线程影响系统性能。
- **任务调度能力**：线程池可以管理任务队列，避免任务超载，并提供灵活的任务调度策略。

---

**3. Java 线程池的实现**

在 Java 中，**`java.util.concurrent`** 包提供了线程池的实现，核心类是 **`ThreadPoolExecutor`**。此外，Java 提供了多种工具类来方便管理和创建线程池。

常用的线程池实现：
- **`FixedThreadPool`**：固定大小的线程池。
- **`CachedThreadPool`**：根据需求动态调整线程数量的线程池。
- **`ScheduledThreadPool`**：支持定时或周期性任务的线程池。
- **`SingleThreadExecutor`**：单线程的线程池。

这些线程池可以通过 **`Executors`** 工具类快速创建。

---

### **4. 线程池的核心参数**

**`ThreadPoolExecutor`** 是 Java 线程池的核心实现，提供了高度的灵活性。它的构造函数包含多个关键参数：

```java
public ThreadPoolExecutor(
    int corePoolSize,        // 核心线程数
    int maximumPoolSize,     // 最大线程数
    long keepAliveTime,      // 非核心线程空闲的存活时间
    TimeUnit unit,           // 时间单位
    BlockingQueue<Runnable> workQueue, // 任务队列
    ThreadFactory threadFactory,       // 线程工厂
    RejectedExecutionHandler handler   // 拒绝策略
)
```

**关键参数说明**：

1. **`corePoolSize`**（核心线程数）：线程池中始终保留的最小线程数，**即这些线程处于空闲状态。核心线程会在任务到来时立刻参与执行**。也就是最少能够处理的线程，随时能够处理
2. **`maximumPoolSize`**（最大线程数）：线程池能够容纳的最大线程数。**在任务负载很高时，会在核心线程数的基础上动态扩展线程数，直到达到最大线程数**。**最大线程数要考虑实际的负载能力**。
3. **`keepAliveTime`**（非核心线程存活时间）：当线程池中的线程数超过核心线程数时，超出的空闲线程会在 `keepAliveTime` 时间后被回收。
4. **`workQueue`**（任务队列）：**当所有核心线程都在执行任务时，新的任务会被放入 `BlockingQueue` 中等待执行**。常见的任务队列有：
   - **`SynchronousQueue`**：不会存储任务，每个任务必须直接交给线程执行。
   - **`LinkedBlockingQueue`**：有界队列，适用于**有界任务**的场景。
   - **`ArrayBlockingQueue`**：固定大小的有界队列，适用于控制请求量的场景。
5. **`threadFactory`**（线程工厂）：用于创建线程，允许自定义线程的创建方式，如给线程命名等。
6. **`handler`**（拒绝策略）：当任务数量超过线程池的处理能力时，任务会被拒绝。常见的拒绝策略有：
   - **`AbortPolicy`**：直接抛出异常（默认）。
   - **`CallerRunsPolicy`**：由调用线程执行该任务。
   - **`DiscardPolicy`**：直接丢弃任务。
   - **`DiscardOldestPolicy`**：丢弃队列中等待时间最久的任务。

---

**5. 常见的线程池类型**

Java 提供了几个常见的线程池类型，可以通过 **`Executors`** 工具类方便创建：

- **FixedThreadPool**：固定大小的线程池。
  - 特点：线程数量固定，适合负载均衡且任务较多的场景。核心线程不会被回收。
  - 创建方法：
    ```java
    ExecutorService fixedThreadPool = Executors.newFixedThreadPool(10);
    ```

- **CachedThreadPool**：可缓存的线程池，线程数量动态调整。
  - 特点：当任务多时创建新线程，当任务少时回收空闲线程。适合短时间并发量高但任务较轻的场景。
  - 创建方法：
    ```java
    ExecutorService cachedThreadPool = Executors.newCachedThreadPool();
    ```

- **ScheduledThreadPool**：支持定时、周期性任务的线程池。
  - 特点：适合周期性任务调度，内部实现类似于 `FixedThreadPool`，但支持延迟执行和周期执行。
  - 创建方法：
    ```java
    ScheduledExecutorService scheduledThreadPool = Executors.newScheduledThreadPool(5);
    ```

- **SingleThreadExecutor**：单线程的线程池。
  - 特点：保证任务按顺序执行，适合需要严格顺序执行的任务场景。
  - 创建方法：
    ```java
    ExecutorService singleThreadExecutor = Executors.newSingleThreadExecutor();
    ```

---

**6. 线程池的工作流程**

线程池的工作流程可以总结为以下几个步骤：

1. **提交任务**：将 `Runnable` 或 `Callable` 任务提交到线程池。
2. **检查核心线程**：线程池首先检查是否有空闲的核心线程，如果有，则直接使用核心线程执行任务。
3. **任务入队**：如果所有核心线程都在忙碌，任务会被放入任务队列中等待执行。
4. **扩展线程**：如果队列已满且任务负载持续增长，线程池会动态创建非核心线程，直到达到最大线程数。
5. **拒绝策略**：当任务数量超过了最大线程数，并且任务队列也已满，线程池执行拒绝策略。

---

**7. 线程池的使用场景**

- **高并发场景**：通过线程池可以在高并发场景下有效控制线程数量，防止系统过载。
- **定时任务**：`ScheduledThreadPool` 非常适合执行定时或周期性的任务，比如定期备份数据、定时清理缓存等。
- **IO 密集型任务**：线程池适合用于处理大量 IO 操作，如数据库查询、文件读写、网络请求等任务。
- **CPU 密集型任务**：针对 CPU 密集型任务，线程池可以通过合理配置线程数，使 CPU 利用率最大化。

---

**8. 线程池的优化与注意事项**

1. **合理配置线程池大小**：
   - 对于 **CPU 密集型** 任务，线程池大小一般设置为 `CPU 核心数 + 1`，使每个线程都能充分利用 CPU。
   - 对于 **IO 密集型** 任务，由于 IO 操作会导致线程等待，可以适当增加线程池的线程数，如 `2 * CPU 核心数`。

2. **使用合适的任务队列**：
   - **无界队列**（如 `LinkedBlockingQueue`）适合处理大量任务，但要小心内存溢出风险。
   - **有界队列**（如 `ArrayBlockingQueue`）可以有效控制系统负载，但要配置合适的大小。

3. **合理处理拒绝策略**：
   - 默认的拒绝策略是抛出异常，开发者可以根据业务需求选择其他策略，比如丢弃任务或将任务交由调用者执行。

4. **线程池关闭**：
   - 在线程池不再使用时，应调用 **`shutdown()`** 方法关闭线程池，确保资源回收。

5. **避免死锁**：
   - 在线程池中执行任务时，如果任务之间存在相互依赖，可能会引发死锁。因此

### 工作机制详细介绍

👾 **启动“线程池工作机制解析模式”...** 🧑‍💻

线程池的工作机制是通过合理的线程管理、任务调度和资源分配，来确保系统在高并发场景下高效执行任务。其核心原理是通过**复用线程**，避免频繁创建和销毁线程带来的开销，并通过**任务队列**和**线程管理**来确保任务能够按照预定策略高效执行。

下面是线程池的**核心工作机制**，从任务提交到任务执行的整个流程：

---

**1. 任务提交阶段**

- 当我们将一个任务提交给线程池时，线程池并不会立即创建新线程来执行该任务，而是先根据其内部的调度机制来判断该如何处理任务。任务一般是通过实现 `Runnable` 或 `Callable` 接口的对象提交给线程池。

- 任务提交的方式通常有两种：
  1. **`execute(Runnable task)`**：提交不需要返回结果的任务。
  2. **`submit(Callable task)`**：提交需要返回结果的任务。

---

**2. 线程池的核心组件**

线程池的工作机制由以下几个**核心组件**来支撑，它们协同工作完成任务的调度和执行：

- **核心线程数 (`corePoolSize`)**：这是线程池在空闲时保持的最小线程数。当任务到来时，优先启用这些核心线程来处理任务。

- **最大线程数 (`maximumPoolSize`)**：线程池在任务高峰时能够扩展的最大线程数。如果任务队列中的任务过多，且核心线程无法及时处理，则线程池会创建新的线程，直到达到最大线程数。

- **任务队列 (`BlockingQueue<Runnable>`)**：用于存放等待执行的任务。如果所有的核心线程都在忙碌，新任务会被放入队列，等待空闲线程处理。

- **线程存活时间 (`keepAliveTime`)**：这是非核心线程在空闲状态下的存活时间。当非核心线程空闲超过这个时间后，线程池会回收这些线程，避免资源浪费。

- **线程工厂 (`ThreadFactory`)**：负责创建新线程，可以自定义线程属性（如线程名称）。

- **拒绝策略 (`RejectedExecutionHandler`)**：当任务队列已满且线程数量达到最大限制时，线程池无法处理新的任务，此时会触发拒绝策略。

---

**3. 线程池的任务处理流程**

线程池的处理流程可以概括为以下几个步骤：

1. **任务提交到线程池**：
   - 任务首先被提交到线程池。线程池会优先检查当前的核心线程数。

2. **核心线程处理**：
   - 如果当前线程池中的线程数少于 `corePoolSize`，线程池将**直接创建新的核心线程**来处理这个任务，而不会将其放入任务队列。

3. **任务入队**：
   - 如果当前核心线程数已经达到 `corePoolSize`，且所有核心线程都在忙碌，那么新任务会被放入**任务队列**（例如 `LinkedBlockingQueue`）。
   - 任务队列等待线程从中取出任务执行。

4. **非核心线程处理**：
   - 如果任务队列满了，且线程池的线程数量还没有达到 `maximumPoolSize`，线程池会继续创建**非核心线程**来处理任务，直到线程数量达到 `maximumPoolSize`。
   
5. **拒绝策略**：
   - 当任务队列已满，并且线程池中的线程数已经达到 `maximumPoolSize`，线程池将根据配置的**拒绝策略**处理新提交的任务。常见的策略包括：
     - 抛出异常（默认）。
     - 丢弃任务。
     - 丢弃最早的任务。
     - 由调用线程执行任务。

6. **任务执行**：
   - 当有线程（核心线程或非核心线程）可用时，任务从队列中取出并执行。任务执行完成后，线程会继续从队列中取下一个任务。
   - 如果线程池中的线程是非核心线程，并且在 `keepAliveTime` 期间没有新的任务进来，该线程将被销毁。

---

**4. 线程池的状态转换**

线程池的工作机制中，还涉及到线程池本身的**状态管理**，以确保线程池的合理运行。线程池有五种状态：

1. **RUNNING**：这是线程池的默认状态，能够接受新的任务并处理任务队列中的任务。
2. **SHUTDOWN**：调用 `shutdown()` 方法后，线程池进入此状态，停止接受新任务，但会继续执行已提交的任务。
3. **STOP**：调用 `shutdownNow()` 后，线程池进入 STOP 状态，会尝试中断正在执行的任务，并清空任务队列。
4. **TIDYING**：当所有任务完成，线程池线程数为 0 时，进入此状态。
5. **TERMINATED**：线程池完全终止的状态。

---

**5. 线程池的拒绝策略**

线程池在极端情况下，无法处理所有提交的任务，这时就会使用**拒绝策略**。常见的拒绝策略如下：

1. **AbortPolicy**（默认）：直接抛出 `RejectedExecutionException` 异常，阻止系统继续提交新任务。
2. **CallerRunsPolicy**：直接由提交任务的线程来执行任务，这样能够降低新任务的提交速率，适用于缓解压力的场景。
3. **DiscardPolicy**：静默丢弃无法处理的任务，不抛出任何异常，适合不关心任务处理失败的场景。
4. **DiscardOldestPolicy**：丢弃队列中最早的未处理任务，然后尝试执行新的任务。

---

**6. 线程池中的任务队列**

线程池使用任务队列来存储待处理的任务，根据不同场景和需求，可以选择不同类型的队列：

1. **`SynchronousQueue`**：每个插入操作必须等待相应的删除操作，适合需要直接交给线程处理的任务，通常与 `CachedThreadPool` 结合使用。

2. **`LinkedBlockingQueue`**：一个基于链表实现的有界（或无界）阻塞队列。适合任务数量不可预估，但希望限制任务队列大小的场景，默认用于 `FixedThreadPool`。

3. **`ArrayBlockingQueue`**：一个基于数组的有界阻塞队列，适合控制任务队列大小，防止系统过载的场景。

4. **`PriorityBlockingQueue`**：基于优先级的阻塞队列，任务按照优先级进行调度，适合需要区分任务优先级的场景。

---

**7. 线程池工作机制的关键点**

1. **任务优先通过核心线程执行**：核心线程是线程池中始终存在的线程，保证了一定的基础处理能力。只有核心线程都在执行任务时，任务才会进入队列。

2. **非核心线程的动态扩展**：当任务负载增加且队列满时，线程池会创建非核心线程来执行任务，但这部分线程会根据 `keepAliveTime` 设置在空闲一段时间后自动销毁。

3. **任务队列的作用**：任务队列是线程池的缓冲区，用来存放当前没有可用线程处理的任务，避免因创建大量线程而导致系统资源耗尽。

4. **拒绝策略保障系统稳定性**：通过拒绝策略，线程池可以优雅地应对任务过载情况，确保系统不会因为过量请求而崩溃。

5. **线程复用**：线程池的核心思想是线程复用，避免了每次任务提交都新建线程的高成本操作，从而提升了应用的性能和响应速度。

---

**总结**

线程池通过**复用线程**、**任务队列管理**以及**动态扩展线程**，可以有效提升并发任务的处理能力，减少频繁创建销毁线程带来的开销。它采用了灵活的配置参数和拒绝策略，能够适应不同的并发场景需求。理解其工作机制有助于我们在高并发场景下合理设计系统，避免资源浪费并提升系统的稳定性。

### 小总结

- **为什么这个项目要使用线程池？**

主要原因还是本次的场景时调用ai服务，调用的速度较慢，考虑木桶效应，对系统较为薄弱的环节添加上线程池。



- 怎么确定线程池参数？

总的还是根据业务不断调试。



**工作机制的总结**

- 当工作队列满的时候，且核心线程都已经被占用，这时候会再将消息放入等待队列

- 如果等待队列也满了，这个时候就会使用线程工厂来增加非核心线程数，直到增加到最大线程数

  

  ![image-20241010000317018](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241010000317018.png)

  



### 编码实现

- 线程池

```java
@Configuration
public class ThreadPoolExecutorConfig {

    @Bean
    public ThreadPoolExecutor threadPoolExecutor() {
        ThreadFactory threadFactory = new ThreadFactory() {
            private int count = 1;

            @Override
            public Thread newThread(@NotNull Runnable r) {
                Thread thread = new Thread(r);
                thread.setName("线程" + count);
                count++;
                return thread;
            }
        };
        ThreadPoolExecutor threadPoolExecutor = new ThreadPoolExecutor(2, 4, 100, TimeUnit.SECONDS,
                new ArrayBlockingQueue<>(4), threadFactory);
        return threadPoolExecutor;
    }
}
```

- 队列实现

```java
@Resource
private ThreadPoolExecutor threadPoolExecutor;

@GetMapping("/add")
public void add(String name) {
    CompletableFuture.runAsync(() -> {
        log.info("任务执行中：" + name + "，执行人：" + Thread.currentThread().getName());
        try {
            Thread.sleep(600000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }, threadPoolExecutor);
}

@GetMapping("/get")
public String get() {
    Map<String, Object> map = new HashMap<>();
    int size = threadPoolExecutor.getQueue().size();
    map.put("队列长度", size);
    long taskCount = threadPoolExecutor.getTaskCount();
    map.put("任务总数", taskCount);
    long completedTaskCount = threadPoolExecutor.getCompletedTaskCount();
    map.put("已完成任务数", completedTaskCount);
    int activeCount = threadPoolExecutor.getActiveCount();
    map.put("正在工作的线程数", activeCount);
    return JSONUtil.toJsonStr(map);
}
```

## 异步调用

异步调用ai服务

![image-20241010222714660](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241010222714660.png)

第二步，添加表格数据的状态

调用ai前更改为执行中

![image-20241010223027786](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241010223027786.png)

等线程执行完毕在更改图表状态的情况

![image-20241010223114826](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241010223114826.png)

### 优化思路

通过第三方调用的服务状态来选择当前系统的策略，就是反向压力

![image-20241010224051797](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241010224051797.png)

# 消息队列

目前的项目仍然存在一些问题



![image-20241015160316259](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241015160316259.png)

使用消息队列进行应用解藕

![  ](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241015160430960.png)

## 优势

实现的是生产者和消费者之间的互不影响，解耦的作用

![image-20241015160957384](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241015160957384.png)

![image-20241015161304042](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241015161304042.png)

1. **解耦（Decoupling）**  
- **特点**：消息队列通过引入一个中间消息代理，使得**消息的生产者和消费者解耦**，即它们不需要直接相互依赖。这意味着，生产者不需要知道消费者的具体实现，只要把消息放入队列，消费者可以在合适的时间自行处理消息。  
- **举例**：假设有一个订单处理系统，用户下单时，系统需要同时更新库存、通知物流、发送确认邮件。如果不使用消息队列，订单服务需要与多个其他服务（库存、物流、邮件）直接进行通信。引入消息队列后，订单系统只需将下单消息放入队列，库存服务、物流服务、邮件服务分别从队列中取出处理。即使某个服务发生故障，也不会影响订单系统的正常运行。  
- **场景**：电商平台的订单系统。下单后，可以通过消息队列将订单状态更新、库存减少、物流通知等操作异步执行，不阻塞用户的下单请求。

---

2. **异步处理（Asynchronous Processing）**  
- **特点**：消息队列允许生产者将消息发送到队列，而不必等待消费者处理完毕。这使得系统中的耗时操作可以被异步处理，避免阻塞调用方。生产者继续执行其他操作，而消费者可以在稍后的时间处理消息。  
- **举例**：用户上传一个视频到视频处理平台，平台需要对视频进行转换（例如，压缩成不同的分辨率），而这可能需要很长时间。如果系统直接处理这些任务，用户可能需要等待很久才能得到反馈。使用消息队列，上传操作可以立即返回成功，而视频处理服务可以异步从消息队列中读取任务并处理视频，用户可以在处理完毕后收到通知。  
- **场景**：视频网站中的视频处理系统。用户上传视频时，生成一个处理任务，将其放入队列，处理服务异步从队列中读取任务并处理。

---

3. **削峰填谷（Peak Shaving and Load Leveling）**  
- **特点**：在高并发场景下，系统的请求量可能瞬间激增，消息队列可以通过缓冲大量的请求，削减高峰期的流量压力。当流量峰值过后，系统可以逐渐从队列中处理剩余的请求，避免瞬时超载。  
- **举例**：在电商大促销时，用户请求量急剧增加，如果订单服务无法承受所有请求，会导致系统崩溃。引入消息队列后，可以将用户请求存放在队列中，订单服务可以根据自身的处理能力按顺序处理请求，避免系统过载。  
- **场景**：电商平台在促销活动期间，通过消息队列处理用户的下单请求，防止订单服务在短时间内被压垮，同时确保所有请求都能被处理。

## 分布式消息队列的优势

分布式消息队列在分布式系统中具有很多优势，它通过将消息存储在多个节点上，确保系统的可扩展性、可靠性和性能优化。以下是它的主要优势：

---

1. **高可用性与容错性**  
   - **特点**：分布式消息队列通过多节点部署，保证了系统的高可用性和容错性。当某个节点发生故障时，其他节点可以继续处理消息，确保系统不会因为单点故障（Single Point of Failure, SPOF）而中断服务。
   - **优势**：即使某一部分出现问题，系统仍然可以正常运行，提升了系统的稳定性和可靠性。

---

2. **可扩展性**  
   - **特点**：分布式消息队列可以通过增加节点来扩展系统的处理能力。这意味着，随着流量和消息量的增长，只需增加更多的消息队列节点来处理更多的负载。
   - **优势**：非常适合大规模、高并发的场景，能够灵活应对业务增长需求，轻松应对海量数据和高吞吐量。

---

3. **负载均衡**  
   - **特点**：分布式消息队列可以将消息的处理任务分配给多个消费者或多个节点，均匀分配负载，避免任何一个节点或服务压力过大。
   - **优势**：提升了系统整体的效率，防止局部过载，并确保所有消息都能及时处理，系统能够高效运行。

---

4. **数据持久化**  
   - **特点**：分布式消息队列通常支持消息的持久化，即将消息存储到磁盘或其他存储系统中，防止在消息传递过程中丢失数据。
   - **优势**：即使出现网络故障或系统崩溃，持久化的消息仍然能够被处理，保障消息的可靠交付。

---

5. **异步通信与解耦**  
   - **特点**：生产者和消费者之间通过消息队列进行异步通信，生产者发送消息到队列中即可，不需要等待消费者立即处理。消息队列充当中间件，使得生产者和消费者之间相互独立，彼此解耦。
   - **优势**：避免了强耦合，使系统设计更加灵活，可以自由扩展和修改服务，而不会影响整体架构。

---

6. **削峰填谷与流量控制**  
   - **特点**：在高并发或流量激增时，分布式消息队列能够充当缓冲区，将请求暂时存储在队列中，等系统有足够资源时再进行处理。
   - **优势**：防止系统在高峰期崩溃，同时确保所有请求都能被处理，有效平滑系统的负载波动。

---

7. **消息的顺序与一致性保证**  
   - **特点**：分布式消息队列可以配置为保证某些情况下消息的顺序处理或一致性。例如，Kafka 通过分区和偏移量机制来确保消息在某些场景下按照顺序处理。
   - **优势**：适用于需要严格顺序处理的应用场景，确保在分布式环境下消息处理顺序不乱。



分布式消息队列的主要优势在于**高可用性、可扩展性、容错性、负载均衡**和**异步解耦**，它可以应对高并发、大数据量的业务场景，同时保证系统的稳定性和消息的可靠传递。这使得分布式消息队列成为现代分布式系统和微服务架构中的关键组件。

### 发布订阅

这个是消息队列里面相对重要的概念

**如果是一个一个发送**，耗时是一方面，还有一个方面就是可能不知道有哪些应用需要通知，可能存在一些冗余的通知

![image-20241015162427513](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241015162427513.png)

![image-20241015162501996](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241015162501996.png)

系统直接发布通知，然后所有的子应用关注了这个订阅

![image-20241015162541754](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241015162541754.png)

## 消息队列的使用场景

![image-20241015162827094](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241015162827094.png)

## 消息队列的缺点
