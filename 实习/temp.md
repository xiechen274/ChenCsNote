

#### 初始数据

1. **第一轮（Turn 1）**（全员弃权）：
   - `Appraiser A`：`Psnweight = 0.5, Weight = 0.3`
   - `Appraiser B`：`Psnweight = 0.5, Weight = 0.3`
2. **第二轮（Turn 2）**（未弃权）：
   - `Appraiser C`：`Psnweight = 1.0, Weight = 0.4`
3. **第三轮（Turn 3）**（全员弃权）：
   - `Appraiser D`：`Psnweight = 1.0, Weight = 0.3`

#### 弃权标记：

- **第一轮（Turn 1）** 和 **第三轮（Turn 3）** 的考核人全员弃权。
- 弃权的轮次为 **Turn 1** 和 **Turn 3**。

------

### 逻辑步骤模拟

#### 1. 第一轮（Turn 1）：全员弃权

- 逻辑

  ：

  1. **计算总轮权重**：
     - `TurnWeight = 0.3`
  2. **分配给其他非弃权轮次**：
     - 计算总非弃权轮次权重：
       - **Turn 2**：`TotalOtherWeight = 0.4`
     - **第二轮（Turn 2）**的比例分配：
       - `ProportionalWeight = 0.4 / 0.4 × 0.3 = 0.3`
  3. **更新第二轮（Turn 2）的权重**：
     - `Appraiser C`：`Weight = 0.4 + 0.3 = 0.7`
  4. 标记 **第一轮** 为已处理：`processedTurns = {1}`。

------

#### 2. 第二轮（Turn 2）：未弃权

- **逻辑**：无弃权，跳过处理。

- 结果

  ：

  - 权重保持不变：
    - `Appraiser C`：`Psnweight = 1.0, Weight = 0.7`

------

#### 3. 第三轮（Turn 3）：全员弃权

- 逻辑

  ：

  1. **计算总轮权重**：
     - `TurnWeight = 0.3`
  2. **分配给其他非弃权轮次**：
     - 计算总非弃权轮次权重：
       - **Turn 2**：`TotalOtherWeight = 0.7`
     - **第二轮（Turn 2）**的比例分配：
       - `ProportionalWeight = 0.7 / 0.7 × 0.3 = 0.3`
  3. **更新第二轮（Turn 2）的权重**：
     - `Appraiser C`：`Weight = 0.7 + 0.3 = 1.0`
  4. 标记 **第三轮** 为已处理：`processedTurns = {1, 3}`。

------

### 结果数据

#### 第一轮（Turn 1）：

- 弃权，不影响最终结果。

#### 第二轮（Turn 2）：

- ```
  Appraiser C
  ```

  ：

  - `Psnweight = 1.0`
  - `Weight = 1.0`

#### 第三轮（Turn 3）：

- 弃权，不影响最终结果。



