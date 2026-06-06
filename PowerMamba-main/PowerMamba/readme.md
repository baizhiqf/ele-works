
The main script to be executed for running experiments is `run_longexp.py`. It coordinates the execution of various models and their hyperparameters across different datasets.

## How to use the scripts:

To run the experiments, you need to use the scripts located in the `scripts` folder. These scripts specify the parameters and configurations required for each model.

### Some Details of the Scripts:
- **Model Name** and **Dataset Directory**: These are the most critical elements inside each script. The features can be `M` which considers all the data and predicts for it; `s` will only consider the targeted data; and `Mm` will only predict for the last `c_out` column. If there is prediction data in your dataset, you should set `include_pred = 1`. The rest of the script contains hyperparameters.
#### `dictionaries` Directory Inside the `scripts` Directory:
For each dataset, you can define a dictionary which contains the following information:
- **`project_dict`**: If you have predictions for some of your columns, indicate it here. The key in the dictionary is the column name, and the values represent:
  - The historical data for that column.
  - The first column number where predictions start for that specific column. You can leave this as `{}` if you are not incorporating external predictions.
  - For example, in the following image, the first number in the dictionary should be the column number for the wind column, and the second one is the column number for the first prediction column, which corresponds to '1h pred'.

<div style="text-align: center; margin-top: 20px;">
    <div style="display: inline-block; text-align: center;">
        <img src="/pics/time_series.png" alt="Performance Results" style="width:400px; height:400px;">
        <p>An Example of how to incorporate the external prediction. For more information, please see the paper.</p>
    </div>
</div>


- **`Col_info_dict`**: Useful for reporting partial MSE. If you have columns that can be categorized (e.g., they are all prices for different regions or loads for different regions), specify them in this dictionary. The format is:
  - The first value is the index where that group of columns starts.
  - The second value is the number of columns in that group.
  - Ensure that columns belonging to the same group are adjacent to each other. If you don't want partial MSE, leave it as `{}`.

### Running Scripts:

To run a script, use the following command in the current directory:

```bash
sh ./directory_to_scripts/scripts/script_name.sh
```

Replace `script_name.sh` with the name of the script you want to execute. For instance, to run the PowerMamba script, use:

```bash
sh ./scripts/PowerMamba.sh
```

---

运行实验的主要脚本是 `run_longexp.py`。它负责协调各种模型及其超参数在不同数据集上的执行。

## 如何使用脚本（中文翻译）：

要运行实验，您需要使用位于 `scripts` 文件夹中的脚本。这些脚本指定了每个模型所需的参数和配置。

### 脚本的一些细节：
- **模型名称**和**数据集目录**：这些是每个脚本中最关键的元素。特征模式可以是 `M`（考虑所有数据进行预测）；`s`（仅考虑目标数据）；`Mm`（仅对最后 `c_out` 列进行预测）。如果您的数据集中包含预测数据，应设置 `include_pred = 1`。脚本的其余部分包含超参数。

#### `scripts` 目录下的 `dictionaries` 目录：
对于每个数据集，您可以定义一个字典，其中包含以下信息：
- **`project_dict`**：如果您对某些列有外部预测，请在此处指明。字典中的键是列名，值表示：
  - 该列的历史数据。
  - 该特定列的预测数据开始的第一个列号。如果您不集成外部预测，可以将其设为 `{}`。
  - 例如，在下图中，字典中的第一个数字应该是风能列的列号，第二个数字是第一个预测列的列号，对应于 '1h pred'。

<div style="text-align: center; margin-top: 20px;">
    <div style="display: inline-block; text-align: center;">
        <img src="/pics/time_series.png" alt="性能结果" style="width:400px; height:400px;">
        <p>如何集成外部预测的示例。更多信息请参见论文。</p>
    </div>
</div>


- **`Col_info_dict`**：用于报告部分MSE。如果您有可以分类的列（例如，它们都是不同地区的价格或不同地区的负荷），请在此字典中指定。格式为：
  - 第一个值是该组列开始的索引。
  - 第二个值是该组中的列数。
  - 确保属于同一组的列彼此相邻。如果您不需要部分MSE，可以将其设为 `{}`。

### 运行脚本：

要运行脚本，请在当前目录中使用以下命令：

```bash
sh ./directory_to_scripts/scripts/script_name.sh
```

将 `script_name.sh` 替换为您要执行的脚本名称。例如，要运行PowerMamba脚本，请使用：

```bash
sh ./scripts/PowerMamba.sh
```